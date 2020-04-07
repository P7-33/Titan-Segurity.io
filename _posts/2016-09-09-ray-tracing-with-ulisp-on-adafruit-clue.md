---
title: 'Ray tracing with uLisp on the Adafruit CLUE
board #Raytracing #uLisp #CLUE #ItsyBitsy #Lisp #Graphics'
date: 2020-02-24T15:44:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/untitled-63.jpg)

The uLisp (Lisp for microcontrollers) website has updated their article on [graphical ray tracing with uLisp](http://www.ulisp.com/show?2NWA) to include the new, powerful [Adafruit Clue board](https://www.adafruit.com/clue) featuring the new nRF52840 processor.

> This is a simple ray tracer written in uLisp, running on a colour TFT display. The scene contains five spheres and a plane.
> 
> The [Adafruit CLUE](https://www.adafruit.com/clue) is an ideal platform for this application. It’s a fast platform for running uLisp, and incorporates a 1.3″ 240×240 colour TFT display (above).
> 
> Here’s the full version of the program for the Adafruit CLUE in a single file: [Ray tracing program CLUE](http://www.ulisp.com/list?30DA).

uLisp contains instructions to work with the hardware in the Lisp environment.

You can also see how the code works well on other Adafruit boards like the [ItsyBitsy M4](https://www.adafruit.com/product/3800) below.

![](https://cdn-blog.adafruit.com/uploads/2020/02/untitled-64.jpg)

> On an Adafruit ItsyBitsy M4 it occupies about 1460 Lisp objects and takes about 230 seconds. It should also run nicely on an Arduino Due or ESP32.
> 
> For details of the wiring to the TFT display, and the display interface, see [Plotting to a colour TFT display](http://www.ulisp.com/show?2NSB). Alternatively you could modify the program to plot to a different display.
> 
> Here’s the full version of the program for a 160×128 colour TFT display in a single file: [Ray tracing program](http://www.ulisp.com/list?2O52).

See the [article here](http://www.ulisp.com/show?2NWA) and [more information about the new CLUE board here](https://www.adafruit.com/clue).