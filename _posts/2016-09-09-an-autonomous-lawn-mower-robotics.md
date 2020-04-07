---
title: 'An autonomous lawn mower #Robotics #Automation @kt320'
date: 2020-01-13T15:49:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/Untitled-42.png)

Via Hackaday, two years ago Kenny Trussell designed a autonomous lawn mower based on an existing riding mower:

> It’s brains consist of a PixHawk board running Ardurover, an Ardupilot derivative for ground vehicles. Navigation is provided by a RTK GPS module that gets error corrections from a fixed base station via an [Adafruit LoRa feather board](https://www.adafruit.com/product/3178), to achieve centimeter level accuracy. To control the mower, Kenny replaced the pneumatic shocks that centred the control levers with linear actuators.

The mower has been cutting large fields (five to 18 acres). It uses the Ardupilot Mission Planner software for which he wrote a custom command line utility to create a concentric route for the mower to follow to completely cover a defined area. It runs off a 386 laptop which is still going strong.

See the [video series below](https://youtu.be/jKDqPt3H2bQ?list=PLIsYv3gzZOt9N9yZmpI_WYiMaBQ6HazOG) for a documented look and the Hackaday article [here](https://hackaday.com/2020/01/10/diy-autonomous-mower-in-the-wild/).

Learn more about Feather boards (including the [LoRa Feather](https://www.adafruit.com/product/3178)) on [Awesome Feather](https://github.com/adafruit/awesome-feather/blob/master/README.md) and [in the Adafruit store](https://www.adafruit.com/category/943).