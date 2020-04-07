---
title: 'Implementations of Cat(1) from Various Sources (2018)'
date: 2020-01-19T07:32:00+01:00
draft: false
---

![](https://avatars1.githubusercontent.com/u/3936?s=400&v=4 "GitHub - pete/cats: Implementations of cat(1) from various sources.")  

```
Here, placed side-by-side for comparison, are GNU's implementation of cat, Plan 9's implementation, Busybox's implementation, and NetBSD's implementation, Seventh Edition Unix (1979), Tenth Edition Unix (1989), and 4.3BSD. For good measure (and because I suppose I am now committed to collecting cats) also included are Second Edition Unix (in assembly) and Inferno's implementation (in Limbo) for good measure. All cat.c files (renamed by prefixing the name of the source source) are presented, unaltered and in their entirety. Note how easy it is to read and understand plan9-cat.c (it should take less than a couple of minutes possibly even for coders that don't know C). Other than that, I think the files speak for themselves. Keep in mind while reading that the cat utility's purpose is to concatenate files. Lastly, here are the line and character counts, sorted: Lines Chars Filename --------------------------- 35 531 plan9-cat.c 48 955 busybox-cat.c 48 986 inferno-cat.b 63 1130 unix7-cat.c 64 646 unix2-cat.s 69 1241 unix10-cat.c 222 3948 4.3bsd-cat.c 316 6952 netbsd-cat.c 782 22684 gnu-cat.c 1647 39073 total 
```

  
  
from Hacker News https://ift.tt/1QD5V5m