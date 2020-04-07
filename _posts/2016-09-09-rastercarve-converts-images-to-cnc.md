---
title: 'RasterCarve Converts Images to CNC'
date: 2020-01-20T04:14:00+01:00
draft: false
---

CNC machines are an essential part of the hacker’s toolset. These computer-controlled cutters of wood, metal and other materials can translate a design into a prototype in short order, making the process of iterating a project much easier. However, the software to create these designs can be expensive, so \[Franklin Wei\] decided to [write his own](https://www.fwei.tk/blog/opening-black-boxes.html). In particular, he decided to write his own program to engrave images, converting a photo into a toolpath that can be cut. The result is [RasterCarve](https://rastercarve.live/), a web app that converts an image into a GCode that can be fed into a CNC machine.

The motivation for this project was to learn how to do it, but also frustration at the cost of software such as [PhotoVCarve](https://www.vectric.com/products/photovcarve). Costing $149, this program does much the same as the one written by \[Wei\], albeit with a number of additional bells and whistles. He does an excellent job of describing how the conversion process works: his code creates a series of paths across the image, then converts the color of each pixel into a depth: The darker the image, the deeper the cut.

He also describes the process of taking this simple code and [converting it into a Javascript web app](https://www.fwei.tk/blog/a-c-programmer-learns-javascript.html), a process that has driven many a programmer to madness. It just goes to show that, although using other people’s stuff is fine, it often makes sense to try and do it yourself.

  
  
from Hackaday https://ift.tt/2R8VCAv  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)