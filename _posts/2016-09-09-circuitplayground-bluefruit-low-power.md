---
title: 'CircuitPlayground Bluefruit low power
tests @adafruit #bluefruit @arduino @circuitpython'
date: 2019-10-25T14:39:00+01:00
draft: false
---

![4333-11](https://cdn-blog.adafruit.com/uploads/2019/10/4333-11.jpg)

![Btpower01](https://cdn-blog.adafruit.com/uploads/2019/10/btpower01.jpg)

Doing some low power testing for a revision of the CircuitPlayground Bluefruit, our prototype has the ability to turn off the neopixels/light/temp/mic sensor in addition to the speaker amp. When we do that, we drop down to 280uA quiescent when we go to sleep (by running delay() in arduino). Running Arduino code is about 6mA.

![Ptpower02](https://cdn-blog.adafruit.com/uploads/2019/10/ptpower02.jpg)

Here’s what it looks like when we wake from sleep and enable the neopixels and sensors, hang out for a bit, then go back to sleep. there’s a skinny spike of 50mA, maybe the neopixel PWM circuitry turning on at once?