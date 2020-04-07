---
title: 'Custom Firmware For Cheap Smart Bulbs Is A Cinch To Tinker With'
date: 2020-02-12T07:55:00+01:00
draft: false
---

It’s the end of another decade, and while we don’t have real hoverboards, flying cars, or affordable dental care, we do have multicolored lightbulbs you can control over WiFi. \[Don Howdeshell\] picked up a couple of cheap Merkury branded units in a Black Friday sale, [and quickly set about hacking them.](http://dhowdy.blogspot.com/2019/12/hacking-cheap-rgb-led-light-bulb-in.html)

By and large, many of these bulbs are manufactured by Tuya and rebranded to whoever happens to place an order. Based on the ESP8266, reflashing the bulbs with custom firmware is simple, [thanks to the Tuya Convert project.](https://github.com/ct-Open-Source/tuya-convert) Using a Linux computer with a WiFi card running in Access Point mode, it spoofs a server that tricks the Tuya product into downloading a firmware update. From there, the bulb is an open book, ready to do your bidding.

One of \[Don\]’s attempts didn’t go so swimmingly, however. Flashing the firmware failed and the bulb was non-functional. \[Don\] elected to to a teardown, photographing it for our perusal, before hooking up to the ESP8266 directly over its serial interface. From there, it was simple to reprogram the bulb with [Tasmota firmware](https://github.com/arendst/Tasmota), getting it back up and running.

[Security alone is a great reason for running your own firmware on IoT devices.](https://hackaday.com/2017/04/21/iot-security-is-hard-heres-what-you-need-to-know/) It never hurts to know what you’re connecting to your network!

  
  
from Hackaday https://ift.tt/2vpSVlT  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)