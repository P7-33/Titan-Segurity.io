---
title: 'NEW PRODUCT – Adafruit eInk Feather Friend with 32KB SRAM'
date: 2019-12-07T01:42:00+01:00
draft: false
---

[![4446](https://cdn-blog.adafruit.com/uploads/2019/12/4446.gif "4446.gif")](https://www.adafruit.com/product/4446)

### NEW PRODUCT – [Adafruit eInk Feather Friend with 32KB SRAM](https://www.adafruit.com/product/4446)

* * *

Easy e-paper finally comes to your Feather with this **Adafruit EInk Feather Friend** that’s designed to make it a breeze to add an eInk display. Chances are you’ve seen one of those new-fangled ‘e-readers’ like the Kindle or Nook. They have gigantic electronic paper ‘static’ displays – that means the image stays on the display even when power is completely disconnected. The image is also high contrast and very daylight readable. It really does look just like printed paper!

[![4446 iso ORIG 2019 12](https://cdn-blog.adafruit.com/uploads/2019/12/4446_iso_ORIG_2019_12.jpg "4446_iso_ORIG_2019_12.jpg")](https://www.adafruit.com/product/4446)

[![4446 demo 02 ORIG 2019 12](https://cdn-blog.adafruit.com/uploads/2019/12/4446_demo_02_ORIG_2019_12.jpg "4446_demo_02_ORIG_2019_12.jpg")](https://www.adafruit.com/product/4446)

We’ve liked these displays for a long time, and we’ve got Arduino/CircuitPython drivers for all of our Feathers, so wouldn’t an e-paper Feather Friend make a ton of sense? Luckily for us, just about every small-medium size EInk display made these days has a standard 24-pin connection. This Friend will add all the power supply support circuitry and level shifting so you can attach your favorite display (up to tri-color 4.2″) and wire it up to your favorite development board.

Using our CircuitPython or Arduino libraries, you can create a ‘frame buffer’ with what pixels you want to have activated and then write that out to the display. Most simple breakouts leave it at that. But…just about all EInk displays are write-only and many only let you update the full display (not partial update). That means you have to buffer the full image you want to display, taking up precious RAM.

[![4446 kit ORIG 2019 12](https://cdn-blog.adafruit.com/uploads/2019/12/4446_kit_ORIG_2019_12.jpg "4446_kit_ORIG_2019_12.jpg")](https://www.adafruit.com/product/4446)

[![4446 side 02 ORIG 2019 12](https://cdn-blog.adafruit.com/uploads/2019/12/4446_side_02_ORIG_2019_12.jpg "4446_side_02_ORIG_2019_12.jpg")](https://www.adafruit.com/product/4446)

**The Eink Feather Friend is much friendlier – it comes with  256 Kilobit (32 Kilobyte) SRAM chip**. That means you can control up to a 4.2″ 300×400 tri-color display (300\*400 \* 2 colors / 8 bits-per-byte = 30KB).  This chip shares the SPI port the eInk display uses, so you only need one extra pin. And, no more frame-buffering! **You can use the SRAM to set up whatever you want to display, then shuffle data from SRAM to eInk when you’re ready**. [**The library we wrote does all the work for you**](https://github.com/adafruit/Adafruit_EPD), [you can just interface with it as if it were an Adafruit\_GFX compatible display](https://github.com/adafruit/Adafruit_EPD). If you prefer not to use the chip, our libraries will automatically use the microcontroller/microcomputer internal RAM.

We even tossed on a MicroSD socket so you can store images, text files, whatever you like to display. Comes assembled and tested, with some header. You’ll need a soldering iron to attach the header for installing onto your Feather. Stacking headers will let you put another FeatherWing on top.

**Does not come with an EInk display or extension cable!** For use with just about any EInk display that has a 24-pin FPC connector. [See these schematics to verify that your display matches before purchasing](https://learn.adafruit.com/assets/57645).

[![4446 quarter ORIG 2019 12](https://cdn-blog.adafruit.com/uploads/2019/12/4446_quarter_ORIG_2019_12.jpg "4446_quarter_ORIG_2019_12.jpg")](https://www.adafruit.com/product/4446)

[In stock and shipping now!](https://www.adafruit.com/product/4446)

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/33XPQ8f  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)