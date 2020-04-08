---
title: 'Artemis is an eyeglass-mounted device … @hackaday uses @adafruit Itsy
Bitsy M4 Express'
date: 2019-12-07T17:41:00+01:00
draft: false
---

![Glasses Sm](https://cdn-blog.adafruit.com/uploads/2019/12/glasses_sm.jpg)

[Upgrade Your Shades To Find Lost Items @ Hackaday](https://hackaday.com/2019/12/07/upgrade-your-shades-to-find-lost-items/).

> The device uses two servos for controlling the laser: one for X-axis control and the other for Y-axis control. The controls are executed from an Adafruit Itsy Bitsy M4 Express microcontroller.

…

> Artemis is an eyeglass-mounted device that can be configured to locate a specific type of object, or a person. When the target is found, Artemis will track it with a laser.
> 
> An eyeglass-mounted camera streams images to a Jetson AGX Xavier. An SSD300 model is used for object localization within these images. When the object of interest has been found, a laser diode is turned on.
> 
> A servo is also mounted on the eyeglasses for X-axis control of the laser. A second servo is mounted on top of the first, at a 90 degree angle, to give Y-axis control. The laser is mounted on the second servo.
> 
> Images are thresholded in OpenCV to determine the location of the laser pointer. With the location of the object, and also the laser, now determined it is possible to adjust the servos to place the laser over the object of interest.

[Read more](https://github.com/nickbild/artemis).