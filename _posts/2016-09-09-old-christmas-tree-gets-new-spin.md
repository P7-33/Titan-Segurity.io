---
title: 'Old Christmas Tree Gets a New Spin'
date: 2019-12-16T07:11:00+01:00
draft: false
---

A couple of Christmases ago, \[Nick\] got tired of trying to evenly decorate his giant fake tree and built an MDF lazy Susan to make it easy as eggnog. But what’s the point of balanced decorations if one side of the tree will always face the wall? This year, \[Nick\] is giving himself the gift of a new project and [motorizing the lazy Susan so the tree slowly rotates](https://nick.zoic.org/art/saturnalia-a-rotating-christmas-tree/).

[![](https://hackaday.com/wp-content/uploads/2019/12/diy-slip-ring.png?w=240)](https://hackaday.com/wp-content/uploads/2019/12/diy-slip-ring.png)The saintly \[Nick\] decided to do this completely out of the junk box, except for all the WS2811 RGB LEDs on order that he hopes to synchronize with the tree’s movement. He started by designing a gear in OpenSCAD to fit the OD of the bearing, a task made much simpler thanks to the open-source gear libraries spinning around out there.

It was hard to get slow, smooth movement from the NEMA-23 he had on hand, but instead of giving up and buying a different motor, he designed a gear system to make it work. Our favorite part has to be the DIY slip ring \[Nick\] made from a phono connector to get around the problem of powering a rotating thing. This is a work in progress, so there are no videos just yet. You can watch [\[Nick\]’s Twitter](https://twitter.com/nickzoic/) for updates.

\[Nick\] didn’t specify why he chose to use WS2811s, but they have gotten pretty cheap. Did you know [you can drive them with VGA](https://hackaday.com/2016/01/04/driving-ws2811-leds-with-vga/)?

Via [Adafruit’s CircuitPython newsletter](https://blog.adafruit.com/2019/12/11/icymi-circuitpython-newsletter-200-circuitpython-libraries-binho-ble-and-more-python-adafruit-circuitpython-icymi-circuitpython-micropython-thepsf-adafruit/)

  
  
from Hackaday https://ift.tt/2LZa6jH  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)