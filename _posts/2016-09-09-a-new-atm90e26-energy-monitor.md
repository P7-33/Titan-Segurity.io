---
title: 'A new ATM90E26 energy monitor FeatherWing by @whatnick
at @PCBWayJP #Feather'
date: 2019-12-16T17:03:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-43.png)

Via [Twitter](https://twitter.com/PCBWayJP/status/1204331574273044480?s=03), [PCBWay](https://twitter.com/PCBWayJP) is selling an [ATM90E26 energy monitor FeatherWing](https://www.pcbway.com/project/gifts_detail/ATM90E26_FeatherWing.html) designed by [Tisham Dhar](https://twitter.com/whatnick).

> **What is it?** An advanced Energy Monitor Featherwing capable of class-1 operation with appropriate Current Transformer and Potential transformer powering it.
> 
> **Why did you make it?** Before I commit a design to a PCB, I usually make a messy jumpers everywhere version on a breadboard. This is not always possible for a full complex design, often sections get committed to PCB and then modules find a home on the overall breadboard prototype.
> 
> This has been the fate of my [ATM90E26 Breakout](https://www.tindie.com/products/whatnick/atm90e26-breakout/). I planned to eventually make it into a single board /accurate wifi enabled Energy Monitor. For now it is living next to a [Feather Huzzah](https://www.adafruit.com/product/2821) on a breadboard. The ATM90E26 has the flexibility to be accessed both over SPI and UART. However the SPI mode it supports is only Mode 3, which is an unsupported mode of the ESP8266 Arduino stack. So I ported my ATM90E26 Arduino interface code over to UART mode with CRC check and everything after a few days of head scratching. You can find it on the [UART branch](https://github.com/whatnick/ATM90E26_Arduino/tree/UART) in github.
> 
> Meanwhile I put it all together into a featherwing form factor for PCB manufacture to make it a more complete dev-kit for easily testing the capabilities of the ATM90E26 in conjunction with all the other devices in the [Adafruit feather](https://www.adafruit.com/feather) family.
> 
> **What makes it special? **This board in combination with a few Feathers and FeatherWings can provide the functionality of the several hundred dollar [Atmel devkit](http://au.mouser.com/ProductDetail/Atmel/ATM90E2X-DB/?qs=sGAEpiMZZMsyTxkJnMM1W6ANc49mzXnPmPsTckpPEGTRvTdFsw7EmQ%3d%3d), it is also more flexible and cheaper than the [Smart Plug](http://au.mouser.com/ProductDetail/Atmel/ATSMARTPLUGEU/?qs=sGAEpiMZZMsg%252bek5lc7F5lNvriRPa95qP%2f%2faf1Ap9D0%3d). However Atmel products are very well engineered and I highly recommend trying them if you have the budget.

This is  a fully open source design (working towards OSHW certification).

See the [product page](https://www.pcbway.com/project/gifts_detail/ATM90E26_FeatherWing.html) and the [video below](https://youtu.be/YI2-IAKHrNQ) for more information.