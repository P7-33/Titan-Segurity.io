---
title: 'Converting a vintage Atari 1020 plotter to use
Grbl_ESP32 #Inktober #Atari #ReverseEngineering @buildlog'
date: 2019-10-08T14:54:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-23.png)

[Bart](https://twitter.com/buildlog) writes on [buildlog.net](http://www.buildlog.net/blog/):

> I decided to use Inktober to work on a new plotter. I am getting a little head start, so I can actually do some plotting in October.
> 
> I decided to try to convert an old **Atari 1020 plotter** to use [Grbl\_ESP32](https://github.com/bdring/Grbl_Esp32) as the controller. It would give the plotter Bluetooth and Wifi support and use gcode to plot. I could talk to the existing controller via the Atari 1020 serial protocol or I could completely replace the controller with the ESP32.
> 
> I decided it would be more fun, challenging and great opportunity to learn some things by replacing the controller. I set the following goals.
> 
> *   **Do no harm.** I want to avoid damaging any parts. Cut no plastic and cut no wires.
> *   **Change only the controller.** I will use the existing, unmodified switches, stepper motors, etc.
> *   **Clean implementation**. Try to make it look original. Use the existing mounting holes. Use existing holes for connectors, etc.

There are four posts so far going through reverse engineering and engineering a new controller board.

[See the progress on the blog here](http://www.buildlog.net/blog/).

Do you like reverse engineering or just an Inktober fan? Let us know in the comments below.