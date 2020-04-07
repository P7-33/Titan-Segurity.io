---
title: 'Is Git Irreplaceable?'
date: 2020-01-07T01:38:00+01:00
draft: false
---

Is Git irreplaceable?
=====================

(1) By wyoung on 2019-07-21 06:34:08

I worry that Git might be the last mass-market DVCS within my lifetime. Git effectively has a global monopoly on DVCSes, and I don't see how you replace such a thing.

Replacing RCS with CVS was easy. Replacing CVS with Subversion was a big fight in many places. Replacing the remaining CVS and Subversion repos with something modern may never happen. Replacing Git with something better looks impossible.

Old small tech monopolies have fallen many times — e.g. VisiCalc — but I'm struggling to come up with a case where a truly global monopoly like Git has fallen to a single replacement. Here are my best examples, and they're all weak:

1.  [Metcalfe](https://en.wikipedia.org/wiki/Robert_Metcalfe)'s original Ethernet has been replaced a bunch of times, but we either keep calling its replacement Ethernet or we quickly make an Ethernet bridge for it. (e.g. WiFi)
    
    Fossil's already participating in the Git monopoly in this way through `fossil git export` and `fossil import git`.
    
2.  Microsoft's long-term stalwarts Windows and Office are dying, but they're not being replaced by a single thing. There's a diaspora for each: mobile OSes, Chrome OS, and desktop Linux on one side, and everything from Markdown to Google Docs on the other.
    
    Fossil is part of the Git diaspora, but that's a long way from achieving anything like a replacement of Git.
    
3.  Adobe's having a hard time hanging onto its old market, but it's because people are abandoning their powerful professional general-purpose tools in favor of task-specific and less-functional alternatives: CMSes instead of page-oriented web design, mobile photo apps instead of Photoshop, the web instead of print...
    
    I can only think of one case where a formerly market-leading Adobe product has been completely replaced by a single thing: Flash and HTML5. Observe that it took many years and a tremendous amount of market power to pull that off. Every other dead Adobe product is going the diaspora route, and the dying ones are going that direction, too.
    
    I believe Adobe's Creative Cloud subscription model is relevant here only in that it is a rational reaction of Adobe's leadership to the dying market, not the cause of it.
    
    Even if you believe CC is killing Adobe, that's irrelevant to our argument here, since subscriptions are the sustaining life force for GitHub, GitLab, BitBucket, etc. not their poison. Fossil's world domination will not come from dissatisfaction over subscription fees elsewhere. To the extent that anyone's replacing those cloud repository services with Fossil, I believe it's far more likely due to a wish for control, security, and overall simplicity than a desire to save money.
    
    The market's spoken on that point already with the move to cloud services, where we relinquish control and tolerate lower security to gain some up-front simplicity. It's really easy to set up a basic Fossil server, but it's not as easy as signing up for a GitHub account. Then if you want to add HTTPS to that, running a Fossil server suddenly becomes [a lot more complicated](https://www.fossil-scm.org/fossil/doc/trunk/www/tls-nginx.md).
    
4.  IPv4 still won't go away despite the standardization of a superior replacement 21 years ago, which subsequently achieved near-complete market penetration a decade or so ago.
    

Fossil can be one of the many little mammals that help take down the Excel and Git dinosaurs, but I cannot see it ever turning into the "human race" of DVCS products and overrunning the planet.

(3) By btiffin on 2019-07-21 16:02:21 and edited on 2019-07-21 16:10:52 [\[link\]](https://fossil-scm.org/forum/honeypot) in reply to [1](https://fossil-scm.org/forum/honeypot)

Even though I find Fossil to be a far more rewarding experience, Git did one thing that few technologies ever have done (any?). Across platforms, across development models, across the entire programming field, a majority of programmers now have a point of common interest, Git. 97% of programmers may only ever use a thin layer of monkey-see monkey-do subcommands and Git..b hand holder websites, but the technology is of common interest. As a profession, we should aim for more of those.

So, learn enough Git to not be left out of the common conversations, and then use Fossil. :-)

_Edit:_ Just as I pressed Submit I realized that SQLite may count as another of the rare ubiquitous technologies, putting Fossil only one small step away from the greatness of a globally accepted point of common interest.

(4) By Dewdman42 on 2019-07-21 17:50:30 [\[link\]](https://fossil-scm.org/forum/honeypot) in reply to [1](https://fossil-scm.org/forum/honeypot)

Unfortunately this is probably true. Git is everywhere. There is as LOT that I like better about fossil, but the truth is that if git included a ticket and wiki system for cheap like fossil does, I would probably switch over to the dark side and use git just in order to be compatible with all the git hooks that are everywhere these days. They are in IDE's, they are on GitHub and other sites, they are just everywhere. If you want to get along with most of the development world, git is the common denominator...like it or not...and there are things I do really dislike about git, but nonetheless that is where it is now. Things can change, we'll see what it looks like in 10 years, but for the foreseeable future that is true.

Nonetheless I continue with fossil for my own small projects because A, I like using it a lot more and B it includes the wiki and ticket system, which is really key for me. In order to setup similar functionality with git requires setting up a huge infrastructure that is way over the top too much for me...for me the sheer simplicity of fossil with a single small executable and a few sqlite files laying around is just way too awesome for the simple work I do.

(7) By ckennedy on 2019-07-23 16:46:39 [\[link\]](https://fossil-scm.org/forum/honeypot) in reply to [4](https://fossil-scm.org/forum/honeypot)

On the Git is everywhere front...

I've lately been playing a little bit with Rust. Cargo (the Rust build tool) supports using Fossil as the SCM. But it sets it up in a very Git way. A ".fossil" repository in the root of your checkout. Even when other tools attempt to support alternatives to Git, they support them in the Git way.

I use Fossil because I don't want to use Git. Git is NOT easier than fossil. Git is a horribly complex system with arcane invocations. Fossil is clean and simple. Like many things in the world today, the common perception is upside down because everything is based on a culture of personality. _If Linus Torvalds says use Git, then by his word, we will use Git._

I wish a culture of competency and logic predominated instead. Then I think Fossil would do better. I will continue to use Fossil because it is the first SCM product that was understandable to me and works well with the way I think and work.

(5) By jungleboogie on 2019-07-22 18:36:04 [\[link\]](https://fossil-scm.org/forum/honeypot) in reply to [1](https://fossil-scm.org/forum/honeypot)

I'm personally not worried about it whether git will be the dominate source control system. I'd rather people focus on building applications and maintaining those applications.

There was a time when it looked like Windows was going to be the only serious operating system for business or home use. Along came Apple computer and later their very polished operating system. Linux, while just a kernel, has fostered many distributions via kernel + userspace GUI stuff. Now there's a new X compositor thing, wayland, appearing. X.org may fade away and perhaps will only be memories in our minds and no longer a window system we remember. Windows has a subsystem layer to run Linux.

Just today someone on the OpenBSD mailing list asked why not use git. Here's the thread: [https://marc.info/?t=156380787000001&r=1&w=2](https://marc.info/?t=156380787000001&r=1&w=2)

All this said, I enjoy Fossil and appreciate its growth in popularity and features.

(6) By andybradford on 2019-07-23 00:44:33 [\[link\]](https://fossil-scm.org/forum/honeypot) in reply to [5](https://fossil-scm.org/forum/honeypot)

```
 > Just today someone on the OpenBSD mailing list asked why not use git. And a few individuals in that discussion also mentioned Fossil as a possible replacement though it was ruled out due to scale issues. I find it unlikely that OpenBSD will switch to any new DVCS or other VCS until the benefits clearly outweigh the costs. Thanks, Andy 
```

(9) By anonymous on 2019-07-23 18:05:50 [\[link\]](https://fossil-scm.org/forum/honeypot) in reply to [6](https://fossil-scm.org/forum/honeypot)

I thought one of the \*BSD projects is (or was) using Fossil. Obviously not OpenBSD.

(10) By wyetr on 2019-07-23 19:01:31 [\[link\]](https://fossil-scm.org/forum/honeypot) in reply to [9](https://fossil-scm.org/forum/honeypot)

Jörg Sonnenberger of the NetBSD project evaluated switching to Fossil some years ago but rejected it due to the time it takes to rebuild the repo lookup tables after the initial on-clone data pull. It took many hours on their busy ~25-year-old repo, so they couldn't tolerate it.

[We have a possible solution for that](https://fossil-scm.org/forum/forumpost/587041dc81), but now we want someone who cares to implement it.

(12) By jungleboogie on 2019-08-10 19:28:10 and edited on 2019-08-10 19:37:52 [\[link\]](https://fossil-scm.org/forum/honeypot) in reply to [6](https://fossil-scm.org/forum/honeypot)

(13) By wyoung on 2019-08-10 23:07:08 [\[link\]](https://fossil-scm.org/forum/honeypot) in reply to [12](https://fossil-scm.org/forum/honeypot)

`got` is still too complicated: it retains the stage/unstage and rebase features of Git.

(8) By anonymous on 2019-07-23 18:03:38 [\[link\]](https://fossil-scm.org/forum/honeypot) in reply to [5](https://fossil-scm.org/forum/honeypot)

> Just today someone on the OpenBSD mailing list asked why not use git.

Because git is the lazy choice.

I don't deny that git works for Linux. Linus is why git works for Linux. Linus demands a high level of discipline from his lieutenants and their lieutenants. I would expect any VCS to work for Linux while under Linus's command.

Why does git work for other projects? My guess is that many (most?) of those use git very simply, avoiding (most of) the features that get git users in trouble.

I say "(most of)" because rebase seems very popular. From my observations, non-core contributors seem to be contributing most on non-core features. I would expect these to be low activity parts of the code base, so much less likely to venture into trouble.

For what it's worth, nearly all of my attempts to contribute changes to even near-core features resulted in many iterations of updating and resolving conflicts before my changes were accepted (or I gave up).

This page was generated in about 0.008s by Fossil 2.11 \[9258d7462e\] 2019-12-26 01:26:58

  
  
from Hacker News https://ift.tt/39MJ9JZ