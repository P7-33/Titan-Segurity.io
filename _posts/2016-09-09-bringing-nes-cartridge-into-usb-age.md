---
title: 'Bringing The NES Cartridge Into The USB Age'
date: 2019-11-28T01:14:00+01:00
draft: false
---

An NES cartridge in its most basic form is a surprisingly simple device, it contains two ROMs hosting all the code and assets of its game, and a Nintendo code chip that provided what was a state-of-the-art consumer DRM system for the 1980s. Decades later its inner workings have been extensively reverse-engineered, and there have been quite a few custom and reprogrammable cartridge designs produced.

This hasn’t stopped \[Troy Denton\] and \[Brad Taylor\] making a cartridge of their own though, and the result of their labours is [a fully USB reprogrammable cartridge for the Nintendo Entertainment System](http://troydenton.ca/?p=260). It provides nonvolatile storage and is a simpler design than you might expect, using a pair of 1 megabit Flash chips and emulating Nintendo’s DRM with an ATtiny microcontroller.

In itself it’s an interesting enough design, but what makes the write-up stand out is the description of having the boards manufactured by a PCBA service, and their subsequent debugging. A surface-mount micro USB socket that shorted out the USB power required a bit of rework to place Kapton tape beneath it, while another clever patch uses the NES clock signal to provide a read-only line for the memory. It’s also interesting to hear about their manual “crowdfunding” approach which was to ask around if anyone else wanted one so they could bring unit cost down by producing more cartridges.

If you’re interested in the NES DRM system, [it’s a subject we’ve touched on in the past](https://hackaday.com/2010/01/20/nes-console-to-cartridge-security-in-depth/).

  
  
from Hackaday https://ift.tt/35JgNhg  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)