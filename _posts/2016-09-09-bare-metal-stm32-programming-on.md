---
title: 'Bare metal STM32 programming on a quadcopter #Quadcopter #Drone #STM32'
date: 2019-12-17T22:11:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-57.png)

Tim Schumacher on [timakro.de posts](https://timakro.de/blog/bare-metal-stm32-programming/) about bare Metal STM32 programming on a Crazepony Mini quadcopter.

> Last year I got the [Crazepony Mini](http://www.crazepony.com/products/mini.html) quadcopter, and just recently I figured out how to program it. I will show my progress in this post, and it will also serve as a getting started guide for programming STM32 microcontrollers. We will build a minimal working example to blink an LED with only the GNU ARM compiler (gcc) and without any library dependencies.
> 
> You can get the quadcopter on eBay for around 100 €. It ships with a remote control that wirelessly connects to the drone. Like the drone the remote control has no casing, which I find for the drone looks really good, but unfortunately makes holding the remote control difficult. Both devices have firmware by Crazepony installed for which they published the source on [GitHub](https://github.com/Crazepony). They seem to be using the Keil IDE. Although it’s mainly made for educational purpose you can totally fly the quadcopter, and I had fun with it for a while.

The chip on the quadcopter is a 32-bit ARM Cortex-M processor with 64 KiB flash memory. On board are a wireless module, a 3-axis digital compass which detects orientation using the earth’s magnetic field, an altimeter that measures height by air pressure and an accelerometer and gyro sensor combined into one chip. In this post we will be using the LEDs on one of the 4 arms and most importantly the integrated USB to serial bridge to flash our program. You can get the schematic for the quadcopter [here](https://github.com/Crazepony/crazepony.github.io/blob/master/assets/schemtics/crazepony-fc-shematics.pdf).

> There are a few ways to flash firmware onto STM32 microcontrollers. You can use one of the debugging interfaces JTAG or Serial Wire Debug (SWD) which also have support for on-chip debugging. Note that SWD despite it’s name does not use the standard serial port of the chip. In fact, using the serial connection also known as UART connection is another and the most basic way to flash the controller. That’s what we will be using.

See the details in [the blog post](https://timakro.de/blog/bare-metal-stm32-programming/). It is great to be able to hack on these projects!

[https://timakro.de/public/bare-metal-stm32-programming/blinking-led.mp4](https://timakro.de/public/bare-metal-stm32-programming/blinking-led.mp4)