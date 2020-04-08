---
title: 'Reverse engineering a Shop Bot
ROM #BASIC #ReverseEngineering @abzman2000'
date: 2019-11-18T16:12:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-53.png)

[Evan’s Techie-Blog](https://abzman2k.wordpress.com/2019/11/13/reverse-engineering-a-shop-bot-rom/) continues exploration of a Shop Bot. Having dumped the ROM on the control board, what did they find? The answers are unexpected:

> After dumping the ROM from the shop bot we were intrigued by what we found.  Some of the strings in the ROM indicated that there was a BASIC interpreter on there, and there was even plaintext BASIC.  After some digging this is what we found.
> 
> Blue Earth Research was a company that made microprocessor development boards, presumably for industrial use.  They packaged (in our case) an 80c32 processor, a [ROM chip](https://abzman2k.wordpress.com/2019/11/12/dumping-the-x88c64-multiplexed-rom/), and I/O expander, and made it all as compact as possible.  They also did work with the 8052 and other processors in that line.  Among the series of boards they offered was the Xplor 32d, the ‘d’ standing for digital as there were boards with on board analog to digital converters.  They provided the BASIC interpreter’s hex file, the assembly source for a program that could load that hex file onto the microprocessor, and the source for libraries for use with peripherals such as a keypad, an HD44780 LCD screen, and X-10 automation hardware.

[See the entire pos](https://abzman2k.wordpress.com/2019/11/13/reverse-engineering-a-shop-bot-rom/)t as they dig into the code the ROM contains, both assembly and BASIC.

![setup](https://abzman2k.files.wordpress.com/2019/11/setup.png?w=450)