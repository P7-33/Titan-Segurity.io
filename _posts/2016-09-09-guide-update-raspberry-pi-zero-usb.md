---
title: 'GUIDE UPDATE: Raspberry Pi Zero USB Gadget IP
Addressing #RaspberryPi #USB #AdafruitLearningSystem @adafruit @jaydoscher'
date: 2020-02-25T16:07:00+01:00
draft: false
---

![https://learn.adafruit.com/turning-your-raspberry-pi-zero-into-a-usb-gadget/overview](https://cdn-blog.adafruit.com/uploads/2020/02/untitled-67.jpg)

Our guide on [Turning your Raspberry Pi Zero into a USB Gadget](https://learn.adafruit.com/turning-your-raspberry-pi-zero-into-a-usb-gadget/overview) has been updated by [Jay Doscher](https://learn.adafruit.com/users/jdoscher) to include [IP Addressing Options](https://learn.adafruit.com/turning-your-raspberry-pi-zero-into-a-usb-gadget/ip-addressing-options) for the latest versions of Raspbian.

> On newer versions of Raspbian, the IP addressing for all network cards is done on the Pi via the program called dhcpcd.  If you just want to set a static IP address, you can edit the **/etc/dhcpcd.conf** file, but we’re going to take a different approach.
> 
> This page in the guide will walk you through:
> 
> *   Disabling dhcpcd
> *   Setting your IP address on usb0 manually
> *   Setting up the l0 and wlan0 interfaces to act normally
> *   Run your own DHCP server on the usb0 port, so your Pi can provide an address to your Linux or Windows PC or Mac without any additional software on your desktop or laptop.

[See this updated guide page now > > >](https://learn.adafruit.com/turning-your-raspberry-pi-zero-into-a-usb-gadget/ip-addressing-options)