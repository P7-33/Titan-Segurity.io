---
title: 'How I Made My Heating Smart Without Damaging Or Replacing
Anything #IoTuesday #AdafruitIO @AdafruitIO'
date: 2020-02-04T15:19:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/img_3420-2.jpg)

[Andy Bradford](https://twitter.com/andycb/status/1223606976246157313) has been wanting to upgrade their heating system for a some time – but their house is rented. Damaging the house would cause them to lose their security deposit, “so the whole system must do no damage, be made only of removable parts and be installed without modifying any of the existing infrastructure.”

How did they do it?

> I used [Tinkercad](https://www.tinkercad.com/) to design a driver head that would fit over the motor shaft and engage with the slot on the control spindle…I designed and printed a bracket that would hold the motor in place….

The system is controlled via an Adafruit Feather ESP8266, connected to [Adafruit IO](http://io.adafruit.com/):

![](https://cdn-blog.adafruit.com/uploads/2020/02/image-10.png)

> Having previously been impressed with [Adafruit IO](https://io.adafruit.com/) in my [air quality project](https://andybradford.dev/2019/11/29/monitoring-my-indoor-air-quality/), I decided to use it again here. I set up a new “heating” feed that I could write a 1 or 0 in to turn the heating on or off.

[Read the full writeup for more information about this project >>>](https://andybradford.dev/2020/02/01/how-i-made-my-heating-smart-without-damaging-or-replacing-anything/)