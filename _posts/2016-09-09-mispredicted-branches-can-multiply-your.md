---
title: 'Mispredicted branches can multiply your running times'
date: 2019-10-16T09:14:00+01:00
draft: false
---

![](https://lemire.me/img/portrait2018facebook.jpg "Mispredicted branches can multiply your running times – Daniel Lemire's blog")  

Modern processors are superscalar, meaning that they can execute many instructions at once. For example, some processors can retire four or six instructions per cycle. Furthermore, many of these processors can initiate instructions out-of-order: they can start working on instructions that appear much later in the code.

Meanwhile most code contains branches (if–then clauses). These branches are often implemented as “jumps” where the processor either goes running instruction further away, or continues on its current path.

It is hard to reconcile branches with out-of-order superscalar execution. To do so, processors have sophisticated branch predictors. That is, the processor tries to predict the future. When it sees branch, and thus a jump, it tries to guess which way it will go.

This often works quite well. For example, most loops are actually implemented as branches. At the end of each iteration in the loop, the processor must predict whether there will be a next iteration. It is often safe for the processor to predict that the loop will continue (forever). The processor will only mispredict one branch per loop in this manner.

There are other common examples. If you are accessing the content of an array, many languages will add “bound checking”: before accessing the array value, there will be a hidden check to see whether the index is valid. If the index is not valid, then an error is generated, otherwise the code proceeds normally. Bound checks are predictable since all accesses should (normally) be valid. Consequently, most processors should be able to predict the outcome nearly perfectly.

What happens if the branch is hard to predict?

What happens inside the processor is that all of the instruction that were executed but that follow the mispredicted branch must be cancelled and the computation must start anew. You should expect a penalty of more than 10 cycles for each mispredicted branch.

It can be multiply the running times.

Let us look at some simple code where we write out random integers to an output array:

```
while (howmany !\= 0) {  
 out\[index\] \= random();  
 index +\= 1;  
 howmany\-\-;  
 }  
 
```

We can generate a decent random number in about 3 cycles on average. That is, the total latency of the random number generator might be 10 cycles. But our processor is superscalar, so we can do several random-number computations at once. Thus we may generate a new random number every 3 cycles or so.

Let us modify slightly this function so that we only write out the odd integers:

```
while (howmany !\= 0) {  
 val \= random();  
 if( val is odd) {  
 out\[index\] \= val;  
 index +\= 1;  
 }  
 howmany\-\-;  
 }  
 
```

Naively we might think that this new function could be faster. Indeed, we might only write out one out of two integers. We have a branch, but checking whether an integer is odd requires checking a single bit.

I benchmarked these two functions in C++ using a skylake processor:

write all random numbers

3.3 cycles per integer

write only odd random numbers

15 cycles per integer

The second function takes about five times longer!

Is there something you can do? Yes. You can just remove the branch. You can characterize an odd integer by the fact that its bitwise logical AND with the value 1 is one. The trick is to increment the array index by one only when the random value is odd.

```
while (howmany !\= 0) {  
 val \= random();  
 out\[index\] \= val;  
 index +\= (val bitand 1);  
 howmany\-\-;  
 }  
 
```

In this new version, we always write the random value to the output array, even when it is not needed. At a glance, it looks wasteful. However, it does away with the mispredicted branches. In practice the performance is nearly as good as the original code, and much better than the version with branches:

write all random numbers

3.3 cycles per integer

write only odd random numbers

15 cycles per integer

**branch removed**

**3.8 cycles per integer**

Could the compiler have solved this problem on its own? In general, the answer is negative. Sometimes compilers have some options to avoid branches entirely even if there is an if-then clause in the original code. For example, branches can sometimes be replaced by “conditional moves” or other arithmetic tricks. However, there are tricks that compilers cannot use safely.

An important take-away is that mispredicted branches are not a minor concern, they can have a large effect.

[My source code is available](https://github.com/lemire/Code-used-on-Daniel-Lemire-s-blog/tree/master/2019/10/14).

  
  
from Hacker News https://ift.tt/33xsgPD