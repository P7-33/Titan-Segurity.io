---
title: 'Traffic Updates On The Seven Seas: Open Source Chart Plotter Using A
Raspberry Pi'
date: 2019-11-05T07:08:00+01:00
draft: false
---

As the Raspberry Pi in its various forms continues to flow into the wild by the thousands, it’s interesting to see its user base expand outside beyond the hacker communities. One group of people who’ve also started taking a liking to it is sailing enthusiasts. \[James Conger\] is one such sailor, and he built his own [AIS enabled chart plotter](https://www.youtube.com/watch?v=PdfLTA2CRL8) for a fraction of the price of comparable commercial units.

![](https://hackaday.com/wp-content/uploads/2019/10/VesselFinder-1.jpg?w=800)

AIS transponders in the Mediterranean. [VesselFinder](https://www.vesselfinder.com/)

Automatic Identification System (AIS) is a GPS tracking system that uses transponders to transmit a ship’s position data to other ships or receiver stations in an area. This is used for collision avoidance and by authorities (and hobbyists) to keep an eye on shipping traffic, and allow for stricken vessels to be found easily. \[James\]’ DIY chart plotter overlays the received AIS data over marine charts on a nice big display. A Raspberry Pi 3B+, [AIS Receiver Hat](https://www.tindie.com/products/astuder/daisy-hat-ais-receiver-for-raspberry-pi/), USB GPS dongle and a makes up the core of the system. The entire setup cost about $350. The Pi runs [OpenCPN](https://opencpn.org/OpenCPN/info/about.html), an open source chart plotter and navigation software package that \[John\] says is rivals most commercial software. As most Pi users will know the SD card is often a weak link, so it’s probably worth having a backup SD card with all the software already installed just in case it fails during a voyage.

We’ve seen [AIS receiver stations](https://hackaday.com/2013/05/06/tracking-ships-using-software-defined-radio-sdr/) built using the RTL-SDR, as well as a number of projects around the AIS equivalent in aviation, [ADS-B](https://hackaday.com/2019/08/14/remote-ads-b-install-listens-in-on-all-the-aircraft-transmissions-with-rtl-sdr-trio-phones-home-on-cellular/). Check out \[John\]’s video after the break.

  
  
from Hackaday https://ift.tt/2WKeR4G  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)