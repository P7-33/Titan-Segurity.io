---
title: 'Raspberry Pi 4 Benchmarks: 32- vs 64-bits'
date: 2020-01-28T13:14:00+01:00
draft: false
---

\[Matteo\] bought a new Raspberry Pi 4. Why not? You get a quad-core ARM processor, up to 4 GB of RAM, and a gigabit ethernet port for $35. However, the default operating system is still a 32-bit system and doesn’t take advantage of the Pi 4’s 64-bit capable CPU. So he installed a light version of 64-bit Debian and ran some [benchmarks for the Raspberry Pi 4 running both 32-bit and 64-bit operating systems](https://medium.com/@matteocroce/why-you-should-run-a-64-bit-os-on-your-raspberry-pi4-bd5290d48947).

It really shouldn’t be surprising that the 64-bit OS did better in nearly every test. If anything is surprising, it may be that the difference is so pronounced. Some of the benchmarks, like Dhrystones, probably don’t relate much to real-life usage. But some things, like computing a hash, is something you probably do pretty often in normal usage, and the timing difference is pronounced.

A few things were limited by things other than the CPU. RAM speed was a little better, but not much. Dropping firewall packets was another big difference. The 32-bit system could drop 268 packets per second, while the 64-bit dropped 557. VPN is another case where other things limited performance so the difference between the operating system size didn’t matter much.

Benchmarks are always tricky, so your mileage — especially your real-life mileage — may vary. However, it does seem like there are some real advantages to dumping the 32-bit operating system.

If you are interested in [performance versus the Pi 3](https://hackaday.com/2019/07/10/raspberry-pi-4-benchmarks-processor-and-network-performance-makes-it-a-real-desktop-contender/), we looked at that earlier. Spoiler alert: it is much better. Or you can [go even further back](https://hackaday.com/2016/03/01/pi-3-benchmarks-the-marketing-hype-is-true/) if you like.

  
  
from Hackaday https://ift.tt/36yIsl1  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)