---
title: 'VGA Signal in a Browser Window, Thanks to Reverse Engineering'
date: 2019-12-30T10:26:00+01:00
draft: false
---

[![](https://hackaday.com/wp-content/uploads/2019/12/VGA2USB-Devices-Square.jpg?w=250)](https://hackaday.com/wp-content/uploads/2019/12/VGA2USB-Devices-Square.jpg)

Epiphan VGA2USB LR VGA-to-USB devices

\[Ben Cox\] found some interesting USB devices on eBay. The Epiphan VGA2USB LR accepts VGA video on one end and presents it as a USB webcam-like video signal on the other. Never have to haul a VGA monitor out again? Sounds good to us! The devices are old and abandoned hardware, but they do claim Linux support, so one BUY button mash later and \[Ben\] was waiting patiently for them in the mail.

But when they did arrive, the devices didn’t enumerate as a USB UVC video device as expected. The vendor has a custom driver, support for which ended in Linux 4.9 — meaning none of \[Ben\]’s machines would run it. By now \[Ben\] was curious about how all this worked and began digging, [aiming to create a userspace driver for the device](https://blog.benjojo.co.uk/post/userspace-usb-drivers). He was successful, and with his usual detail \[Ben\] explains not only the process he followed to troubleshoot the problem but also how these devices (and his driver) work. Skip to the end of the project page for the summary, but the whole thing is worth a read.

The resulting driver is not optimized, but will do about 7 fps. \[Ben\] even rigged up a small web server inside the driver to present a simple interface for the video in a pinch. It can even record its output to a video file, which is awfully handy. The code is available [on his GitHub repository](https://github.com/benjojo/userspace-vga2usb/), so give it a look and maybe head to eBay for a bit of bargain-hunting of your own.

  
  
from Hackaday https://ift.tt/2Qz3ObE  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)