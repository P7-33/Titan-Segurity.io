---
title: 'A Printed Case for Your ESP Environmental Sensors'
date: 2019-11-28T10:04:00+01:00
draft: false
---

We’ve said it before but it’s worth repeating: rolling your own hardware solution is _ridiculously_ easy these days. If you want to make a network attached environmental sensor, you wire a DHT11 up to an ESP8266 and you’re done. Time to move onto the software. In fact, it can take longer to come up with some kind of suitable enclosure for your hardware project than it does to assemble the thing.

Which is why \[Pixel Hawk\] has come up with this [elegant 3D printed enclosure for the ESP8266 and ESP32](https://www.thingiverse.com/thing:3947394). It’s designed to hold the microcontroller in the bottom compartment, while the environmental sensor (either the DHT11 or DHT22) is mounted to the top so it’s exposed to the outside. The case snap fits together so you don’t have to worry about gluing it, and there’s even an opening so you can keep the USB cable plugged in.

In the notes for the design, he mentions that in testing it was determined that the heat of the ESP itself can skew the temperature readings. So he recommends putting the microcontroller to sleep whenever possible, and keeping reads short so the enclosure doesn’t have time to heat up. He’s also created an alternate version of the case with more openings which should help combat this issue if you need to keep the chip awake.

If you’re looking for a complete solution, \[Pixel Hawk\] _has_ included the source code he personally used to get his ESP32 sensor talking to Blynk, but you certainly don’t have to go that route if you don’t want to. There’s no shortage of existing projects out there that will help you [get started with whole-house environmental monitoring](https://hackaday.com/2017/11/20/esp8266-home-monitor-is-stylishly-simplistic/). Our very own [\[Elliot Williams\] happens to be partial to MQTT](https://hackaday.com/2019/11/07/found-footage-elliot-williams-talks-nexus-technologies/) when he wants to get all his gadgets to play nice.

  
  
from Hackaday https://ift.tt/2R4PFou  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)