---
title: 'Exploring Early ’90s Video Game Architecture With Another World'
date: 2020-01-18T04:17:00+01:00
draft: false
---

Curious about past computer architectures? Software engineer \[Fabien Sanglard\] has been experimenting with [porting _Another World_](http://fabiensanglard.net/another_world_polygons/index.html), an action-adventure platformer, to different machines and comparing the results in his “Polygons of Another World” project.

The results are pretty interesting. Due to the game’s polygon-based graphics, optimizations vary widely across different architectures, with tricks allowing the software to run on hardware released five years before the game’s publication. The consoles explored are primarily from the early ’90s, ranging from the Amiga 500, Atari ST, IBM PC, and Super Nintendo to the Sega Genesis.![](https://hackaday.com/wp-content/uploads/2020/01/arrival.gif?w=320)

The actual game contains very little code, with the original version at 6000 lines of assembly and the PC DOS executable only containing 20 KiB. The executable simply exists as a virtual machine host that reads and executes uint8\_t opcodes, with most of the business logic implemented with bytecode. The graphics use 16 palette-based colors, despite the Amiga 500 supporting up to 32 colors. However, the aesthetics still fit the game nicely, with some very pleasant pixel art.

There’s a plethora of cool tricks that emerge in each of the ports, starting with the original Amiga 500 execution. Prior to the existence of the CPU/GPU architecture, microprocessors had blitters – logic blocks that rapidly modified data within the memory, capable of copying large swathes of data in parallel with the CPU, freeing up the CPU for other operations.

![](https://hackaday.com/wp-content/uploads/2020/01/transparency2.gif?w=320)

To display the visuals, a framebuffer containing a bitmap drives the display. There are three framebuffers used, two for double buffering and one for saving the background composition to avoid redrawing static polygons. Within the framebuffer, several tricks are used to improve the graphical experience. For scenes with translucent hues, special values are interpreted from the framebuffer index by “reading the framebuffer index, adding 0x8 and writing back”.

Challenges also come when manipulating pixels given each machine’s CPU and bus bandwidth limitations. For filling in bits, the blitter uses a feature called “Area Fill Mode” that scans left to right to find edges, rendering the bit arrays with spaces between lines filled in. Since the framebuffer is stored in five separate areas of memory – or bitplanes – this requires drawing the lines and filling in areas four times, multiplying by the hundreds of polygons rendered by the engine. The solution was to [set up a temporary “scratchpad” buffer](https://scalibq.wordpress.com/2011/12/04/just-keeping-it-real-part-3/) and rendering a polygon into the clean space. The polygon can then get copied to the screen area with a masked blit operation since the blitter can render anywhere in memory.

Intrigued? The series continues with deep dives into [Atari ST](http://fabiensanglard.net/another_world_polygons_atariST/index.html), [IBM PC](http://fabiensanglard.net/another_world_polygons_PC_DOS/index.html), and upcoming writeups on SEGA Genesis/MegaDrive.

  
  
from Hackaday https://ift.tt/2TDwnbd  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)