---
title: 'Bringing Architecture of Operating Systems to XXI Century – Part IV'
date: 2019-11-11T04:01:00+01:00
draft: false
---

   
[![“No Bugs” Hare](http://ithare.com/wp-content/uploads/BB_userpic_0013b.png)](http://ithare.com/author/nobugs)

Author:

**[“No Bugs” Hare](http://ithare.com/author/nobugs)**  Follow: [![Twitter](http://ithare.com/wp-content/uploads/socialnet_twitter1.png)](https://twitter.com/intent/user?screen_name=NoBugsHare)[![Facebook](http://ithare.com/wp-content/uploads/socialnet_facebook.png)](https://www.facebook.com/pages/No-Bugs-Hare/631718570287515)

Job Title:

**Sarcastic Architect**

Hobbies:

**Thinking Aloud**, **Arguing with Managers**, **Annoying HRs**,  
**Calling a Spade a Spade**, **Keeping Tongue in Cheek**

When I finish a first draft, I often look back at first chapters I wrote and laugh at them. They’re like pictures of yourself in middle school. You’re embarrassed to see them.

— Scott Westerfeld —

_Continued from [Part I. Changes in IT Over Last 50 Years,](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-i-changes-in-it-since-over-last-50-years/)_ _[Part II. Desirable Improvements](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-ii-desirable-improvements/)_, and _[Part III. Basic Ideas](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iii-basic-ideas/)_.

I know it was long time no see, but now (I hope) I am back from my hiatus, and hope to get up to speed pretty soon.

As we discussed basic ideas behind our ideal OS, we can try to draw some kind of design for it.

APIs and Resource Management
----------------------------

operating systems perform two essentially unrelated functions: providing application programmers … a clean abstract set of resources instead of the messy hardware ones and managing these hardware resources

— Andrew S. Tanenbaum —

As I understand the quote above from [\[Tanenbaum\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-Tanenbaum), an OS is all about two major things: (a) APIs, and (b) resource management.

### APIs

![Assertive hare:](http://ithare.com/wp-content/uploads/BB_emotion_0007b.png)“I do NOT feel that an OS is defined by its kernel; rather, an OS is defined by its APIs.Let’s start with APIs first. In this regards, as it was mentioned in Basic Idea number 3, I do NOT feel that an OS is defined by its kernel; rather, an OS is defined by its APIs.

In general, the question of API is a very complicated one, but to give some idea about what constitutes a “good” event-driven API, I’d consider C++ API with functions more or less resembling [\[Node.cpp\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-Node.cpp) – or its cousin, Node.js. I know that I will be ridiculed at every corner for saying it (“Hey, he wants to bring JS to the OS”) – but here it is; of course, I do NOT mean having any JS in the kernel – it is just that Node.js APIs represent a good _example_ of reasonable app-level functions (at least for the server-side).

#### Await

As a side note, I’d argue that APIs should be extended to support _await_\-style non-blocking programming. It simplifies development soooo significantly that I consider it Extremely Nice to Have for a usable modern system.

#### API Groups

As discussed in Basic Idea number 4, we do want to separate APIs into well-defined API groups, and have all the drivers/apps to _declare _which API groups they’re using. This will allow to (a) have a very clear compatibility matrix between drivers/apps and supported devices, and (b) keep APIs as high-level as possible, while enabling low-end access _to those apps which really need it_ (at the cost of reduced portability)_._

##### Legacy Threads

![Judging hare:](http://ithare.com/wp-content/uploads/BB_emotion_0009b.png)“Under our new OS, threading is strongly discouragedOne of the IMNSHO-outdated APIs which we will still have to simulate under our new OS, is threading. It should be separated to one of API groups – and will be available only to kernels L3 and up (see below on kernel levels). Under our new OS, threading is strongly discouraged (as it was discussed, at app level we should concentrate on higher-level concepts of non-blocking and multi-coring – which do NOT necessarily need threads to be implemented).

##### HPC

HPC is one thing which does deserve special treatment by an OS. And HPC – especially of descriptive future-based flavour – can and should be explicitly supported (with scheduling left to OS). Realistically, we shouldn’t expect HPC for anything but L4M kernels.

#### Static Analysis

As it was noted in Basic Idea number 5, static analysis is an important part of our XXI-century OS. Particular examples of static analysis include such things as:

*   providing guarantees against memory corruption (see, for example, memory-safe-cpp in [\[Node.cpp\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-Node.cpp)).
*   providing guarantees against runaway handlers (using techniques such as WCET, and WCET-based automated insertion of “yield” points into the code).

Resource Management
-------------------

Per [\[Tanenbaum\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-Tanenbaum), the second major part of the OS is resource management. From our current perspective, our OS kernel will have to manage 3 distinct types of resources:

*   CPU
*   RAM
*   external devices (most of them interrupt-driven, some possibly use DMA)

At the moment, we won’t tell how exactly we’re going to manage these resources, but we’ll come to it when discussing our kernel(s).

Multiple Basic Kernels
----------------------

![Hare with an idea:](http://ithare.com/wp-content/uploads/BB_emotion_0023b.png)“we'll try to make _several different kernels_ (with implementations being different, but providing the same set of basic APIs)First, let’s design an overall structure of our kernel. However, according to Basic Idea 3 (and contrary to most of OS’s out there), we’ll try to make _several different kernels_ (with implementations being different, but providing the same set of basic APIs).

Note that what we’ll get here, will have significant resemblances with [\[Samek\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-Samek) – and we’ll highlight these resemblances at appropriate places.

### Kernel L1 – Simplistic

Let’s start with the very simple kernel intended for the simplest non-MMU-enabled MCUs (and severely constrained on RAM too); as a good example, we can think of ARM Cortex M and Cortex R series.

#### L1 Resource Management

Let’s describe how our simplistic kernel is going to manage different types of resources.

##### RAM

Our simplest kernel will have only one thread of execution, and only one stack; also it will have a static “staging area” (to pass the data from interrupt handlers to the main loop, as described below). The rest can be occupied by heap.

Note that even at L1 we may utilize hardware-based memory protection such as the one provided by MPU or MMU. On MPU-supporting MCUs, different FSMs can be separated. However, as number of MPU regions is usually very limited, separating heaps, whenever heap sizes for different FSMs are not well-known, may cause too much of RAM waste (which can be addressed by relocating allocators, but relocation comes with its own costs).

##### CPU

Within L1 kernel, the code will be organized as a main event loop, which sleeps all the time (on something like ARM’s WFI/WFE or x86’s HLT), but whenever some information comes in from an external device, this peaceful sleep will get interrupted. Interrupt will get processed on the same stack where event handler is running; interrupt handler will pass information to a special in-memory staging area – and will terminate ASAP.

Then, CPU will get out of HLT/WFI, and our kernel will read interrupt-provided information from the staging area, and will process incoming event based on this information – invoking app-level event handler if necessary.

Let’s note that with our approach, as long as all we have is short-term reactions to incoming events (which is typical for tons of interactive systems) – we can process things without passing them around in threads – but rather process the whole thing with an absolute minimum of beating around the bush (which, at least in theory, implies absolutely maximum performance).

Let’s also note that nothing prevents us from having multiple FSMs running within the same main loop; moreover, it is perfectly possible to prioritize them – and as long as ALL our event handlers complete really fast, the whole thing will work without much problems.

On the other hand, under such a simplistic kernel, there is no such thing as pre-emption; in turn, it means that a runaway event handler can easily stall the whole system. It is not _as _bad as it might look at the first glance (as any potentially-blocking OS operation effectively terminates current event handler), but still does represent a real-world danger.

Still, to address it, at least two very different (and potentially combinable) approaches are possible:

*   WCET-like static analysis as mentioned above
*   ![Hare thumb up:](http://ithare.com/wp-content/uploads/BB_emotion_0012b.png)“surprisingly, very many real-world FSMs CAN be re-initialized it is possible to have an OS-level watchdog – which wakes up at regular intervals[1](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitfootnote-1) and aborts current event handler if it runs too long; of course, in such a case internal state of the FSM MIGHT be damaged – but we’re still ok _as long the FSM can be re-initialized from scratch_, And surprisingly, very many real-world FSMs CAN be re-initialized (such FSMs range from most of the drivers to things such as TCP stack).

* * *

1 on interrupt, of course

##### External Devices

Interrupt-driven external devices fit Simplistic kernel (just as any other event-driven kernel) like a glove – such processing naturally fits within interrupt handling / event handling schema described above. DMAs can be handled within the same model quite easily too.

One potential issue is those devices which are NOT interrupt-driven. In such cases (which are relatively rare for production-level development) , it may be necessary to handle such devices using polling. Most of the time, we can get away (as long as such polling is not too time-critical) with polling on timer interrupts. The only realistic problem occurs when the whole thing is soooo time-critical that we have to (not just “want to”, but “HAVE to”) use tight loops to measure time delays (ouch and triple-ouch!); in such cases (which SHOULD NOT happen but still DO happen especially on lower-end MCUs), it still MIGHT be possible to use our kernel (blocking all the other handlers until such absolutely-time-critical delay is handled) – at least as long as at every given moment, there is only one such tight loop.[2](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitfootnote-2)

* * *

2 and if there is a need to have more than one tight loop at any given moment – it means that the whole thing won’t work regardless of code

#### Determinism with Optional Recording/Replay

Our simplistic kernel  is conceptually similar to “Cooperative” kernel [\[QV\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-QV)[3](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitfootnote-3).

However, one feature which is NOT present in [\[QV\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-QV) but was mentioned in our Basic Ideas, is that we can (and should) allow kernel to run a (circular) log of all the events which were fed to a specific app/driver[4](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitfootnote-4)– which will allow us to _replay _what has happened on our device, on another device (as long as an app/driver is _exactly _the same). This facilitates such all-important things as post-mortem debugging, fault tolerance, low-latency node migration, and so on.

BTW, recording/replay can be used even for lower-end MCUs (or at least for higher-end versions-with-more-RAM of those lower-end production MCUs).

* * *

4 more strictly – to a specific FSM

#### L1 Pros and Cons

Our simplistic kernel, is well, simple, and is very easy on resources; in particular, RAM layout has only one stack, which makes this design feasible for lower-end and/or time-critical[5](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitfootnote-5) MMU-less MCUs (those currently starting at about $1). In addition, it supports optional recording/replay, enabling a whole bunch of useful-in-production features. Last but not least, it is as power-friendly as possible (being in WFI/HLT state enables modern CPUs to minimize power consumption, which is very important both for battery-driven devices – for obvious reasons, and for mains-powered devices – we don’t want to generate more CO2 than absolutely necessary, don’t we?)

![Thinking hare:](http://ithare.com/wp-content/uploads/BB_emotion_0011b.png)“On the negative side, our L1 kernel does NOT allow to interrupt an already-running event handler, even for a higher-priority FSM.On the negative side, our L1 kernel does NOT allow to interrupt an already-running event handler, even for a higher-priority FSM. This, in turn, prevents its use in certain time-critical use cases.

* * *

5 think Cortex-M and Cortex-R respectively

### Kernel L2 – Prioritized

To mitigate this lack of prioritization and allow to interrupt an already-running handler by a higher-priority one, an alternative kernel can be introduced (similar to QK from [\[Samek\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-Samek)). Basic idea is that if within an interrupt, we realize that incoming interrupt/event belongs to a higher-priority FSM that currently running one, we can start building stack for the higher-priority FSM on top of existing stack (it will require very careful asm-level trickery but is perfectly feasible).

Moreover, we can say that in case of long-running events, we can use timer to interrupt a long-running event – allowing to process a same-priority event over a long-running one. However, within an L2 kernel we still won’t be able to _interleave _two long-running events – and will have to wait for one of them to complete before the second one can be processed.

#### L2 Resource Management – Differences from L1

Under L2, RAM management is very similar to L1 (except for more sophisticated stack management as described above). In particular, we still have one single stack (big phew for MMU-less MCUs).

CPU management is also very similar to L1 – except for better responsiveness for higher-priority FSMs, and management of external devices is virtually identical to that of under L1 kernel.

#### L2 Pros and Cons

Being very similar to L1, L2 kernel shares most of its pros and cons with L1. In particular, L2 kernel can still run on MMU-less RAM-constrained MCUs, it is also power-friendly, and also provides for recording/replay with all the associated goodies.

As an improvement over L1, L2 kernel allows to handle prioritised FSMs better, and allows to deal with one really-long-running event handler (as long as it is low-priority one) without killing the whole FSM.

![Surprised hare:](http://ithare.com/wp-content/uploads/BB_emotion_0006b.png)“functionally, L2 kernel still doesn't provide true protection from runaway handlers (that is, besides static analysis and WCET).On the negative side, L2 is a bit more complicated compared to L1; and functionally, it still doesn’t provide true protection from runaway handlers (that is, besides static analysis and WCET).

### Kernel L3 – Preemptive

As a step further from L2 (and to the best of my knowledge, this step is NOT described in [\[Samek\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-Samek)), we can use split-stacks (somewhat similar to -fsplit-stack in GCC/Clang), to enable true protection from runaways – while still being able to run on a MMU-less MCU. If our compiler guarantees that:

*   the whole stack frame is always allocated at the very beginning of the function, and is always released at the very end of the function, and that
*   whenever stack frame is allocated/deallocated, (de)allocation procedure can be adjusted as we need it

then we can allow interleaving stack fragments for concurrently running event handlers. Indeed, under L2 kernel it is already possible for a higher-priority (“new”) event handler to run on top of the stack of already-running (“old”) event handler. What was not possible under L2 is that if “new” handler runs for too long, we couldn’t start running an “old” handler again before “new” handler completes.

Under L3 with its split stacks, if we ever feel like resuming “old” handler without “new” one being terminated, we can do it. If we decide to resume “old” handler, we simply resume running it; if it doesn’t need any more new stack – it will simply run within already-existing stack frame; however, if “old” handler will ever want to call another (non-inlined) function – then allocation procedure for the new stack frame will realize that immediately-following stack addresses are already in use (by “new” handler), so split-stack is needed, and new stack frame will be created on top of already-existing stack frames of “new” handler. If at later point we’ll need to run “new” handler again, another split-stack may become necessary, and so on.

Also note that starting from L3, we can support Legacy Threads.

#### L3 Resource Management – Differences from L2

Under L3, RAM management is still very similar to L2 and to L1 (except for even more sophisticated stack management as described above). In particular, even with L3 we STILL have one single stack (another big phew for MMU-less MCUs).

On the other hand, CPU management becomes quite different from L2 – and we can implement _real _preemption for concurrently-running event handlers. However, management of external devices is still virtually identical to that of under L2/L1 kernel.

#### L3 Pros and Cons

![Hare thumb up:](http://ithare.com/wp-content/uploads/BB_emotion_0012b.png)“While L3 kernel can STILL run on MMU-less RAM-constrained MCUs, it provides responsiveness which is comparable to that of multi-stack kernels.L3 kernel is an interesting beast. While it can STILL run on MMU-less RAM-constrained MCUs (and keeping other goodies such as being power-friendly and providing for recording/replay), it provides responsiveness which is comparable that of multi-stack kernels.  In addition, it allows protection against run-away handlers even _without relying on static analysis._

On the negative side, L3 is significantly more complicated compared to L2 (and requires support of compilers too); also, its split-stack could carry an observable performance penalty compared to multiple stacks (that is, IF you can afford multiple stacks – which usually requires an MMU-enabled CPU).

### Kernel L4 – Multi-Stack

L4 kernel is quite different from all our previous kernels in that it employs multiple stacks. And as soon as we allow multiple stacks – everything (besides answering a question “where to put these stacks on a non-MMU’d device”) becomes simple: as soon as we want to pre-empt, we are simply switching to another handler – which has its own stack. Bingo!

Let’s also note that L4 with a support for Legacy Threads is very similar to QXK kernel from [\[Samek\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-Samek).

#### L4 Resource Management – Differences from L3

Under L4, RAM management becomes substantially different from that of under L3 – in particular, multiple stacks have to be allocated (and in anywhere general case, this requires an MMU).

On the other hand, CPU management and management of external devices stay similar to that of under L3 kernel.

#### L4 Pros and Cons

Realistically, most of the time L4 kernel will need a MMU-enabled CPU; this is its main drawback. On the other hand, it still keeps goodies such as being power-friendly and providing for recording/replay.

On the positive side, L4 doesn’t need compiler support, and doesn’t carry performance penalty due to split-stacks. It makes L4 a fairly obvious choice for heavy-weight MMU-enabled CPUs (such as Cortex A, x64, etc.).

Let’s note that while L4 kernel is quite similar to existing kernels – it exhibits substantial advantages over them; in particular, for a purely interactive system we still do NOT need to incur penalties due to threading (and especially due to thread sync); also, determinism and resulting goodies are a Big Thing(tm) for production.

### Extending to Multi-Core – L3M, L4M

Up to this point, all our kernels were oriented for one single CPU core. While strictly speaking, any of our single-core kernels can be extended to support multi-core configurations, realistically I expect L3M and L4M to be by far the most popular ones.

![Surprised hare:](http://ithare.com/wp-content/uploads/BB_emotion_0022b.png)“multi-coring is essentially a special case of balancing shared-nothing nodesExtending a single-core kernel to multi-core is a breeze – well, as soon as we realise that multi-coring is essentially a special case of balancing shared-nothing nodes between different boxes, and implement it. And inter-box balancing is what pretty much any cloud system does these days, so reasonably efficient techniques for doing it do exist and are rather well-known.

L4M is capable of supporting HPC API[6](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitfootnote-6); also let’s note that L4M – with Legacy Threading API – provides environment which is virtually indistinguishable from that of existing OS’s.

* * *

6 well, L3M is also able to do it, but I have my doubts about practicality of this approach. Courses for horses.

Conclusion
----------

Now we’re in position to wrap it up the whole mini-series on moving OS’s into XXI century.

*   ![Assertive hare:](http://ithare.com/wp-content/uploads/BB_emotion_0019b.png)“Since 60-70s, the world has moved very significantly from the concept of batch calculations towards interactive systemsIn _[Part I](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-i-changes-in-it-since-over-last-50-years/)_, we established that the world has moved Very Significantly since 60-70s when the fundamentals of the existing OS’s were established; in particular, the world has moved very significantly from the concept of batch calculations towards interactive systems. Hardware improvements were also abundant, and as we’ve seen, some of them are very relevant to the OS architecture.
*   In _[Part II](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-ii-desirable-improvements/)_, we found a list of desirable improvements for our OS’s. This list is long, and includes things starting from Flexibility (as in “ability to run the same code in kernelland or in userland depending on specific deployment requirements”), all the way to Improved Performance.
*   In _[Part III](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iii-basic-ideas/),_ we make a few basic ideas, which should shape architecture of our future OS.
*   And in this final part, we proposed a more-or-less specific design for our OS for XXI Century. It is important to note that some of our multiple kernels did resemble existing embedded systems (in particular, QV, QK, and QXK kernels) – and our L4M kernel seems to provide virtually the same functionality as existing OS’s.

Bingo! It is apparently possible both to have our cake and to eat it too. Whether such good ideas will ever materialize – is a different story. On a positive note, currently we’re working on [\[Node.cpp\]](http://ithare.com/bringing-architecture-of-operating-systems-to-xxi-century-part-iv-first-draft/#rabbitref-Node.cpp) – an app-level framework similar to Node.js but preliminary 5x(!) faster; given time, Node.cpp may even evolve to support bare metal, and at that point it will become a foundation to build our OS of XXI century on top of it.

### Acknowledgement

Cartoons by Sergey Gordeev[![IRL](http://ithare.com/wp-content/uploads/irl-link.png)](http://ithare.com/real-people-behind-the-hare#sergey-gordeev) from [Gordeev Animation Graphics](http://gagltd.eu/), Prague.

  
  
from Hacker News https://ift.tt/32rOQse