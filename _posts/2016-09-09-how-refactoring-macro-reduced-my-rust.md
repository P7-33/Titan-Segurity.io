---
title: 'How refactoring a macro reduced my Rust project build time from 4 hours to 40sec'
date: 2020-01-20T04:53:00+01:00
draft: false
---

![](https://aws1.discourse-cdn.com/business5/uploads/rust_lang/original/2X/8/83e41956eccfd67ad6ff76f15a2c22e58db31d4f.svg "5 hours to compile macro, what can I do? - The Rust Programming Language Forum")  

I have a very large macro instantiation, which takes 4 or 5 hours to compile with Rust 1.40, so I'm looking to improve this unreasonably long build time.

The macro wasn't always this slow to build, it seems to have gotten slower with newer versions of Rust, although I haven't pinpointed the exact point it regressed, it was always still slower than I would have liked (I recall it was around 30 minutes in earlier versions, still uncomfortably long for new contributors). I have avoided modifying this file as long as I can to avoid the long recompilation on my system, but I plan to expand this macro in the near future, so it is time to finally tackle this compilation problem.

What can I do to reduce the multi-hour compile times for this macro?

Here is the file with the macro in question, for reference:  

[github.com](https://github.com/iceiix/stevenarella/blob/master/blocks/src/lib.rs)

```
 #![recursion_limit="600"] extern crate steven_shared as shared; use crate::shared::{Axis, Direction, Position}; use collision::Aabb3; use cgmath::Point3; use lazy_static::lazy_static; use std::collections::HashMap; pub mod material; pub use self::material::Material; pub use self::Block::*; pub trait WorldAccess { fn get_block(&self, pos: Position) -> Block; } 
```This file has been truncated. [show original](https://github.com/iceiix/stevenarella/blob/master/blocks/src/lib.rs)

The big macro is `define_blocks`.

Here's what I have tried so far:

**1\. Reduce the size of the macro instantiation**  
If I remove all but two of the "blocks" (definitions which the macro matches against), then a release build completes in less than a second. So the compile time is definitely correlated with the size of what I pass to the macro. I haven't bothered to gather more data points (number of blocks x time to build) and graph the relationship (exponential?), but it is clearly related.

This is the first thing I tried, confirming the macro is the cause of the slowdown. But I actually need to pass all those definitions to the macro, because that's what it is for.

I suppose I could rewrite this code by hand to not use macros. This could be one potential fix for the problem but I have a lot of functionality invested into this macro and would like to keep for now it if possible. Which brings me to:

**2\. Enable macro expansion tracing**  
Using the nightly [trace\_macros](https://doc.rust-lang.org/unstable-book/library-features/trace-macros.html) feature, with `trace_macros!(true)` before `define_blocks!()`.

Observing the trace output, the macro expansion completes in about 9 seconds. Not hours, so the problem must be elsewhere.

**3\. Profile the compiler**  
Building with the `-Z time-passes` rustc compiler flag described in [Guide to Rustc Development](https://rust-lang.github.io/rustc-guide/queries/profiling.html). Using the same optimization level as in the default release profile:

```
blocks $ cargo clean ; time cargo rustc -- -C 'opt-level=3' -Z time-passes 
```

Completed in 5 hours 9 minutes. The end of the output shows what is taking so long:

```
 time: 0.002 codegen passes [4gqa868n29dtlfbb] time: 0.652 LTO passes time: 0.075 codegen passes [473etbgnzq2x8af8] time: 3.476 LTO passes time: 4.218 LTO passes time: 4.255 codegen passes [22fyvf1uiha0mrri] time: 4.234 codegen passes [6ffwyc85r8r5jgh] time: 63.064 LTO passes time: 15574.417 codegen passes [2w3r8ppd44eh9kz5] time: 15707.329 LLVM passes time: 0.003 serialize work products time: 0.746 linking time: 15771.815 total Finished dev [unoptimized + debuginfo] target(s) in 263m 19s real 309m45.295s user 198m44.124s sys 14m54.290s 
```

15574.417 seconds spent in "codegen passes" from LLVM. This sounds optimization-related.

**4\. Compare optimization levels**  
No optimization, finishes in less than 2 minutes:

```
cargo clean ; time cargo rustc -- -C 'opt-level=0' -Z time-passes Finished dev [unoptimized + debuginfo] target(s) in 1m 41s 
```

Basic optimization, only 2 minutes:

```
cargo clean ; time cargo rustc -- -C 'opt-level=1' -Z time-passes Finished dev [unoptimized + debuginfo] target(s) in 2m 05s 
```

"Some" optimizations (opt-level=2) ran for 3.7+ hours and consumed 20 GB of memory before I killed the process, so I estimate it takes on the same order of magnitude as full optimizations (opt-level=3) as in the release build (5.15 hours). Whatever is causing the slowdown occurs with the optimization passes enabled at optimization level 2+.

**5\. Count lines of LLVM IR generated**  
Found this handy `cargo llvm-lines` tool here: [Improve compile time and executable size by counting lines of LLVM IR](https://users.rust-lang.org/t/improve-compile-time-and-executable-size-by-counting-lines-of-llvm-ir/14203)

When I run it on my project (in an debug build so it doesn't take forever), the top functions are:

```
 Compiling steven_blocks v0.0.1 (steven/blocks) Finished dev [unoptimized + debuginfo] target(s) in 1m 19s 151828 2 core::ops::function::FnOnce::call_once 43954 488 core::option::Option::map 24252 896 core::ptr::real_drop_in_place 19669 1 steven_blocks::Block::get_model 15834 39 alloc::raw_vec::RawVec::reserve_internal 14674 1 steven_blocks::Block::get_flat_offset 12548 1 steven_blocks::Block::get_hierarchical_data 12362 1 steven_blocks::Block::get_collision_boxes 11195 1 steven_blocks::Block::get_model_variant 9678 1 ::fmt 
```

The getters in Block are all macro-generated code that matches on `*self` to insert arbitrary expressions specific to the "block", for example this is get\_model:

```
 #[allow(unused_variables)] pub fn get_model(&self) -> (String, String) { match *self { $( Block::$name { $($fname,)? } => { let parts = $model; (String::from(parts.0), String::from(parts.1)) } )+ } } 
```

19669 is a lot of lines of IR, but I don't think this is incorrect. There really are that many expressions (currently 300, one for each block definition), each of varying complexity.

A possible angle of attack could be to try to rewrite the code with the goal of reducing the number of IR lines generated. Open to suggestions of how to do this. One idea is to replace the huge `match` generated code with a data structure, such as a HashMap. Mapping the keys should be straightforward (the block identifiers), but the values are arbitrary expressions dependent on other variables defined in the block definition. Which is why this was all generated by a macro in the first place. Would like to preserve this macro as-is if I can.

**6\. Reduce optimization level in sub-crate manifest**  
As the crate compiles 153x faster with basic optimizations, I thought I would settle for reducing the optimization level from the default full optimizations for the release profile, by adding this to `blocks/Cargo.toml`:

```
[profile.release] opt-level = 1 
```

This worked... when I tested the crate by itself. However, the crate is nested in another project, and it turns out the manifest profile configuration is actually ignored except at the top-level, as documented in [The Cargo Book](https://doc.rust-lang.org/cargo/reference/manifest.html#the-profile-sections):

> Cargo supports custom configuration of how rustc is invoked through profiles at the top level. Any manifest may declare a profile, but only the top level package’s profiles are actually read. All dependencies’ profiles will be overridden. This is done so the top-level package has control over how its dependencies are compiled.

If I reduce the optimization level at the top-level package, then building is fast as expected, but I want to optimize everything except this blocks-macro package as much as possible (in fact my program won't run properly without full optimizations, it is too slow). Only the crate with the gigantic `define_blocks!` macro builds slowly, so that's all I need to reduce the optimization level for, but it fails due to this rule.

**7\. Reduce optimization level in sub-crate config profile**  
Can dependencies have their own separate opt-level? Not yet, but [config profiles](https://doc.rust-lang.org/nightly/cargo/reference/unstable.html#config-profiles) should allow this in nightly, and as I understand it, [profile-overrides](https://github.com/rust-lang/cargo/pull/7591) will be in Rust 1.41.

First attempt, I placed this file in blocks/.cargo/config:

```
[profile.release] opt-level = 1 
```

and executed with `cargo +nightly build --release -Z config-profile`. But using the profile-overrides feature should work come 1.41 and it does work well in nightly, by adding this to the top-level Cargo.toml:

```
cargo-features = ["profile-overrides"] ... [profile.release.package.steven_blocks] opt-level = 1 
```

Finally, I have a decent workaround. I'll have to switch from stable to nightly, for the time being, and sacrifice the optimizations for this crate, but at least I can develop and iterate quickly.

Yet I am still left wondering, what exactly in LLVM optimization could be this slow? Is there anyway I can dig deeper into the 4 hour "codegen passes" phase? Is it possible to identify and disable or speedup the problematic optimization?

  
  
from Hacker News https://ift.tt/2RqolQ8