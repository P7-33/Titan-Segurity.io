---
title: 'No nuances, just buggy code (was: related to Spinlock implementation)'
date: 2020-01-05T06:08:00+01:00
draft: false
---

By:

Linus Torvalds

(torvalds.delete@this.linux-foundation.org), January 3, 2020 6:05 pm

Beastian (no.email.delete@this.aol.com) on January 3, 2020 11:46 am wrote:  
\> I'm usually on the other side of these primitives when I write code as a consumer of them,  
\> but it's very interesting to read about the nuances related to their implementations:  
  
The whole post seems to be just wrong, and is measuring something completely different than what the author thinks and claims it is measuring.  
  
First off, spinlocks can only be used if you actually know you're not being scheduled while using them. But the blog post author seems to be implementing his own spinlocks in user space with no regard for whether the lock user might be scheduled or not. And the code used for the claimed "lock not held" timing is complete garbage.  
  
It basically reads the time before releasing the lock, and then it reads it after acquiring the lock again, and claims that the time difference is the time when no lock was held. Which is just inane and pointless and completely wrong.  
  
That's pure garbage. What happens is that  
  
(a) since you're spinning, you're using CPU time  
  
(b) at a random time, the scheduler will schedule you out  
  
(c) that random time might ne just after you read the "current time", but before you actually released the spinlock.  
  
So now you still hold the lock, but you got scheduled away from the CPU, because you had used up your time slice. The "current time" you read is basically now stale, and has nothing to do with the (future) time when you are _actually_ going to release the lock.  
  
Somebody else comes in and wants that "spinlock", and that somebody will now spin for a long while, since nobody is releasing it - it's still held by that other thread entirely that was just scheduled out. At some point, the scheduler says "ok, now you've used your time slice", and schedules the original thread, and _now_ the lock is actually released. Then another thread comes in, gets the lock again, and then it looks at the time and says "oh, a long time passed without the lock being held at all".  
  
And notice how the above is the _good_ schenario. If you have more threads than CPU's (maybe because of other processes unrelated to your own test load), maybe the next thread that gets shceduled isn't the one that is going to release the lock. No, that one already got its timeslice, so the next thread scheduled might be _another_ thread that wants that lock that is still being held by the thread that isn't even running right now!  
  
So the code in question is pure garbage. You can't do spinlocks like that. Or rather, you very much can do them like that, and when you do that you are measuring random latencies and getting nonsensical values, because what you are measuring is "I have a lot of busywork, where all the processes are CPU-bound, and I'm measuring random points of how long the scheduler kept the process in place".  
  
And then you write a blog-post blamings others, not understanding that it's your incorrect code that is garbage, and is giving random garbage values.  
  
And then you test different schedulers, and you get different random values that you think are interesting, because you think they show something cool about the schedulers.  
  
But no. You're just getting random values because different schedulers have different heuristics for "do I want to let CPU bound processes use long time slices or not"? Particularly in a load where _everybody_ is just spinning on the silly and buggy benchmark, so they all look like they are pure throughput benchmarks and aren't actually waiting on each other.  
  
You might even see issues like "when I run this as a foreground UI process, I get different numbers than when I run it in the background as a batch process". Cool interesting numbers, aren't they?  
  
No, they aren't cool and interesting at all, you've just created a particularly bad random number generator.  
  
So what's the fix for this?  
  
Use a lock where you _tell the system_ that you're waiting for the lock, and where the unlocking thread will let you know when it's done, so that the scheduler can actually work _with_ you, instead of (randomly) working against you.  
  
Notice, how when the author uses an actual std::mutex, things just work fairly well, and regardless of scheduler. Because now you're doing what you're supposed to do. Yeah, the timing values might still be off - bad luck is bad luck - but at least now the scheduler is _aware_ that you're "spinning" on a lock.  
  
