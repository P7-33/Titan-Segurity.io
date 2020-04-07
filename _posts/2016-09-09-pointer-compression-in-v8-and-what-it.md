---
title: 'Pointer Compression in V8 (and what it means for browser exploits)'
date: 2020-02-03T02:43:00+01:00
draft: false
---

![](https://lh4.googleusercontent.com/proxy/3UrZBfVvdq1wo6RcwONFvzvhNZMZWBqmrLYlf-emasRyyfgQG6F7fGfvecsYDNPcSMp7=w1200-h630-p-k-no-nu "Pointer Compression in V8")  

Syed Faraz Abrar

Summary
=======

In this blog post, I will provide some details on how the Chromium developers implemented pointer compression in V8. I will also talk about what this means from an exploit development perspective.

Introduction
============

I’ve been an intern at InfoSect for the past couple of weeks now, and in this time, I’ve had to do a bunch of security related research into both V8 and Spidermonkey. One of the things that I spent a short amount of my time on was pointer compression in V8. I hadn’t heard of the term at all until Bruno Keith ([@bkth\_](https://twitter.com/bkth_)) mentioned it on twitter some time in December last year. The V8 developers also [made a blog post to celebrate V8 v8.0](https://v8.dev/blog/v8-release-80) where they mentioned that implementing pointer compression had allowed them to save up to 40% in usage of heap memory! That’s a big improvement, so let’s take a look at what pointer compression is and what it means from an exploit developer’s perspective.

Disclaimer
==========

This is not intended to be an introductory guide by any means. You are expected to be familiar with JavaScript engine internals, and at least somewhat familiar with JavaScript engine exploitation.

What is pointer compression?
============================

The V8 heap
-----------

Before I get into what pointer compression is, I’ll briefly talk about what the V8 heap is.

When you create any objects, arrays, or functions (the latter two are both considered as objects) in JavaScript, they are placed on the V8 heap. If you’re familiar with Linux exploitation, this heap is not the same as the region labeled **\[heap\]** that you would see in GDB. Instead, this heap consists of multiple mmapped sections of memory that are usually the lowest memory mappings in the program. Here is what I mean:

The sections of memory that have their upper 32 bits set to 0x0000177f are all essentially the V8 heap. Within the source code, this entire memory space is known as the **isolate**. As you can see, these are mapped to the lowest memory addresses, right below the binary’s text segment mappings. V8’s young generation and old generation both reside somewhere within these mapped memory regions, and pretty much anything that is allocate-able in JavaScript, barring some exceptions, is allocated within this region of memory.

  

The thing to notice here is that the upper 32 bits of this entire heap is always the same per run. The 0x0000177f value will change between multiple runs, but within a single run, only the lower 32 bits will differ between different objects on the heap.

Pointer compression
-------------------

When V8 didn’t have pointer compression, any pointers in the V8 heap that pointed to other objects in the V8 heap would be stored as 64-bit pointers. Now, if you think about it, this is essentially a waste, since the upper 32 bits of every single pointer would be the same, so storing the upper 32 bits with every single pointer doesn’t make sense. It would be better to store the lower 32 bits within the heap, and only store the upper 32 bits once through some other means.

  

The Chromium team thought about this and ended up deciding to implement pointer compression for the V8 heap. Their design decisions are documented in [this document](https://docs.google.com/document/d/10qh2-b4C5OtSg-xLwyZpEI5ZihVBPtn1xwKBbQC26yI/edit).

  

Essentially, they ended up deciding to take the upper 32 bits of the V8 heap’s memory space (known as the **isolate root**) and storing it in one specific register (R13) that they decided to call the **root register**. Now, any pointers in the V8 heap are 32-bit pointers that only store the lower 32 bits of their actual 64-bit address.

  

**Note –** in the case of the above example, the **isolate root** would be 0x0000177f00000000

  

This is what pointer compression is. The pointers on the heap are compressed when they point to somewhere else in the V8 heap. Any time they need to be accessed, the **isolate root** that is stored in the **root register** is simply added to the compressed 32 bit address stored in the V8 heap, and then subsequently dereferenced.

  

A downside to this is that the V8 heap can not be any greater than 4 GB as that is the maximum limit of a 32-bit address space. This is fine for browsers, as the heap doesn’t need to be greater than 4 GB anyway. It becomes a problem with things like node.js that require larger heaps. Because of this, pointer compression is disabled for node.js until a better solution can be figured out.

  

You can see some implementation details of pointer compression in V8 in the following files:

  

v8/src/common/ptr-compr.h  
v8/src/common/ptr-compr-inl.h

What does this mean for exploitation?
=====================================

Well, to start off with, there isn’t really an easy way to leak the **isolate root** (upper 32 bits of the V8 heap memory space) through JS, but if you think about it, there really isn’t a need to do that in the first place.

  

If you can massage a vulnerability into addrof and fakeobj primitives, you can fake a JSArray and control the elements pointer to gain arbitrary r/w primitives. The catch here is that these primitives would only let you perform arbitrary reads and writes within the V8 heap. Why you ask? Because the elements pointer of a JSArray stores a 32-bit compressed pointer, and if you change it to an arbitrary 32-bit memory address, performing reads and writes using this elements pointer will cause V8 to add the **isolate root** to the 32-bit address each time, meaning you are stuck within the V8 heap no matter what you do.

  

The way around this is to then go the classic route of allocating an ArrayBuffer on the V8 heap and overwriting its backing store to an arbitrary 64-bit memory address. Then, performing reads and writes with it using either a TypedArray or a DataView object will grant you an arbitrary r/w primitive within the entire 64-bit address space.

  

The reason this works is because the backing stores of array buffers are allocated using PartitionAlloc (I’m not entirely sure if this is still the case, but this was the case approximately 3-4 years ago, and I haven’t seen anything to suggest that it has changed). All PartitionAlloc allocations go on a separate memory region that is not within the V8 heap. This means that the backing store pointer needs to be stored as an uncompressed 64-bit pointer, since its upper 32 bits are not the same as the **isolate root** and thus _have_ to be stored with the pointer.

Conclusion
==========

In conclusion, pointer compression as it has been implemented currently only ever so slightly affects exploitation in the sense that all tagged pointers stored on the V8 heap now only take up 32 bits, which means you’ll need two separate pairs of arbitrary r/w primitives: one pair for performing arbitrary r/w within the V8 heap using a fakeobj (or similar) primitive, and another pair for performing arbitrary r/w elsewhere using the backing store of an ArrayBuffer.

  
  
from Hacker News https://ift.tt/37TRIS1