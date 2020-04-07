---
title: 'NanoVNA Tests Antenna Pattern'
date: 2020-01-12T07:32:00+01:00
draft: false
---

When \[Jephthai\] wanted to build his own Yagi antenna, he turned to MMANA software for antenna modeling. This is an antenna analysis program that uses the moment method to calculate parameters for different antenna geometries. After building the Yagi, the predicted tuning and impedance matched the real antenna nicely. But what about the radiation pattern? To test that, he used [a NanoVNA and a clever test setup](https://imgur.com/gallery/5zWhpTA).

He needed a test spot out of the antenna’s near field so he set up his workstation 18 feet away from the test antenna which was on a mount that could rotate. On the edge of the workstation table — affixed with painter’s tape — is a NanoVNA connected to a laptop.

The rest is just sweat work. First, make a measurement on the resonant frequency. Then rotate the antenna 10 degrees and repeat. After 36 measurements you have the entire circle.

Plotting the resulting data with GNUPlot matched up pretty well with the antenna’s predicted performance. This was actually the second attempt and in the report, \[Jephthai\] reports that keeping alignment is critical to get everything to work. You can see in his pictures some of the steps he took to maintain consistency.

Another aid to consistency was the use of the [NanoVNASaver software](https://github.com/mihtjel/nanovna-saver). This software allows for a frequency sweep along with a display and the creation of Touchstone files.

We’ve looked at the [NanoVNA before](https://hackaday.com/2019/08/11/nanovna-is-a-50-vector-network-analyzer/). If you’d rather view your antenna pattern as a 3D volume, [break out the 3D printer](https://hackaday.com/2017/06/11/3d-printed-radiation-patterns/).

  
  
from Hackaday https://ift.tt/2uBtBc0  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)