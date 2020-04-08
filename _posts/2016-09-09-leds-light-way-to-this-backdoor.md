---
title: 'LEDs Light The Way To This Backdoor'
date: 2019-09-27T12:04:00+01:00
draft: false
---

A curious trend for some years in the world of PC hardware has been that of attaching LEDs to all the constituent parts of a computer. The idea is that somehow a gaming rig that looks badass will somehow be just a little bit faster. [As \[Graham  Sutherland\] discovered](https://twitter.com/gsuberland/status/1175570500292108289) when he wanted to extinguish the LEDs on his new Gigabyte graphics card, these LEDs can present an unexpected security hazard.

The key to their insecurity comes in the Gigabyte driver. This is a piece of software that you would normally expect to be an abstraction layer with an interface visible to your user level privilege, and a safe decoupling between that and the considerably more security sensitive hardware layer from which the LED bus can be found. Instead of this, the Gigabyte driver is more of a wrapper that simply exposes the LED bus directly to the user level. It’s intended that user-level code can easily bit-bang WS2812 LEDs without hinderance, but its effect is to provide a gaping hole in the security layers intended to keep malicious code away from the hardware. The cherry on the cake is provided by the discovery of a PIC microcontroller on the bus which can be flashed with new code, providing an attacker with persistent storage unbeknownst to the operating system or CPU.

The entire Twitter thread is very much worth reading wether you are a PC infosec savant or a dilettante, because not only should we all know something about the mechanisms of PC backdoors we should also be aware that sometimes a component as innocuous as an LED can be a source of a security issue.

Thanks \[Slurm\] for the tip.

Gigabyte motherboard picture: Gani01 \[[Public domain](https://commons.wikimedia.org/wiki/File:Gigabyte_motherboard2.JPG)\].

  
  
from Hackaday https://ift.tt/2nOh6GN  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)