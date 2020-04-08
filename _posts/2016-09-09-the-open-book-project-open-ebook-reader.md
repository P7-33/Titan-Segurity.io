---
title: 'The Open Book Project – an open eBook
reader #ebook #CircuitPython #Feather #SAMD51 @josecastillo @Hackaday @MicrochipMakes'
date: 2019-11-01T14:42:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-2.png)

[Joey Castillo](https://twitter.com/josecastillo) is working on his [Open Book Project](https://github.com/joeycastillo/The-Open-Book/tree/master/Open%20Book%20Feather). [Via Twitter](https://twitter.com/josecastillo/status/1188843059628380160):

> Meet the very first Open Book, in lovely [@oshpark](https://twitter.com/oshpark) purple! A Feather-form SAMD51 board (inspired greatly by the [@Adafruit](https://twitter.com/adafruit) [PyBadge](https://www.adafruit.com/product/4200)) with eInk screen, 8 buttons, headphone jack, STEMMA ports and more. Some things to fix in Rev 2 but it’s getting very close ![🙂](https://s.w.org/images/core/emoji/12.0.0-1/72x72/1f642.png) 

[Via Hackaday](https://hackaday.com/2019/10/31/building-an-open-hardware-ebook-reader/): The Open Book Project has taken a somewhat circuitous path to get to this first prototype, and Joey had previously developed and built the “eBook Feather Wing”. While they look very similar, that earlier incarnation required an [Adafruit Feather](https://www.adafruit.com/category/943) to operate and was used to help refine the firmware and design concepts that would go into the final hardware.

The Open Book is powered by a (Microchip) ATSAMD51N19A processor with a GD25Q16 2MB flash chip to hold the [CircuitPython code](https://circuitpython.org/), and a microSD slot to store the actual book files. It also features support for audio output via a standard 3.5 mm headset jack, an RGB status LED, and expansion ports that tap into the I2C interface for adding whatever other hardware you can dream up.

One of the most interesting aspects of this Creative Commons licensed reader is the extensive self documentation \[Joey\] has included on the silkscreen. Every major component on the back of the PCB has a small description of its purpose and in some cases even a breakdown of the pin assignments.

See Joey’s [Twitter](https://twitter.com/josecastillo/status/1188843059628380160) and the [project GitHub](https://github.com/joeycastillo/The-Open-Book/tree/master/Open%20Book%20Feather) and read the [Hackaday article](https://hackaday.com/2019/10/31/building-an-open-hardware-ebook-reader/). Love this project!

![Image](https://pbs.twimg.com/media/EH-ec0OWoAA9lo4?format=jpg&name=4096x4096)

![Image](https://pbs.twimg.com/media/EH-ec0OXUAcFRSc?format=jpg&name=4096x4096)