---
title: 'Feel the Force with a Pocket Magnetometer'
date: 2020-01-25T07:08:00+01:00
draft: false
---

With the rise of affordable 3D printers, we just don’t see the projects in Tic Tac boxes that we used to. That’s kind of a shame. Not only are you upcycling existing plastic when you use one, they’re decently sized component vessels for pocket builds such as \[rgco\]’s [portable magnetometer](https://www.instructables.com/id/Portable-Magnetometer/), especially if you can get the 100-count box. Best of all, they’re see-through!

Sure, you could get a magnetometer app for your phone to test out the strength of your Buckyballs, but this is more fun, and you can use it in more places. This build doesn’t take much — an Arduino Nano reads from a Hall effect sensor and outputs the magnetic flux density in militeslas (mT) on an OLED. Fortifying the sensor by mounting it inside the body of an old (also see-through!) ballpoint pen body is a nice touch.

In order to calibrate it, \[rgco\] made a solenoid by wrapping a length of PVC with magnet wire. The code for this very portable and low-cost magnetometer measures the magnetic field 2000 times in under three-tenths of a second, and outputs both the mean and the standard deviation of these measurements.

Magnetometers can ID all kinds of things from submarines to Suburbans. [Here’s an ESP8266 magnetometer that opens a driveway gate when it detects the car](https://hackaday.com/2019/09/10/detecting-cars-with-an-esp8266-magnetometer/).

  
  
from Hackaday https://ift.tt/2NZU1ep  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)