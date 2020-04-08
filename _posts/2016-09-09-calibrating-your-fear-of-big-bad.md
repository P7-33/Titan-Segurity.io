---
title: 'Calibrating your fear of big bad optimizing compilers'
date: 2019-10-13T10:04:00+01:00
draft: false
---

### Welcome to LWN.net

The following subscription-only content has been made available to you by an LWN subscriber. Thousands of subscribers depend on LWN for the best news from the Linux and free software communities. If you enjoy this article, please consider accepting the trial offer on the right. Thank you for visiting LWN.net!

### Free trial subscription

Try LWN for free for 1 month: no payment or credit card required. [Activate your trial subscription now](https://lwn.net/Promo/slink-trial2-3/claim) and see why thousands of readers subscribe to LWN.net.

October 11, 2019

(Many contributors)

This article was contributed by Jade Alglave, Will Deacon, Boqun Feng, David Howells, Daniel Lustig, Luc Maranget, Paul E. McKenney, Andrea Parri, Nicholas Piggin, Alan Stern, Akira Yokosawa, and Peter Zijlstra

As noted [earlier](https://lwn.net/Articles/793253/), when compiling Linux-kernel code that does a plain C-language load or store, as in "a=b", the C standard grants the compiler the right to assume that the affected variables are neither accessed nor modified by any other thread at the time of that load or store. The compiler is therefore permitted to carry out a surprisingly large number of optimizations, any number of which might ruin your concurrent code's day. Given that current compilers usually do not emit diagnostics warning of potential ruined days, it would be good to have other tools take on this task. One such tool is the [Kernel Thread Sanitizer (KTSAN)](https://github.com/google/ktsan/wiki), but its great strength, the ability to analyze huge bodies of code such as the Linux kernel, is also its great weakness, namely the need to use approximate (though still quite good) analysis techniques.

**Quick Quiz 1**:

But we shouldn't be afraid at all for things like on-stack or per-CPU variables, right?

[Answer](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#qq1answer)

What is needed is a tool that can do exact analyses of huge bodies of code, but unfortunately the universe is under no compunction to give us what we think we need. We have therefore upgraded the [Linux Kernel Memory Model (LKMM)](https://github.com/torvalds/linux/tree/master/tools/memory-model) to do exact analyses of small bodies of code, and this upgrade was accepted into the Linux kernel during the v5.3 merge window. The challenge of doing exact analyses of large bodies of code thus remains open, but in the meantime we have another useful tool at our disposal.

The following sections describe how to use this upgrade to LKMM:

1.  [Goals and non-goals](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Goals%20and%20Non-Goals)
2.  [A plain example](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#A%20Plain%20Example)
3.  [A less-plain example](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#A%20Less-Plain%20Example)
4.  [Locking](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Locking)
5.  [Reference counting](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Reference%20Counting)
6.  [Read-copy update (RCU)](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Read-Copy%20Update%20(RCU))
7.  [Debug output](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Debug%20Output)
8.  [Access-marking policies](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Access-Marking%20Policies)
9.  [Limitations](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Limitations)
10.  [Summary](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Summary)

This is followed by the inevitable [answers to the quick quizzes](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Answers%20to%20Quick%20Quizzes).

#### Goals and non-goals

TL;DR: The goal of LKMM is to help people understand Linux-kernel concurrency.

A key point from the first article is that we simply do not have a full catalog of all compiler optimizations that currently exist, let alone of all possible compiler options that might one day exist. Furthermore, the kernel must, in many cases, [live outside of the bounds of the C standard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0124r6.html), and thus cannot simply make direct use of the C11 memory model. The details of the compiler, of the compiler options used in Linux-kernel builds, and all of the architecture-specific code therefore impinge on LKMM—and vice versa.

Because of all of these complications and uncertainties, LKMM cannot possibly be a cut-and-dried judge and juror for all Linux-kernel memory-ordering matters. It should instead be seen as an advisor. Now, in generic, non-performance-critical code, it might be wise to pay extremely close attention to LKMM's advice. On the other hand, developers writing fastpath code might need to take an LKMM warning as a sign of the need to be careful, rather than as an error message to be fixed at all costs.

With that in mind, let's look at some LKMM litmus-test examples involving plain C-language accesses.

#### A plain example

Consider the following message-passing litmus test using plain C-language accesses and read and write memory barriers:

> Litmus Test #1```
>  1 C C-MP+p-wmb-p+p-rmb-p 2 3 { 4 } 5 6 P0(int \*x0, int \*x1) 7 { 8 \*x0 = 1; 9 smp\_wmb(); 10 \*x1 = 1; 11 } 12 13 P1(int \*x0, int \*x1) 14 { 15 int r1; 16 int r2; 17 18 r1 = \*x1; 19 smp\_rmb(); 20 r2 = \*x0; 21 } 22 23 exists (1:r1=1 /\\ 1:r2=0) 
> ```

As always, this litmus test can be run from within the kernel's tools/memory-model directory using the following command:

> ```
>  herd7 -conf linux-kernel.cfg /path/to/litmus/tests/C-MP+p-wmb-p+p-rmb-p.litmus 
> ```

Here, the "/path/to/litmus/tests" is of course replaced by the path to the directory containing your litmus tests. (See the README file in that same directory for installation instructions and [an earlier LWN article](https://lwn.net/Articles/720550/) for more details on litmus tests.) The output of this command is shown below:

> Outcome for Litmus Test #1 (linux-kernel model)```
>  1 Test C-MP+p-wmb-p+p-rmb-p Allowed 2 States 4 3 1:r1=0; 1:r2=0; 4 1:r1=0; 1:r2=1; 5 1:r1=1; 1:r2=0; 6 1:r1=1; 1:r2=1; 7 Ok 8 Witnesses 9 Positive: 1 Negative: 3 10 Flag data-race 11 Condition exists (1:r1=1 /\\ 1:r2=0) 12 Observation C-MP+p-wmb-p+p-rmb-p Sometimes 1 3 13 Time C-MP+p-wmb-p+p-rmb-p 0.00 14 Hash=055863a755bfaf3667f1667e6d660349 
> ```

**Quick Quiz 2**:

But suppose only one of the accesses to a given variable is a plain C-language access, and that access is the only store. Should this be considered a data race?

[Answer](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#qq2answer)

**Quick Quiz 3**: Why the cop-out? Why not just do the work required to ensure that the list of states and the Observation line are all accurate?  
[Answer](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#qq3answer)

Line 10 contains the key advice: "Flag data-race". This advice means that the Observation line's verdict is untrustworthy and that the list of states on lines 3-6 is unreliable. The problem is that this litmus test has at least one data race, meaning that there are multiple concurrent accesses to a given variable, at least one of which is a plain C-language access and at least one of which is a store.

The variable x1 is clearly subject to a data race because it can be accessed concurrently by a pair of plain accesses, at least one of which is a write. However, x1 only ever takes on the values zero and one, so the data race on that variable [might be tolerable](http://lkml.kernel.org/r/20190606061438.nyzaeppdbqjt3jbp@gondor.apana.org.au), at least assuming a healthy fear of the big bad optimizing compiler. But what if we want to check for other data races?

The solution is to tell LKMM that you are excluding x1 from data-race flagging. One way to do this is to add READ\_ONCE() and WRITE\_ONCE() to the litmus test (as opposed to your Linux-kernel code), preferably with a comment explaining the situation:

> Litmus Test #2```
>  1 C C-MP+p-wmb-o+o-rmb-p 2 3 { 4 } 5 6 P0(int \*x0, int \*x1) 7 { 8 \*x0 = 1; 9 smp\_wmb(); 10 WRITE\_ONCE(\*x1, 1); // Tolerate data race 11 } 12 13 P1(int \*x0, int \*x1) 14 { 15 int r1; 16 int r2; 17 18 r1 = READ\_ONCE(\*x1); // Tolerate data race 19 smp\_rmb(); 20 r2 = \*x0; 21 } 22 23 exists (1:r1=1 /\\ 1:r2=0) 
> ```

LKMM still flags a data race:

> Outcome for Litmus Test #2 (linux-kernel model)```
>  1 Test C-MP+p-wmb-o+o-rmb-p Allowed 2 States 3 3 1:r1=0; 1:r2=0; 4 1:r1=0; 1:r2=1; 5 1:r1=1; 1:r2=1; 6 No 7 Witnesses 8 Positive: 0 Negative: 3 9 Flag data-race 10 Condition exists (1:r1=1 /\\ 1:r2=0) 11 Observation C-MP+p-wmb-o+o-rmb-p Never 0 3 12 Time C-MP+p-wmb-o+o-rmb-p 0.00 13 Hash=743f0171133035c53a5a29972b0ba0fd 
> ```

The reason for this is that the plain C-language accesses to x0 can also execute concurrently, and one of these accesses is a write. We could fix this by also marking the x0 accesses with READ\_ONCE() and WRITE\_ONCE(), but an alternative is to avoid concurrency on x0 as follows:

> Litmus Test #3```
>  1 C C-MP+p-wmb-o+o+ctrl-rmb-p 2 3 { 4 } 5 6 P0(int \*x0, int \*x1) 7 { 8 \*x0 = 1; 9 smp\_wmb(); 10 WRITE\_ONCE(\*x1, 1); // Tolerate data race 11 } 12 13 P1(int \*x0, int \*x1) 14 { 15 int r1; 16 int r2; 17 18 r1 = READ\_ONCE(\*x1); // Tolerate data race 19 if (r1) { 20 smp\_rmb(); 21 r2 = \*x0; 22 } 23 } 24 25 exists (1:r1=1 /\\ 1:r2=0) 
> ```

The if statement on line 19, when combined with the smp\_wmb() on line 9, is intended to guarantee that lines 8 and 21 never execute concurrently. Running the model yields:

> Outcome for Litmus Test #3 (linux-kernel model)```
>  1 Test C-MP+p-wmb-o+o+ctrl-rmb-p Allowed 2 States 2 3 1:r1=0; 1:r2=0; 4 1:r1=1; 1:r2=1; 5 No 6 Witnesses 7 Positive: 0 Negative: 2 8 Condition exists (1:r1=1 /\\ 1:r2=0) 9 Observation C-MP+p-wmb-o+o+ctrl-rmb-p Never 0 2 10 Time C-MP+p-wmb-o+o+ctrl-rmb-p 0.00 11 Hash=01fe003cd2759d9284d40c081007c282 
> ```

There is no longer a data race flagged, and the cyclic outcome no longer occurs. Therefore, if we are willing to live in sufficient fear of the compiler to keep accesses to

x1

sane on the one hand and if we add a conditional check protecting

x0

on the other, we can obtain the required outcome.

In this case, because of the smp\_wmb() and the fact that there was only a single use of the value read, all that was needed to tell LKMM about a tolerated data race was to use WRITE\_ONCE() and READ\_ONCE() in the corresponding litmus test. Unfortunately, some situations require a bit more work, as will be hinted at in the next section.

The compiler has great freedom to optimize plain accesses, and with this great freedom comes great complexity. To see this, consider the following litmus test:

> Litmus Test #4```
>  1 C C-read-multiuse 2 3 { 4 } 5 6 P0(int \*a) 7 { 8 \*a = 1; 9 } 10 11 P1(int \*a, int \*b, int \*c) 12 { 13 int r1; 14 15 r1 = \*a; 16 \*b = r1; 17 \*c = r1; 18 } 19 20 locations \[1:r1; a; b; c\] 21 exists(b=1 /\\ c=0) 
> ```

As we should by now expect, this results in a data race:

> Outcome for Litmus Test #4 (linux-kernel model)```
>  1 Test C-read-multiuse Allowed 2 States 2 3 1:r1=0; a=1; b=0; c=0; 4 1:r1=1; a=1; b=1; c=1; 5 No 6 Witnesses 7 Positive: 0 Negative: 2 8 Flag data-race 9 Condition exists (b=1 /\\ c=0) 10 Observation C-read-multiuse Never 0 2 11 Time C-read-multiuse 0.00 12 Hash=0cab074d9a510f141aae9026ce447828 
> ```

Creating a data-race-tolerant litmus test is straightforward:

> Litmus Test #5```
>  1 C C-read-multiuse-drt1 2 3 { 4 } 5 6 P0(int \*a) 7 { 8 WRITE\_ONCE(\*a, 1); // Tolerate data race 9 } 10 11 P1(int \*a, int \*b, int \*c) 12 { 13 int r1; 14 15 r1 = READ\_ONCE(\*a); // Tolerate data race 16 \*b = r1; 17 \*c = r1; 18 } 19 20 locations \[1:r1; a; b; c\] 21 exists(b=1 /\\ c=0) 
> ```

And this both tolerates the data race and excludes the undesirable outcome:

> Outcome for Litmus Test #5 (linux-kernel model)```
>  1 Test C-read-multiuse-drt1 Allowed 2 States 2 3 1:r1=0; a=1; b=0; c=0; 4 1:r1=1; a=1; b=1; c=1; 5 No 6 Witnesses 7 Positive: 0 Negative: 2 8 Condition exists (b=1 /\\ c=0) 9 Observation C-read-multiuse-drt1 Never 0 2 10 Time C-read-multiuse-drt1 0.00 11 Hash=96b3ae01a3c486885df1aec4d978bad9 
> ```

Job done, right?

Not quite, courtesy of the aforementioned complexity. Recall that compilers can [invent loads](https://lwn.net/Articles/793253/#Invented%20Loads). Therefore, a better translation to a data-race-tolerant litmus test would duplicate the load from shared variable a as follows:

> Litmus Test #6```
>  1 C C-read-multiuse-drt2 2 3 { 4 } 5 6 P0(int \*a) 7 { 8 WRITE\_ONCE(\*a, 1); // Tolerate data race 9 } 10 11 P1(int \*a, int \*b, int \*c) 12 { 13 int r1; 14 int r2; 15 16 r1 = READ\_ONCE(\*a); // Tolerate data race 17 \*b = r1; 18 r2 = READ\_ONCE(\*a); // Tolerate data race 19 \*c = r2; 20 } 21 22 locations \[1:r1; a; b; c\] 23 exists(b=1 /\\ c=0) 
> ```

And this still tolerates the data race and excludes the undesirable outcome:

> Outcome for Litmus Test #6 (linux-kernel model)```
>  1 Test C-read-multiuse-drt2 Allowed 2 States 3 3 1:r1=0; a=1; b=0; c=0; 4 1:r1=0; a=1; b=0; c=1; 5 1:r1=1; a=1; b=1; c=1; 6 No 7 Witnesses 8 Positive: 0 Negative: 3 9 Condition exists (b=1 /\\ c=0) 10 Observation C-read-multiuse-drt2 Never 0 3 11 Time C-read-multiuse-drt2 0.01 12 Hash=17ff8b2e2c285776994d4488fcdcd3bb 
> ```

So _now_ the job is done, right?

Still not quite. Recall that compilers can [reorder code](https://lwn.net/Articles/793253/#Code%20Reordering). And there is nothing telling the compiler that the store to b needs to precede the store to c; additionally, the fact that the actual code uses a plain C-language load from shared variable a allows the compiler to assume (incorrectly, in this case) that shared variable a isn't changing. We therefore need to account for that with another data-race-tolerant litmus test that does the reordering, for example, as follows:

> Litmus Test #7```
>  1 C C-read-multiuse-drt3 2 3 { 4 } 5 6 P0(int \*a) 7 { 8 WRITE\_ONCE(\*a, 1); // Tolerate data race 9 } 10 11 P1(int \*a, int \*b, int \*c) 12 { 13 int r1; 14 int r2; 15 16 r2 = READ\_ONCE(\*a); // Tolerate data race 17 \*c = r2; 18 r1 = READ\_ONCE(\*a); // Tolerate data race 19 \*b = r1; 20 } 21 22 locations \[1:r1; a; b; c\] 23 exists(b=1 /\\ c=0) 
> ```

This still tolerates the data race, but allows the undesirable outcome:

> Outcome for Litmus Test #7 (linux-kernel model)```
>  1 Test C-read-multiuse-drt3 Allowed 2 States 3 3 1:r1=0; a=1; b=0; c=0; 4 1:r1=1; a=1; b=1; c=0; 5 1:r1=1; a=1; b=1; c=1; 6 Ok 7 Witnesses 8 Positive: 1 Negative: 2 9 Condition exists (b=1 /\\ c=0) 10 Observation C-read-multiuse-drt3 Sometimes 1 2 11 Time C-read-multiuse-drt3 0.01 12 Hash=61f32f3a79e57808d348f31f5800ae1d 
> ```

**Quick Quiz 5**:

But wait! Given that

READ\_ONCE()

provides no ordering, why would Litmus Test #5 avoid the undesirable outcome?

[Answer](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#qq5answer)

This example illustrates the need to carefully think through the possible compiler optimizations when using plain C-language loads and stores in situations involving data races. It also illustrates the possible need to use multiple litmus tests to fully analyze the possible outcomes.

So should use of plain C-language loads and stores for shared variables be completely abolished throughout the kernel?

Absolutely not.

For one thing, it is often the case that a given plain C-language load and store will be data-race free, as illustrated by the next few sections.

The prevalence and usefulness of locking, particularly on systems with modest numbers of CPUs, is one reason why C and C++ did not add concurrency features for the first few decades of their existence. We should therefore expect that fully locked concurrent code should do fine with plain C-language accesses. For example, consider this fully locked store-buffering litmus test:

> Litmus Test #8```
>  1 C C-SB+l-p-p-u+l-p-p-u 2 3 { 4 } 5 6 P0(int \*x0, int \*x1, spinlock\_t \*s) 7 { 8 int r1; 9 10 spin\_lock(s); 11 \*x0 = 1; 12 r1 = \*x1; 13 spin\_unlock(s); 14 } 15 16 P1(int \*x0, int \*x1, spinlock\_t \*s) 17 { 18 int r1; 19 20 spin\_lock(s); 21 \*x1 = 1; 22 r1 = \*x0; 23 spin\_unlock(s); 24 } 25 26 exists (0:r1=0 /\\ 1:r1=0) 
> ```

As expected, LKMM shows that this litmus test produces only the expected serialized outcomes, and does so without data races:

> Outcome for Litmus Test #8 (linux-kernel model)```
>  1 Test C-SB+l-p-p-u+l-p-p-u Allowed 2 States 2 3 0:r1=0; 1:r1=1; 4 0:r1=1; 1:r1=0; 5 No 6 Witnesses 7 Positive: 0 Negative: 2 8 Condition exists (0:r1=0 /\\ 1:r1=0) 9 Observation C-SB+l-p-p-u+l-p-p-u Never 0 2 10 Time C-SB+l-p-p-u+l-p-p-u 0.01 11 Hash=a1b190dd8375d869bc8826836e05f943 
> ```

But locking is not the only data-race-free synchronization primitive.

Reference counting has, if anything, been in use longer than has locking. It should therefore be no surprise that it is possible to atomically manipulate reference counts in such a way as to permit plain C-language access to shared variables. One approach uses atomic\_dec\_and\_test() so that the task that decrements the reference count to zero owns all the data. The following (fanciful) litmus test illustrates this design pattern:

> Litmus Test #9```
>  1 C C-SB+p-rc-p-p+p-rc-p-p 2 3 { 4 atomic\_t rc=2; 5 } 6 7 P0(int \*x0, int \*x1, atomic\_t \*rc) 8 { 9 int r0; 10 int r1; 11 12 \*x0 = 1; 13 if (atomic\_dec\_and\_test(rc)) { 14 r0 = \*x0; 15 r1 = \*x1; 16 } 17 } 18 19 P1(int \*x0, int \*x1, atomic\_t \*rc) 20 { 21 int r0; 22 int r1; 23 24 \*x1 = 1; 25 if (atomic\_dec\_and\_test(rc)) { 26 r0 = \*x0; 27 r1 = \*x1; 28 } 29 } 30 31 exists ~((0:r0=1 /\\ 0:r1=1 /\\ 1:r0=0 /\\ 1:r1=0) \\/ 32 (0:r0=0 /\\ 0:r1=0 /\\ 1:r0=1 /\\ 1:r1=1)) 
> ```

Initially, each process owns its variable, that is, P0() owns x0 and P1() owns x1. This reference count rc is initialized to the value 2 on line 4, indicating that both processes still own their respective variables. Each process updates its variable (lines 12 and 24), then releases its reference on rc (lines 13 and 25). The "winning" process that decrements rc to zero reads out both values, so that its values of r0 and r1 are equal to the value 1. The "losing" process's local variables remain zero. The exists clause on line 31 verifies this relationship:

> Outcome for Litmus Test #9 (linux-kernel model)```
>  1 Test C-SB+p-rc-p-p+p-rc-p-p Allowed 2 States 2 3 0:r0=0; 0:r1=0; 1:r0=1; 1:r1=1; 4 0:r0=1; 0:r1=1; 1:r0=0; 1:r1=0; 5 No 6 Witnesses 7 Positive: 0 Negative: 2 8 Condition exists (not (0:r0=1 /\\ 0:r1=1 /\\ 1:r0=0 /\\ 1:r1=0 \\/ 0:r0=0 /\\ 0:r1=0 /\\ 1:r0=1 /\\ 1:r1=1)) 9 Observation C-SB+p-rc-p-p+p-rc-p-p Never 0 2 10 Time C-SB+p-rc-p-p+p-rc-p-p 0.02 11 Hash=7692409758270a77b577b11ab7cca3e3 
> ```

**Quick Quiz 6**:

I have seen plain C-language incrementing and decrementing of reference counters. How can that possibly work?

[Answer](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#qq6answer)

As expected, there are no data races and the "winner" always safely reads out the data.

A common RCU use case inserts items into a linked data structure. If these items are initialized prior to insertion and if the non-pointer fields are never changed after insertion, then plain C-language accesses can be used throughout, as illustrated by this litmus test:

> Litmus Test #10```
>  1 C C-MP+p-rap+rl-rd-p-rul 2 3 { 4 int z=42; (\* Initial garbage value \*) 5 int y=2; 6 int \*x=&y; (\* x is the list head; initially it points to y \*) 7 } 8 9 P0(int \*\*x, int \*y, int \*z) 10 { 11 \*z = 1; 12 rcu\_assign\_pointer(\*x, z); // Now x points to z. 13 } 14 15 P1(int \*\*x, int \*y, int \*z) 16 { 17 int \*r1; 18 int r2; 19 20 rcu\_read\_lock(); 21 r1 = rcu\_dereference(\*x); // Pick up list head. 22 r2 = \*r1; // Pick up value. 23 rcu\_read\_unlock(); 24 } 25 26 locations \[x; y; z\] 27 exists (1:r1=z /\\ 1:r2=42) (\* Better not be pre-initialization value!!! \*) 
> ```

**Quick Quiz 7**:

But given that Litmus Test #10 has no

synchronize\_rcu()

, what is the purpose of the

rcu\_read\_lock()

on line 17 and the

rcu\_read\_unlock()

on line 20?

[Answer](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#qq7answer)

(Note that herd requires

(\*

a different comment syntax

\*)

in the initializer portion of the file.) Lines 5 and 6 abuse

herd7

to create a rudimentary linked data structure, with

x

initially referencing

y

.

P0()

initializes

z

on line 11 and links it into the list on line 12.

P1()

then picks up pointer

x

and dereferences it within the confines of an RCU read-side critical section in the normal manner.

This avoids data races and also prevents P0() from seeing pre-initialization garbage in z, which LKMM confirms:

> Outcome for Litmus Test #10 (linux-kernel model)```
>  1 Test C-MP+p-rap+rl-rd-p-rul Allowed 2 States 2 3 1:r1=y; 1:r2=2; x=z; y=2; z=1; 4 1:r1=z; 1:r2=1; x=z; y=2; z=1; 5 No 6 Witnesses 7 Positive: 0 Negative: 2 8 Condition exists (1:r1=z /\\ 1:r2=42) 9 Observation C-MP+p-rap+rl-rd-p-rul Never 0 2 10 Time C-MP+p-rap+rl-rd-p-rul 0.01 11 Hash=fbe83006932079946732b23c5af9033d 
> ```

It is also necessary to remove data from linked data structures and free them, at least if we are to avoid memory leaks. This process is illustrated with a similar litmus test:

> Litmus Test #11```
>  1 C C-MP+rap-sync-p+rl-rd-rd-rul 2 3 { 4 int z=1; 5 int y=2; 6 int \*x=&y; (\* x is the list head; initially it points to y \*) 7 } 8 9 P0(int \*\*x, int \*y, int \*z) 10 { 11 rcu\_assign\_pointer(\*x, z); // Now x points to z. 12 synchronize\_rcu(); 13 \*y = 0; // Emulate kfree(y). 14 } 15 16 P1(int \*\*x, int \*y, int \*z) 17 { 18 int \*r1; 19 int r2; 20 21 rcu\_read\_lock(); 22 r1 = rcu\_dereference(\*x); // Pick up list head. 23 r2 = \*r1; // Pick up value. 24 rcu\_read\_unlock(); 25 } 26 27 locations \[1:r1; x; y; z\] 28 exists (1:r2=0) (\* Better not be freed!!! \*) 
> ```

This again avoids data races and also prevents readers from creating a use-after-free bug:

> Outcome for Litmus Test #11 (linux-kernel model)```
>  1 Test C-MP+rap-sync-p+rl-rd-rd-rul Allowed 2 States 2 3 1:r1=y; 1:r2=2; x=z; y=0; z=1; 4 1:r1=z; 1:r2=1; x=z; y=0; z=1; 5 No 6 Witnesses 7 Positive: 0 Negative: 2 8 Condition exists (1:r2=0) 9 Observation C-MP+rap-sync-p+rl-rd-rd-rul Never 0 2 10 Time C-MP+rap-sync-p+rl-rd-rd-rul 0.00 11 Hash=abfbb3196e583a4f3945a3e3846442b0 
> ```

It is also possible to use synchronize\_rcu() as an [extremely heavy memory barrier](https://lwn.net/Articles/573497/), gaining an effect similar to Litmus Test #3:

> Litmus Test #12```
>  1 C C-MP+p-sync-o+rl-o-ctrl-p-rul 2 3 { 4 } 5 6 P0(int \*x0, int \*x1) 7 { 8 \*x0 = 1; 9 synchronize\_rcu(); 10 WRITE\_ONCE(\*x1, 1); 11 } 12 13 P1(int \*x0, int \*x1) 14 { 15 int r1; 16 int r2; 17 18 rcu\_read\_lock(); 19 r1 = READ\_ONCE(\*x1); 20 if (r1) { 21 r2 = \*x0; 22 } 23 rcu\_read\_unlock(); 24 } 25 26 exists (1:r1=1 /\\ 1:r2=0) 
> ```

LKMM confirms that this avoids both data races and the undesirable outcome flagged by the exists clause:

> Outcome for Litmus Test #12 (linux-kernel model)```
>  1 Test C-MP+p-sync-o+rl-o-ctrl-p-rul Allowed 2 States 2 3 1:r1=0; 1:r2=0; 4 1:r1=1; 1:r2=1; 5 No 6 Witnesses 7 Positive: 0 Negative: 2 8 Condition exists (1:r1=1 /\\ 1:r2=0) 9 Observation C-MP+p-sync-o+rl-o-ctrl-p-rul Never 0 2 10 Time C-MP+p-sync-o+rl-o-ctrl-p-rul 0.00 11 Hash=7672d2fc273055d3dcf0fc68801e113a 
> ```

In short, these past few sections have shown a few of the great many situations in which plain C-language accesses to shared variables are perfectly safe and legitimate. However, [Mr. Murphy](https://en.wikipedia.org/wiki/Murphy%27s_law) guarantees that complications can always arise, and one such complication is presented in the following section.

Suppose that you have a nice simple reference-counting scheme like the one shown in Litmus Test #9, but you need to add a printk() or an event trace to help debug some related problem. The straightforward approach might result in the following:

> Litmus Test #13```
>  1 C C-SBr+p-rc-p-p+p-rc-p-p+p 2 3 { 4 atomic\_t rc=2; 5 } 6 7 P0(int \*x0, int \*x1, atomic\_t \*rc) 8 { 9 int r0; 10 int r1; 11 12 \*x0 = 1; 13 if (atomic\_dec\_and\_test(rc)) { 14 r0 = \*x0; 15 r1 = \*x1; 16 } 17 } 18 19 P1(int \*x0, int \*x1, atomic\_t \*rc) 20 { 21 int r0; 22 int r1; 23 24 \*x1 = 1; 25 if (atomic\_dec\_and\_test(rc)) { 26 r0 = \*x0; 27 r1 = \*x1; 28 } 29 } 30 31 P2(int \*x0, int \*x1) // Emulate debug output. 32 { 33 int r0; 34 int r1; 35 36 r0 = \*x0; 37 r1 = \*x1; 38 } 39 40 exists ~(0:r0=0:r1 /\\ 1:r0=1:r1 /\\ ~(0:r0=1:r0) /\\ ~(0:r0=1:r1)) 
> ```

Unfortunately, this straightforward approach results in data races:

> Outcome for Litmus Test #13 (linux-kernel model)```
>  1 Test C-SBr+p-rc-p-p+p-rc-p-p+p Allowed 2 States 2 3 0:r0=0; 0:r1=0; 1:r0=1; 1:r1=1; 4 0:r0=1; 0:r1=1; 1:r0=0; 1:r1=0; 5 No 6 Witnesses 7 Positive: 0 Negative: 8 8 Flag data-race 9 Condition exists (not (0:r0=0:r1 /\\ 1:r0=1:r1 /\\ not (0:r0=1:r0) /\\ not (0:r0=1:r1))) 10 Observation C-SBr+p-rc-p-p+p-rc-p-p+p Never 0 8 11 Time C-SBr+p-rc-p-p+p-rc-p-p+p 0.05 12 Hash=f752f7f65493e036e734709bdb9233be 
> ```

One response to this situation would be to quickly apply WRITE\_ONCE() to all the now-conflicting plain C-language stores, namely those on lines 12 and 24. However, in larger code bases, the typos that are likely to ensue might introduce bugs, and frequent applying and removing of WRITE\_ONCE() would certainly be a maintenance nightmare.

Another response would be to take a look at the [table in the first article in this series](https://lwn.net/Articles/793253/#How%20Real%20Is%20All%20This?) and to note that the only common-case store transformation is [store fusing](https://lwn.net/Articles/793253/#Store%20Fusing), which should not be problem for otherwise correct concurrent code. This suggests that use of READ\_ONCE() is much more important than use of WRITE\_ONCE(), a position recently [taken](https://lore.kernel.org/lkml/CAHk-=wiOhiAJVU71968tAND6rrEJSaYPg7DXK6Y6iiz7_RJACw@mail.gmail.com/) and later [reiterated](https://lore.kernel.org/lkml/CAHk-=whjEq6uEt0o0Ur9Epa7EKVvEFUVJVFJ+heJCv9ehV7pyA@mail.gmail.com/) by none other than Linus Torvalds.

Some might attack this position as a head-in-the-sand denial of the C standard, but as Torvalds [pointed out](https://lore.kernel.org/lkml/CAHk-=wi_KeD1M-_-_SU_H92vJ-yNkDnAGhAS=RR1yNNGWKW+aA@mail.gmail.com/):

If such garbage happens, we need to fix the compiler, the same way we already do with

> \-fno-strict-aliasing  
> \-fno-delete-null-pointer-checks  
> \-fno-strict-overflow  

because all those "optimizations" are just fundamentally unsafe and wrong.

In short, the kernel community will be taking on the responsibility of ensuring that new releases of the compiler won't break their code, and taking appropriate actions to deal with any problematic optimizations that might appear. For an example, consider [this one](https://lore.kernel.org/lkml/20190821103200.kpufwtviqhpbuv2n@willie-the-truck/), [which has a fix for volatile](https://gcc.gnu.org/ml/gcc-patches/2019-08/msg01538.html) on the way. And, to be fair, this community has had its share of successes, so that many past [problems](https://lwn.net/Articles/478657/) have been resolved.

But what about those of us who would [prefer not to live in quite so much fear of the big bad optimizing compiler](https://lore.kernel.org/lkml/20190820135612.GS2332@hirez.programming.kicks-ass.net/)? Again quoting [Torvalds](https://lore.kernel.org/lkml/CAHk-=wiOhiAJVU71968tAND6rrEJSaYPg7DXK6Y6iiz7_RJACw@mail.gmail.com/):

In the end, the most common reason for a WRITE\_ONCE() is mostly just "to visually pair up with the non-synchronized read that uses READ\_ONCE()".

**Quick Quiz 8**:

Are you

_sure_

that

_all_

situations involving data races need at least one

READ\_ONCE()

?

[Answer](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#qq8answer)

Thus, if you want to use

WRITE\_ONCE()

for a data-racy store, Torvalds is OK with that as long as there is a corresponding

READ\_ONCE()

of that same variable.

One approach is to mark all accesses that are subject to data races, both loads and stores. To this end, here is a list of situations allowing plain loads and stores for some accesses to a given variable, while requiring markings (such as READ\_ONCE() and WRITE\_ONCE()) for other accesses to that same variable:

1.  A shared variable is only modified by a given owning CPU or thread, but is read by other CPUs or threads. All stores must use WRITE\_ONCE(). The owning CPU or thread may use plain loads. Everything else must use READ\_ONCE() for loads.
2.  A shared variable is only modified while holding a given lock, but is read by code not holding that lock. All stores must use WRITE\_ONCE(). CPUs or threads holding the lock may use plain loads. Everything else must use READ\_ONCE() for loads.
3.  A shared variable is only modified while holding a given lock by a given owning CPU or thread, but is read by other CPUs or threads or by code not holding that lock. All stores must use WRITE\_ONCE(). The owning CPU or thread may use plain loads, as may any CPU or thread holding the lock. Everything else must use READ\_ONCE() for loads.
4.  A shared variable is only accessed by a given CPU or thread and by a signal or interrupt handler running in that CPU's or thread's context. The handler can use plain loads and stores, as can any code that has prevented the handler from being invoked, that is, code that has blocked signals and/or interrupts. All other code must use READ\_ONCE() and WRITE\_ONCE().
5.  A shared variable is only accessed by a given CPU or thread and by a signal or interrupt handler running in that CPU's or thread's context, and the handler always restores the values of any variables that it has written before return. The handler can use plain loads and stores, as can any code that has prevented the handler from being invoked, that is, code that has blocked signals and/or interrupts. All other code can use plain loads, but must use WRITE\_ONCE() to prevent store tearing, store fusing, and invented stores.

**Quick Quiz 9**:

What needs to happen if an interrupt or signal handler might itself be interrupted?

[Answer](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#qq9answer)

In most other cases, loads from and stores to a shared variable must use

READ\_ONCE()

and

WRITE\_ONCE()

or stronger, respectively. But it bears repeating that neither

READ\_ONCE()

nor

WRITE\_ONCE()

provide any ordering guarantees other than within the compiler.

Other developers might choose to omit the WRITE\_ONCE() calls (perhaps give or take stores of constants), but otherwise follow the advice shown above. Still other developers might choose more aggressive paths.

LKMM now handles plain loads and stores, but at the end of the day, coding decisions are of course in the hands of the developers and maintainers.

Many of the limitations [called out in the 2017 LKMM LWN article](https://lwn.net/Articles/720550/#Conclusions) still apply, but they do bear repeating:

1.  Multiple access sizes are not supported.
2.  Partially overlapping access sizes are not supported.
3.  Nontrivial variables, including arrays and structures, are not supported. However, trivial linked lists are still supported.
4.  Dynamic memory allocation is not supported.
5.  Exceptions and interrupts are not supported.
6.  I/O, including DMA, is not supported.
7.  Self-modifying code is not supported, despite its being used in a surprisingly large number of places in the kernel, including the "alternative" mechanism, the function tracer, the eBPF JIT compiler, and the module loader.
8.  This memory model does not constitute an official statement by the various CPU vendors on their respective architectures, despite some of their employees being on the author list. For example, any of these vendors might report bugs at any time against any version of this memory model. This memory model is therefore not a substitute for a carefully designed and vigorously executed validation regime. In addition, this memory model is under active development and might change at any time. Finally, despite much welcome progress, there are still quite a few CPU families lacking formal memory models.
9.  It is quite possible that this memory model will disagree with CPU architectures or with real hardware. For example, the model might well choose to allow behavior that all CPUs forbid if forbidding that behavior would render the model excessively complex. On the other hand, any situation where the model forbids behavior that some CPU allows constitutes a bug, either in the model or in the CPU. However, there is work underway to automatically check that LKMM's verdict on specific litmus tests is compatible with herd-based formal models for the underlying hardware.
10.  This tool is exponential in nature. Litmus tests that seem quite small compared to the entire Linux kernel might well take geologic time for the herd tool to analyze. That said, this tool can be extremely effective in exhaustively analyzing the code at the core of a synchronization primitive.
11.  The herd tool can only detect problems for which you have coded an assertion. This weakness is common to all formal methods, and is one reason that we expect testing to continue to be important. In the [immortal words of Donald Knuth (scroll to the bottom)](https://www-cs-faculty.stanford.edu/~knuth/faq.html): "Beware of bugs in the above code; I have only proved it correct, not tried it."

However, there have been some areas of progress since 2017:

1.  Limited arithmetic is now available.
2.  A great many read-modify-write atomic operations are now supported, but the kernel community creates new ones at a surprisingly rapid rate. Therefore, it is unlikely that LKMM will be able to claim full coverage of all the kernel's read-modify-write atomic operations, at least not for very long.
3.  [SRCU](https://mirrors.edge.kernel.org/pub/linux/kernel/people/paulmck/LWNLinuxMM/srcu.html) is now supported. However, the modeling of RCU and SRCU still excludes asynchronous grace-period primitives such as call\_rcu() and srcu\_barrier().
4.  [Locking](https://mirrors.edge.kernel.org/pub/linux/kernel/people/paulmck/LWNLinuxMM/lock.html) is now supported, but only exclusive locking. Reader-writer locking is still on the to-do list, as is the recently proposed double-lock that can have multiple readers or multiple writers, but not both readers and writers at the same time.
5.  Plain C-language accesses are now supported, and compiler optimizations are modeled by (conservatively) flagging data races.

A number of LKMM's limitations appear to be inherent, but the good news is that significant progress has been made. However, the conservative treatment of data races means that LKMM should not be put forward as the final arbiter of what constitutes correct use of plain C-language accesses. As noted in the first article, in some cases developers and maintainers will continue to need to live with a healthy fear of the big bad optimizing compiler.

This article has demonstrated LKMM's new ability to handle plain C-language accesses using a pair of extended examples, and then shown how locking, reference counting, and RCU can be used in conjunction with plain accesses in a data-race-free manner. It then looked at complications due to debug output, presented a couple of possible access-marking policies, and finally presented an updated view of LKMM's limitations and progress.

This article showed that, although LKMM takes an expansive view of the concept of data races, it is easy to force it to model less expansive views. One approach is to mark selected accesses with READ\_ONCE() or WRITE\_ONCE() in the litmus test. For cases where the compiler has more freedom, it may be necessary to supply a number of litmus tests, each representing a different set of possible compiler optimizations.

LKMM is thus useful for modeling plain C-language accesses across a wide range of access-marking policies, and should thus be useful to a wide range of developers and maintainers.

#### Acknowledgments

As before, we owe thanks to a surprisingly large number of compiler writers and members of the C and C++ standards committees who introduced us to some of the things a big bad optimizing compiler can do, and to SeongJae Park for his help in rendering an earlier draft of [the access-marking polices section](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Access-Marking%20Policies) human-readable. We are also grateful to Kara Todd for her support of this effort.

**Quick Quiz 1**: But we shouldn't be afraid at all for things like on-stack or per-CPU variables, right?

**Answer**: Although on-stack and per-CPU variables are often guaranteed to be untouched by other CPUs and tasks, the kernel really does allow them to be concurrently accessed in many cases. You do have to go out of your way to make this happen, say by explicitly passing the address of such a variable to another thread, but it's certainly not impossible.

For example, the \_wait\_rcu\_gp() function uses an on-stack \_\_rs\_array\[\] array of rcu\_synchronize structures which, in turn, contain rcu\_head and completion structures. The address of the rcu\_head structure is passed to call\_rcu(), which results in concurrent accesses to this structure, and eventually also to the completion structure.

Similar access patterns may be found for per-CPU variables.

[**Back to Quick Quiz 1**.](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Quick%20Quiz%201)

**Quick Quiz 2**: But suppose only one of the accesses to a given variable is a plain C-language access, and that access is the only store. Should this be considered a data race?

**Answer**: Yes, this would definitely be a data race.

The plain C-language access might be subject to store tearing, code reordering, invented stores, and store-to-load transformations. Any of these transformations could ruin your concurrent algorithm's day.

However, as will be discussed in the [Debug output](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Debug%20Output) section, there is some reason to believe that compilers are less likely to adversely optimize stores than loads. It all depends on how much fear you need in your life.

[**Back to Quick Quiz 2**.](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Quick%20Quiz%202)

**Quick Quiz 3**: Why the cop-out? Why not just do the work required to ensure that the list of states and the Observation line are all accurate?

**Answer**: Because providing perfect accuracy would require perfect foresight, in particular, knowing exactly what optimizations all compilers, past, present, and future, might apply to this code. Worse yet, this list of optimizations will vary from compiler to compiler, and even with different command-line options for the same compiler. Therefore, LKMM's only real alternative is to throw up its hands and warn the user of the data race.

[**Back to Quick Quiz 3**.](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Quick%20Quiz%203)

**Quick Quiz 4**: But the outcome "1:r1=0; 1:r2=1;" also disappeared. Why?

**Answer**: If r1 is zero, the load into r2 never happens, which means that r2 retains its initial value of zero. The outcome "1:r1=0; 1:r2=1;” therefore cannot happen.

Had we instead marked accesses to x0 in Litmus Test #2 with READ\_ONCE() and WRITE\_ONCE(), all three outcomes would still be possible. (But don't take our word for it, try it out!

[**Back to Quick Quiz 4**.](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Quick%20Quiz%204)

**Quick Quiz 5**: But wait! Given that READ\_ONCE() provides no ordering, why would [Litmus Test #5](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#litmus5) avoid the undesirable outcome?

**Answer**: First, please note that READ\_ONCE() really does provide _some_ ordering, namely, it prevents the compiler from reordering the READ\_ONCE() with any other marked access. However, this restriction in no way applies to the CPU.

But CPU-level ordering is not required because, as the name suggests, READ\_ONCE(a) is guaranteed to read a only once, and thus store the same value to both b and c. Because the undesirable outcome shown in the exists clause requires different final values for b and c, READ\_ONCE() suffices despite its lack of ordering properties.

[**Back to Quick Quiz 5**.](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Quick%20Quiz%205)

**Quick Quiz 6**: I have seen plain C-language incrementing and decrementing of reference counters. How can that possibly work?

**Answer**: It can work if the reference counter in question is protected by a lock. But yes, if there is no lock, then incrementing and decrementing of reference counters must be done via the handy and convenient atomic operations that the kernel provides for this purpose.

[**Back to Quick Quiz 6**.](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Quick%20Quiz%206)

**Quick Quiz 7**: But given that Litmus Test #10 has no synchronize\_rcu(), what is the purpose of the rcu\_read\_lock() on line 17 and the rcu\_read\_unlock() on line 20?

**Answer**: In theory, they could be omitted because there is in fact no synchronize\_rcu() for them to interact with. They nevertheless serve as valuable documentation. In addition, their presence could save considerable time and frustration should someone later add an updater to this litmus test.

[**Back to Quick Quiz 7**.](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Quick%20Quiz%207)

**Quick Quiz 8**: Are you _sure_ that _all_ situations involving data races need at least one READ\_ONCE()?

**Answer**: First, developers who are concerned about store tearing, fused stores, invented stores, or store-to-load transformations will consider a situation involving concurrent stores to the same variable to be a data race if at least one of them is a plain C-language store, regardless of READ\_ONCE().

But suppose that the variable is both loaded from and stored to, and that there are concurrent stores which might reasonably be marked with WRITE\_ONCE() by sufficiently fearful developers. Are we sure that at least one of the loads from that variable will need to use READ\_ONCE()?

We should be reasonably sure, but of course not [_absolutely_ sure](https://lore.kernel.org/lkml/20190817222834.GJ28441@linux.ibm.com/). For example, in theory, all of the stores to a given variable could be executed while read-holding a given reader-writer lock and all loads could be executed while write-holding that same lock. In this case, only the stores are involved in data races. In practice, what would be the use case for such a thing?

[**Back to Quick Quiz 8**.](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Quick%20Quiz%208)

**Quick Quiz 9**: What needs to happen if an interrupt or signal handler might itself be interrupted?

**Answer**: Then that interrupt handler must follow the same rules that are followed by other interrupted code. Only those handlers that cannot be themselves interrupted or that access no variables shared with an interrupting handler may safely use plain accesses, and even then only if those variables cannot be concurrently accessed by some other CPU or thread.

[**Back to Quick Quiz 9**.](https://lwn.net/SubscriberLink/799218/54a30b2467e46e16/#Quick%20Quiz%209)

> **Did you like this article?** Please accept our [trial subscription offer](https://lwn.net/Promo/slink-trial2-3/claim) to be able to see more content like it and to participate in the discussion.

* * *

(

[Log in](https://lwn.net/Login/?target=/Articles/799218/)

to post comments)

  
  
from Hacker News https://ift.tt/2B8AXnu