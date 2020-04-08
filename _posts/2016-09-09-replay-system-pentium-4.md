---
title: 'Replay System (Pentium 4)'
date: 2019-12-06T01:40:00+01:00
draft: false
---

The **replay system** is a little-known subsystem within the [Intel](https://en.wikipedia.org/wiki/Intel "Intel") [Pentium 4](https://en.wikipedia.org/wiki/Pentium_4 "Pentium 4") processor.[\[1\]](https://en.wikipedia.org/wiki/Replay_system#cite_note-1) Its primary function is to catch operations that have been mistakenly sent for execution by the processor's [scheduler](https://en.wikipedia.org/wiki/Instruction_scheduling "Instruction scheduling"). Operations caught by the replay system are then re-executed in a loop until the conditions necessary for their proper execution have been fulfilled.[\[2\]](https://en.wikipedia.org/wiki/Replay_system#cite_note-xbitlabs-2)

Overview
--------

The replay system came about as a result of Intel's quest for [ever-increasing clock speeds](https://en.wikipedia.org/wiki/Megahertz_myth "Megahertz myth"). These higher clock speeds necessitated very lengthy [pipelines](https://en.wikipedia.org/wiki/Pipeline_(computing) "Pipeline (computing)") (up to 31 stages in the [Prescott](https://en.wikipedia.org/wiki/Intel_Prescott "Intel Prescott") core). Because of this, there are six stages between the scheduler and the [execution units](https://en.wikipedia.org/wiki/Execution_unit "Execution unit") in the Prescott core. In an attempt to maintain acceptable performance, Intel engineers had to design the scheduler to be very optimistic.[\[2\]](https://en.wikipedia.org/wiki/Replay_system#cite_note-xbitlabs-2)

The scheduler in a Pentium 4 processor is so aggressive that it will send operations for execution without a guarantee that they can be successfully executed. (Among other things, the scheduler assumes all data is in level 1 "[trace cache](https://en.wikipedia.org/wiki/Trace_cache "Trace cache")" [CPU cache](https://en.wikipedia.org/wiki/CPU_cache "CPU cache").) The most common reason execution fails is that the requisite data is not available, which itself is most likely due to a cache miss. When this happens, the replay system signals the scheduler to stop, then repeatedly executes the failed string of dependent operations until they have completed successfully.[\[2\]](https://en.wikipedia.org/wiki/Replay_system#cite_note-xbitlabs-2)[\[3\]](https://en.wikipedia.org/wiki/Replay_system#cite_note-3)

Performance considerations
--------------------------

Not surprisingly, in some cases the replay system can have a very bad impact on performance. Under normal circumstances, the execution units in the Pentium 4 are in use roughly 33% of the time. When the replay system is invoked, it will occupy execution units nearly every available cycle. This wastes power, which is an increasingly important architectural design metric, but poses no performance penalty because the execution units would be sitting idle anyway. However, if [hyper-threading](https://en.wikipedia.org/wiki/Hyper-threading "Hyper-threading") is in use, the replay system will prevent the other thread from utilizing the execution units. This is the true cause of any performance degradation concerning hyper-threading. In Prescott, the Pentium 4 gained a replay queue, which reduces the time the replay system will occupy the execution units.[\[2\]](https://en.wikipedia.org/wiki/Replay_system#cite_note-xbitlabs-2)

In other cases, where each thread is processing different types of operations, the replay system will not interfere, and a performance increase can appear. This explains why performance with hyper-threading is application-dependent.[\[2\]](https://en.wikipedia.org/wiki/Replay_system#cite_note-xbitlabs-2)

See also
--------

References
----------

<img src="https://en.wikipedia.org/wiki/Special:CentralAutoLogin/start?type=1x1" alt="" title="" />

  
  
from Hacker News https://ift.tt/2YnwisM