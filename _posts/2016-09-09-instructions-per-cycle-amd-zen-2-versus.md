---
title: 'Instructions per cycle: AMD Zen 2 versus Intel'
date: 2019-12-06T07:10:00+01:00
draft: false
---

![](https://lemire.me/img/portrait2018facebook.jpg "Instructions per cycle: AMD Zen 2 versus Intel – Daniel Lemire's blog")  

The performance of a processor is determined by several factors. For example, processors with a higher frequency tend to do more work per unit of time. Physics makes it difficult to produce processors that have higher frequency.

Modern processors can execute many instructions per cycle. Thus a 3.4GHz processor has 3.4 billion cycles per second, but it might easily execute 7 billion instructions per second on a single core.

Up until recently, Intel produced the best commodity processors: its processors had the highest frequencies, the most instructions per cycle, the most powerful instructions and so forth. However, Intel is increasingly being challenged. One smaller company that is making Intel nervous is AMD.

[It has been reported that the most recent AMD processors](https://www.guru3d.com/articles_pages/amd_ryzen_7_3800x_review,9.html) surpass Intel in terms of instructions per cycle. However, it is not clear whether these reports are genuinely based on measures of instruction per cycle. Rather it appears that they are measures of the amount of work done per unit of time normalized by processor frequency.

In theory, a processor limited to one instruction per cycle could beat a modern Intel processor on many tasks if they had powerful instructions and faster data access. Thus “work per unit of time normalized per CPU frequency” and “instructions per cycle” are distinct notions.

I have only had access to a recent AMD processors (Zen 2) for a short time, but in this short time, I have routinely found that it has a lower number of instructions per cycle than even older Intel processors.

Let us consider a piece of software that has a high number of instructions per cycle, the fast JSON parser [simdjson](https://github.com/lemire/simdjson). I use GNU GCC 8 under Linux, I process a test file called twitter.json using the benchmark command line parse. I record the number of instructions per cycle, as measured by CPU counters, in the two stages of processing. The two stages together effectively parse a JSON document. This is an instruction-heavy benchmark: the numbers of mispredicted branches and cache misses are small. I use an AMD Rome (server) processor.

I find that AMD is about 10% to 15% behind Intel.

Another problem that I like is bitset decoding. That is given an array of bits (0s and 1s), I want to find the location of the ones. See my blog post [Really fast bitset decoding for “average” densities](https://lemire.me/blog/2019/05/03/really-fast-bitset-decoding-for-average-densities/). I benchmark just the “basic” decoder.

```
void basic\_decoder(uint32\_t \*base\_ptr, uint32\_t &base,   
 uint32\_t idx, uint64\_t bits) {  
 while (bits !\= 0) {  
 base\_ptr\[base\] \= idx + \_tzcnt\_u64(bits);  
 bits \= bits & (bits \- 1);  
 base++;  
 }  
 }  
 
```

[My source code is available](https://github.com/lemire/Code-used-on-Daniel-Lemire-s-blog/tree/master/2019/05/03).

So AMD runs at half the IPC of an old Intel processor. That is quite poor!

Of course, your results will vary. And I am quite willing to believe that in many, maybe even most, real-world cases, AMD Zen 2 can do more work per unit of work than the best Intel processors. However I feel that we should qualify these claims.

  
  
from Hacker News https://ift.tt/2recTOw