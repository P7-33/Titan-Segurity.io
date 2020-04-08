---
title: 'Dashboard Dongle Teardown Reveals Hardware Needed to Bust Miles'
date: 2019-12-16T13:57:00+01:00
draft: false
---

Progress and the proliferation of computers in automotive applications have almost made the shade tree mechanic a relic of the past. Few people brave the engine compartment of any car made after 1999 or so, and fewer still dive into the space behind the dashboard. More’s the pity, because someone may be trying to turn back the odometer with [one of these nefarious controller area network (CAN bus) dongles](https://www.youtube.com/watch?v=f4af1OBU5nQ).

Sold through [the usual outlets](https://www.ebay.com/sch/i.html?_from=R40&_nkw=can+filter+18+in+1&_sacat=0&LH_BIN=1&_sop=15) and marketed as “CAN bus filters,” \[Big Clive\] got a hold of one removed from a 2015 Mercedes E-Class sedan, where a mechanic had found it installed between the instrument cluster and the OEM wiring harness. When the dongle was removed, the odometer instantly added 40,000 kilometers to its total, betraying someone’s dishonesty.

\[Big Clive\]’s subsequent teardown of the unit showed that remarkably little is needed to spoof a CAN bus odometer. The board has little more than an STM32F microcontroller, a pair of CAN bus transceiver chips, and some support circuitry like voltage regulators. Attached to a wiring harness that passes through most of the lines from the instrument cluster unmolested while picking off the CAN bus lines, the device can trick the dashboard display into showing whatever number it wants. The really interesting bit would be the code, into which \[Clive\] does not delve. That’s a pity, but as he points out, it’s likely the designers set the lock bit on the microcontroller to cover their tracks. There’s no honor among thieves.

We found this plunge into the dark recesses of the automotive world fascinating, and \[Big Clive\]’s tutelage top-notch as always. If you need to get up to speed on CAN bus basics, check out [\[Eric Evenchick\]’s series on automotive network hacking](https://hackaday.com/2013/10/21/can-hacking-introductions/).

\[rasz\_pl\] sent us a tip on this one. Thanks!

  
  
from Hackaday https://ift.tt/36EElnJ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)