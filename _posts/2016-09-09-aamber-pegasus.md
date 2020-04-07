---
title: 'Aamber Pegasus'
date: 2020-01-24T03:35:00+01:00
draft: false
---

[![Aamber Pegasus Photo.jpg](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Aamber_Pegasus_Photo.jpg/300px-Aamber_Pegasus_Photo.jpg)](https://en.wikipedia.org/wiki/File:Aamber_Pegasus_Photo.jpg)

The 1981 Technosys Aamber Pegasus shown here in its suitcase style cardboard case.

Developer

Hardware design - Stewart J Holmes  
Software design - Paul Gillingwater, Nigel Keam and Paul Carter.

Manufacturer

[Technosys](https://en.wikipedia.org/wiki/Technosys "Technosys") Research Labs.[\[1\]](https://en.wikipedia.org/wiki/Aamber_Pegasus#cite_note-apple1502-1)

Type

[Home computer](https://en.wikipedia.org/wiki/Home_computer "Home computer")

Release date

1981; 39 years ago (1981)

[CPU](https://en.wikipedia.org/wiki/Central_processing_unit "Central processing unit")

[MC6809C](https://en.wikipedia.org/wiki/Motorola_6809 "Motorola 6809") CPU

Memory

4k [RAM](https://en.wikipedia.org/wiki/Random-access_memory "Random-access memory"), later versions 64k RAM

Input

[Keyboard](https://en.wikipedia.org/wiki/Keyboard_(computing) "Keyboard (computing)")

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7d/Aamber_Pegasus_PCB_2569.jpg/300px-Aamber_Pegasus_PCB_2569.jpg)](https://en.wikipedia.org/wiki/File:Aamber_Pegasus_PCB_2569.jpg)

Aamber Pegasus PCB with MONITOR 1.0, FORTH 1.1A and FORTH 1.1B EPROMs installed.

The **Aamber Pegasus** is a home computer first produced in [New Zealand](https://en.wikipedia.org/wiki/New_Zealand "New Zealand") in 1981 by [Technosys](https://en.wikipedia.org/wiki/Technosys "Technosys") Research Labs.[\[1\]](https://en.wikipedia.org/wiki/Aamber_Pegasus#cite_note-apple1502-1)

The hardware was designed by Stewart J Holmes. The software was designed by Paul Gillingwater, Nigel Keam and Paul Carter.

It is thought that Apple Computers introduction of the Apple II computer into the New Zealand market, and its subsequent heavy educational discounting was the final nail in the coffin for Technosys and the Aamber Pegasus computer. Total production numbers are unknown, but it is thought "around one hundred" were sold.[\[2\]](https://en.wikipedia.org/wiki/Aamber_Pegasus#cite_note-2)[\[3\]](https://en.wikipedia.org/wiki/Aamber_Pegasus#cite_note-3)

Technical specifications
------------------------

Software
--------

An optional multi ROM board in conjunction with a rotating dial allowed switching between 6 [EPROM](https://en.wikipedia.org/wiki/EPROM "EPROM") banks containing multiple language environments, games and applications. The EPROM based language environments include EXTENDED [BASIC](https://en.wikipedia.org/wiki/BASIC "BASIC"), [PASCAL](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)"), BASIC (a variant of [TinyBASIC](https://en.wikipedia.org/wiki/TinyBASIC "TinyBASIC")), MAD ([Assembler](https://en.wikipedia.org/wiki/Assembly_language#Assembler "Assembly language")/[Disassembler](https://en.wikipedia.org/wiki/Disassembler "Disassembler")) and [FORTH](https://en.wikipedia.org/wiki/Forth_(programming_language) "Forth (programming language)"). Games available on EPROM are [TANKS](https://en.wikipedia.org/wiki/Tank_(arcade_game) "Tank (arcade game)"), [INVADERS](https://en.wikipedia.org/wiki/Space_Invaders "Space Invaders") and [GALAXY WARS](https://en.wikipedia.org/wiki/Galaxy_Wars "Galaxy Wars"). Other software included MONITOR (the system BIOS which needed to be present for the system to run) and a word processor application called WORD. The system allowed loading of programs by cassette. Some available cassettes include [SNAKES](https://en.wikipedia.org/wiki/Snake_(video_game) "Snake (video game)"), [STAR TREK](https://en.wikipedia.org/wiki/Star_Trek_(text_game) "Star Trek (text game)"), [HANGMAN](https://en.wikipedia.org/wiki/Hangman_(game) "Hangman (game)") and CHARACTER GENERATOR.

Networking
----------

A network version of the Aamber Pegasus provided connectivity to a 6809-based server (SWTPC-6809).[\[4\]](https://en.wikipedia.org/wiki/Aamber_Pegasus#cite_note-4) Especially the networking version attempted to address the New Zealand Government's computers in schools initiative,[\[5\]](https://en.wikipedia.org/wiki/Aamber_Pegasus#cite_note-5) but never produced the hoped-for large orders.

Unusual design features
-----------------------

One of the most unusual aspects of the machine is that to save the cost of a CRTC, the processor set up some bits on the 6821(PIA) to control the row being read out, then stepped through a series of NOPs so that the address lines of the CPU could act as a big counter. This counter drove the X address of the display RAM. On every row, the CPU updates the row number selected from the character ROM (and programmable character RAM) and every 16th row it increments the Y address of the display RAM. At the end of the screen the output is blanked, and the CPU gets to do some “real” work until the FIRQ pin is pulsed by the 50 Hz line from the power supply. Essentially the Pegasus used the mains frequency to trigger vertical sync. Because of this, the CPU is ~90% occupied as a counter, so in a non-real-time application you could disable the FIRQ (one bit in the 6809's CC reg) and the Pegasus ran ~10x faster – albeit with a blank screen. In this respect it was similar to the Sinclair [ZX81](https://en.wikipedia.org/wiki/ZX81 "ZX81") which used its ‘FAST’ mode in much the same way.

On the left side of the Pegasus motherboard you can see a small blob of putty. This putty is hiding a series of diodes that act as a simplistic 8-bit ID. This 8-bit ID will only allow EPROMs encoded with a corresponding ID to work in any individual machine. For example, an EPROM from a machine numbered 2569 will not work in another Pegasus with a different ID.

Modern emulation
----------------

The MAME emulator supports the Aamber Pegasus under the name "Pegasus",[\[6\]](https://en.wikipedia.org/wiki/Aamber_Pegasus#cite_note-6) and a number of the original manuals are available at the Internet Archive.[\[7\]](https://en.wikipedia.org/wiki/Aamber_Pegasus#cite_note-7)

See also
--------

References
----------

<img src="https://en.wikipedia.org/wiki/Special:CentralAutoLogin/start?type=1x1" alt="" title="" />

  
  
from Hacker News https://ift.tt/33lIj3c