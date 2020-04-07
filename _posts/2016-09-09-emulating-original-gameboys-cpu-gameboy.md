---
title: 'Emulating the Original Gameboy’s
CPU #Gameboy #Nintendo #Gaming @nenharma82'
date: 2019-12-31T22:11:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-109.png)

Raphael Stäbler [writes on Medium](https://medium.com/@raphaelstaebler/building-a-gameboy-from-scratch-part-2-the-cpu-d6986a5c6c74) a series about emulating the Original Gameboy’s CPU.

> To build an emulation of a CPU you basically just need to implement these three steps. First the emulated CPU fetches an operation, then it decodes the operation and finally it executes the operation. After that it’s back to step one.
> 
> The Gameboy’s CPU is known as the DMG CPU. It is equipped with 6 registers of 16 bit each and they’re called AF, BC, DE, HL, SP and PC.

And in getting instructions (fetching):

> Execution simply starts at location `0`, that’s where the Gameboy’s boot ROM is located at. My Gameboy won’t incorporate the original boot ROM and start directly with the game. The first instruction for cartridges is at the memory address `0x0100` (the hexadecimal notation for `0000000100000000`). That’s the initial value of my program counter (PC register) and that’s where the CPU is going to look for the first 8 bits of the first operation to be executed.
> 
> I’m talking about fetching instructions from memory but I haven’t even talked about memory itself. That’s okay, though. For now let’s just assume we have some addressable memory and that there’s an actual executable program stored in it.

The details of the emulator are [in the article here](https://medium.com/@raphaelstaebler/building-a-gameboy-from-scratch-part-2-the-cpu-d6986a5c6c74).

See how the CPU was [emulated in C code](https://github.com/blazer82/gb.teensy/blob/master/lib/CPU/CPU.cpp). The entire CPU emulator is [on GitHub](https://github.com/blazer82/gb.teensy) and it looks as if there is a Gameboy emulator in progress with a Teensy 4 microcontroller and an LCD display.

![Demo GIF](https://raw.githubusercontent.com/blazer82/gb.teensy/master/demo/demo1.gif)