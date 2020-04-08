---
title: 'Show HN: A simple garbage collector for C'
date: 2019-12-20T04:46:00+01:00
draft: false
---

![](https://avatars1.githubusercontent.com/u/515019?s=400&v=4 "GitHub - mkirchner/gc: Simple, zero-dependency garbage collection for C")  

[](https://github.com/mkirchner/gc#gc-mark--sweep-garbage-collection-for-c)gc: mark & sweep garbage collection for C
====================================================================================================================

`gc` is an implementation of a conservative, thread-local, mark-and-sweep garbage collector. The implementation provides a fully functional replacement for the standard POSIX `malloc()`, `calloc()`, `realloc()`, and `free()` calls.

The focus of `gc` is to provide a conceptually clean implementation of a mark-and-sweep GC, without delving into the depths of architecture-specific optimization (see e.g. the [Boehm GC](https://www.hboehm.info/gc/) for such an undertaking). It should be particularly suitable for learning purposes and is open for all kinds of optimization (PRs welcome!).

The original motivation for `gc` is my desire to write [my own LISP](https://github.com/mkirchner/stutter) in C, entirely from scratch - and that required garbage collection.

### [](https://github.com/mkirchner/gc#acknowledgements)Acknowledgements

This work would not have been possible without the ability to read the work of others, most notably the [Boehm GC](https://www.hboehm.info/gc/), orangeduck's [tgc](https://github.com/orangeduck/tgc) (which also follows the ideals of being tiny and simple), and [The Garbage Collection Handbook](http://gchandbook.org).

[](https://github.com/mkirchner/gc#table-of-contents)Table of contents
----------------------------------------------------------------------

[](https://github.com/mkirchner/gc#documentation-overview)Documentation Overview
--------------------------------------------------------------------------------

[](https://github.com/mkirchner/gc#quickstart)Quickstart
--------------------------------------------------------

### [](https://github.com/mkirchner/gc#download-and-test)Download and test

```
$ git clone git@github.com:mkirchner/gc.git $ cd gc $ make test $ make coverage # to open the current coverage in a browser 
```

### [](https://github.com/mkirchner/gc#basic-usage)Basic usage

```
... #include "gc.h" ... void some\_fun() { ... int\* my\_array = gc\_calloc(gc, 1024, sizeof(int)); for (size\_t i; i<1024; ++i) { my\_array\[i\] = 42; } ... // look ma, no free! } int main(int argc, char\* argv\[\]) { gc = gc\_start(gc, &argc); ... some\_fun(); ... gc\_stop(gc); return 0; }
```

[](https://github.com/mkirchner/gc#core-api)Core API
----------------------------------------------------

This describes the core API, see `gc.h` for more details and the low-level API.

### [](https://github.com/mkirchner/gc#starting-stopping-pausing-resuming-and-running-gc)Starting, stopping, pausing, resuming and running GC

In order to initialize and start garbage collection, use the `gc_start()` function and pass a _bottom-of-stack_ address:

```
void gc\_start(GarbageCollector\* gc, void\* bos);
```

The bottom-of-stack parameter `bos` needs to point to a stack-allocated variable and marks the low end of the stack from where [root finding](https://github.com/mkirchner/gc#root-finding) (scanning) starts.

Garbage collection can be stopped, paused and resumed with

```
void gc\_stop(GarbageCollector\* gc); void gc\_pause(GarbageCollector\* gc); void gc\_resume(GarbageCollector\* gc);
```

and manual garbage collection can be triggered with

```
size\_t gc\_run(GarbageCollector\* gc);
```

### [](https://github.com/mkirchner/gc#memory-allocation-and-deallocation)Memory allocation and deallocation

`gc` supports `malloc()`, `calloc()`and `realloc()`\-style memory allocation. The respective funtion signatures mimick the POSIX functions (with the exception that we need to pass the garbage collector along as the first argument):

```
void\* gc\_malloc(GarbageCollector\* gc, size\_t size); void\* gc\_calloc(GarbageCollector\* gc, size\_t count, size\_t size); void\* gc\_realloc(GarbageCollector\* gc, void\* ptr, size\_t size);
```

It is possible to pass a pointer to a desctructor function through the extended interface:

```
void\* dtor(void\* obj) { // do some cleanup work obj->parent\->deregister(); obj->db\->disconnect() ... // no need to free obj } ... SomeObject\* obj = gc\_malloc\_ext(gc, sizeof(SomeObject), dtor); ...
```

`gc` supports static allocations that are garbage collected only when the GC shuts down via `gc_stop()`. Just use the appropriate helper function:

```
void\* gc\_malloc\_static(GarbageCollector\* gc, size\_t size, void (\*dtor)(void\*));
```

Static allocation expects a pointer to a finalization function; just set to `NULL` if finalization is not required.

Note that `gc` currently does not guarantee a specific ordering when it collects static variables, If static vars need to be deallocated in a particular order, the user should call `gc_free()` on them in the desired sequence prior to calling `gc_stop()`, see below.

It is also possible to trigger explicit memory deallocation using

```
void gc\_free(GarbageCollector\* gc, void\* ptr);
```

Calling `gc_free()` is guaranteed to (a) finalize/destruct on the object pointed to by `ptr` if applicable and (b) to free the memory that `ptr` points to irrespective of the current scheduling for garbage collection and will also work if GC has been paused using `gc_pause()` above.

### [](https://github.com/mkirchner/gc#static-variables)Static variables

### [](https://github.com/mkirchner/gc#helper-functions)Helper functions

`gc` also offers a `strdup()` implementation that returns a garbage-collected copy:

```
char\* gc\_strdup (GarbageCollector\* gc, const char\* s);
```

[](https://github.com/mkirchner/gc#basic-concepts)Basic Concepts
----------------------------------------------------------------

The fundamental idea behind garbage collection is to automate the memory allocation/deallocation cycle. This is accomplished by keeping track of all allocated memory and periodically triggering deallocation for memory that is still allocated but [unreachable](https://github.com/mkirchner/gc#reachability).

Many advanced garbage collectors also implement their own approach to memory allocation (i.e. replace `malloc()`). This often enables them to layout memory in a more space-efficient manner or for faster access but comes at the price of architecture-specific implementations and increased complexity. `gc` sidesteps these issues by falling back on the POSIX `*alloc()` implementations and keeping memory management and garbage collection metadata separate. This makes `gc` much simpler to understand but, of course, also less space- and time-efficient than more optimized approaches.

### [](https://github.com/mkirchner/gc#data-structures)Data Structures

The core data structure inside `gc` is a hash map that maps the address of allocated memory to the garbage collection metadata of that memory:

The items in the hash map are allocations, modeles with the `Allocation` `struct`:

```
typedef struct Allocation { void\* ptr; // mem pointer size\_t size; // allocated size in bytes char tag; // the tag for mark-and-sweep void (\*dtor)(void\*); // destructor struct Allocation\* next; // separate chaining } Allocation;
```

Each `Allocation` instance holds a pointer to the allocated memory, the size of the allocated memory at that location, a tag for mark-and-sweep (see below), an optional pointer to the destructor function and a pointer to the next `Allocation` instance (for separate chaining, see below).

The allocations are collected in an `AllocationMap`

```
typedef struct AllocationMap { size\_t capacity; size\_t min\_capacity; double downsize\_factor; double upsize\_factor; double sweep\_factor; size\_t sweep\_limit; size\_t size; Allocation\*\* allocs; } AllocationMap;
```

that, together with a set of `static` functions inside `gc.c`, provides hash map semantics for the implementation of the public API.

The `AllocationMap` is the central data structure in the `GarbageCollector` struct which is part of the public API:

```
typedef struct GarbageCollector { struct AllocationMap\* allocs; bool paused; void \*bos; size\_t min\_size; } GarbageCollector;
```

With the basic data structures in place, any `gc_*alloc()` memory allocation request is a two-step procedure: first, allocate the memory through system (i.e. standard `malloc()`) functionality and second, add or update the associated metadata to the hash map.

For `gc_free()`, use the pointer to locate the metadata in the hash map, determine if the deallocation requires a destructor call, call if required, free the managed memory and delete the metadata entry from the hash map.

These data structures and the associated interfaces enable the management of the metadata required to build a garbage collector.

### [](https://github.com/mkirchner/gc#garbage-collection)Garbage collection

`gc` triggers collection under two circumstances: (a) when any of the calls to the system allocation fail (in the hope to deallocate sufficient memory to fulfill the current request); and (b) when the number of entries in the hash map passes a dynamically adjusted high water mark.

If either of these cases occurs, `gc` stops the world and starts a mark-and-sweep garbage collection run over all current allocations. This functionality is implemented in the `gc_run()` function which is part of the public API and delegates all work to the `gc_mark()` and `gc_sweep()` functions that are part of the private API.

`gc_mark()` has the task of [finding roots](https://github.com/mkirchner/gc#finding-roots) and tagging all known allocations that are referenced from a root (or from an allocation that is referenced from a root, i.e. transitively) as "used". Once the marking of is completed, `gc_sweep()` iterates over all known allocations and deallocates all unused (i.e. unmarked) allocations, returns to `gc_run()` and the world continues to run.

### [](https://github.com/mkirchner/gc#reachability)Reachability

`gc` will keep memory allocations that are _reachable_ and collect everything else. An allocation is considered reachable if any of the following is true:

1.  There is a pointer on the stack that points to the allocation content. The pointer must reside in a stack frame that is at least as deep in the call stack as the bottom-of-stack variable passed to `gc_start()` (i.e. `bos` is the smallest stack address considered during the mark phase).
2.  There is a pointer inside `gc_*alloc()`\-allocated content that points to the allocation content.
3.  The allocation is tagged with `GC_TAG_ROOT`.

### [](https://github.com/mkirchner/gc#the-mark-and-sweep-algorithm)The Mark-and-Sweep Algorithm

The naïve mark-and-sweep algorithm runs in two stages. First, in a _mark_ stage, the algorithm finds and marks all _root_ allocations and all allocations that are reachable from the roots. Second, in the _sweep_ stage, the algorithm passes over all known allocations, collecting all allocations that were not marked and are therefore deemed unreachable.

### [](https://github.com/mkirchner/gc#finding-roots)Finding roots

At the beginning of the _mark_ stage, we first sweep across all known allocations and find explicit roots with the `GC_TAG_ROOT` tag set. Each of these roots is a starting point for [depth-first recursive marking](https://github.com/mkirchner/gc#depth-first-recursive-marking).

`gc` subsequently detects all roots in the stack (starting from the bottom-of-stack pointer `bos` that is passed to `gc_start()`) and the registers (by [dumping them on the stack](https://github.com/mkirchner/gc#dumping-registers-on-the-stack) prior to the mark phase) and uses these as starting points for marking as well.

### [](https://github.com/mkirchner/gc#depth-first-recursive-marking)Depth-first recursive marking

Given a root allocation, marking consists of (1) setting the `tag` field in an `Allocation` object to `GC_TAG_MARK` and (2) scanning the allocated memory for pointers to known allocations, recursively repeating the process.

The underlying implementation is a simple, recursive depth-first search that scans over all memory content to find potential references:

```
void gc\_mark\_alloc(GarbageCollector\* gc, void\* ptr) { Allocation\* alloc = gc\_allocation\_map\_get(gc->allocs, ptr); if (alloc && !(alloc->tag & GC\_TAG\_MARK)) { alloc->tag |= GC\_TAG\_MARK; for (char\* p = (char\*) alloc->ptr; p < (char\*) alloc->ptr + alloc->size; ++p) { gc\_mark\_alloc(gc, \*(void\*\*)p); } } }
```

In `gc.c`, `gc_mark()` starts the marking process by marking the known roots on the stack via a call to `gc_mark_roots()`. To mark the roots we do one full pass through all known allocations. We then proceed to dump the registers on the stack.

### [](https://github.com/mkirchner/gc#dumping-registers-on-the-stack)Dumping registers on the stack

In order to make the CPU register contents available for root finding, `gc` dumps them on the stack. This is implemented in a somewhat portable way using `setjmp()`, which stores them in a `jmp_buf` variable right before we mark the stack:

```
... /\* Dump registers onto stack and scan the stack \*/ void (\*volatile \_mark\_stack)(GarbageCollector\*) = gc\_mark\_stack; jmp\_buf ctx; memset(&ctx, 0, sizeof(jmp\_buf)); setjmp(ctx); \_mark\_stack(gc); ...
```

The detour using the `volatile` function pointer `_mark_stack` to the `gc_mark_stack()` function is necessary to avoid the inlining of the call to `gc_mark_stack()`.

  
  
from Hacker News https://github.com/mkirchner/gc