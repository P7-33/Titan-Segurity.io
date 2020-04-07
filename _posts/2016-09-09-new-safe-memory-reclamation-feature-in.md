---
title: 'New Safe Memory Reclamation Feature in UMA'
date: 2020-01-26T02:42:00+01:00
draft: false
---

New Safe Memory Reclamation feature in UMA
==========================================

**Jeff Roberson** [jroberson at jroberson.net](mailto:freebsd-arch%40freebsd.org?Subject=Re%3A%20New%20Safe%20Memory%20Reclamation%20feature%20in%20UMA&In-Reply-To=%3Calpine.BSF.2.21.9999.2001250820220.1198%40desktop%3E "New Safe Memory Reclamation feature in UMA")  
_Sat Jan 25 18:58:29 UTC 2020_

* * *

```
Hello Folks, I want to make the larger community aware of a substantial feature coming to UMA soon. The review is at [https://reviews.freebsd.org/D22586](https://reviews.freebsd.org/D22586) along with some perf results. SMR is a technique that allows for various types of lockless synchronization by eliminating use-after-free hazards. This is in the same family as RCU/QSBR/EPOCH/Parsec. There is quite a lot of material available on the uses of these algorithms. Most of these algorithms suffer from holding on to freed memory for a relatively long period of time and reclaiming it when it's cache-cold. This also creates quite a lot of resource starvation edge cases. This is evident by the amount of code in RCU on linux intended to work around these issues. These algorithms are generally best with a small write/free workload and a very heavy read workload. For the virtual memory system I needed something that could sustain relatively rapid frees. I have ended up with a scheme that integrates with the allocator and uses a novel epoch/version tracking mechanism. The pair of these gives me 3x faster performance with 1/20th the memory overhead of our existing epoch implementation in my obviously contrived perf test. I do not want to imply that if we replaced the network epoch with uma smr the network stack would go 3x faster. I do think there may be benefits there especially for things with high turnover like pcbs. I do not yet have support for sleepable sections so there is a lot of technical space between here and there. There is a lot of information in the review and comments in the code. I will be validating on weaker memory ordering architectures. I need to write a man page. I would like to find a snappy name to avoid confusion with other algorithms. If anyone has suggestions I am open to it. Thanks, Jeff 
```

* * *

* * *

[More information about the freebsd-arch mailing list](https://lists.freebsd.org/mailman/listinfo/freebsd-arch)  

  
  
from Hacker News https://ift.tt/2sXjlul