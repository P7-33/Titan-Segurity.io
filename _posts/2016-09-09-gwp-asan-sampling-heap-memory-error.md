---
title: 'GWP-ASan: Sampling heap memory error detection in-the-wild'
date: 2019-11-12T18:33:00+01:00
draft: false
---

Posted by Vlad Tsyrklevich, Dynamic Tools Team

Memory safety errors, like use-after-frees and out-of-bounds reads/writes, are a leading source of vulnerabilities in C/C++ applications. Despite investments in preventing and detecting these errors in Chrome, over 60% of high severity vulnerabilities in Chrome are memory safety errors. Some memory safety errors don’t lead to security vulnerabilities but simply cause crashes and instability.

Chrome uses state-of-the-art techniques to prevent these errors, including:

*   [Coverage-guided](https://llvm.org/docs/LibFuzzer.html) [fuzzing](https://en.wikipedia.org/wiki/American_fuzzy_lop_(fuzzer)) with [AddressSanitizer](https://clang.llvm.org/docs/AddressSanitizer.html) (ASan)
*   Unit and integration testing with ASan
*   Defensive programming, like custom libraries to perform safe math or provide bounds checked containers
*   Mandatory code review

Chrome also makes use of sandboxing and exploit mitigations to complicate exploitation of memory errors that go undetected by the methods above.

AddressSanitizer is a compiler instrumentation that finds memory errors occurring on the heap, stack, or in globals. ASan is highly effective and one of the lowest overhead instrumentations available that detects the errors that it does; however, it still incurs an average 2-3x performance and memory overhead. This makes it suitable for use with unit tests or fuzzing, but not deployment to end users. Chrome used to deploy [SyzyASAN instrumented binaries](https://blog.chromium.org/2013/05/testing-chromium-syzyasan-lightweight.html) to detect memory errors. SyzyASAN had a similar overhead so it was only deployed to a small subset of users on the canary channel. It was discontinued after the Windows toolchain switched to LLVM.

GWP-ASan, also known by its recursive backronym, GWP-ASan Will Provide Allocation Sanity, is a sampling allocation tool designed to detect heap memory errors occurring in production with negligible overhead. Because of its negligible overhead we can deploy GWP-ASan to the entire Chrome user base to find memory errors happening in the real world that are not caught by fuzzing or testing with ASan. Unlike ASan, GWP-ASan can not find memory errors on the stack or in globals.

GWP-ASan is currently enabled for all Windows and macOS users for allocations made using malloc() and PartitionAlloc. It is only enabled for a small fraction of allocations and processes to reduce performance and memory overhead to a negligible amount. At the time of writing it has found [over sixty bugs](https://bugs.chromium.org/p/chromium/issues/list?q=Hotlist%3DGWP-ASan&can=1) (many are still restricted view). About 90% of the issues GWP-ASan has found are use-after-frees. The remaining are out-of-bounds reads and writes.

To learn more, check out our full write up on GWP-ASan [here](https://www.chromium.org/Home/chromium-security/articles/gwp-asan).

[![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?d=yIl2AUoC8zA)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=HmaU6SwWG6c:pljgPwYGZgI:yIl2AUoC8zA) [![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?i=HmaU6SwWG6c:pljgPwYGZgI:V_sGLiPBpWU)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=HmaU6SwWG6c:pljgPwYGZgI:V_sGLiPBpWU)

![](http://feeds.feedburner.com/~r/GoogleOnlineSecurityBlog/~4/HmaU6SwWG6c)  
  
from Google Online Security Blog https://ift.tt/2ry1J76  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)