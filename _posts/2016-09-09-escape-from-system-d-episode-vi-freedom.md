---
title: 'Escape from System D, episode VI: freedom in sight'
date: 2019-12-20T08:46:00+01:00
draft: false
---

![](https://s0.wp.com/i/blank.jpg "Escape from System D, episode VI: freedom in sight – Software is Crap")  

I don’t write often enough about my _init_\-system-slash-service-manager, Dinit ([https://github.com/davmac314/dinit](https://github.com/davmac314/dinit)). Lots of things have happened since I began writing it, and this year I’m in a new country with a new job, and time to work on just-for-the-hell-of-it open-source projects is limited. And of course, writing blog posts detracts from time that could be spent writing code.

But the truth is: it’s come a long way.

Dinit has been booting my own system for a long while, and other than a few hiccups on odd occasions it’s been quite reliable. But that’s just my own personal experience and hardly evidence that it’s really as robust and stable as I’d like to claim it is. On the other hand, it’s now got a pretty good test suite, it’s in the OpenBSD ports tree, and it still [occasionally has Fedora RPMs built](https://copr.fedorainfracloud.org/coprs/mskarbek/dinit/), so it’s possible there are other users out there (I know of only one other person who definitely uses Dinit on any sort of regular basis, and that’s not as their system _init_). I’ve ran static analysis on Dinit and fixed the odd few problems that were reported. I’ve fuzz-tested the control protocol.

Keeping up motivation is hard, and finding time is even harder, but I still make slow progress. I released another version recently, and it’s got some nice new features that will make using it a better experience.

Ok, compared to Systemd it lacks some features. It doesn’t know anything about Cgroups, the boot manager, filesystem mounts, dynamic users or binary logging. For day-to-day use on my personal desktop system, none of this matters, but then, I’m running a desktop based on Fluxbox and not much else; if I was trying to run Gnome, I’d rather expect that some things might not work quite as intended (on the other hand, maybe I could Elogind and it would all work fine… I’ve not tried, yet).

On the plus side, compared to Systemd’s binary at 1.5mb, Dinit weighs in at only 123kb. It’s much smaller, but fundamentally almost as powerful, in my own opinion, as the former. Unlike Systemd, it works just fine with alternative C libraries like Musl, and it even works (though not with full support for running as _init_, yet) on other operating systems such as FreeBSD and OpenBSD. It should build, in fact, on just about any POSIX-compliant system, and it doesn’t require any dependencies (other than an event loop library which is anyway bundled in the tarball). It’ll happily run in a container, and doesn’t care if it’s not running as PID 1. (I’ll add Cgroups support at some point, though it will always be optional. I’m considering build time options to let it be slimmed down even from the current size). What it needs more than anything is _more users_.

Sometimes I feel like there’s no hope of avoiding a Systemd monoculture, but occasionally there’s news that shows that other options remain alive and well. Debian is having a vote on whether to continue to support other init systems, and to what extent; we’ll see soon enough what the outcome is. Adélie linux recently announced support for using Laurent Bercot’s S6-RC (an init alternative that’s certainly solid and which deserves respect, though it’s a little minimalist for my own taste). Devuan continues to provide a Systemd-free variant of Debian, as Obarun does for Arch Linux. I’d love to have a distribution decide to give Dinit a try, but of course I have to face the possibility that this will never happen.

I’ll end with a plea/encouragement: if you’re interested in the project at all, please do download the source, build it (it’s easy, I promise!), perhaps configure services and get it to run. And let me know! I’m happy to receive constructive feedback (even if I won’t agree with it, I want to hear it!) and certainly would like to know if you have any problem building or using it, but even if you just take a quick peek at the README and a couple of source files, feel feel to drop me a note.

  
  
from Hacker News https://ift.tt/38UltTy