---
title: 'Deconstructing Sega’s System 16
Security #Console #Gaming #VintageComputing'
date: 2019-10-21T15:08:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-75.png)

Eduardo Cruz writes on [the Arcade Hacker blog](http://arcadehacker.blogspot.com/) about security in the Sega System 16 gaming console.

> Sega’s System 16 was a new arcade platform introduced in 1986 as a successor to the earlier 8 bit Z80 designs Sega System 1 and System 2. The new system brought in many system upgrades including 16 bit Motorola 68000 CPUs and pioneering security.
> 
> Above all, System 16 was one of Sega’s most successful games platform, seeing the release of countless epic games that form part of our collective childhood memories. Among my favorites titles are Shinobi, Golden Axe, Outrun, or Michael Jackson’s Moonwalker to name a few, I bet you have yours too.
> 
> The platform got subsequent updates and revisions introducing improvements to base specs and integration of chips. The initial System 16A was released in 1986 followed soon by the more common System 16B in 1987, a later revision known as System 18 was introduced in 1989.

The platform had some beefy specs for the time – the System 16A:

> Main CPU: Motorola 68000 or Hitachi FD1089/FD1094 security modules @ 10 MHz  
> Memory: 16kB + 2 kB  
> Sound CPU: NEC uPD780C-1 (Zilog Z80) @ 4 MHz  
> FM synthesis sound chip: Yamaha YM2151 @ 4 MHz (8 FM synthesis channels)  
> PCM sound chip: NEC uPD7751@ 6 MHz, ADPCM channels: 3, Audio bit depth: 8-bit  
> Custom GPU chipset: 315-5011 sprite line comparator, 315-5012 sprite generator, 2× 315-5049 tilemap chips, 315-5107 & 315-5108 display timers, 315-5143 & 315-5144 sprite chips, 315-5149 video mixer  
> Performance: 12.5874 MHz sprite line buffer render clock, 6.2937 MHz sprite line buffer scan/erase & pixel clock  
> Display resolution: 320×224 to 342×262 (horizontal), 224×320 to 262×342 (vertical), progressive scan  
> Graphical planes and sprite capabilities: 2 tile layers (row & column scrolling, 8×8 tiles), 1 text layer, 1 sprite layer. Dual line buffers, double buffering, 128 on-screen sprites, 800 sprite pixels (800.75 sprite processing ticks) per scanline, 100 sprites per scanline, 16 colors per sprite, 8 to 256 width, 8 to 256 height

![](https://1.bp.blogspot.com/-b-bzvDr-lcY/XaGw89uIHtI/AAAAAAAAC78/_1Og9DCtHrw-dNUDpXmM3C8QcCyiHHhvwCLcBGAsYHQ/s1600/AlienSyndrome.pcb.jpg)

Security
--------

With the introduction of System 16, selected games replaced the main system 68000 CPU with secretive Hitachi branded device modules, these modules were Hitachi FD1089 revisions A and B, and a more commonly found Hitachi FD1094.

> Most modules feature a sticker with a seven-digit code unique per game title and region. For arcade operators or collectors trying to replace these modules with a regular 68000 CPU or a different Hitachi module, this would result in a non-working game. A battery inside also plays a fatal role, losing its power renders the module unusable.
> 
> In combination with encrypted roms the modules provided Sega with a way to control piracy and stop unauthorized board conversions (when a game base system is reused for a different game).

[See the article for more information](http://arcadehacker.blogspot.com/2019/10/deconstructing-sega-system16-security-part1.html).