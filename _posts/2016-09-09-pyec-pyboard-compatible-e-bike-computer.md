---
title: 'pyEC: a pyBoard compatible e-bike computer #MicroPython @Makestuff4Fun'
date: 2020-02-27T17:37:00+01:00
draft: false
---

![](http://makestuff4.fun/wp-content/uploads/2020/02/pyEC-Overview.jpg)

Brian [writes on makestuff4.fun](http://makestuff4.fun/2020/02/09/pyec/) about pyEC, a pyBoard compatible e-bike computer.

> The pyEC is a [pyBoard](https://pyboard.org/) compatible multipurpose board capable of talking with just about anything on your E-bike. In fact it’s more a general purpose board capable of doing a whole host of digital electronic tasks. If you are not familiar with the pyBoard, it’s a STM32 based board that runs a type of Python for microcontrollers, [MicroPython](http://micropython.org/).
> 
> The idea behind the pyEC is that there are a number of layers interconnected to provide just the functionality you need and none of what you don’t. The main board, or “Layer” as I’ve taken to calling them, is the main pyBoard v1.1 compatible board. It has a ton packed into a 4cm\*4cm package. 50 pin header for inter-layer communications, CAN, OP Amp, Buzzer, LEDs, SD Card socket, user & reset switches and of course USB for debugging and loading on new programs.
> 
> Most connectivity has been moved to other “layers”. The “Control Layer” is just that, it controls all the layers and has the MCU. Without any additional layers it can basically just blink and beep.

See additional details about this project in [the blog post](http://makestuff4.fun/2020/02/09/pyec/).