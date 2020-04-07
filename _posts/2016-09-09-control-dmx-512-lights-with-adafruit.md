---
title: 'Control DMX-512 lights with an Adafruit Feather
microcontroller #Feather #DMX @Adafruit @bikerglen'
date: 2020-02-26T23:07:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/untitled-69.jpg)

[Glen Akins posts](https://bikerglen.com/blog/dmx-featherwing-light-controller/) his design for a DMX-512 FeatherWing to connect to an [Adafruit Feather M0 Basic Proto](https://www.adafruit.com/product/2772) board to automate Color Kinetics and other RGB light fixtures.

> If you wish to use the board exactly as designed, you can order a blank board from OSH Park [here](https://oshpark.com/shared_projects/xnTMPyYn). If not, you can download the Eagle [design files](https://github.com/bikerglen/atsamd21-poe-dmx-controller/tree/master/boards/dmx-featherwing) from Github, make your desired modifications, create Gerbers, and order boards from your favorite PCB manufacturer. My top and bottom silkscreens are located on layers 121 and 122 respectively so you may need to alter your CAM processor script to output these layers to the silkscreen Gerber files.

The full details are provided for building the DMX ‘Wing including files and bill of materials.

The Feather M0 is programmed with the Arduino IDE. Networking is via the [Particle Ethernet board](https://www.adafruit.com/product/4003).

See [the post](https://bikerglen.com/blog/dmx-featherwing-light-controller/) for full details. Nice work!

![Once the software is debugged, the USB cable can be disconnected and the boards powered using the optional PoE module.](https://bikerglen.com/wp/wp-content/uploads/2020/02/ethernet-poe-dmx-no-usb-1024x683.jpg)