---
title: 'Metro M7 RT1011 w/AirLift WiFi @EspressifSystem @NXP @arduino @adafruit'
date: 2020-03-01T02:24:00+01:00
draft: false
---

![3320Metrom701-1](https://cdn-blog.adafruit.com/uploads/2020/02/3320metrom701-1.jpg)

![3320Metrom702](https://cdn-blog.adafruit.com/uploads/2020/02/3320metrom702.jpg)

It’s not out yet…so don’t ask! It was so cold out, we stayed in and worked on the Metro M7 featuring the iMX RT1011 (the lil sister chip to the RT1062 that stars in the Teensy 4). This chip is really fast, clocking at 500 MHz, and has 128K of RAM. For FLASH, it uses an external QSPI chip which we’ll share for filesystem use as well. On the left we put an ESP32 footprint, we use the ESP32 as a WiFi co-processor. You can power it over USB C or a 9V DC power jack, we’ll probably change out the 3V LDO regulator for a buck, since the current requirements are going to be high on this board. This is only 2 layers, but we think it might be OK.