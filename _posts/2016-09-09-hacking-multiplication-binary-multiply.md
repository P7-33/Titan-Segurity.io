---
title: 'Hacking Multiplication: Binary Multiply on Paper'
date: 2020-02-08T04:32:00+01:00
draft: false
---

We’ve often noted that whether had ancient man known binary, we could all count to 1023 on our fingers. We thought about that while watching \[Numberphile’s\] latest video about [“Russian” multiplication](https://www.youtube.com/watch?v=HJ_PP5rqLg0) (see below). Apparently, the method dates back quite a way, sometimes known as Ethiopian or peasant multiplication. Even the ancient Egyptians did a form of it.

If you’ve ever written long multiplication code for a microcontroller, you can probably tell how this works. Each halving of the number amounts to a right shift. Each doubling is a left shift. Throwing out the even numbers means you only take the values when the least-significant bit is zero. [Booth’s algorithm](https://en.wikipedia.org/wiki/Booth%27s_multiplication_algorithm) is more efficient, but the “Russian” method is simple to do on paper.

The main difference between the Russian and Egyptian methods is if you start with one of the multiplicands (Russian) or start with 1 and work your way up (Egyptian). Either way, you ought to start with the smallest multiplicand.

For example, suppose you have 321 x 17. You would pick 17 since it is smaller and halve it to form the left side of your table. Throw away any halves as those are bits shifting off the right-hand side. The right side of the table starts with the other number (321) and doubles on each row. So:

```
17     321  
 8     642  
 4    1284  
 2    2568  
 1    5136
```

The rows for 8, 4, and 2 are even, so they represent multiply by zero in the long division. You can cross them out. That leaves the row for 17 and 1. Adding those up, you get 5457, the correct answer.

If you want to see the binary case, consider 9×3, which we know is 27 and using the Russian method works out to 9+18. In binary, we would say:

```
    1001  
x   0011  
\-----------  
 000000  
  000000  
   10010 (18)  
    1001  (9)  
\-------------  
 0011011 (27)
```

Oddly, this is only one way the Egyptians knew how to calculate. Some of how they dealt with fractions was not [completely understood until 2002](https://emlr.blogspot.com/).

This is a great example of how a rote method works, even if you [don’t understand why](https://hackaday.com/2019/02/15/understanding-math-rather-than-merely-learning-it/), but it is better if you do understand. Of course, these days, we can just [ask a computer](https://hackaday.com/2019/05/11/mathics-how-to-do-hard-math-when-youre-not-an-mit-janitor/).

m

  
  
from Hackaday https://ift.tt/3bptl0W  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)