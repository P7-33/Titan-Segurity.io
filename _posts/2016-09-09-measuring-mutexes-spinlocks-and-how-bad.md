---
title: 'Measuring mutexes, spinlocks and how bad the Linux scheduler is'
date: 2020-01-01T01:55:00+01:00
draft: false
---

![](https://s0.wp.com/i/blank.jpg "Measuring Mutexes, Spinlocks and how Bad the Linux Scheduler Really is | Probably Dance")  

This blog post is one of those things that just blew up. From a tiny observation at work about odd behaviors of spinlocks I spent months trying to find good benchmarks, (still not entirely successful) writing my own spinlocks, mutexes and condition variables and even contributing a patch to the Linux kernel. The main thing I’ll try to answer is to give some more informed guidance on the endless discussion of mutex vs spinlock. Besides that I found that most mutex implementations are really good, that most spinlock implementations are pretty bad, and that the Linux scheduler is OK but far from ideal. The most popular replacement, the MuQSS scheduler has other problems instead. (the Windows scheduler is pretty good though)

So this all started like this: I overheard somebody at work complaining about mysterious stalls while porting Rage 2 to Stadia. The only thing those mysterious stalls had in common was that they were all using spinlocks. I was curious about that because I happened to be the person who wrote the spinlock we were using. The problem was that there was a thread that spent several milliseconds trying to acquire a spinlock at a time when no other thread was holding the spinlock. Let me repeat that: The spinlock was free to take yet a thread took multiple milliseconds to acquire it. In a video game, where you have to get a picture on the screen every 16 ms or 33 ms (depending on if you’re running at 60hz or 30hz) a stall that takes more than a millisecond is terrible. Especially if you’re literally stalling all threads. (as was happening here) In our case we were able to make the problem go away by replacing spinlocks with mutexes, but that leads to the question: How do you even measure whether a spinlock is better than a mutex, and what makes a good spinlock?

If you search for this you’ll find lots of benchmarks that all come to the conclusion that spinlocks are better. (like [this](http://demin.ws/blog/english/2012/05/05/atomic-spinlock-mutex/), [this](http://www.alexonlinux.com/pthread-mutex-vs-pthread-spinlock) or [this](https://nathanpetersen.com/2019/02/17/optimizing-for-workloads-linux-spinlocks-vs-mutexes/)) What these benchmarks have in common is that they measure code in which there is nothing else to do except fight over the lock. In that environment the only thing that makes sense is to use a spinlock. Because if you go to sleep, all that will happen is that some other thread will wake up that will fight over the same lock.

Is that realistic? It depends on your setup. Usually you’ll want to create one software thread per hardware thread and if you only have exactly that, then there really is no benefit of ever going to sleep. (as long as you make sure to not block the other hyper-thread running on the same core) But in practice it doesn’t work out that cleanly. Maybe a third party library has its own threads that run besides your threads (doing audio processing or physics calculations or who knows what) or maybe you’ll have some work that needs to run “at some point, as long as it doesn’t get in the way” which you’ll schedule to run at low priority “in the gaps” when other threads are blocked. If you don’t have that, and your cores are actually well-used, I would be very impressed. So none of these benchmarks are realistic because, at least in games, there is usually other work that could happen other than spinning until you get the lock.

Even if you are in the situation where there is one software thread per hardware thread and you think you’re doing the right thing by using a spinlock, you might be making future code evolution harder. If in the future you use a library that does its own threading or somebody wants to come along and add a “low priority” thread that can run in the gaps and do some work that doesn’t need to get done immediately, they’ll have to go through and replace your spinlocks with mutexes. (there is probably also a battery-life argument to be made, but I don’t know enough about that)

And finally, none of those benchmarks measure the problem that I ran into: A thread that took a crazy long time to acquire a lock. These benchmarks measure throughput, not latency. (to be fair I also wouldn’t have thought to measure latency until it became a problem)

Defining Mutexes and Spinlocks
------------------------------

But before we move on, I have already gone on for too long without describing the terms. When I say “mutex” I mean a synchronization primitive that will make the thread go to sleep if it’s blocked. Spinlocks do not go to sleep if they don’t acquire the lock, they just try again. There are also “adaptive mutexes” which will try to spin for a while and if they’re not successful, they’ll go to sleep to let other threads run. And finally all of these have “fair” versions which guarantee progress for all threads. Without fairness, if you have two threads, A and B, you could in theory get a situation where A keeps on getting the lock and B is always just a bit too late. This is never a problem with two threads, but the more threads you have, the more likely you are to get those cases where one thread is left out for a very long time.

If you need a mutex in C++, std::mutex is actually really good on all the platforms that I know of. If you need a spinlock, you might be tempted to use [std::atomic\_flag](https://en.cppreference.com/w/cpp/atomic/atomic_flag), which looks like it’s perfectly intended for writing a spinlock (and that’s what my spinlock was using when we encountered the problem that started this investigation) but there is a subtle problem with atomic\_flag. I learned about the problem by reading the [slides](https://gpuopen.com/gdc-presentations/2019/gdc-2019-s2-amd-ryzen-processor-software-optimization.pdf) of an AMD presentation at this years Game Developer Conference. On page 46 of those [slides](https://gpuopen.com/gdc-presentations/2019/gdc-2019-s2-amd-ryzen-processor-software-optimization.pdf) we find that you should prefer “test and test-and-set” over just test-and-set. To illustrate what that means, let me first implement a terrible spinlock using std::atomic\_flag:

```
 struct terrible\_spinlock { void lock() { while (locked.test\_and\_set(std::memory\_order\_acquire)) { } } void unlock() { locked.clear(std::memory\_order\_release); } private: std::atomic\_flag locked = ATOMIC\_FLAG\_INIT; }; 
```

To lock we call test\_and\_set which will return the old state. If it was false, nobody else has called test\_and\_set yet. If it was true, somebody else has already called this and we’ll have to try again. In unlock we just clear the flag again. The memory orderings tell the compiler and the CPU about which re-orderings are allowed. They are very important to avoid memory barriers and to keep the fast path (when the lock is free to take) fast, but they’re a big topic in themselves and will not be explained in this blog post.

So why is this terrible? The first reason is that while we’re spinning like this, we appear to the CPU and to the OS like a very busy thread and we will never be moved out of the way. So if the thread that has the lock is not currently running, we could be blocking it from running, causing it to not give up the lock.

But even if we added a way to indicate that other threads should take priority (like \_mm\_pause() or std::this\_thread::yield()) we have a second problem that has to do with the ownership of cache lines on multi-core processors. To ensure correctness when multiple processors are writing to the same memory, there are protocols for which processor is allowed to write. All current processor use some variant of the [MESI protocol](https://en.wikipedia.org/wiki/MESI_protocol), in which you have to force the “invalid” state on all other cores when modifying a cache line. That means that if multiple cores are banging on the spinlock above, they keep on fighting over who gets ownership and keep on invalidating the cache line for others. This leads to lots of coordination work and transferring of memory between the CPU caches, slowing down the whole system. In the AMD slides above they have a benchmark where one thread is doing a bunch of matrix multiplications, and fifteen threads are banging on a spinlock. On a terrible spinlock like this the matrix multiplications became ten times slower, even though they’re not even touching the same cache line. Completely unrelated work slows down.

So here is a spinlock written according to the AMD recommendations:

```
 struct spinlock\_amd { void lock() { for (;;) { bool was\_locked = locked.load(std::memory\_order\_relaxed); if (!was\_locked && locked.compare\_exchange\_weak(was\_locked, true, std::memory\_order\_acquire)) break; \_mm\_pause(); } } void unlock() { locked.store(false, std::memory\_order\_release); } private: std::atomic locked{false}; }; 
```

This fixes both of the issues above. (but we’ll still make one more improvement further down) It solves the first problem by calling \_mm\_pause() which the CPU uses as a hint that the other hyper-thread running on the same core should run instead of this thread, and it solves the second problem by loading the memory before attempting to make a change to it. In the MESI protocol this means that the cache line can be in the “shared” state on all cores which requires no communication between the CPU cores until the data actually changes.

So now that we have a spinlock that’s not terrible lets try benchmarking this.

Measuring Latency
-----------------

It’s always difficult to try to reproduce one-off occurrences like the one that started my investigation. Just because we saw a thread taking milliseconds to acquire a spinlock doesn’t mean that the problem was actually with the spinlock. Maybe something else was wrong. How do you even measure rare things like that? First off lets start with the simplest possible thing. On multiple threads run this loop:

```
 for (size\_t i = num\_loops; i != 0; --i) { auto time\_before = std::chrono::high\_resolution\_clock::now(); mutex.lock(); auto wait\_time = std::chrono::high\_resolution\_clock::now() - time\_before; longest\_wait = std::max(wait\_time, longest\_wait); mutex.unlock(); } 
```

So we take a timestamp before we call lock and a timestamp after we have succeeded in locking the mutex. (or a spinlock. It’s a template) Then we remember the longest time it took. In my benchmark num\_loops is 16384 (no particular significance to that number, just something that doesn’t run too fast or too slow) and I repeat the entire test 100 times to get more than one measurement. Then I take the four runs out of the hundred that had the longest waits and print how long the longest wait in that run was. The results are shocking:

Type

Average test duration

Four longest waits

std::mutex

62 ms

2.9 ms, 2.8 ms, 1.5 ms, 1.4 ms

terrible\_spinlock

825 ms

103.5 ms, 90.6 ms, 77.1 ms, 75.7 ms

spinlock\_amd

68 ms

62.3 ms, 61.5 ms, 60.9 ms, 59.8 ms

These are measurements for running the above test code on sixteen threads on a AMD Ryzen 7 1700. (which has eight cores, sixteen hyperthreads) The “average test duration” is the average time that it took to finish running the above loop in 16384 iterations on all cores. Based on that column we can confirm that using the terrible spinlock really does slow things down by a factor of 10, just like in the benchmark in the AMD presentation.

In the “longest wait” column we see huge wait times for the spinlocks. One of the threads in the spinlock\_amd test had to wait for 62.3 ms when the whole test only took 68 ms on average. Meaning most of the other threads probably got to finish their loops entirely before it even got to run once.

There is one improvement we can easily make to the spinlock to help with the really bad latency cases, we can call std::this\_thread::yield:

```
 struct spinlock { void lock() { for (int spin\_count = 0; !try\_lock(); ++spin\_count) { if (spin\_count ❬ 16) \_mm\_pause(); else { std::this\_thread::yield(); spin\_count = 0; } } } bool try\_lock() { return !locked.load(std::memory\_order\_relaxed) && !locked.exchange(true, std::memory\_order\_acquire); } void unlock() { locked.store(false, std::memory\_order\_release); } private: std::atomic❬bool❭ locked{false}; }; 
```

It’s roughly the same code as before except I replaced compare\_exchange with exchange and every once in a while I call std::this\_thread::yield(). Why every 16 spins? I tried a lot of different options and this one did well. The difference between \_mm\_pause() and yield() is that \_mm\_pause() is a hint for the CPU while yield() is a hint for the OS. In theory I shouldn’t need to hint anything to the OS here since I’m running sixteen software threads on sixteen hardware threads, but in practice it helps a lot. The longest wait gets reduced to 11.4 ms.

One question you may have is that since yield() is a OS call, don’t we lose the benefits of spinlocks? Because if we’re going to call into the OS anyway, why not use a full mutex? The answer is that yield() is actually a very cheap call. On my machine it takes roughly 130 nanoseconds, in both Linux and Windows. (that is of course if nothing else needs to run. If something else needs to run then we’ll have to wait longer to come back) We can afford to lose 130 nanoseconds every once in a while to keep the simplicity of a spinlock.

In any case all of these are terrible results. The best thing we’ve seen so far, std::mutex, can still take 3ms to acquire the lock. I think it’s about time that we give these “fair” mutexes a look.

The simplest fair exclusion mechanism to write is a ticket spinlock. The idea is that when you enter lock() you take a ticket and you wait for your number to be called. To implement that you just need to increment numbers, so the implementation is pretty simple:

```
 struct ticket\_spinlock { void lock() { unsigned my = in.fetch\_add(1, std::memory\_order\_relaxed); for (int spin\_count = 0; out.load(std::memory\_order\_acquire) != my; ++spin\_count) { if (spin\_count ❬ 16) \_mm\_pause(); else { std::this\_thread::yield(); spin\_count = 0; } } } void unlock() { out.store(out.load(std::memory\_order\_relaxed) + 1, std::memory\_order\_release); } private: std::atomic❬unsigned❭ in{0}; std::atomic❬unsigned❭ out{0}; };
```

When we enter we increment the “in” variable and then spin until the “out” variable has the same value. It looks more complicated than it is because of all the memory orderings and the spin count logic. Btw everyone gets the memory orderings on the unlock wrong. The load can be relaxed, and the increment does not have to be an atomic increment, but the store has to be a release. If you use an atomic fetch\_add() here, the fast path (when the lock is free to take) will be twice as slow. Does the ticket\_spinlock help? Here is the full table with all entries:

Type

Average test duration

Four longest waits

std::mutex

62 ms

2.9 ms, 2.8 ms, 1.5 ms, 1.4 ms

terrible\_spinlock

825 ms

103.5 ms, 90.6 ms, 77.1 ms, 75.7 ms

spinlock\_amd

68 ms

62.3 ms, 61.5 ms, 60.9 ms, 59.8 ms

spinlock

69 ms

11.4 ms, 10.8 ms, 10.4 ms, 9.9 ms

ticket\_spinlock

93 ms

1.5 ms, 1.5 ms, 1.49 ms, 1.48 ms

The ticket spinlock is worse on throughput, taking almost 50% longer to finish the test, but the wait time is pretty consistent. Where does that 1.5ms come from? I think it’s related to how long a scheduler time slice is on Linux, because it makes sense that the biggest outlier would be the time that it takes to get scheduled again. (remember these are outliers, the average wait is much shorter) We’ll see below that Windows does much better, because with the ticket\_spinlock, when it’s your time to get the lock, there is no way that it takes 1.5 ms for all the other threads to go through that tiny critical section, so we are mostly measuring scheduler overhead here.

Oh and if you want a fair mutex algorithm, (as opposed to a fair spinlock) they get much more complicated. You might be tempted to turn the ticket\_spinlock into a ticket\_mutex by using a futex, and this does work (it’s shown in [this talk](https://www.youtube.com/watch?v=Zcqwb3CWqs4#t=30m21s)) but it’s not ideal since you have no way of waking up the right sleeper. So every time that you increment you have to wake all sleepers and all but one will immediately go back to sleep. So a good fair mutex will usually involve some kind of linked list built on the stack of the sleeping threads, but that is hard to do, especially since you don’t want to be 100% fair because that really slows you down. (it’s called a [Lock Convoy](https://en.wikipedia.org/wiki/Lock_convoy)) It’s too much for this blog post to cover.

Measuring Idle Time
-------------------

You may have noticed that I’m not actually measuring the exact situation that we had at work. I said that a spinlock was free to take but it still took several milliseconds to be acquired. That’s not what I’m measuring above. When I have a large delay of acquiring the spinlock in the above, that is probably because some other thread keeps on winning and keeps on making progress. So depending on how you spread the work between the threads, this might not be a problem.

So how would we measure the situation I had at work? What I really want to measure is if nobody has the lock and somebody wants to take the lock, and it’s not being taken. It’s a bit harder to measure, but here is an attempt:

```
 for (size\_t i = num\_loops; i != 0; --i) { mutex.lock(); auto wait\_time = std::chrono::high\_resolution\_clock::now() - time\_before; if (first) first = false; else if (wait\_time ❭ longest\_idle) longest\_idle = wait\_time; time\_before = std::chrono::high\_resolution\_clock::now(); mutex.unlock(); } 
```

So I switched the order around. Instead of saving the timestamp before taking the lock, I save the timestamp just before releasing the lock. Then the next thread entering can measure how much time has passed since the last thread gave up the lock. The check for “if (first)” is necessary because in the first iteration of the loop the time wouldn’t have been set yet. Somebody has to give up the lock once for me to get a useful measurement. If there are long times where the lock is not being held even though a thread wants to take it, this would detect that.

Before showing the results I have to mention that finding long times here is more rare, so I ran the entire benchmark 1000 times instead of 100 times, as above. But then I found crazy outliers like the one I noticed at work right away:

Type

Average test duration

Four longest idle times

std::mutex

86 ms

0.8 ms, 0.28 ms, 0.26 ms, 0.25 ms

terrible\_spinlock

852 ms

134.8 ms, 124.6 ms, 119.7 ms, 96.5 ms

spinlock\_amd

65 ms

7.0 ms, 6.9 ms, 0.54 ms, 0.45 ms

spinlock

66 ms

1.4 ms, 1.2 ms, 0.33 ms, 0.32 ms

ticket\_spinlock

95 ms

13.0 ms, 3.3 ms, 2.6 ms, 2.4 ms

So this table is different from the previous table in that it shows how long the mutex was not being held even though somebody was trying to enter. Meaning for the terrible spinlock there was literally a time where the spinlock wasn’t being held, somebody was trying to enter, and it took them 134 ms to do so. The other, better spinlock implementations do much better, but on all of them we see wait times of more than a millisecond. The spinlock that I had written at work was probably slightly worse than spinlock\_amd in the table above, so no wonder we were seeing crazy long pauses. If I can reproduce these hitches in a couple of seconds in an artificial benchmark like this, of course you would see it if you profile a game for hitches for long enough. And we can also see why replacing the spinlock with a mutex solved the problem.

I have to say that I am really weirded out by the ticket\_spinlock performing this badly. I can’t explain what’s happening there. Why would that one in particular spend several milliseconds leaving the lock idle? Does the OS keep on giving time to the wrong threads? Does it ignore my yield calls? I actually can’t explain what’s happening with any of the spinlock cases. What is going on that we are literally spending more than a millisecond not holding the lock even though there are threads that would want to enter? It’s time to finally look at the Windows scheduler, because it does much better here.

Windows Scheduler
-----------------

Running the same benchmarks on the same machine in Windows, here are the results for the longest waits (the first table):

Type

Average test duration

Four longest waits

std::mutex

60ms

24.1 ms, 20.1 ms, 17.4 ms, 17.0 ms

terrible\_spinlock

168 ms

32.2 ms, 30.0 ms, 27.3 ms, 26.1 ms

spinlock\_amd

67 ms

61.1 ms, 57.8 ms, 57.0 ms, 56.5 ms

spinlock

63 ms

48.0 ms, 40.0 ms, 40.0 ms, 36.2 ms

ticket\_spinlock

95 ms

0.78 ms, 0.34 ms, 0.27 ms, 0.2 ms

Immediately we get a different feel. std::mutex makes individual threads wait longer, but runs faster overall. terrible\_spinlock does better for some reason, and ticket\_spinlock performs very well: It only has one outlier that isn’t all that bad, otherwise it has the best wait times we’ve seen yet.

Where Windows really does better is in the idle times:

Type

Average test duration

Four longest idle times

std::mutex

56 ms

0.58 ms, 0.46 ms, 0.27 ms, 0.19 ms

terrible\_spinlock

188 ms

21.1 ms, 20.9 ms, 18.2 ms, 18.0 ms

spinlock\_amd

68 ms

17.3 ms, 6.6 ms, 5.0 ms, 4.9 ms

spinlock

62 ms

0.16 ms, 0.14 ms, 0.14 ms, 0.14 ms

ticket\_spinlock

94 ms

0.38 ms, 0.35 ms, 0.26 ms, 0.25 ms

These numbers look much better. With std::mutex and with a properly written spinlock, the lock never sits idle for long. This is exactly what you want and what you’d expect. spinlock\_amd still has long times where the lock is free to take but nobody takes it. This just shows that you do need to call yield() while you’re spinning, even if you have one software thread per hardware thread. Otherwise the OS just might not schedule the right thread for some reason.

Alternative Linux scheduler
---------------------------

Really the Windows results just shows us that the Linux scheduler might take an unreasonably long time to schedule you again even if every other thread is sleeping or calls yield(). The Linux scheduler has been known to be problematic for a long time. A popular alternative scheduler was BFS, which among other things had this in it’s FAQ:

> For years we’ve been doing our workloads on linux to have more work than we had CPUs because we thought that the “jobservers” were limited in their ability to utilise the CPUs effectively (so we did make -j6 or more on a quad core machine for example). This scheduler proves that the jobservers weren’t at fault at all, because make -j4 on a quad core machine with BFS is faster than \*any\* choice of job numbers on CFS

BFS has since evolved into MuQSS, which is maintained by Con Kolivas [here](http://www.users.on.net/~ckolivas/kernel/). In order to run this, I had to compile my own Linux kernel. I tried watching a video on the side and for most of the build that worked, but then at a certain point the build used all 16 cores to compress something and my video stuttered and the audio went bad and it just became totally unwatchable. Worse than anything I had ever experienced on Windows. Trying the same thing again with MuQSS I had no problems. The video kept on playing fine. So while subjectively it’s immediately better, let’s try running our benchmarks on it to see how it performs. First, here are the results for the longest wait time again:

Type

Average test duration

Four longest waits

std::mutex

60 ms

0.20 ms, 0.18 ms, 0.18 ms, 0.17 ms

terrible\_spinlock

813 ms

94.4 ms, 8.6 ms, 8.6 ms, 7.1 ms

spinlock\_amd

72 ms

63.9 ms, 63.8 ms, 59.7 ms, 57.3 ms

spinlock

21 ms

7.3 ms, 6.6 ms, 4.2 ms, 4.0 ms

ticket\_spinlock

2538 ms

23.1 ms, 16.3 ms, 16.2 ms, 15.4 ms

And once again they look very different. ticket\_spinlock fell off a cliff and runs super slowly. std::mutex now performs great (slightly faster than before) and has very short wait times. spinlock somehow got crazy fast. Apparently this code can run three times faster. Who knew that the scheduler can have that much of an impact? (if I run this benchmark single-threaded, it finishes in just under 1 ms. So on sixteen threads it needs to take at least 16ms. 21ms is pretty close to ideal)

Let’s also look at how this scheduler performs when the mutex is free to take and somebody wants to take it. How long does it sit idle?

Type

Average test duration

Four longest idle times

std::mutex

73 ms

0.15 ms, 0.11 ms, 0.10 ms, 0.09 ms

terrible\_spinlock

1433 ms

94.8 ms, 85.1 ms, 83.6 ms, 72.1 ms

spinlock\_amd

67 ms

4.8 ms, 4.7 ms, 4.0 ms, 2.9 ms

spinlock

22 ms

4.4 ms, 4.3 ms, 3.8 ms, 3.7 ms

ticket\_spinlock

2518 ms

18.6 ms, 2.1 ms, 1.9 ms, 1.4ms

MuQSS does not do as well here as Windows. ticket\_spinlock performs terribly again, worse than terrible\_spinlock. On all the spinlocks we see long times where the lock just sat idle even though somebody was trying to acquire it. Only by using std::mutex can we ensure that we don’t get random long stalls. But when we do use std::mutex, we get much better results than with the default Linux scheduler.

So what conclusions can we draw from this? MuQSS is promising but it clearly has problems. It’s very impressive that the spinlock is suddenly three times faster than anything we saw with the other schedulers. But it’s a real problem that ticket\_spinlock suddenly performs terrible. I am pretty sure that people use ticket\_spinlocks in production.

SCHED\_RR and SCHED\_FIFO
-------------------------

When you create a thread on Linux you can say that you want to use a different scheduler. So I switched back to the normal Linux scheduler and tried creating threads with SCHED\_RR and SCHED\_FIFO. The first result is that your system slows to a crawl because those threads take priority over everything else. Even mouse movement gets choppy. But the idle times were much better. The results for both options were similar, so I’ll just show the results for SCHED\_RR. First lets get the wait times out of the way:

Type

Average test duration

Four longest waits

std::mutex

62 ms

4.4 ms, 4.3 ms, 1.5 ms, 1.5 ms

terrible\_spinlock

848 ms

10.3 ms, 4.9 ms, 3.3 ms, 3.0 ms

spinlock\_amd

73 ms

67.1 ms, 66.6 ms, 66.0 ms, 64.0 ms

spinlock

66 ms

5.2 ms, 4.4 ms, 4.1 ms, 3.8 ms

ticket\_spinlock

97 ms

9.0 ms, 0.28 ms, 0.16 ms, 0.14 ms

The results are actually pretty similar to the normal scheduler. The biggest difference is that ticket\_spinlock has much shorter waits. (except for one huge outlier) But looking at the times that the mutex sat idle we can see a bigger difference:

Type

Average test duration

Four longest idle times

std::mutex

76 ms

0.13 ms, 0.12 ms, 0.12 ms, 0.12 ms

terrible\_spinlock

2043 ms

40.6 ms, 4.2 ms, 1.2 ms, 0.76 ms

spinlock\_amd

70 ms

0.13 ms, 0.09 ms, 0.09ms, 0.09 ms

spinlock

62 ms

0.23 ms, 0.19 ms, 0.16 ms, 0.15 ms

ticket\_spinlock

97 ms

26.8 ms, 10.1 ms, 1.9 ms, 0.15 ms

Here the results look very different. The biggest idle times for std::mutex look better than they looked on Windows. ticket\_spinlock looks bad because it has three big outliers, but otherwise it was actually really stable. spinlock\_amd has the shortest idle times yet. If you don’t yield with this scheduler, the OS will let you run so the lock never sits idle.

So why isn’t this the default? The big problem is that these threads essentially run at a crazy high priority and you’re starving everything else on the system. I’ve heard stories of game developers trying to use SCHED\_FIFO or SCHED\_RR on Linux and while it seemed great for the game at first, they actually ran into problems because they were locking up other parts of the system, causing weird unexpected deadlocks for the game. They also ran into problems because not all of their threads needed the high priority thread options and those threads now never got to run. In the end it wasn’t worth it.

Further Work and Benchmark Code
-------------------------------

I think this is a good point to end the blog post. There are many open questions remaining (How do adaptive mutexes perform? What makes a good mutex? What is the right way to benchmark mutex throughput?) but this blog post is already quite long and already covers a lot of different topics. Those other questions will either have to wait for a future blog post, or you’ll have to investigate them yourself with my benchmarking code, which is uploaded [here](https://github.com/skarupke/mutex_benchmarks). (it requires [google benchmark](https://github.com/google/benchmark))

Guidance
--------

So what should we do based on the above? I hope to have convinced you to avoid spinlocks, even for very short sections. Spinlocks are only a benefit if you really really care about the fast path and are certain that the lock will essentially always be free to take. On my computer the fast path on a spinlock is roughly 7ns and on a mutex it’s roughly 14ns, so both of those numbers are very fast. But when spinlocks go bad, the scheduler can be really confused, at least on Linux. Maybe future scheduler improvements will change the results on this. It was very interesting to see that the spinlock was three times faster using the MuQSS scheduler.

But even taking that into account you get the problem that nothing else can run on your core. If you manage to use all your cores well using spinlocks, I would be very impressed. Chances are that if you want to fully utilize all your cores, you will eventually add work that can run “in the gaps” at low priority, and that’s only possible if you use mutexes, because you need to let the scheduler know what your gaps are. (of course this doesn’t apply if your work is very uniform, like you’re using 16 cores to compress a file or something like that. In that case there are no gaps to fill)

The other conclusion to take so far is that schedulers are an open problem. The Windows scheduler certainly does best on not keeping the lock idle (as long as you use std::mutex or a good spinlock) but the Linux schedulers have problems. This was known for a while simply because audio can stutter on Linux when all cores are busy (which doesn’t happen on Windows) but it’s good to have benchmarks for this. It is really bad that a lock can sit idle for milliseconds even though somebody is trying to get it. Now that game developers are slowly moving onto Linux, I predict that hiccups like that will go away within a couple years, as more work will be done on the scheduler.

  
  
from Hacker News https://ift.tt/2MHZcPz