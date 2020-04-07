---
title: 'LED Flame Illuminates the Beauty of Noise'
date: 2019-12-29T01:26:00+01:00
draft: false
---

Have you ever wrapped up a nice blinky project only to be disappointed by the predictability of the light or the color patterns? When it came to [lighting this LED candle](https://www.instructables.com/id/LED-Flame-Controlled-by-Noise), so was \[fungus amungus\]. But there’s a better way, and it involves noise.

[![](https://hackaday.com/wp-content/uploads/2019/12/perlin-flamin-1.gif?w=275)](https://hackaday.com/wp-content/uploads/2019/12/perlin-flamin-1.gif)Perlin noise was created in the early 80s by Ken Perlin while he was working on the movie _Tron_. Frustrated by the current state of computer graphics and too limited on space to use images, he devised an algorithm for generating natural-looking textures. Basically, you generate a bunch of numbers between 0 and 1, then assign values to those numbers, such as a range of greyscale values from black (0) to white (1), or the values from the color wheel. The result is much prettier than random numbers because the neighboring values for any given number aren’t radically different. You get nice randomness with hardly any overhead.

\[fungus amungus\] is using the FastLED’s noise function to generate the numbers, but there’s a whole lot more going on here. As he explains in the excellent video after the break, if you want to animate these values, you just add another dimension of them. Although \[fungus amungus\] is using a Trinket Pro and a NeoPixel ring, we think a simplified version could be done with a Circuit Playground Express using the built-in LEDs.

If you want to do it the hard way, [start by making your own NeoPixel ring](https://hackaday.com/2018/06/16/definitely-not-neopixel-rings-from-scratch/).

  
  
from Hackaday https://ift.tt/365JaGZ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)