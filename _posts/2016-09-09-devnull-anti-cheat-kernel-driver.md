---
title: '/Dev/Null: Anti-Cheat Kernel Driver'
date: 2020-02-04T02:31:00+01:00
draft: false
---

_Disclaimer: This post is kinda tech-heavy and concerns anti-cheat tooling that won’t be exclusive to League of Legends. Other games (like Project A) will be protected by the referenced upgrade before LoL is._

In a partnered study lasting approximately 8 years and backed by $20 million in federal funding, leading scientists managed to chronologically place the invention of cheating somewhere between 3.5 billion BCE and November 20th, 1985. While its precise origin remains indeterminate, one reality has become accepted as established fact: Cheaters gonna cheat.

Over the last two decades, the development of cheats and the technology to prevent them have escalated from the honorable fight for control of game client memory into methods that attempt to modify the underlying operating system—or even the hardware—of a cheater’s machine. These techniques can compromise an anti-cheat’s ability to retrieve good data, and that effect is compounded if that anti-cheat has to run in user-mode.  

**What is user-mode?**
----------------------

It describes a privilege level within an operating system, specifically the most restrictive tier software can run at. Your web browser, your legitimate copy of WinRAR, and your favorite games all run in user-mode. Within it, an application cannot directly “see outside” of itself, and instead, code must generally rely on OS’ native APIs to read or write memory not within its own process. Or to wrap that up in a semi-intelligible metaphor: We (in user-mode) have to ask the kitchen (Microsoft Windows) what’s been added to our beef goulash (League of Legends).

_![Kernel_Drivers_Image.png](https://images.contentstack.io/v3/assets/blt731acb42bb3d1659/blt28df09c60292cc6c/5e3101fd14bf1c024132f20e/Kernel_Drivers_Image.png)_

__If you’ve ever heard some stable genius hit you with a “lol my cheat is ring 0 undetected,” this is what they were referring to right before they were banned.__

  
In the last few years, cheat developers have started to leverage vulnerabilities or corrupt Windows’ signing verification to run their applications (or portions of them) at the kernel level. The problem here arises from the fact that **code executing in kernel-mode can hook the very system calls we would rely on to retrieve our data, modifying the results to appear legitimate in a way we might have difficulty detecting.** We’ve even seen specialized hardware utilizing DMA1 to read and process system memory—a vector that, done perfectly, could be undetectable2 from user-mode.

Now, while most players might find the idea of a corrupted Windows installation objectionable, a disturbing number of cheaters have shown themselves to be downright enthusiastic about the opportunity to jump onto some guy’s botnet in exchange for the ability to orbwalk. **So, an abundance of cheats currently run at a higher privilege level than our anti-cheat does**. To put that in the terms of our immaculate kitchen analogy: When we ask the head chef if our goulash ingredients are actually farm-to-table, some random dude in a toque convinces restaurant management that he’s “got this,” and then replies to our request with a “sure my guy, dig in.”

_1 DMA here refers to “Direct Memory Access,” a method by which a piece of hardware could, as you’ve probably suspected, directly access memory, windows API not required. Some of the more mature cheating communities [have used it](https://blog.esea.net/esea-hardware-cheats/) to rebroadcast memory to a separate computer for later processing and ESP._

_2 We straight hired the guy that developed the technique to detect it._  

**Why are you telling me this?**
--------------------------------

Well historically, your favorite anti-cheat team has been forced to play this game from the user-level, effectively giving cheaters a much-needed, twelve-stroke handicap. We haven’t needed both arms yet, primarily because we have the advantage of steady paychecks and the lack of strict bedtimes at our immediate disposal. But as much as we might like the idea of an ever-escalating appsec war with teenagers, we’re now entering a [multi-game universe](https://www.youtube.com/watch?v=h4FGqymg4k4&t=1876s) where linear time and sleep deficits will make this particular strategy untenable.

This is why **some of Riot’s future titles will be protected by a kernel driver**.

**I think I’m going to panic?**
-------------------------------

There are several reasons you should absolutely not do that.

1.  Stress can lead to excess hair loss, and I don’t want your head to get cold.
2.  This isn’t giving us any surveillance capability we didn’t already have. If we cared about grandma’s secret recipe for the perfect Christmas casserole, we’d find no issue in obtaining it strictly from user-mode and then selling it to The Food Network. The purpose of this upgrade is to monitor system state for integrity (so we can trust our data) and to make it harder for cheaters to tamper with our games (so you can’t blame aimbots for personal failure).
3.  This isn’t even news. Several third party anti-cheat systems—like EasyAntiCheat, Battleye, and Xigncode3—are already utilizing a kernel driver to protect your favorite AAA games. We’re just installing our own sous-chef to the Windows kitchen, so that when we hit em with a “where’s the beef,” we know we’re getting an honest answer.
4.  It will be significantly harder to create undetected cheats: protecting you from aimbots, protecting us from Reddit, and protecting cheaters from themselves.

We believe anti-cheat is one of the most important components of an online multiplayer game, and we want you to play in a world where you never have to doubt the abilities of your opponent. There is no cure for cheat fever, **but we will continue to do anything it takes to bring you the best competitive experience possible**.

Transmission complete, but I’ll be returning in approximately four megaseconds to tell you about bots in your ARAMs, a follow-up to our award-winning novella, “[Removing Cheaters from League](https://nexus.leagueoflegends.com/en-us/2018/10/dev-removing-cheaters-from-lol/).

  
  
from Hacker News https://ift.tt/2ujERtI