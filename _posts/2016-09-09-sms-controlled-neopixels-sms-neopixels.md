---
title: 'SMS controlled NeoPixels #SMS #NeoPixels @biglesp'
date: 2019-11-06T16:08:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-13.png)

[Les Pounder](https://twitter.com/biglesp) has [another terrific build](https://bigl.es/friday-fun-sms-controlled-neopixels/) using a [Raspberry Pi](https://www.adafruit.com/product/3055) – controlling multicolored [NeoPixel LEDs](https://www.adafruit.com/product/1463) via SMS (text messages).

> If you have read my blog for a bit, you will know that I love NeoPixels and I love hacking with them. So when I learnt about Nexmo, a service that offers SMS and voice telephony over the web, I wondered how I could use it with my favourite hack.

The project uses the Nexmo API and Node-RED to read an incoming SMS and extract either the name of a predetermined color, or an RGB color value. This is then passed to a node which will control the NeoPixels.

[See the whole project article here](https://bigl.es/friday-fun-sms-controlled-neopixels/). Great work Les!

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-14.png)