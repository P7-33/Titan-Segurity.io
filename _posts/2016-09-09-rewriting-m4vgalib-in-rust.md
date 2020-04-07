---
title: 'Rewriting M4vgalib in Rust'
date: 2020-01-01T10:55:00+01:00
draft: false
---

Rewriting m4vgalib in Rust
==========================

2019-02-23

If this isn't your first time visiting my blog, you may recall that I've spent the past several years building an [elaborate microcontroller graphics demo](http://cliffle.com/tags/glitch-demo/) using C++.

Over the past few months, I've been rewriting it — in [Rust](https://rust-lang.org/).

This is an interesting test case for Rust, because we're very much in C/C++'s home court here: the demo runs on the bare metal, without an operating system, and is very sensitive to both CPU timing and memory usage.

The results so far? **The Rust implementation is simpler, shorter (in lines of code), faster, and smaller (in bytes of Flash)** than my heavily-optimized C++ version — and because it's **almost entirely safe code,** several types of bugs that I fought regularly, such as race conditions and dangling pointers, are now caught _by the compiler._

It's fantastic. Read on for my notes on the process.

Executive summary
=================

*   The Rust tools and library ecosystem are fantastic. Simply having a package manager is an incredibly important advance.
    
*   When I am writing C++, I'm thinking about undefined behavior and bugs the compiler won't catch. When I'm writing Rust, I'm thinking instead about how to optimize things or add features. There is a very real [cognitive load](https://en.wikipedia.org/wiki/Cognitive_load) difference and it makes me more productive.
    
*   Rust's safety features, such as bounds checking, have caught bugs and have not caused performance problems. (With one exception, discussed below; in that case the fix was simple.)
    
*   The port revealed _significant subtle bugs in the C++ code_ when the Rust compiler wouldn't let me do certain things...that turned out to be legitimately incorrect things to do.
    

Motivation
==========

I wrote [m4vgalib](https://github.com/cbiffle/m4vgalib/) and the [attendant demos](https://github.com/cbiffle/m4vgalib-demos/) as an exercise in hard-real-time programming. I wanted to see how far I could push C++, so I avoided assembly language everywhere except certain routines that weren't possible without it.

Now, given my [feelings about C++](http://cliffle.com/blog/prefer-rust/), I want to see how far I can push Rust — specifically, safe Rust. See, despite having written C++ as my day job for many years, I'm aware that most of the common security/reliability bugs we see in software today are a result of flaws in the C and C++ languages. Rust fixes _essentially all of these flaws._ So I've been keeping an eye on it for a while. More reliable software with less work? _Yes please._

My graphics demos are so resource-constrained, and so timing-sensitive, that they fall squarely into the traditional domain of assembly and C — a domain that has been well-defended for years. Can I build the same thing using a memory-safe language? Could I use the additional brain-space that I'm _not_ spending on remembering C++'s initialization order rules (for example) to make a better system with more features?

The answer so far seems to be yes.

Rust has a package manager
==========================

This is a late addition to my notes, because I've gotten so used to it in languages like Rust, Haskell, Python...even JavaScript...that I had forgotten what a giant thing this is.

Programming languages fall into two categories: those that were designed before the advent of modern package managers[1](http://cliffle.com/blog/m4vga-in-rust/#packman), and those designed after. There's a very important difference between these two categories:

*   Pre-package-manager languages try to have an everything-plus-the-kitchen-sink standard library, and developers tend to avoid third-party libraries.
    
*   Post-package-manager languages go for a more minimal standard library, and developers are accustomed to extending it with packages.
    

In particular, C falls in the first category, and Rust falls in the second.

Adding a new third-party dependency to a C project is, at best, a giant pain. It might not support your build system, you're probably going to have to figure out some include-path magic, and it's almost certainly not built with the same linter settings. At worst, it might be using an incompatible subset of core language features, like exceptions vs. not. C programmers (myself included) tend to avoid such dependencies at all costs, _up to and including rewriting everything themselves._ ([Guilty.](https://github.com/cbiffle/etl/)) This is a huge drain on productivity and creates new bugs each time.

For contrast: there came a moment when porting my Conway's Game of Life implementation when I needed a random number generator, to seed the playing field. Rust's standard library _doesn't contain a random number generator._ Instead, I added a dependency on [the `rand` crate](https://crates.io/crates/rand/), let it automatically download and build, and continued programming.

I see the C++ community watching Rust and [trying to adapt our best features](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), but imagine what a standardized C++ build system and package manager would do for the language.

On `no_std`
===========

For bare-metal programming specifically, the _truly killer feature_ of Rust is the `no_std` ecosystem.

C++ has a monolithic standard library with an amazing set of cool stuff in it (because, as I noted in the last section, of when it was written). However, the library embeds some important assumptions. In particular, it is written for a "normal" C++ execution environment, which for our purposes means two things:

1.  There is a heap, and it's okay to allocate/free whenever.
2.  Exceptions are turned on.

In most high-reliability, hard-real-time embedded environments, neither of these statements is true. We eschew heaps because of the potential for exhaustion and fragmentation; we eschew exceptions because the performance of unwinding code is unpredictable and vendor-dependent[2](http://cliffle.com/blog/m4vga-in-rust/#exceptions).

Now, there are _parts_ of the C++ standard library that you can use safely in a no-heap, no-exceptions environment. Header-only libraries like `type_traits` are probably fine. Simple primitive types like `atomic` are ... probably fine?

I keep saying "probably" because the no-heap, no-exception subset of the C++ standard is _not clearly defined._ (The C++ standards folk have, in fact, resisted doing this, arguing that it would fragment the language; this ship has most definitely sailed.) As a result, it's really easy to _accidentally_ introduce a heap dependency, or to _accidentally_ use an API that can't indicate failure when exceptions are disabled (like `std::vector::push_back`).

The Rust standard library has a critical difference: it's divided into two parts, `std` and `core`. `std` is like the C++ equivalent. `core`, on the other hand, is how `std` itself is implemented, and _doesn't assume the existence of things like "the heap," threads, and the like._ While code depends on `std` by default, you can set an attribute, `no_std`, to request only `core`.

This is a tiny design decision with huge implications:

1.  By setting the `#[no_std]` attribute on a crate, you're opting out of the default dependency on `std`. Any attempt to use a feature from `std` is now a compile time error[3](http://cliffle.com/blog/m4vga-in-rust/#stderr) — but you can still use `core`.
    
2.  You can trust _other_ crates to do the same, so you can use third-party libraries safely if they, too, are `no_std`. Many crates are either `no_std` by default, or can have it enabled at build time.
    
3.  `core` is small enough that porting it to a new platform is easy -- significantly easier, in fact, than porting `newlib`, the standard-bearer for portable embedded C libraries.
    

For `m4vgalib` I rewrote almost all my dependencies to get a system that wouldn't throw or allocate. In Rust, I don't have to do that!

On API design
=============

Rust's ownership rules produce a sort of bizarro-world of API design.

*   Some (uncommon, but reasonable) API designs won't make it past the borrow checker. (In nearly every case, these are APIs that were _easy to use incorrectly_ in other languages.
    
*   Some API patterns that are grossly unsafe or unwise in other languages are routine in Rust because of lifetime checking.
    

As an example of the latter: it is common, and safe, to loan out stack-allocated data structures _to other threads_ with no runtime checks. (See: [scoped threads in crossbeam](https://docs.rs/crossbeam/0.7.1/crossbeam/thread/).)

Another: it is normal in Rust text-processing code to deal in `&str`, which is equivalent to a C++ `string_view`. Storing a `string_view` in C++ (say, in the heap) is an incredibly bad idea, because [it's easy for it to become a dangling pointer](https://github.com/isocpp/CppCoreGuidelines/issues/1038); C++ programs resort to defensive copying to avoid this. On the other hand, Rust programs routinely store `&str`, copying only when the borrow checker can't prove that the code is correct.

When this is working well, it can cause abstractions and complexity to dissolve.

Concrete example: `m4vgalib` (C++) lets applications provide custom _rasterizers_ that are invoked to generate pixel data. They are subclasses of the `Rasterizer` library class, which sports a single virtual member function (called — wait for it — `rasterize`). You register a `Rasterizer` with the driver by putting a pointer to it into a table. Once registered, the `Rasterizer` will have its `rasterize` function called from an interrupt handler once per scanline.

You, the application author, have some responsibilities to use this API safely:

1.  The `Rasterizer` object needs to hang around until you're done with it — it might be `static` or it might be allocated from a carefully-managed arena. Otherwise, the ISR will try to use dangling pointers, and that's bad.
    
2.  While the `Rasterizer` object is accessible by the ISR, it can be entered at _basically any time_ by code running at interrupt priority. Because we can't disable interrupts without distorting the display, this means that your application code that shares state with the `Rasterizer` (say, a drawing loop) needs to be written carefully to avoid data races. Commonly, this means double-buffering with a `std::atomic` flip signal...and some manually-inserted barriers...and some squinting and care to avoid accessing other state incorrectly.
    
3.  Before disposing of the `Rasterizer` object, you must un-register it with the driver. This prevents an ISR from dereferencing its dangling pointer, which, again, would be bad.
    

I recreated the C++ API verbatim in Rust, and immediately started to run into ownership issues. My internal monologue went something like this:

*   "Okay, here's a `Raster` trait and an implementation thereof."
    
*   "Hm. How can I pass a reference to this to an interrupt handler? In C++ I stuffed a pointer into a global variable, but Rust's the rules around `static` state seem to prevent that."
    
*   "Okay, I've built an abstraction (`IRef`) to enable that to be done safely; only it turns out I didn't actually want to give _all_ of the `Rasterizer` to the ISR, because I want to draw into its background buffer and make other state changes. It needs to be shared with the main rendering loop!"
    
*   "If I split the `Rasterizer` into two parts and give _one_ to the ISR, how do I communicate between them when it comes time to flip buffers? Do I need to pepper my code with `Cell` to do interior mutability?"[4](http://cliffle.com/blog/m4vga-in-rust/#cell)
    
*   "This feels a lot like the problem that [scoped threads](https://docs.rs/crossbeam/0.7.1/crossbeam/thread/) solves."
    
*   "...heeeeey, how do they implement this?"
    

Taking inspiration from crossbeam, I added code to loan a _closure_, rather than an object, to the ISR. Closures are fundamentally different, from an API perspective, because they can capture local state easily -- and that capture is visible to the borrow checker, to avoid races or dangling pointers.

In the end, the Rust API wound up being _very_ different: there is no `Rasterizer` trait, and there are no rasterizers. There are only functions. This makes new effects _much_ easier to write. For example, this one draws a red line that sweeps down the display at 60 pixels/second:

```
 let red\_line \= SpinLock::new(Wrapping(0)); vga.with\_raster( // The raster callback is invoked on every horizontal retrace to // provide new pixels. It runs in interrupt context. |line, tgt, ctx| { if line \== \*red\_line.lock() % 1024 { fill(tgt, RED); } else { fill(tgt, BLACK); } }, // The scope callback is executed to run application logic. As soon as // it returns, the raster callback is revoked from the ISR, so we know // that state is no longer shared with interrupts. |vga| loop { vga.sync\_to\_vblank(); \*red\_line.lock\_mut() += 1; }) 
```

This makes the problem of sharing state trivial: have the state in scope when you declare these closures, and share it using normal Rust techniques.

In addition to being easier to use, this API is also much harder to _misuse_: it's essentially impossible to accidentally introduce a data race. This is because the raster callback is required to be `Send`, meaning it can safely be transferred across threads (or, here, to an interrupt handler, which is like a second thread). If the closure had captured some state that _isn't_ thread-safe, like a simple `mut` local variable or a `Cell`, it is a compile error. (`SpinLock` in the code above is thread-safe.)

As of C++11, C++ has closures with captures. You could almost implement this same API in `m4vgalib`. But I wouldn't, because...

*   **It wouldn't be robust.** Capturing stack structures by reference creates a real risk that you'll accidentally leak the reference into a larger scope, e.g. by storing it in a global or member field of a long-lived object. Plus, C++'s type system doesn't have any notion of thread-safety, so nothing would stop you from sharing a non-threadsafe structure with the ISR. It's all [footguns](https://en.wiktionary.org/wiki/footgun).
    
*   **It might require allocations.** In Rust, the ISR invokes the closure generically through the `FnMut` trait that all closures implement. In C++, there is no direct equivalent; closures do not have vtables, but must be wrapped in a heap-allocated `std::function` to be used dynamically. (In Rust, closures also do not have vtables, because we don't do virtual dispatch the same way. That's a longer story.)
    

On binary size
==============

Rust has a reputation for producing larger binaries than C++. This reputation appears to be undeserved.

If you run a release build of one of the demos and run `size`, you will find binaries that are larger than their C++ equivalents. For example, here's a comparison of `horiz_tp` written in each language:

```
  text data bss dec hex filename 4463 16 179688 184167 2cf67 cpp/horiz\_tp 21010 92 180872 201974 314f6 rust/horiz\_tp 
```

**This comparison is misleading.** The C++ codebase goes to some length to avoid including extraneous material in Flash — in particular, it compiles out all assert messages. Rust, on the other hand, is built with support for stack unwinding and panic messages. (Why? Because Rust came with support for funneling those messages over JTAG and into my debugger through the processor's ITM block. C++ had no such support, so I didn't waste the Flash.)

But this means each binary contains all the panic strings, plus all the message formatting code. If you would like to produce smaller binaries, and are willing to sacrifice panic messages, you need to build with a different feature set:

```
 $ cargo build --release --no-default-features --features panic-halt 
```

In this mode, the binaries are much smaller:

```
 text data bss dec hex filename 4366 104 180860 185330 2d3f2 horiz\_tp 4404 104 180796 185304 2d3d8 xor\_pattern 6688 104 180152 186944 2da40 conway 
```

In fact, _the binaries are 3-9% smaller than in C++,_ despite compiling the C++ with `-Os` and the Rust with (the equivalent of) `-O3`.

Size has not been a issue for this project.

On memory safety
================

I'm currently using `unsafe` in 35 places. _None of them are for Rust-specific performance reasons._ (I say "Rust-specific" because some of them are calling into assembly routines, which definitely exist for performance reasons, but are identical in C++.)

The majority of `unsafe` code (**13 instances**) is related to a class of API deficits in the `stm32f4` device interface crate I'm using. It treats any field in a register for which it doesn't have defined valid bit patterns as potentially unsafe... and then fails to define most of the register fields I'm using. Not sure why. I imagine this can be fixed. (I've already upstreamed part of the fix.)

After that, the leading causes are situations that are _inherently_ unsafe. In these cases the right solution is to wrap the code in a neat, safe API (and I have):

*   5 cases: Getting exclusive references to shared mutable global data, which is super racy unless you're careful.
*   4 cases: Calling into assembly code, which can do literally whatever it wants and so must be handled carefully.
*   4 cases: Managing the DMA controller, which is basically a peripheral for doing unsafe memory things.
*   3 cases: Implementing custom mutex-like types.
*   2 cases: Setting up the CPU and hardware environment.
*   2 cases: Doing something scary with `core::mem::transmute` to implement an inter-thread reference sharing primitive:

_These are the reason `unsafe` exists:_ so that I can do these things without having to change languages or use assembler. (Note that unsafe Rust is still a more featureful place than safe C.)

This leaves two `unsafe` uses that can likely be fixed:

*   Taking a very lazy shortcut with `core::mem::transmute` that can probably be improved.
*   Deliberately aliasing a `[u32]` as `[u8]`, which is memory-safe but endian-sensitive.

If you wanted to check every potential source of memory and data race bugs in the Rust codebase, you would need to review these 35 locations; you can find them all trivially using `grep`. To perform the same review in `m4vgalib`, you would be reading **10,692 lines of unsafe code.** That is, every C++ statement that I wrote.

Bounds checks
=============

I can't bring up memory safety without someone taking a potshot at Rust's bounds checking for arrays. Since `m4vga` demands pretty high performance, I've been auditing the machine code produced by `rustc`.

In the performance critical parts of the code, bounds checks were either _already eliminated at compile time,_ or could be eliminated by a simple refactoring of the code.

_The demos spend effectively no time evaluating bounds checks._

There are two relevant patterns in the current code.

First: in Rust, we can pass a fixed-length array by reference _without it degrading into a pointer as it does in C._ For instance,

```
 fn get\_element\_3(array: \[u8; 10\]) -> u8 { // This bounds check is trivially proven and will not be // performed at runtime.  array\[3\] } // This attempt to pass a 2-element array is a compile // error. get\_element\_3(\[0; 2\]); 
```

Neither of those statements holds in C. As a result, we use fixed-length arrays in several places in the demo where we didn't in C++.

Second, if the length of an array is known (to us, the programmer) but not _known_ (to the poor compiler), we can hoist bounds checks to a convenient place. For instance, this routine as written performs runtime bounds checks at each loop iteration:

```
 // Note that the array is a slice of runtime-determined length. fn fill\_1024(array: &mut \[u8\], color: u8) { for i in 0..1024 { array\[i\] \= color; } } 
```

We can check the length outside the loop, and make the length visible to the compiler, like this:

```
 fn fill\_1024(array: &mut \[u8\], color: u8) { // Perform an explicit, checked, slice of the array before // entering the loop. let array \= &mut array\[..1024\]; for i in 0..1024 { array\[i\] \= color; } } 
```

On safety from data races
=========================

Most of the actual _thinking_ that I had to do during the port — as opposed to mechanically translating C++ code into Rust — had to do with ownership and races.

(This won't surprise anyone who remembers learning Rust.)

`m4vga` is a prioritized preemptive multi-tasking system: it runs application code at the processor's Thread priority, and interrupts it with a collection of three interrupt service routines that generate video.

And, to keep things interesting, they all share data with each other. There's potential for all manner of interesting data races. (And believe me, most of them happened during the development of the C++ codebase.)

The C++ code uses a data race mitigation strategy that I call _convince yourself it works once and then hope it never breaks._ (I can use a snarky name like that because I'm talking about work _I did._) In a couple of places I used `std::atomic` (or my own intrinsics, before `atomic` stabilized — yes, this code is old), and in others I relied on the assumption that I was running on an Cortex-M3/M4 and crossed my fingers.

I could certainly use the same strategy in Rust by employing `unsafe` code. But that's boring.

Instead, I figured out which pieces of data were shared between which tasks, grouped them, and wrapped them with custom bare-metal mutex types. Whenever a thread or ISR wants to access data, it locks it, performs the access, and unlocks it. This costs a few cycles more than the C++ "hold my beer" approach, but that hasn't been an issue even in the latency-sensitive parts of the code.

Because of Rust's ownership and thread-safety rules, you can _only_ share data between threads and ISRs if it's packaged in one of these thread-safe containers. In Rust terms, the containers convert a type that is `Send`, or safe to move _between_ threads but not safe to use _concurrently_, into a type that is `Sync`, or safe for concurrent use. If you add some new data and attempt to share it without protecting it, your code will simply not compile. This means _I don't have to think about data races_ except when I'm hacking the internals of a locking primitive, so I can think about other things instead.

On lock contention, we `panic!`. This is a hard-real-time system; if data isn't available on the cycle we need it, the display is going to distort and there's no point in continuing. Late data is wrong data, after all. Using Rust's `panic!` facility has the pleasant side effect of printing a human-readable error message on my debugger (thanks to the `panic_itm` crate).

So far two interesting side effects have come up:

1.  Having to think about task interactions has led to a much better factoring of the driver code, which was initially laid out like the C++ code.
    
2.  I found an actual bug _that also exists in the C++ code_. There was a subtle data race between rasterization and the start-of-active-video ISR. I caught it and fixed it in the Rust. I haven't yet updated the C++ (because meh... it would just regress.)
    

[#c++](http://cliffle.com/tags/c/) [#embedded](http://cliffle.com/tags/embedded/) [#graphics](http://cliffle.com/tags/graphics/) [#rust](http://cliffle.com/tags/rust/)

  
  
from Hacker News https://ift.tt/2sE04xH