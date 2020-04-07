---
title: 'A Network Attached VFD Tube Clock'
date: 2020-02-06T10:32:00+01:00
draft: false
---

The elegance of Power over Ethernet (PoE) is that you can provide network connectivity and power over a single cable. Unfortunately not nearly enough hardware seems to support this capability, forcing intrepid hackers to take matters into their own hands. The latest in this line of single-cable creations is [this beautiful Vacuum Fluorescent Display (VFD) clock from \[Glen Akins\]](https://bikerglen.com/blog/poe-vfd-tube-clock/).

[![](https://hackaday.com/wp-content/uploads/2020/02/poevfd_detail.jpg?w=347)](https://hackaday.com/wp-content/uploads/2020/02/poevfd_detail.jpg)

Testing the VFD tube socket

One of the key advantages VFDs have over their Nixie precessessors is greatly reduced energy consumption, and after \[Glen\] ran the numbers, he saw that a display using six VFD tubes could easily be powered with standard PoE hardware. With this information, he started designing the PCB around the early 1990s era IV-12 tube, which has the advantage of being socketed so he could easily remove them later if necessary.

\[Glen\] first had to create a schematic and PCB footprint for the IV-12 tube that he could import into Eagle, which he was kind enough to share should anyone else be working with these particular tubes down the line. After a test of the newly designed socket was successful, he moved onto the rest of the electronics.

The clock is powered by a Microchip PIC18F67J60, which connects to the Ethernet network and pulls the current time down from NTP. After seeing so many clocks use an ESP to connect to the Internet over WiFi, there’s something refreshing about seeing a wired version. The tube segments are driven by a HV5812, also Microchip branded. Lastly, \[Glen\] used a number of DC/DC converters to generate the 1.5 V, 3.3 V, 5 V, and 25 V necessary to drive all the electronics and VFDs.

We absolutely love the simplicity of this clock, from its sleek aluminum enclosure to that single RJ45 jack on the back. But if you’re looking for something with a bit more flash, [\[Glen\] also put together some PoE Christmas lights over the holidays](https://hackaday.com/2019/12/31/poe-powers-christmas-lights-but-opens-up-so-much-more/) which share a number of design elements with this project.

\[Thanks to Irish for the tip.\]

  
  
from Hackaday https://ift.tt/2tCyH7U  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)