---
title: 'ESP32-Cam Does Time Lapse'
date: 2020-01-29T01:44:00+01:00
draft: false
---

Just a few years ago, had someone asked you how much a digital camera with WiFi would cost, you probably wouldn’t have said $6. But that’s about how much \[Bitluni\] paid for an ESP32-CAM. He wanted to try making the little camera do time lapse, and it [turns out that’s pretty easy to do](https://bitluni.net/esp32camtimelapse).

Of course, the devil is in the details. The camera starts out needing configuration on the USB interface and that enables the set up of Arduino integration and WiFi configuration. Because it stores each frame of the image on an SD card, the board can’t take rapid-fire pictures. \[Bitluni\] reports a 3-second delay was about the shortest he could manage, but for most purposes, he was using at least ten seconds.

The program has a live preview window to help you set up the shot, but before you recordings start that should be turned off so as not to overload the little processor and the I/O busses. The result is a bunch of JPG images that you can easily convert that to a video on a PC if you wish.

This might be a good way to fit a camera on a [3D printer](https://hackaday.com/2018/04/13/3d-printer-time-lapse-videos-ditch-the-blur/), especially if the time lapse effect was desired. Otherwise, you might sync to a layer change. Now all \[bitluni\] needs is an [orbital rig](https://hackaday.com/2016/08/23/time-lapse-rig-puts-gopro-into-orbit-in-your-shop/).

  
  
from Hackaday https://ift.tt/37B6gFZ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)