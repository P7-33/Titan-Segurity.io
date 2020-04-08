---
title: 'Motor Temperature Estimation Without a Sensor'
date: 2019-11-11T16:57:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-30.png)

[Ben at uildits posts](http://build-its-inprogress.blogspot.com/2019/10/motor-temperature-estimation-without.html) about concerns for motor temperature in the use of their [Mini Cheetahs](https://build-its-inprogress.blogspot.com/search/label/HobbyKing%20Cheetah):

> …(Our) robots need to be even more robust than the original one.
> 
> One piece of that is preventing the motors from burning out.  During normal operation with a good locomotion controller, the motors barely even get above ambient (even going 3.7 m/s, the motors weren’t warm to the touch afterwards).  However, it’s really easy to write a controller that rapidly heats up the motors without actually _doing_ anything – railing torque commands back-and-forth due to instability, joints mechanically stuck against something, machine-learning algorithm flailing around wildly, etc.

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-31.png)

The usual way to do this would probably be to add a thermistor in the windings. But one can use some math to get an idea of what’s going on without such sensors.

> The temperature estimate uses an observer to combine two sources of information:  A thermal model of the motor, and a temperature “measurement” based on the resistance temperature coefficient of the copper in the windings. The resistance of the motor is estimated based on applied voltage, measured current, measured speed and known motor parameters, and compared against the resistance at a known temperature.  Sounds pretty simple, right? Of course not.

See the [video](https://youtu.be/mk1XINcKHq8) below and [the blog post](http://build-its-inprogress.blogspot.com/2019/10/motor-temperature-estimation-without.html) for the detailed analysis.