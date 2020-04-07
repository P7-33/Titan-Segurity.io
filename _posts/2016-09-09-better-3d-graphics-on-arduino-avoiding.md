---
title: 'Better 3D graphics on the Arduino: avoiding flickering and
tearing #Arduino #Graphics'
date: 2019-12-30T17:41:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-108.png)

The [crawlingrobotfortress blog posts](http://crawlingrobotfortress.blogspot.com/2015/12/better-3d-graphics-engine-on-arduino.html) about creating better 3D graphics on the Arduino Uno. With the speed and memory of Arduino 328 boards, flickering and image tearing may be common:

> A while ago I purchased a cheap $4 Chinese LCD Arduino shield from Ebay. The board arrived with no documentation. … The vendor provided an archive containing a few amusingly translated datasheets, as well as a copy of [Adafruit’s Arduino LCD drivers](https://learn.adafruit.com/adafruit-gfx-graphics-library/overview). Evidently the product is a clone of the [Adafruit LCD shields](https://www.adafruit.com/products/1651), and uses the [ILI9341 LCD driver](https://forum.arduino.cc/index.php?topic=181679.0). I had hoped to use the display to show short animated GIF loops. This is not, in practice, possible. Test animations loaded slowly, with noticeable [flicker](https://en.wikipedia.org/wiki/Flicker_%28screen%29) and [vertical tearing](https://en.wikipedia.org/wiki/Screen_tearing). The Arduino does not have enough speed or bandwidth to render full-screen animation frames, but what about 3D vector graphics?

Both optimizing ILI9341 LCD drivers and rendering basic wireframe meshes have been done before. [XarkLabs](https://github.com/XarkLabs) provides an optimized fork of [Adafruit’s library](https://learn.adafruit.com/adafruit-gfx-graphics-library/overview). Youtube user electrodacus has also implemented an optimize driver for the ILI9341 communicating over SPI. Existing 3D wireframe demonstrations, even [ones using optimized drivers](http://www.mrt-prodz.com/blog/view/2015/05/tiny-3d-engine-on-the-atmega328-arduino-uno), display a noticeable flicker when the animation updates. This flicker is caused by the delay between when the previous frame is erased and when the new frame is drawn.

> There simply isn’t enough processing power on the Arduino to render anything significant within one frame length, and isn’t enough memory to perform off-screen rendering. The ILI9341 supports a 16-bit RGB color interface with 320×240 pixels, and buffering even a single frame would take 150 kilobytes of memory, compared to the AtMega328’s two kilobytes of RAM.
> 
> The solution is to render animation frames in such a way that the intermediate rendering stages are not noticeable to the human eye. This can be achieved by rendering subsequent frames on top of previous frames without erasing, and then erasing only those pixels that have changed.

See the techniques in [the article here](http://crawlingrobotfortress.blogspot.com/2015/12/better-3d-graphics-engine-on-arduino.html) and in the video below.