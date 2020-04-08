---
title: 'Emulated Iopl()'
date: 2019-11-16T11:29:00+01:00
draft: false
---

### Welcome to LWN.net

The following subscription-only content has been made available to you by an LWN subscriber. Thousands of subscribers depend on LWN for the best news from the Linux and free software communities. If you enjoy this article, please consider accepting the trial offer on the right. Thank you for visiting LWN.net!

### Free trial subscription

Try LWN for free for 1 month: no payment or credit card required. [Activate your trial subscription now](https://lwn.net/Promo/slink-trial2-3/claim) and see why thousands of readers subscribe to LWN.net.

By **Jonathan Corbet**  
November 8, 2019

Operating systems and computing hardware both carry a lot of their history with them. The x86 I/O-port mechanism is one piece of that history; it is rarely used by hardware designed in the last 20 years, but it must still be supported. That doesn't mean that this support can't be cleaned up and improved, though, especially when the old implementation turns out to have some unpleasant properties. An example can be seen in

[the iopl() patch set](https://lwn.net/ml/linux-kernel/20191106193459.581614484@linutronix.de/)

from Thomas Gleixner.

On most architectures, I/O is handled through memory-mapped I/O (MMIO) regions. A peripheral device will make a set of registers available as a range of memory; that range is then mapped into the processor's address space. Device drivers can then interact with the device by reading from and writing to those registers using normal memory accesses (or something close to that). This mechanism is flexible and it allows, for example, a set of registers to be mapped into a user-space process if the need arises; user-space drivers generally depend on this capability.

Back in the early days of the x86 architecture, though, things were done a little differently. A separate address space was created for up to 65536 I/O ports, which have to be accessed via special instructions. Even devices that could map memory ranges for other purposes would use I/O ports for their control interfaces. The instructions for accessing I/O ports are necessarily privileged, so user-space code cannot normally use them.

Once again, though, there is value in driving devices from user space at times. To support this functionality, the x86 designers created two separate ways to give an otherwise unprivileged process access to I/O ports:

*   The I/O privilege level (IOPL) is a two-bit variable that controls how much privilege a process must have to access I/O ports. It is normally set to zero, meaning that this access is only available when running in kernel mode. Setting it to three makes I/O-port operations available to ordinary user-space processes. Changing the I/O privilege level for a specific process (done with the [iopl()](http://man7.org/linux/man-pages/man2/iopl.2.html) system call) can thus make all I/O ports available to that process.
*   The I/O port permissions bitmap stored in the [task state segment (TSS)](https://en.wikipedia.org/wiki/Task_state_segment) can be used to grant access to specific ports. If the bit corresponding to a given port is zero, then the running task is allowed to access that port. The [ioperm()](http://man7.org/linux/man-pages/man2/ioperm.2.html) system call is used to manipulate this bitmap.

A privileged process can call either iopl() or ioperm() to gain access to I/O ports. Calling ioperm() will increase the process's context-switch time, though, since the 8KB bitmap must be copied during a switch; for that reason, some applications use iopl(), even though it opens access to far more ports than needed.

There is, however, one other little problem with iopl(): an elevated I/O privilege level also allows the current process to disable and enable interrupts. That, as Gleixner pointed out, is less than ideal. A rogue process could easily lock up the CPU by disabling interrupts and looping, but the real issue is that there are no defined semantics for user space disabling interrupts. Kernel developers tend to assume that interrupts will be enabled while user space is running, but a process with an elevated IOPL can violate that assumption. Nothing good can be expected to come from a process actually exercising this privilege, but it simply comes as part of an elevated IOPL.

The most pleasing solution, Gleixner said, would be to just get rid of iopl() entirely, but there are still applications that depend on it so that cannot be done. But, perhaps, there is another solution: emulating iopl() by using the bitmap instead. If a process has an I/O privilege bitmap with all bits cleared, it has access to all I/O ports, just like it would with an elevated IOPL. But the ability to disable interrupts would be taken away.

Even doing that would be a problem if there were any applications that depend on the ability to disable interrupts in user space. Gleixner searched for such applications, but the only thing he found was a "really ancient X implementation". That code wouldn't run on current systems anyway, so it is not a concern. Hopefully there is nothing else out there that eluded Gleixner's search.

Switching to using the bitmap for iopl() solves the interrupt problem, but there is still the issue of the performance hit. A couple of optimizations in the patch set take care of that issue, though. Most processes don't use the bitmap at all; rather than set the bitmap to all ones for such processes, it is enough to change the pointer to the bitmap in the TSS to an invalid value and access to I/O ports will be denied. In the case of a context switch where both the incoming and outgoing processes are using the bitmap, only the portion with cleared bits needs to be copied, speeding that operation as well. In the end, the overhead of emulated iopl() is not zero, but it seems to be close enough.

Linus Torvalds [pointed out](https://lwn.net/ml/linux-kernel/CAHk-=wjXcS--G3Wd8ZGEOdCNRAWPaUneyN1ryShQL-_yi1kvOA@mail.gmail.com/) that performance could be improved further by just leaving the I/O bitmap in place until something forces it to be changed. This optimization is aimed at the case where there is only one process running with access to I/O ports — a case that is likely to hold much of the time. Gleixner [indicated](https://lwn.net/ml/linux-kernel/alpine.DEB.2.21.1911070843490.1869@nanos.tec.linutronix.de/) that he would look at implementing this change.

Willy Tarreau [suggested](https://lwn.net/ml/linux-kernel/20191107091704.GA15536@1wt.eu/) taking another step and just using an all-zeroes bitmap for any process that has called ioperm(). The result would be that a call that currently only grants access to specific ports would instead grant access to _all_ ports. The calling process already has the privilege to request access to those ports, he said, so there wouldn't really be a security issue with that change. Eric Biederman [pointed out](https://lwn.net/ml/linux-kernel/87h83fd4a2.fsf@x220.int.ebiederm.org/), though, that [DOSEMU](http://www.dosemu.org/) actually counts on ioperm() not giving access to more ports than requested, so this idea is not workable in the end.

There was no opposition to the patch set in general, so a version of it is likely to be merged sometime in the near future. Then the kernel will have managed to leave behind a little piece of inconvenient legacy behavior, which can only be a good thing.

> **Did you like this article?** Please accept our [trial subscription offer](https://lwn.net/Promo/slink-trial2-3/claim) to be able to see more content like it and to participate in the discussion.

* * *

(

[Log in](https://lwn.net/Login/?target=/Articles/804143/)

to post comments)

  
  
from Hacker News https://ift.tt/2pmdJYM