Or, if you really want to use use spinlocks (hint: you don't), make sure that while you hold the lock, you're not getting scheduled away. You need to use a realtime scheduler for that (or _be_ the kernel: inside the kernel spinlocks are fine, because the kernel itself can say "hey, I'm doing a spinlock, you can't schedule me right now").  
  
But if you use a realtime scheduler, you need to be aware of the other implications of that. There are many, and some of them are deadly. I would suggest strongly against trying. You'll likely get all the other issues wrong anyway, and now some of the mistakes (like unfairness or \[priority inversions) can literally hang your whole thing entirely and things go from "slow because I did bad locking" to "not working at all, because I didn't think through a lot of other things".  
  
Note that even OS kernels can have this issue - imagine what happens in virtualized environments with overcommitted physical CPU's scheduled by a hypervisor as virtual CPU's? Yeah - exactly. Don't do that. Or at least be aware of it, and have some virtualization-aware paravirtualized spinlock so that you can tell the hypervisor that "hey, don't do that to me right now, I'm in a critical region".  
  
Because otherwise you're going to at some time be scheduled away while you're holding the lock (perhaps after you've done all the work, and you're _just_ about to release it), and everybody else will be blocking on your incorrect locking while you're scheduled away and not making any progress. All spinning on CPU's.  
  
Really, it's that simple.  
  
This has absolutely nothing to do with cache coherence latencies or anything like that. It has everything to do with badly implemented locking.  
  
I repeat: **do not use spinlocks in user space, unless you actually know what you're doing**. And be aware that the likelihood that you know what you are doing is basically nil.  
  
There's a very real reason why you need to use sleeping locks (like pthread\_mutex etc).  
  
In fact, I'd go even further: don't _ever_ make up your own locking routines. You _will_ get the wrong, whether they are spinlocks or not. You'll get memory ordering wrong, or you'll get fairness wrong, or you'll get issues like the above "busy-looping while somebody else has been scheduled out".  
  
And no, adding random "sched\_yield()" calls while you're spinning on the spinlock will not really help. It will easily result in scheduling storms while people are yielding to all the wrong processes.  
  
Sadly, even the system locking isn't necessarily wonderful. For a lot of benchmarks, for example, you want unfair locking, because it can improve throughput _enormously_. But that can cause bad latencies. And your standard system locking (eg pthread\_mutex\_lock() may not have a flag to say "I care about fair locking because latency is more important than throughput".  
  
So even if you get locking technically _right_ and are avoiding the outright bugs, you may get the wrong kind of lock behavior for your load. Throughput and latency really do tend to have very antagonistic tendencies wrt locking. An unfair lock that keeps the lock with one single thread (or keeps it to one single CPU) can give _much_ better cache locality behavior, and _much_ better throughput numbers.  
  
But that unfair lock that prefers local threads and cores might thus directly result in latency spikes when some other core would really want to get the lock, but keeping it core-local helps cache behavior. In contrast, a fair lock avoids the latency spikes, but will cause a lot of cross-CPU cache coherency, because now the locked region will be much more aggressively moving from one CPU to another.  
  
In general, unfair locking can get _so_ bad latency-wise that it ends up being entirely unacceptable for larger systems. But for smaller systems the unfairness might not be as noticeable, but the performance advantage _is_ noticeable, so then the system vendor will pick that unfair but faster lock queueing algorithm.  
  
(Pretty much every time we picked an unfair - but fast - locking model in the kernel, we ended up regretting it eventually, and had to add fairness).  
  
So you might want to look into not the standard library implementation, but specific locking implentations for your particular needs. Which is admittedly very very annoying indeed. But don't write your own. Find somebody else that wrote one, and spent the decades actually tuning it and making it work.  
  
Because you should **never ever** think that you're clever enough to write your own locking routines.. Because the likelihood is that you aren't (and by that "you" I very much include myself - we've tweaked all the in-kernel locking over _decades_, and gone through the simple test-and-set to ticket locks to cacheline-efficient queuing locks, and even people who know what they are doing tend to get it wrong several times).  
  
There's a reason why you can find _decades_ of academic papers on locking. Really. It's hard.  
  
Linus

  
  
from Hacker News https://ift.tt/36rJe3I