---
title: 'Linus: People should aim to make “badly written” code “just work”'
date: 2019-12-01T03:49:00+01:00
draft: false
---

Re: Linux 2.6.29
================

\[Posted March 31, 2009 by corbet\]

**From**:

 

Linus Torvalds

**To**:

 

Kyle Moffett

**Subject**:

 

Re: Linux 2.6.29

**Date**:

 

Wed, 25 Mar 2009 20:40:23 -0700 (PDT)

**Message-ID**:

 

**Cc**:

 

Jeff Garzik , Matthew Garrett , Theodore Tso , Christoph Hellwig , Jan Kara , Andrew Morton , Ingo Molnar , Alan Cox , Arjan van de Ven , Peter Zijlstra , Nick Piggin , Jens Axboe , David Rees , Jesper Krogh , Linux Kernel Mailing List

**Archive-link**:

 

[Article](http://www.mail-archive.com/search?l=mid&q=alpine.LFD.2.00.0903252017100.3032%40localhost.localdomain)

```
 On Wed, 25 Mar 2009, Kyle Moffett wrote: \> \> Well, I think the goal is not to \*replace\* the POSIX API or even \> provide "transactional" guarantees. The performance penalty for \> atomic transactions is pretty high, and most programs (like GIT) don't \> really give a damn, as they provide that on a higher level.  Speaking with my 'git' hat on, I can tell that - git was designed to have almost minimal requirements from the filesystem, and to not do anything even half-way clever. - despite that, we've hit an absolute metric sh\*tload of filesystem bugs and misfeatures. Some very much in Linux. And some I bet git was the first to ever notice, exactly because git tries to be really anal, in ways that I can pretty much guarantee no normal program \_ever\_ is. For example, the latest one came from git actually checking the error code from 'close()'. Tell me the last time you saw anybody do that in a real program. Hint: it's just not done. EVER. Git does it (and even then, git does it only for the core git object files that we care about so much), and we found a real data-loss CIFS bug thanks to that. Afaik, the bug has been there for a year and half. Don't tell me nobody uses cifs. Before that, we had cross-directory rename bugs. Or the inexplicable "pread() doesn't work correctly on HP-UX". Or the "readdir() returns the same entry multiple times" bug. And all of this without ever doing anything even \_remotely\_ odd. No file locking, no rewriting of old files, no lseek()ing in directories, no nothing. Anybody who wants more complex and subtle filesystem interfaces is just crazy. Not only will they never get used, they'll definitely not be stable. \> To be honest I think we could provide much better data consistency \> guarantees and remove a lot of fsync() calls with just a basic \> per-filesystem barrier() call.  The problem is not that we have a lot of fsync() calls. Quite the reverse. fsync() is really really rare. So is being careful in general. The number of applications that do even the \_minimal\_ safety-net of "create new file, rename it atomically over an old one" is basically zero. Almost everybody ends up rewriting files with something like open(name, O\_CREAT | O\_TRUNC, 0666) write(); close(); where there isn't an fsync in sight, nor any "create temp file", nor likely even any real error checking on the write(), much less the close(). And if we have a Linux-specific magic system call or sync action, it's going to be even more rarely used than fsync(). Do you think anybody really uses the OS X FSYNC\_FULL ioctl? Nope. Outside of a few databases, it is almost certainly not going to be used, and fsync() will not be reliable in general. So rather than come up with new barriers that nobody will use, filesystem people should aim to make "badly written" code "just work" unless people are really really unlucky. Because like it or not, that's what 99% of all code is. The undeniable FACT that people don't tend to check errors from close() should, for example, mean that delayed allocation must still track disk full conditions, for example. If your filesystem returns ENOSPC at close() rather than at write(), you just lost error coverage for disk full cases from 90% of all apps. It's that simple. Crying that it's an application bug is like crying over the speed of light: you should deal with \*reality\*, not what you wish reality was. Same goes for any complaints that "people should write a temp-file, fsync it, and rename it over the original". You may wish that was what they did, but reality is that "open(filename, O\_TRUNC | O\_CREAT, 0666)" thing. Harsh, I know. And in the end, even the \_good\_ applications will decide that it's not worth the performance penalty of doing an fsync(). In git, for example, where we generally try to be very very very careful, 'fsync()' on the object files is turned off by default. Why? Because turning it on results in unacceptable behavior on ext3. Now, admittedly, the git design means that a lost new DB file isn't deadly, just potentially very very annoying and confusing - you may have to roll back and re-do your operation by hand, and you have to know enough to be able to do it in the first place. The point here? Sometimes those filesystem people who say "you must use fsync() to get well-defined semantics" are the same people who SCREWED IT UP SO DAMN BADLY THAT FSYNC ISN'T ACTUALLY REALISTICALLY USEABLE! Theory and practice sometimes clash. And when that happens, theory loses. Every single time. Linus 
```

* * *

(

[Log in](https://lwn.net/Login/?target=/Articles/326505/)

to post comments)

  
  
from Hacker News https://ift.tt/35Qraji