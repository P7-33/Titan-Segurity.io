---
title: 'Raspberry Pi 4 WiFi stops working at 2560x1440 screen resolution'
date: 2019-11-28T06:04:00+01:00
draft: false
---

[Enrico Zini](https://www.enricozini.org/)

Raspberry Pi 4 WiFi stops working at 2560x1440 screen resolution
================================================================

This is part of a series of post on the design and technical steps of creating [Himblick](https://www.enricozini.org/blog/2019/himblick), a digital signage box based on the Raspberry Pi 4.

One full day of crazy debugging, and the result is that if the Raspberry Pi 4 outputs HDMI at a resolution of 2560x1440, the WiFi stops working.

Any lower resolution we tried, from 2048x1080 down, does not show this problem.

We reproduced this:

*   on both microHDMI outputs
*   with two different cables: one with a microHDMI to HDMI dongle adapter, one direct microHDMI to HDMI
*   with three different RaspberryPi units
*   with 4 different power supplies: one rated at 2A, one rated at 3A, one rated at 3A bought in the Raspberry Pi shop in Cambridge, and a laptop USB-C charger
*   with stock Raspbian Buster Lite
*   with stock Raspbian Buster
*   killing every process in the system, starting the network manually with `wpa_supplicant` and `dhclient`, and starting X manually with `sudo X`
*   with two different SD cards

[At the bottom of this forum thread](https://www.raspberrypi.org/forums/viewtopic.php?t=247982#p1514642) (`guestxyz` dated Aug 07) someone mentioned screen resolution, which is what finally prompted us to try that. Thanks, `guestxyz`!

After confirming what the trigger was that caused the problem and chatting about it on IRC, [olasd](https://blog.olasd.eu/) found [this forum thread](https://www.raspberrypi.org/forums/viewtopic.php?t=254640) where more people are experiencing similar issues.

Further things left to try after chatting about it on IRC:

*   whether disconnecting the HDMI cable from the Pi end (with X still started at high resolution and everything) make the WiFi work again
*   switching the monitor to another input while the Pi is at 2560x1440
*   letting the monitor go into power saving mode while the Pi is at 2560x1440
*   [cable chokes](https://en.wikipedia.org/wiki/Ferrite_bead)

Generated with [staticsite](https://github.com/spanezz/staticsite) on 2019-11-28 02:00:02.794868+01:00.

  
  
from Hacker News https://ift.tt/2XQwjVM