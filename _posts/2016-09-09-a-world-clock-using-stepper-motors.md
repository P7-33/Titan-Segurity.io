---
title: 'A world clock using stepper motors #Clock @McuOnEclipse'
date: 2019-12-17T19:32:00+01:00
draft: false
---

[Erich Styger](https://twitter.com/McuOnEclipse) [blogs about a project](https://mcuoneclipse.com/2019/11/24/world-stepper-clock-with-nxp-lpc845/) to World Stepper Clock with a NXP LPC845.

> I really love clocks. I think this is I am living here in Switzerland. Beside of that: clock projects are just fun :-). After I have completed a single clock using stepper motors (see “[DIY Stepper Motor Clock with NXP LPC845-BRK](https://mcuoneclipse.com/2019/08/25/diy-stepper-motor-clock-with-nxp-lpc845-brk/)“), I wanted to build a special one which is able to show up to four different time zones: Below an example with London (UK), New York (USA), Beijing (China) and Lucerne (Switzerland):

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-52.png)

> A microcontroller (NXP LPC845, ARM Cortex-M0) is driving 8 stepper motors, one clock uses two motors, each individually controlled. Because the motors are special 360° motors, the zero position is determined with a magnet and a hall sensor for each hand. Using a serial connection, the clock can be configured. Because the clock can be away from a host PC, the clock uses RS-485 (to communicate).

See the [video](https://youtu.be/W1imaXLmnp4) above and [see the blog post](https://mcuoneclipse.com/2019/11/24/world-stepper-clock-with-nxp-lpc845/) for additional videos and detailed build notes.