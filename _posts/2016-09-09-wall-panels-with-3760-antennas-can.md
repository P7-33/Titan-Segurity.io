---
title: 'Wall Panels With 3760 Antennas Can Increase Wireless Range'
date: 2020-02-16T04:10:00+01:00
draft: false
---

Most of us know that to get the best possible WiFi signal, you want there to be as few walls as possible between you and the Access Point. But that might soon change, as researchers at MIT have found [a way to make surfaces increase signal strength](http://news.mit.edu/2020/smart-surface-smart-devices-mit-csail-0203). Called RFocus, the technique uses a wall panel covered in simple antennas to dynamically focus or reflect RF energy towards a intended receiver.

The normal methods to increase wireless range usually involve increasing the transmitter output or adding larger, more efficient, or directional antennas to the receivers and transmitters. But these techniques are limited when you need to the reduce power consumption and size of the devices. The MIT teams approached the problem from a completely different angle, by optimizing the environment.

The wall panel in question consist of 94 PCBs, each containing 40 passive antenna elements in the form of copper rectangles. Each element is a quarter wavelength long (125 mm for 2.4 Ghz), and on its own it doesn’t have any real effect on the signals, allowing it to pass through the panel. Between the ends of elements are small RF switches, that can close to combine two antenna elements into single half wavelength antenna, creating a reflector. When this is applied across the panel in different patterns it can effectively beamform the signal to focus it at different points in space.

The RF switches are connected to shift registers, which are all controlled via a single SPI bus with an Arduino. Each RF switch is activated in a pseudo-random sequence, changing the configuration of the panel 10,000 times in 100 ms. The signal strength at the receiver is reported to the panel controller for each configuration, allowing the controller to select the best configuration for any single transmitter. In a scenario where multiple low-power sensor nodes are deployed, this can allow the receiver to “focus” on each node in turn. The full paper is a very interesting read, [downloadable as a PDF](https://arxiv.org/pdf/1905.05130.pdf).

RF is generally considered the black magic of electronics, but it can all become a bit clearer with a basic knowledge of [antenna theory](https://hackaday.com/2020/02/04/ham-antennas-from-mit/) and [modulation schemes](https://hackaday.com/2020/01/28/rf-modulation-crash-course-for-hackers/).

Thanks to \[Qes\] for the tip!

  
  
from Hackaday https://ift.tt/38w0vKr  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)