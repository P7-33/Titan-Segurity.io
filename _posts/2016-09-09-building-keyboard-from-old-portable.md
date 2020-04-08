---
title: 'Building a keyboard from an old portable (electronic) typewriter'
date: 2019-11-09T07:31:00+01:00
draft: false
---

A while back I picked up an old Canon Typestar IV portable typewriter in a junk shop: this is one of a class of electronic typewriter known as the ‘thermal wedgie’: battery powered, printing via a thermal print head to either heat sensitive paper or with a special ribbon, they’re light, small and extremely quiet. Mine will run off rechargeable batteries. Unfortunately the ribbons are impossible to find and is it’s not valuable and I have no need for one anyway, I’ve ripped the guts out and crudely turned it into what’s turned out to be a really rather nice USB keyboard — the keyswitches are excellent.

[![](http://cowlark.com/2019-11-03-keyboard/typewriter.jpg)](http://cowlark.com/2019-11-03-keyboard/typewriter.jpg)

…and if you want to see it in action, here’s the demo reel.

VIDEO

I haven’t identified the keyswitches yet The keyswitches are [SMK spring over dome](https://deskthority.net/wiki/SMK_spring_over_dome): they’re linear with a very quiet tactile bump near the bottom of the travel, and super smooth. Each switch has a discrete rubberdome in a box housing which pushes a carbon pad against a PCB. For detailed pictures of the inside, there’s [an excellent teardown on Deskthority](https://deskthority.net/viewtopic.php?f=62&t=19859&start=).

The very special ribbon lasted for about half an hour before it ran out, but I did manage to do a video demonstrating the typewriter with some light disassembly to see how it worked. The print quality was pretty good, actually.

VIDEO

Incidentally, these ribbons record every single keypress for posterity. Mine contained quite a lot of incriminating personal information about the previous owner, including name, address, Swiss medical insurance number, disability information, etc. Be warned.

(As a special bonus video, those of you into OCD/AMSR stuff might enjoy this video of me [painstakingly reattaching all the keycaps after cleaning them](https://www.youtube.com/embed/Wj29_DuSvYU)…)

So, actually replacing the guts with a USB controller was interesting. I used a [PSoC5 CY8CKIT-059 development board](https://www.cypress.com/documentation/development-kitsboards/cy8ckit-059-psoc-5lp-prototyping-kit-onboard-programmer-and). This is a 80MHz ARM device with a small amount of RAM and a built-in FPGA, costing about $10-$15 depending on country. It’s completely overkill for this sort of application but I had one on my desk, and the development tools are great, although very proprietary and closed source. It’s flexible enough and has enough GPIO pins that I could simply wire every input or output from the keyboard to the board and then worry about the mapping later.

[![](http://cowlark.com/css/link.svg)The source code's Github repository](https://github.com/davidgiven/maxii-keyboard/tree/master/typestar4-keyboard.cydsn)

If you're interested in the firmware source code, it's here. It's not in very good shape but might serve as a decent example of how to implement a USB keyboard and USB CDC serial port on a PSoC5 device.

One interesting thing I discovered, which required me to modify the keyboard PCB to work around, was that the Shift Lock key worked the traditional typewriter way, rather than the modern computer way: you press it and it engages (and the nice little integrated LED comes on), but to disengage shift lock you press the Shift key instead. Pressing Shift Lock again does nothing. This was actually handled in discrete logic on the PCB, which I had to rip out.

The keyboard also has an integrated 15-character-plus-lots-of-bespoke-symbols LCD display. This is internally driven by a completely standard HD44780 derivative. The PSoC5 is completely capable of driving this, so I wired it up to a USB serial port. The computer’s now capable of displaying any text it likes on it. Admittedly, fifteen characters isn’t much, but it’s perfectly adequate for a word count. There’s so much spare flash and RAM on the microcontroller, actually, that I did have thoughts about adding a calculator or Forth interpreter, but luckily I got distracted by something else before that happened…

[![](http://cowlark.com/2019-11-03-keyboard/lcd.jpg)](http://cowlark.com/2019-11-03-keyboard/lcd.jpg)

There were also rather fewer modifier keys than I was hoping for. The keyboard was arranged as a matrix probe affair, so that the microcontroller energies one probe line at a time and then checks the sense lines for a signal. These have problems with rollover. While they typically work fine for typing, modifier keys on such keyboards are typically wired directly to the keyboard controller so that they don’t count towards the rollover limit.

I wanted to use this for a PC keyboard, which comes with Control, Shift, Meta and Alt modifier keys as standard; plus, because the keyboard doesn’t have a navigation cluster, I wanted to add an extra modifier key as a layer switch to allow direct access to these. This required further modification to the PCB to remove these keys from the keyboard matrix and wire them directly to the PSoC5 board.

[![](http://cowlark.com/2019-11-03-keyboard/closeup.jpg)](http://cowlark.com/2019-11-03-keyboard/closeup.jpg)

The end result is extremely nice, and I even managed to keep most of the paper feed mechanism (although I had to cut off the print head and motor assembly). With the lid closed, it looks just like it originally did, if you disregard the USB cable. Sadly, it’s not as comfortable to type on as I hoped. The layout’s not quite standard, missing a few important keys used for programming, which is what I do most; it’s also raised further than I’d like. I haven’t tried it with a wrist rest, though.

I recorded most of the work for posterity. If you’re into long, tedious workbench videos, enjoy! Or not, as you wish.

VIDEO VIDEO VIDEO VIDEO

  
  
from Hacker News https://ift.tt/36D7NLV