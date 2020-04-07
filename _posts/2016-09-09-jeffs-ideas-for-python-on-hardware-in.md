---
title: 'Jeff’s Ideas for Python on Hardware in 2020 – Time & Timekeeping'
date: 2020-01-02T18:13:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/persistence-crop.jpg)
=======================================================================

Introduction

Hi!  I’m Jeff Epler, AKA @jepler.  Python has long had a special place in my heart, because it is the computer language that makes me feel like I can accomplish anything I dream up.

When it comes to CircuitPython I’m new and have a lot to learn, but one thing I have seen is that it’s important to go in depth on an idea and make sure that the code in the core is ready to support a wide range of uses.  When we do this, we can find and fix problems before a new user having her first experience with CircuitPython has trouble.

One direction I’d like to dive deep is timekeeping.  If that sounds interesting to you, read on…

Timekeeping and Time Measurement
================================

I’m a bit of a [time nut](http://www.leapsecond.com/time-nuts.htm), so I’d like to enable CircuitPython to keep better time.  It won’t necessarily be my focus in 2020, but it’s a set of thoughts to fall back on if I’m ever idle.  What would it take to make projects like these possible in CircuitPython?

*    GPS Disciplined Oscillator
*    Frequency Counter accurate to 1 ppm (6 digits)
*    WWVB Receiver
*    World Clock

Enhance the time module
-----------------------

In CircuitPython today, timekeeping depends on the “SysTick”, and requires attention from the CPU every millisecond or a tick can be lost.  This happens regularly during certain tasks, like updating large numbers of neopixels. We should modify most of the routines in the time module to use a built in RTC counter instead of the SysTick counter, on all ports where this is possible.  This would probably still count time at around 1ms granularity, but would no longer risk losing time even while doing tasks that fully occupy the CPU for more than 1ms at a time.  This may also enable calibration of a board’s timing crystal, to reduce the number of seconds per day gained or lost while the device is running. Except optionally adding a calibration value in boot.py, this would be transparent to users of CircuitPython.

Enhance the frequencyio module
------------------------------

A GPS Disciplined Oscillator (GPSDO) is a clock signal (often 1MHz or 10MHz) that is regulated very precisely using the GPS time as a reference.  A Frequency Counter is a device to measure the frequency of a signal.

A key sub-problem of these tasks is to continuously count the relative rates of two input signals in the background, while continuing to do Python tasks in the foreground.   Right now, frequencyio only supports counting frequency in the foreground.

Enhance the pulseio module
--------------------------

WWVB is a radio signal that can be received almost everywhere in North America.  Its signal can tell you the current time, once per minute. If you have a self-setting wall clock in your home, it’s probably using this kind of signal.

For a WWVB Receiver, you need to continuously receive a low bandwidth (1 symbol per second) signal in the background while the foreground Python code decodes the signal received in a previous minute and does other tasks such as updating a clock display.  Right now, pulseio only supports recording pulses in the foreground.

Enhance timezone handling
-------------------------

For a World Clock, you need the ability to work with standard “tzinfo” files, to convert among local time, UTC time, and other world time zones.  This might be as simple as porting the python package [dateutil](https://dateutil.readthedocs.io/en/stable/) to circuitpython, or it might end up requiring new code designed just for CircuitPython.  In the end, you would be able to convert times between UTC and various local times.

\[Image Credit: [Mike Steele via Flickr](https://www.flickr.com/photos/21022123@N04/15694508911), cropped for presentation\]