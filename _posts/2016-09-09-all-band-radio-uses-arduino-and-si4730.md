---
title: 'All Band Radio Uses Arduino and Si4730'
date: 2020-02-13T04:55:00+01:00
draft: false
---

It is getting harder and harder to tell homemade projects from commercial ones. A good case in point is \[Mirko’s\] [all band radio](https://create.arduino.cc/projecthub/mircemk/diy-si4730-all-band-radio-lw-mw-sw-fm-1894d9) which you can see in the video below the break. On the outside, it has a good looking case. On the inside, it uses a Si4730 radio which has excellent performance that would be hard to get with discrete components.

The chip contains two RF strips with AGC, built-in converters to go from analog to digital and back and also has a DSP onboard. The chip will do FM 64 to 108 MHz and can demodulate AM signals ranging from 153 kHz to 279 kHz, 520 kHz to 1.71 MHz, and 2.3 MHz to 26.1 MHz. It can even read RDS and RBDS for station information. The output can be digital (in several formats) or analog.

The radio takes serial (I2C) commands, and the Arduino converts the user interface so that you can control it. The chip comes in several flavors, each with slightly different features. For example, the Si4731 and Si4735 have the RDS/RBDS decoder, and the shortwave mode is available on Si4734 and Si4735. Confused? [Page 2 of the programming guide](https://www.silabs.com/documents/public/application-notes/AN332.pdf) should help. According to \[Mirko\], he used a 4730, but it still did shortwave with the 4735 library.

Breakout boards with the chip are just a few bucks. It appears the chip has the technical capability to receive single sideband, but it requires a poorly documented patch. It is in recent versions of [this library](https://github.com/pu2clr/SI4735), though.

We always smile when we think that [AM is still alive and kicking](https://hackaday.com/2018/07/24/edwin-armstrongs-battle-for-fm-radio/). Perhaps this is the modern take on that first [crystal radio project](https://hackaday.com/2018/01/19/a-modern-take-on-the-crystal-radio/).

  
  
from Hackaday https://ift.tt/2SFnxrh  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)