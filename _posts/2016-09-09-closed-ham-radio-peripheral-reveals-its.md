---
title: 'Closed Ham Radio Peripheral Reveals Its Windows Secrets'
date: 2020-02-17T04:10:00+01:00
draft: false
---

The student radio society in Trondhjem owns a Flex 6500-radio, with its associated Maestro panel peripheral. This is a software defined radio, and the Maestro is a computer containing just enough of an embedded version of Windows to run its front-end software. Unfortunately for our Norwegian radio amateur friends it runs very little else, even to the extent of being unable to connect to public WiFi that requires a web log-in. This was particularly annoying as the student network does this and they’d had to create their own hotspot, so [they’ve provided some details](https://www.la1k.no/2020/01/08/flexradio-maestro-hacking-part-1-public-wifi-and-wallpapers/) on how they were able to open it up a little to do a bit more.

At first they were cagey about the exact nature of the exploit they used to penetrate the device’s defenses, but since then they’ve published [a second installment with full details](https://www.la1k.no/2020/01/29/flexradio-maestro-hacking-part-2-revealing-the-backdoor/). It involved gaining access to the filesystem and a terminal through a right-click menu from a web browser screen within the Maestro software, then using that access to change configuration such that it could be exposed across the network. From there they were able to treat it much as they would a normal Windows installation, including putting other software such as SmartSDR onto it.

This piece of work provides a fascinating insight into an embedded Windows device, and leaves us as usual surprised by the ease of the exploit. We’d say it’s something of a brave move for a company to ship a feature-limited product to radio amateurs of all people, a community that has been experimenting and finding whatever means  to extend the capabilities of their equipment for over a hundred years. [Perhaps Flexradio’s eyes are on greater things](https://hackaday.com/2019/09/05/ham-radio-company-wins-big/).

  
  
from Hackaday https://ift.tt/39FRsXe  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)