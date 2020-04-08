---
title: 'A More Natural Stackless Coroutine in C That Maintains Local Variables'
date: 2019-12-03T05:47:00+01:00
draft: false
---

I've discussed a stackful coroutine implementation to coordinate CUDA stream [last year](https://liuliu.me/eyes/coroutine-to-coordinate-cuda-streams/).

That was an implementation based on `swapcontext` / `makecontext` APIs. Increasingly, when I thought about porting [nnc](https://libnnc.org) over to WASM, it becomes problematic because these APIs are more or less deprecated. Popular libc implementations such as [musl](https://www.musl-libc.org/) don't have implementation of these methods.

After the [article](https://liuliu.me/eyes/coroutine-to-coordinate-cuda-streams/), it became obvious that I cannot `swapcontext` into the internal CUDA thread (that thread cannot launch any kernels). Thus, the real benefit of such stackful coroutine is really about convenience. Writing a coroutine that way is no different from writing a normal C function.

This is the moment where C++ makes sense. The coroutine proposal in C++20 is a much better suit. The extra bits of compiler support just make it much easier to write.

If we don't use `swapcontext` / `makecontext`, the natural choice is either `longjmp` / `setjmp` or good-old [Duff's device](https://en.wikipedia.org/wiki/Duff%27s_device). It is a no-brainer to me that I will come back to [Duff's device](https://en.wikipedia.org/wiki/Duff%27s_device). It is simple enough and the most platform-agnostic way.

There are many existing stackless coroutines implemented in C. The most interesting one with [Duff's device](https://en.wikipedia.org/wiki/Duff%27s_device) is [Protothreads](http://dunkels.com/adam/pt/). To me, the problem with [Protothreads](http://dunkels.com/adam/pt/) is its inability to maintain local variables. Yes, you can allocate additional states by passing in additional parameters. But it can quickly become an exercise and drifting away from a simple stackless coroutine to one with all bells-and-whistles of structs for some parameters and variables. You can declare everything as `static`. But it is certainly not going to work other than the most trivial examples.

I've spent this weekend to sharpen my C-macro skills on how to write the most natural stackless coroutine in C. The implementation preserves local variables. You can declare the parameters and return values almost as natural as you write normal functions.

Here is an example of how you can write a function-like stackless coroutine in C:

`co_decl_task` will declare the interface and the implementation. You can also separate the interface into header file with `co_decl` and implementation into `co_task`. In this case, `static` keyword continues to work to scope the coroutine to file-level visibility. Taking a look at this:

The first parameter is the return type, and then function name, parameters, all feel very natural to C functions. The local variable has to be declared within the `private` block, that's the only catch.

To access parameters and local variables, you have to use `CO_P` / `CO_V` macro to wrap the access, otherwise it is the same.

Of course, there are a few more catches:

1.  No variadic parameters;
2.  No variable length local arrays;
3.  No void, `()` meant for that in parameters, and you can simply omit the return type if you don't need them.

There is no magic really, just some ugly macros hide away the complexity of allocating parameters / local variables on the heap and such.

There are examples in the repo that shows the usage of `co_resume`, `co_await`, `co_yield`, `co_decl`, `co_task`, `co_decl_task` and `co_return` in varies formats. You can check out more there: [https://github.com/liuliu/co](https://github.com/liuliu/co)

Currently, I have a single-threaded scheduler. However, it is not hard to switch that to a multi-threaded scheduler with the catch that you cannot maintain the dependencies as a linked-list, but rather a tree.

It is a weekend exercise, I don't expect to maintain this repo going forward. Some form of this will be ported into [nnc](https://libnnc.org).

Closing Thoughts
----------------

In theory, `swapcontext` / `makecontext` can make a much more complex interaction between functions that an extra scheduler object is not needed. For what it's worth, [Protothreads](http://dunkels.com/adam/pt/) also doesn't have a central scheduler. But in practice, I found it still miles easier to have a scheduler like what [libtask](https://swtch.com/libtask/) does. Tracking and debugging is much easier with a central scheduler especially if you want to make that multi-thread safe as well.

  
  
from Hacker News https://ift.tt/34I4dP8