---
title: 'A single diode temperature sensor with
Arduino #Arduino #Temperature #Sensors @CavePearlLog'
date: 2019-11-12T15:05:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-41.png)

The Cave Pearl Project [dives (pun intended) into](https://thecavepearlproject.org/2019/11/04/single-diode-temperature-sensor-with-arduino-icu-via-reverse-bias-leakage/) using diodes as thermal sensors. Dig a bit into “The Art of Electronics” (maybe a lot) and you see that many common diodes have regions which vary by temperature. The post goes into detail about this and using the property on the limited 8-bit Atmel 328P microcontroller.

> It’s worth noting that _most_ diode based temperature sensors use [the change in forward voltage](https://hackaday.com/2018/04/16/two-cent-temperature-sensors/)  because that relationship is linear, with about 2mV less voltage drop for every degree increase of temperature.  But chasing a few millivolts with Arduino’s 10-bit ADC only allows a precision of ±1°C unless you add amplification, or some [other trick.](https://thecavepearlproject.org/2017/02/27/enhancing-arduinos-adc-resolution-by-dithering-oversampling/)
> 
> By comparison, leakage current can be expected [to double with every 10°C increase](https://www.digikey.com/eewiki/display/Motley/Diodes#Diodes-LeakageLeakage) in temperature, making **higher resolutions possible** with the same hardware. The trade off is using a non-linear relationship which produces **variable resolution over the sensing range**. And since leakage is also a byproduct of manufacturing variations you need to calibrate each diode individually. That’s a show-stopper in production environments where that time costs more than the whole device, but not so much for DIY projects which need to run-test their build for a few days anyway. We don’t usually send a logger into the field until it’s had _several weeks_ of stable operation.

The post goes into detail and provides code which could be very helpful to others.

See [the full post here](https://thecavepearlproject.org/2019/11/04/single-diode-temperature-sensor-with-arduino-icu-via-reverse-bias-leakage/) and it’s very much worth reading about [their whole project here](https://thecavepearlproject.org/). Fascinating!

![](https://edwardmallon.files.wordpress.com/2014/01/inspectingtheflowmeters.jpg)

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/2X5v6JE  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)