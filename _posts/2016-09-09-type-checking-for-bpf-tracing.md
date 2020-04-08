---
title: 'Type Checking for BPF Tracing'
date: 2019-11-09T01:31:00+01:00
draft: false
---

**Benefits for LWN subscribers**

The primary benefit from [subscribing to LWN](https://lwn.net/subscribe/) is helping to keep us publishing, but, beyond that, subscribers get immediate access to all site content and access to a number of extra site features. Please sign up today!

By **Jonathan Corbet**  
October 28, 2019

The

[BPF in-kernel virtual machine](https://lwn.net/Articles/740157/)

has brought a new set of capabilities to a number of functional areas in the kernel, including, significantly,

[tracing](https://lwn.net/Articles/787131/)

. Since BPF programs run in the kernel, much effort goes into ensuring that they will not cause problems for the running system; to that end, the BPF verifier checks every possible aspect of each BPF program's behavior to ensure that it is safe to run in the kernel — with one notable exception. With a patch set titled "

[revolutionize bpf tracing](https://lwn.net/ml/netdev/20191016032505.2089704-1-ast@kernel.org/)

", Alexei Starovoitov aims to close that loophole and eliminate a set of potential problems in a widely used class of BPF programs.

BPF is heavily used in tracing applications to gain access to useful kernel information and to perform data aggregation in kernel space. There are two variants of these programs. If a tracepoint has been placed in a useful location in the kernel, a BPF program can be attached there; otherwise, a kprobe can be placed at (almost) any kernel location and used to trigger a BPF program. Either way, the BPF verifier currently has little visibility into the data that will be passed to those programs.

Consider, for example, the trace\_kfree\_skb tracepoint placed in [net\_tx\_action()](https://elixir.bootlin.com/linux/v5.4-rc2/source/net/core/dev.c#L4575). When this tracepoint triggers, any handlers (including attached BPF programs) will be passed two pointers, one to the sk\_buff structure representing the network packet of interest, and one to the function that is freeing that packet. The type information associated with those pointers is lost, however; the program itself just sees a pair of 64-bit unsigned integers. Accessing the kernel data of interest requires casting those integers into pointers of the correct type, then using helpers like bpf\_probe\_read() to read the data behind those pointers. A series of bpf\_probe\_read() calls may be needed to walk through a data structure and get to the data the tracing program is actually looking for.

The problem is that a BPF program can cast one of these values into any type it likes; the result need not correspond to the actual type of that data. A mistake could cause a BPF program to go off into the weeds; in one worst-case scenario, the program could wander into a memory-mapped I/O area and cause some real damage. This isn't generally a security issue, since tracing is a privileged operation to begin with, but it is a safety issue — exactly the sort of issue that the BPF verifier is meant to prevent.

This problem has existed since the kernel first gained the ability to attach BPF programs to tracepoints and kprobes. Meanwhile, BPF developers have been working on [an entirely different problem](https://lwn.net/Articles/773198/): the lack of binary portability for BPF programs. These programs go digging around in kernel data structures, but the layout and content of those structures varies depending on the kernel configuration, the underlying architecture, and more. The data of interest to any given program may be located 12 bytes into a structure on one kernel, but only 8 bytes into that structure on a different kernel. Without the ability to "relocate" these references, BPF users must rebuild their programs on every target system.

The "compile once run everywhere" effort has, over the last couple of years or so, worked to address this problem through the creation of a compact, machine-readable description of the kernel's data structures. This "BPF type format" (BTF) data is provided by the kernel itself, but it can be used by user-space support libraries to adjust a binary BPF program for a local kernel before loading it, mostly solving the binary portability issue. But it turns out that BTF information has other uses as well.

In particular, it is possible to annotate tracepoints with information about the types of the data values passed to handler programs. That allows the verifier to ensure that those programs are working with the correct data types. It also makes it possible for the C handler programs to follow pointers directly; when those programs are compiled to BPF and loaded into the kernel, the verifier can implicitly substitute the bpf\_probe\_read() calls where they are needed — after performing the necessary type checking, of course.

The end result of all this will be BPF tracepoint handler programs that are safer and far less error-prone to write. Whether tracing is "revolutionized" remains to be seen, but it is clearly improved in a significant way.

What is decidedly not revolutionized is data access within kprobe handlers. A kprobe can be set anywhere in the running kernel, and it is given access to the contents of the processor registers when the probe is hit. It is not, at this point, possible for the verifier to know what will be in those registers at that time, so this kind of checking cannot be done. That means that, especially in the parts of the kernel that are not amenable to the addition of proper tracepoints, the use of BPF programs without this sort of type checking will have to continue.

That said, progress is progress, and this work will increase the safety of much of the tracing code that is currently in use. It has been queued in the bpf-next tree so, barring some sort of last-minute hitch, it can be expected to show up in the 5.5 kernel.

* * *

(

[Log in](https://lwn.net/Login/?target=/Articles/803258/)

to post comments)

Please remember that the kernel is for running userspace!

Posted Oct 30, 2019 4:11 UTC (Wed) by **ringerc** (subscriber, #3071) \[[Link](https://lwn.net/Articles/803421/)\]

I'm excited to see where BPF / eBPF tracing is going.

Remember userspace
------------------

But I'm also seeing echoes of a repeating pattern here. Userspace, as always, seems to be relegated to an uninteresting afterthought. Perhaps less so than was the case with perf, but still to a concerning degree.

Generations of tools with production userspace as an afterthought
-----------------------------------------------------------------

We've been through a lot of tracing tools and frameworks both for generating/annotating traceable data and for collecting/processing it. uprobes,

`ftrace`

, dtrace-for-linux, SystemTap, linux-perf and

`perf_events`

, LTTng, and more. They're inter-related and not a simple generational series of changes. But one pattern seems to have persisted pretty strongly: nothing works very well with "real world" production userspace deployments initially, yet earlier generations of tools tend to be abandoned. If you go to use one tool you're told it's obsolete, you should use the new one instead, but that one doesn't actually work on any of the systems widely deployed in production and won't for a long time yet. When it does, it probably doesn't support external debuginfo (like every system has had for 10+ years) for another year or two after that, because really, who debugs packaged binaries on production systems? So this time around I'm going to plead for some attention to userspace, including the boring parts of userspace above the C library, allocator and syscall wrappers. Because tracing is incredibly useful when working with complex real world systems, in production, supporting live workloads. But that seems to be the last priority when tools are being worked on. (If I can get involved in relevant testing, UX, bug fixing etc please reach out; craig.ringer@2ndquadrant.com is the best address and make sure to mention tracing in the subject.)

SystemTap is amazing with userspace (now)
-----------------------------------------

I recently got around to learning SystemTap after, again, being unable to make perf do what I want for my tracing needs. It's \*amazing\*. It has a few frustrating deficiencies and I understand that its "kernel modules compiled on demand" design doesn't have a future. But the tool itself is like nothing else I've ever used, it's incredible, warts and all. In particular:

*   It can traverse complex data structures, with logic where needed not just simple expressions
*   It can access global variables (via DWARF lookups, with debuginfo) which is vital in nontrivial systems
*   It can integrate events from multiple tracked processes to observe complex behaviour of multi-process systems
*   It can place all sorts of probe events on function calls, returns, static tracepoint markers, statement level probes, process start/end, and much more
*   ... and it makes all that pretty easy so you can focus on the actual details of the program you are tracing without rewriting half the tools you need each time.

### Example I used it for in PostgreSQL

With SystemTap I was able to rapidly gain insight into the deep guts of PostgreSQL's behaviour in a way I've never been able to do before, even when patching PostgreSQL itself and post-processing trace logs. I can follow the lifecycle of nontrivial events in the system and collect timing and stats on them. My stap script observes a lot of activity:

```
 \* observe all backend fork()s to determine backend process type (postmaster, logical or physical walsender, client backend, etc) and decide what to observe in that backend dynamically \* For user backends: \* frontend connects \* backend attaches \* backend starts transaction \* backend assigns non-virtual transaction-id \* backend ends txn? \* rollback? Stop tracking \* commit? \* See if we need to follow it through logical decoding or not by inspecting the state at commit time (current db, active replication slots, etc) \* prepare 2pc txn? \* Add it to a "prepared xacts" track-list \* backend runs a 2PC commit prepared or rollback prepared? \* record time from prepare to commit/rollback \* then observe logical decoding as if it's a normal commit \* logical replication walsender backends: \* notice when we start buffering data for a new committed xid, start timing \* wait for logical decoding to finish buffering the commit \* when commit is decoded, record total buffering time \* observe output plugin calls when buffered commit is being sent to client. Take timing info and stats on the types of operations sent and processing duration. Record info on skipped-over rows, tables, etc where we buffered them but discarded the buffered data. \* record time final commit sent to client \* wait for the receiver to confirm that the txn was received in full \* record time client confirmed commit \* logical replication receiver / apply worker backends: \* observe when a commit arrives from the logical walsender \* associate it with the timing data collected for it on the origin side \* record how long we take to apply it, whether it waits for locks, which ones and for how long \* report final apply time \* Generate summary statistics periodically and on exit \* Optionally generate detailed trace logs of targeted activity, optionally filtered to focus only on one client application / client connection 
```

It's amazing to have this level of insight. And now that I've written the basic tapset to inspect the relevant parts of PostgreSQL I can massage it to extract all sorts of timing, performance, and behaviour data. (It'd be a lot more amazing if it weren't for some bugs in systemtap that make it a LOT harder to make the foundations I wrote reusable, though, per reports to the seemingly dead systemtap mailing list). I even extended it so it can associate two sides of a network connection as logical replication peers (if they're on the same host only, so far) and observe message-passing timings and processing delays across the wire. So I can see whether the sending side is waiting for more data to send, waiting for the client to consume its buffer, etc. I can see if the sender is delayed by the client waiting on a lock, waiting on I/O, etc.

Out with the old, in with the new? Again?
-----------------------------------------

But I've since learned that SystemTap is considered pretty much dead and obsolete. Yet I cannot use eBPF on any production systems I'm likely to encounter in the next year or two. And even then, will I be able to get this level of access to userspace? Meanwhile perf never really gained complete enough tracing features to be of much use without a large amount of postprocessing using "perf script". It cannot even time syscalls from the enter to the exit sdt probe!

So please consider userspace
----------------------------

I'd love to help out if anyone working on these tools wants constructive input, testing, bug checking etc from someone who works on the PostgreSQL database backend in real world production deployments. Reach out to me, craig.ringer@2ndquadrant.com.

  
  
from Hacker News https://ift.tt/33u5icI