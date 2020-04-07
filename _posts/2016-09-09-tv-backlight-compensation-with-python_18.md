---
title: 'TV backlight compensation with Python #Python #Television'
date: 2020-02-18T15:24:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/untitled-41.jpg)

There is nothing like getting a, LED TV for free. But Pekka Väänänen found free isn’t perfect.

> My Panasonic’s backlight is slightly broken causing an uneven pink color when it should be white.
> 
> The backlight LED array doesn’t emit enough blue or green light. This means most screen areas acquire a red tint. This is surprisingly passable in many films, but in black-and-white cinema it’s pretty terrible. It’s not possible to fix the red tint with regular color correction, since only some of the LEDs are broken. So maybe we could only tweak colors only near the broken LEDs?

[See how Pekka fixed the color situation](http://www.lofibucket.com/articles/tv_backlight_compensation.html) by capturing what the TV was presenting as a “white” background and using a correction using Python code. The results are amazing.

![Red blotches become visible when watching "Take Care of Your Scarf, Tatiana".](http://www.lofibucket.com/articles/img/tv/kaurism%C3%A4ki_before_thumb.jpg)