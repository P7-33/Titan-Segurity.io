---
title: 'How to create an LED Rave Mask using Arduino, NeoPixels, and
C++ #NeoPixels #Arduino #Wearables'
date: 2020-03-02T14:53:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/03/untitled-1.jpg)

Armaiz Adenwala [blogs](https://armaizadenwala.com/blog/how-to-create-a-led-rave-mask-using-arduino/) about making an LED rave mask. The build is well documented and works with common parts like Arduino and [NeoPixel RGB programmable LEDs](https://www.adafruit.com/category/168). The code is in C++ and on [GitHub](https://github.com/ArmaizAdenwala/arduino-led-mask).

> The mask itself consists of 7 rows of [**WS2182B 144 LEDs/m NeoPixels**](https://www.adafruit.com/product/1506). There are a total of 161 LEDs, with the first row being 26. Each row decrements by 1, which means the 7th row will have 19 NeoPixels. Since we are decrementing by an odd number, we will line up the pixels to be in-between the two pixels above it. This results in a hexagon-like geometric pattern which will allow us to make awesome patterns for our visuals.

![](https://armaizadenwala.com/static/arduino_led_rave_mask-cbcb9a94a3265c77dae8108b8c000073.png)

See the [video below](https://youtu.be/-JsS84euiK8) for the mask in operation and the [blog post](https://armaizadenwala.com/blog/how-to-create-a-led-rave-mask-using-arduino/) for build details.