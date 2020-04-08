---
title: 'Base64 encoding and decoding at almost the speed of a memory copy'
date: 2019-11-06T07:22:00+01:00
draft: false
---

Title:Base64 encoding and decoding at almost the speed of a memory copy
=======================================================================

(Submitted on 2 Oct 2019)

> Abstract: Many common document formats on the Internet are text-only such as email (MIME) and the Web (HTML, JavaScript, JSON and XML). To include images or executable code in these documents, we first encode them as text using base64. Standard base64 encoding uses 64~ASCII characters: both lower and upper case Latin letters, digits and two other symbols. We show how we can encode and decode base64 data at nearly the speed of a memory copy (memcpy) on recent Intel processors, as long as the data does not fit in the first-level (L1) cache. We use the SIMD (Single Instruction Multiple Data) instruction set AVX-512 available on commodity processors. Our implementation generates several times fewer instructions than previous SIMD-accelerated base64 codecs. It is also more versatile, as it can be adapted---even at runtime---to any base64 variant by only changing constants.

Submission history
------------------

From: Daniel Lemire \[

[view email](https://arxiv.org/show-email/7815b31b/1910.05109)

\]

**\[v1\]**

Wed, 2 Oct 2019 15:39:28 UTC (88 KB)

  
  
from Hacker News https://ift.tt/33kGSSL