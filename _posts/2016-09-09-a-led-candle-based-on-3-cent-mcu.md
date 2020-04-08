---
title: 'A LED-Candle based on the 3 cent MCU #Microcontrollers'
date: 2019-10-09T14:24:00+01:00
draft: false
---

[Tim’s blog](https://cpldcpu.wordpress.com/2019/09/28/a-led-candle-based-on-the-3-cent-mcu/) goes into using the most inexpensive microcontrollers on the market, using a flickering LED candle as the test circuit.

> After having reviewed [sub $0.10 microcontrollers recently](https://cpldcpu.wordpress.com/2019/08/12/the-terrible-3-cent-mcu/), it’s time for some projects using the Padauk PFS154 and PMS150C. Considering my [previous investigation](https://cpldcpu.wordpress.com/2013/12/08/hacking-a-candleflicker-led/) of electronic and non-electronic candles, it appears only natural to chose this as a target for the lowest cost microcontrollers.

The software is based on an emulation of a flicker-LED IC. PWMs on the PFS154 and PMS150C are used to control the brightness of the LED. The PWM value is updated 30 times per second using an algorithm that generates a distribution of random numbers that is biased toward maximum brightness. A video of the results is above. The C-code for PFS154 can be found [here](https://github.com/cpldcpu/SimPad/tree/master/Toolchain/examples/candleflicker). The implementation for PMS150C in assembler can be found[ here](https://gist.github.com/cpldcpu/aa103568cd30d851d814072fabe5d0a4).

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-29.png)

Tim next goes into using an LED as a light sensor with the microcontrollers.

Overall the conclusion:

> For practical purposes, it appears that the Padauk MCUs are best suited for purely digital applications. When trying to use the analog periphery, it seems to be advised to limit it to low impedance or buffered analog signals.

Read [the whole article here](https://cpldcpu.wordpress.com/2019/09/28/a-led-candle-based-on-the-3-cent-mcu/).

![](https://cpldcpu.files.wordpress.com/2019/09/flickerfilter.png?w=1024)