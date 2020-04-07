---
title: 'Brent’s Thoughts about Python on Hardware 2020 #CircuitPython2020 #IoT'
date: 2020-01-07T02:21:00+01:00
draft: false
---

Hi – I’m Brent Rubell (@brentru on github, @brentrubell on twitter).  Last year I structured [my ideas and thoughts about CircuitPython in 2019 as a wishlist](https://gist.github.com/brentru/d63f23d2ff8b35d118f100e06cad4211). I’d like to start by reflecting where we currently stand on the items on this wishlist and then list what I’d like to see in 2020.

Author’s note: A large amount of my work for Adafruit revolves around wireless projects and protocols. These thoughts will be very “iot-centric”.

![](https://cdn-blog.adafruit.com/uploads/2020/01/IoT_CircuitPython_and_Blinka_Logo_s_.png)

2019 began with a _fancy_ new library named ESP32SPI which allows CircuitPython devices to communicate with an ESP32 running [a fork of the NINA-W102 firmware over SPI](https://github.com/adafruit/nina-fw). This was created specifically for the PyPortal which was released towards the end of 2018.

Adafruit produced new hardware (wings, shields, and more!) with ESP-32 Co-Processors dubbed Adafruit AirLift. The new hardware, in-turn, brought more activity to both the nina firmware and ESP32SPI libraries.

Docmolo added Enterprise WPA2, Mscosti added an AP mode so you can put the ESP32 into AP mode so devices can connect to its local network, and I added  user-defined X.509 certificates for server authentication.

![](https://cdn-blog.adafruit.com/uploads/2020/01/Pasted_Image_1_2_20__3_15_PM-480x480.png)

One of the main things I wanted in 2019 was a dedicated MQTT Client for CircuitPython. [CircuitPython MiniMQTT was released over the summer](https://learn.adafruit.com/mqtt-in-circuitpython).

CircuitPython hardware is now able to interface with Adafruit IO, AWS IoT, Google Cloud Core IoT, Azure IoT, any MQTT broker and any REST API.

There’s also have a simplified Release Page and a new website – [https://circuitpython.org/](https://circuitpython.org/downloads)

As for my **2020 wishlist…**

*   New WiFi Chipsets/Modules: The ESP32 was released in 2016. I’d like to see a silicon vendor release a competitor to the ESP32 with an onboard secure element.
*   Dynamic DisplayIO “Widgets”
    *   Easy-to-use module(s) with APIs to build graphs, buttons to tap, switches to toggle, text elements, virtual keyboards, mouse cursor.
        *   Similar to Adafruit IO Blocks, but for CircuitPython hardware with screens.
*   a DisplayIO GUI Builder
    *   a cross-platform compatible (web-based?) wysiwyg UI builder
    *   Works with variable screen sizes (PyPortal, PyGamer, community boards)
*   New Ethernet Hardware with CircuitPython modules
    *   Calling all hardware designers – I’d love a FeatherWing with PoE and Ethernet ![🙂](https://s.w.org/images/core/emoji/12.0.0-1/72x72/1f642.png)
        *   [The Wiznet W6100 supports IPv4/IPv6 ![😉](https://s.w.org/images/core/emoji/12.0.0-1/72x72/1f609.png) ](https://www.wiznet.io/product-item/w6100/)
*   Better integration with security elements like the [ATECC608 breakout](https://www.adafruit.com/product/4314)
*   Provisioning AirLift hardware without manually editing secrets.py
*   _Testing_: A PyTest or PyUnit-like CircuitPython module would be incredibly useful, even if pared down.
*   Low-Power Mode(s)
*   Asynchronous Programming: With new libraries like MiniMQTT and TinyLoRa, I’d _love _to have a way to run networking events in “the background” to allow user-code to handle physical interactions with Python hardware.

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/2tDEBFy  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)