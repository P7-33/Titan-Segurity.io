---
title: 'The new 8-bit Commander X16 computer – Philosophy and
Specification @pagetable'
date: 2019-10-25T15:09:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-91.png)

Via [Pagetable.com](https://www.pagetable.com/?p=1373), Michael Steil discusses involvement in the Commander X16 project.

> The Commander X16 is a new 8 bit computer designed by David Murray of the well-known [“The 8-Bit Guy” online video channel](https://www.youtube.com/channel/UC8uT9cgJorJPWu7ITLGo9Ww).
> 
> 8 bit computers are great for learning about computer architecture, because they are simple enough that they can be fully understood, and they are great for learning to program, because they boot straight into a programming language. But 8 bit computers also have some annoyances like cheap, non-standard keyboards, TV-out and the reliance on floppy disks (or rather expensive SD card adapters).
> 
> Therefore, David is designing a new 8 bit computer in the style of Commodore computers like the VIC-20 and the C64, fixing the annoyances of retro computers by having:
> 
> VGA output (in addition to composite)  
> support for standard PS/2 keyboards (instead of a cheap built-in keyboard with a non-standard layout)  
> SD card for storage (instead of an additional floppy drive)  
> RS232 port for efficient cross-development  
> efficient modern power supply

![](https://cdn-blog.adafruit.com/uploads/2019/10/hello_world.gif)

From the software side, the Commander X16 feels like a Commodore computer. It’s ROM contains the “KERNAL” operating system derived from the C64 version, as well as an enhanced version of Commodore/Microsoft BASIC based on V2. (GIF above).

> Consequently, the X16 can be considered a sibling of the computers from the Commodore 8 bit family (PET, VIC-20, C64, CBM2, Plus/4, C128 and C65). It is not meant to be fully compatible with any of these machines, but it is as compatible as a Plus/4 is with a C64: BASIC programs without PEEK and POKE as well as machine code programs that only use the documented KERNAL API (e.g. BSOUT $FFD2) will just work, but existing code that accesses hardware would have to be ported.
> 
> The fact that the X16 breaks compatibility with the C64 is what I find particular interesting. Most retro projects try to recreate a classic computer. Users will start their favorite two games and then get bored. The X16 is a new system, with new tricks to discover – but familiar to people who know the C64.

[See the post for additional details](https://www.pagetable.com/?p=1373).