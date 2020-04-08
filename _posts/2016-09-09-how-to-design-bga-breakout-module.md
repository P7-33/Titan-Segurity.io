---
title: 'How To Design A BGA breakout Module'
date: 2019-11-17T07:08:00+01:00
draft: false
---

Surface mount devices can take some adjusting to for hackers primarily used to working with through-hole components. Despite this, the lure of the hottest new parts has enticed even the most reticent to learn to work with the technology. Of course, time rolls on and BGA parts bring further difficulties. \[Nate\] from SparkFun worked on the development of the RedBoard Artemis, [and broke down the challenges involved.](https://www.sparkfun.com/news/3122)

[The RedBoard Artemis](https://www.sparkfun.com/products/15444) is an Arduino-compatible devboard built around the Ambiq Apollo3 chip. In addition to packing Bluetooth and 1 MB of Flash, it’s also capable of running TensorFlow models and using tiny amounts of power. The chip comes in an 81-Ball Grid Array at 0.5mm pitch, which meant SparkFun’s usual PCB fabrication methods weren’t going to cut it.

An initial run of prototype boards was run using 4 layers, blind and buried vias, and other fancy tricks to break out all the necessary signals. While this worked well, it was expensive and inefficient. The only part of the board that needed such fabrication was around the chip itself; the rest of the board could be produced with cheaper 2-layer methods. To improve this for mass production, instead, an SMD module was created to house the Apollo3, which could then be dropped into new designs on cheaper boards as necessary.

\[Nate\] does a great job of explaining the engineering involved, as well as sharing useful tips for others going down a similar path. So far, this is just part 1, with future posts promising to cover the RF shield design and FCC certification process. [\[Nate\] has always been keen to share his wisdom](https://hackaday.com/2017/02/15/sparkfun-gets-back-to-their-roots-with-sparkx/), and we can’t wait to see what comes next!

  
  
from Hackaday https://ift.tt/2CQZ1vY  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)