---
title: 'VC4 and V3D OpenGL Drivers for Raspberry
Pi @Raspberry_Pi #PiDay #RaspberryPi'
date: 2019-10-18T08:11:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/RPi-CI-500x308.jpg)

The original developer of the open source VC4 and V3D OpenGL drivers used by Raspberry Pi, Eric Anholt, is no longer developing these drivers. Here is Iago Toral, who, with a team from Igalia has stepped in to continue Anholt’s work.

via [RaspberryPi.org](https://www.raspberrypi.org/blog/vc4-and-v3d-opengl-drivers-for-raspberry-pi-an-update/)

> The GPU bundled with Raspberry Pi 4 is a VideoCore VI capable of OpenGL ES 3.2, a significant step above the VideoCore IV present in Raspberry Pi 3 which could only do OpenGL ES 2.0. Despite the fact that both GPU models belong in Broadcom’s VideoCore family, they have quite significant architectural differences, so we also have two separate OpenGL driver implementations. Unfortunately, as you may have guessed, this also means that driver work on one GPU won’t be directly useful for the other, and that any new feature development that we do for the Raspberry Pi 4 driver stack won’t naturally transport to Raspberry Pi 3.
> 
> The driver code for both GPU models is available in the [Mesa upstream repository](https://gitlab.freedesktop.org/mesa/mesa/). The codename for the VideoCore IV driver is VC4, and the codename for the VideoCore VI driver is V3D. There are no downstream repositories – all development happens directly upstream, which has a number of benefits for end users:
> 
> 1.  It is relatively easy for the more adventurous users to experiment with development builds of the driver.
> 2.  It is fairly simple to follow development activities by tracking merge requests with the `V3D` and `VC4` labels.

[Learn more!](https://www.raspberrypi.org/blog/vc4-and-v3d-opengl-drivers-for-raspberry-pi-an-update/)

* * *

[![3055 06](https://cdn-blog.adafruit.com/uploads/2017/01/3055-06.jpg "3055-06.jpg")](https://www.adafruit.com/raspberrypi)Each Friday is [PiDay](http://www.adafruit.com/blog/?main_page=blog&s=%23piday) here at Adafruit! Be sure to check out our [posts](http://www.adafruit.com/blog/category/raspberry-pi/), [tutorials](http://learn.adafruit.com/category/raspberry-pi) and new [Raspberry Pi related products](http://www.adafruit.com/raspberrypi). Adafruit has the largest and best selection of Raspberry Pi accessories and all the code & tutorials to get you up and running in no time!

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/31tPd4J  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)