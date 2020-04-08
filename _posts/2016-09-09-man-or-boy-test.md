---
title: 'Man or boy test'
date: 2019-11-28T06:54:00+01:00
draft: false
---

```
begin real procedure A(k, x1, x2, x3, x4, x5); value k; integer k; real x1, x2, x3, x4, x5; begin real procedure B; begin k := k \- 1; B := A := A(k, B, x1, x2, x3, x4) end; if k ≤ 0 then A := x4 + x5 else B end outreal(1,A(10, 1, \-1, \-1, 1, 0)) end 
```

There are three Algol features used in this program that can be difficult to implement properly in a compiler:

These things are however not what the test is about; they're merely prerequisites for the test to at all be meaningful. What the test is _about_ is whether the different references to _B_ resolve to the _correct_ instance of _B_ — one that has access to the same _A_\-local symbols as the _B_ that created the reference. A "boy" compiler might for example instead compile the program so that _B_ always accesses the topmost _A_ call frame.

  
  
from Hacker News https://ift.tt/2xhJzZ3