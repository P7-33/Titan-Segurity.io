---
title: 'Core XY Explained'
date: 2019-11-13T01:08:00+01:00
draft: false
---

If you are building a CNC machine, a 3D printer, or even a plotter, you have a need for motion in both the X and Y directions. There are many ways to accomplish this, for example, some printers move the tool in the X direction and the bed in the Y direction while others move the entire X carriage in the Y direction and yet more use a delta mechanism. However, one of the oldest means of doing this is the Core XY method. It is interesting because both motors remain stationary and the business end moves entirely on belts or cords. This is similar to the H-Bot technique, but with some differences. \[Michael Laws\] has a video (see below) that [explains how two stationary motors can move a tool anywhere in an XY region](https://www.youtube.com/watch?v=_ramiM3KHYE).

The idea behind Core XY goes back to at least old drafting tables. You can think of it as an object held by two ends of the same belt. As one end of the belt gets shorter the other end gets longer. The belts are arranged so that motion of one motor causes the tool to move at a 45 degree angle. That means you have to move both motors to go in a straight line.

There’s some distinct advantages to doing things this way, but — of course — also some trade offs. There’s no perfect world and every choice you make will change the design of your machine in some way.

The video also talks about some other mechanisms, including delta printers. Controlling these printers takes a little extra math, although the math of a core XY mechanism isn’t all that tricky.

We have looked at a few machines that use [core XY before](https://hackaday.com/2018/08/03/classy-corexy-build-breaks-down-the-design-pinchpoints/). We’ve also compared the mechanism to the similar [H-Bot design](https://hackaday.com/2016/02/29/design-analysis-core-xy-vs-h-bot/).

  
  
from Hackaday https://ift.tt/2O5RGhh  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)