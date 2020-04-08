---
title: 'A GPL3 Sniffer for Bluetooth 5 –
Sniffle #Bluetooth #BLE #Debugging #Development #OpenSource @NCCsecurityUS'
date: 2019-10-11T14:24:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Bluetooth.png)

Via [NCC Group](https://www.nccgroup.trust/us/our-research/sniffle-a-sniffer-for-bluetooth-5/) who has released **Sniffle**, a Bluetooth 5 signal sniffer.

> Sniffle is the world’s first open source sniffer for Bluetooth 5, and also backwards compatible with Bluetooth 4.x LE.
> 
> It runs on Texas Instruments CC26x2 microcontrollers, including the low cost CC26x2 Launchpad development board.

The host side software for Sniffle is written in **Python**, enabling easy extension and modification, and providing cross platform support. In addition to displaying packets on the terminal console in real time, the host side software can save captured traffic to a standard PCAP format compatible with the Ubertooth. This allows easy analysis with Wireshark and other open source tools.

Sniffle has a number of that allow easy, convenient, and reliable sniffing. A major feature is the ability to capture advertisements for a particular MAC address on all three primary advertising channels using a single sniffer by hopping through advertising channels together with the target.** This makes connection detection three times more reliable than most existing sniffers that only stay on a single advertising channel.** Sniffle can usually detect connection establishment with over 90% reliability.

Other features of Sniffle include:  
• Support for BT5/4.2 extended length advertisement and data packets  
• Support for BT5 Channel Selection Algorithms #1 and #2  
• Support for all BT5 PHY modes (1M, 2M, and FEC coded modes)  
• Support for sniffing only advertisements and ignoring connections  
• Support for channel map, connection parameter, and PHY change operations  
• Support for advertisement filtering by MAC address and RSSI

A reliable and easy to use sniffer can greatly facilitate the development, debugging, testing, and reverse engineering of devices using Bluetooth 5 and 4.x LE.

Sniffle is available on GitHub at [https://github.com/nccgroup/sniffle](https://github.com/nccgroup/sniffle) under a [GPL version 3 license](https://github.com/nccgroup/Sniffle/blob/master/LICENSE). See [the repository](https://github.com/nccgroup/sniffle) and the [NCC Group website](https://www.nccgroup.trust/us/our-research/sniffle-a-sniffer-for-bluetooth-5/) for additional details.