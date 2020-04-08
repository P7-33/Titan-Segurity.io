---
title: 'How I Switched to Plan 9'
date: 2019-12-05T05:05:00+01:00
draft: false
---

How I Switched To Plan 9
========================

Background
----------

Hi, I’m [SL](http://stanleylieber.com). You may remember me from my classic appearances in [contentious 9fans threads](https://9fans.topicbox.com/groups/9fans/Tf27e6479d8812712-Mf5d76f728866828465e3e33e/9fans-is-the-vanilla-plan-9-still-alive), or maybe you’ve read [one of my books](http://massivefictions.com).

I’m a veteran UNIX admin of 20+ years. I produced a bunch of multimedia stuff on a Macbook in the mid-2000s. I ran [9front](http://9front.org) on all my production servers and on my personal laptop (my main personal computer) almost exclusively from 2011 to 2017. In early 2017 I moved to a new job that involved a lot of traveling and infrequent access to WiFi. It also turned out that carrying a second laptop (besides my work laptop) added too much bulk/weight to all the stuff I already had to carry everywhere I went. I bought one of those early iPad Pros equipped with an LTE connection and did most of my necessarily mobile computing via that device for the better part of two years. I was able to rig up a command line connection to 9front using a native iOS SSH client and `drawterm -G`. I explained how this was accomplished in a [previous blog post](http://helpful.cat-v.org/Blog/2018/03/08/0/). Infrequently, I carried a [ThinkPad X230 Tablet](http://fqa.9front.org/fqa3.html#thinkpad_x230t_3434-db7), and later a ThinkPad X250 along with me, piggybacking off the iPad’s WiFi tethering.

The experience sucked. Replacing a general purpose computer with a jacked-up surveillance sensor package is not my idea of solving the problem of mobile computing. Lugging around extra pounds put a lot of strain on my already compromised back. Something had to give.

No pun intended.

Recently, I acquired a used [ThinkPad X1 Tablet (1st Gen)](http://openbsd.stanleylieber.com/hardware/thinkpad/x1t/g1/). This thing is small enough to fit in my bag, works well with both OpenBSD and 9front, and weighs almost as little as my iPad Pro with it’s folding keyboard cover. Finally, I’m back in business.

What Plan 9 Does For Me
-----------------------

Plan 9 excels at text manipulation. Conveniently, the entire system is controlled via text interfaces. [Private namespaces](http://doc.cat-v.org/plan_9/4th_edition/papers/names) ratchet this up into something even an idiot like me can use to construct efficient workflows.

_I can’t understand something presented to me that’s very complex._ – Ken Thompson

With the exception of multimedia and the modern web, all my needs are met. Pretty much anything people do with traditional UNIX terminals can be done at least as efficiently from a Plan 9 window. Even one accessed over SSH from an inferior operating system.

Is there support for playing audio (MP3, FLAC, etc.)? Yes.

Is there support for playing video? No.

Read this incomplete list of commonly requested software that ships with 9front: [http://fqa.9front.org/fqa1.html#1.8](http://fqa.9front.org/fqa1.html#1.8)

Watch this introductory video: [https://youtu.be/6m3GuoaxRNM](https://youtu.be/6m3GuoaxRNM)

Any more questions?

**Spoiler:** If you don’t care about my personal experience you can skip this blog post and proceed directly to the 9front Frequently Questioned Answers (FQA) section on using 9front, here: [http://fqa.9front.org/fqa8.html](http://fqa.9front.org/fqa8.html). The information is more technically informative but lacks the endearing flavor of my personal bullshit.

Text Editing
------------

I started trying to use Plan 9 in 2009. I had been editing tons of PHP code in OpenBSD using [vi(1)](https://man.openbsd.org/vi). A lot of fighting with cut and paste. In the midst of this gargantuan project at work I was reading my way through [http://cat-v.org](http://cat-v.org) for the first time. I decided to give [sam(1)](http://sam.cat-v.org) a try.

It was love at first sight. I never wanted to go back, and consequently I didn’t. Here was the solution to my distaste with `ex`: [structural regular expressions](http://doc.cat-v.org/bell_labs/structural_regexps/). I started out running the (at that time) very old portable version of `sam` in the OpenBSD ports tree, then ended up installing Plan 9 in QEMU, using the entire operating system as a glorified IDE. Wait, `vi` _who?_

_I’m tired of using vi._ – Bill Joy

Me too, buddy.

IRC
---

Programming from within Plan 9 naturally led to me wanting IRC and my text editor on the same screen at the same time. Luckily, there were several IRC clients to choose from. The simplest of which, [ircrc](http://code.9front.org/hg/plan9front/file/f4f9414878e1/rc/bin/ircrc), was a _shell script._ Remember that for later. Owing to Plan 9’s file interfaces, private namespaces, and modular design, much of the system is effectively built out of shell scripts.

**Note:** This would be a good time to familiarize yourself with Brian Kernighan and Rob Pike’s seminal [The UNIX Programming Environment](http://books.cat-v.org/computer-science/unix-programming-environment/). I re-read it at about this time, and felt like I was really starting to _understand_ it for the first time. Unlike modern UNIX, Plan 9 satisfies all the demands made by _TUPE._

`ircrc` was fine, but eventually I wanted a persistent client, something that better approximated `irssi` running in `tmux` on a remote shell server. This desire coincided nicely with my first attempts to setup a permanent Plan 9 server. I found what I was looking for in [irc7](http://plan9.stanleylieber.com/src/irc7.tgz), a client split into its own client/server components, with one part holding open a persistent connection to an IRC server on an always-up Plan 9 machine, and the other part serving as my interface to IRC on my personal machine, whenever and wherever I happened to be located.

E-mail
------

I found that I was spending more and more time in my Plan 9 installation in QEMU, and less and less time in UNIX proper. The next natural desire was getting e-mail into the mix. At this point I was still using Google’s gmail product, which I was able to [access over IMAP](http://fqa.9front.org/fqa8.html#8.4.1.1.1) using Plan 9’s native [upas](http://fqa.9front.org/fqa8.html#8.4.1) mail subsystem. I was shocked to discover that `upas` dated from 1984. (**Footnote:** It was not susceptible to the Morris worm.)

After a while I decided I didn’t want to be used by gmail anymore, so after many years I resumed hosting my own e-mail using the aforementioned `upas'` SMTPD and SMTP mechanisms. Yes, I’m still able to access my mailboxes over IMAP from whatever computer or device is readily at hand, or by simply logging in to the remote Plan 9 server and running [mail(1)](http://man.9front.org/1/mail) like a normal human being. One benefit of receiving mail on Plan 9 is that I’m able to configure spam filtering, mailing list sorting, autoresponders, etc., using the same kind of [simple shell scripts](http://man.9front.org/1/filter) that control the rest of the system. Here, again, learning the fundamentals pays dividends throughout the experience. It’s almost as if time spent learning one part of the system can be profitably applied elsewhere. As a heavy computer user for over thirty years, this still strikes me as suspiciously sensible.

WWW
---

9front ships with two web browsers, both written as jokes and abandoned by their authors in prior decades. Neither of them support Javascript, CSS, or anything beyond a meager subset of HTML. Of the two, 9front’s evolution of [Tom Duff’s](https://en.wikipedia.org/wiki/Tom_Duff) [mothra(1)](http://fqa.9front.org/fqa8.html#8.4.5.1) is perfectly usable if the aforementioned Rube Goldberg extensions are not required. Trying to use Plan 9 but still needing a modern web browser is a conundrum that has inspired many fledgling Plan 9 users to give up hope and [retreat](http://9front.org/buds.html) to the safety of their Macbooks. (**See also:** [9fans](https://9fans.topicbox.com/groups/9fans/Tf27e6479d8812712-Mf5d76f728866828465e3e33e/9fans-is-the-vanilla-plan-9-still-alive))

By the time I was ready to ditch the host operating system and install Plan 9 on bare hardware, my desire for the modern web experience had ebbed to an all time low. I went several years only touching a featureful browser when absolutely necessary. Which always felt gross. Your mileage may vary.

Torrents
--------

9front ships with a [native torrent client](http://man.9front.org/1/torrent) that works very well but does not support magnet URLs. For a long time this didn’t bother me because magnet links were (unlike today) not often required, and in any case, I could always just use a UNIX machine to perform the download. At some point the sheer inadequacy of this excuse began to wear thin. Why did I want to be forever tethered to UNIX? I finally got rid of the modern web browser, and now _this?_ Usefully, Plan 9 became a first class citizen to the [Go programming language](http://golang.org) community. Some Go torrent clients [actually work on Plan 9](https://github.com/anacrolix/torrent).

**Note:** Plan 9 may not be used to download legally encumbered material without express permission from the rights holder.

Making Books
------------

At the end of the day, what do I actually do with my computer?

I’m a writer. I write books. I use Plan 9 to type, format, collate, and prepare camera ready output for those books. Just like Brian Kernighan with his [Linotron 202](http://doc.cat-v.org/unix/typesetting/digital-restoration-and-typesetter-forensics/) (and, I should add, using many of the same software tools.)

Some examples of the build process include:

[https://code.9front.org/hg/fqa.9front.org](https://code.9front.org/hg/fqa.9front.org)

[https://bitbucket.org/stanleylieber/1f300](https://bitbucket.org/stanleylieber/1f300)

[https://bitbucket.org/stanleylieber/thrice\_great\_hermes](https://bitbucket.org/stanleylieber/thrice_great_hermes)

Start by reading each `mkfile`.

Is That It? I Gotta Go.
-----------------------

Seriously, what do you do with your computer?

Over time 9front sanded off its rough edges. I can do just about everything I need to do from a bare metal install. Today, we even have [vmx(1)](http://man/9front.org/1/vmx) for hosting OpenBSD or Linux virtual machines (just in case you need to interface with the U.S. government via the now-required modern web browser). A previous release of the [9front DASH1 manual](http://9front.org/propaganda/books) was created entirely on a ThinkPad running 9front (and [Gimp](https://www.gimp.org/) running inside OpenBSD running inside `vmx(1)`). 9front now even ships with a primitive [Microsoft Paint clone](http://man.9front.org/1/paint), several native [Sega](http://man.9front.org/1/sega) and [Nintendo](http://man.9front.org/1/nintendo) emulators, and a full port of [DOOM](http://man.9front.org/1/games). I never would have dreamed anything like this was possible back in 2009. As time goes by, there is less and less reason to boot anything else.

For what I do, I’m perfectly happy with it.

  
  
from Hacker News https://ift.tt/2YioZlL