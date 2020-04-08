---
title: 'Reverse-Engineering Xiaomi IoT Firmware'
date: 2019-10-25T03:06:00+01:00
draft: false
---

IoT devices rarely ever just do what they’re advertised. They’ll almost always take up more space than they need to – on top of that, their processor and memory alone should be enough to run a multitude of other tasks while not necessarily compromising the task they were built to do.

That’s partially the motivation for rooting any device, but for Xiaomi devices, it’s a bit more fun – that is to say, it’s a little bit harder when you’re [reverse engineering](https://dgiese.scripts.mit.edu/talks/DEFCON26/DEFCON26-Having_fun_with_IoT-Xiaomi.pdf) its firmware from scratch.

Similar to his other DEF CON 26 talk on [modifying](https://www.youtube.com/watch?v=Qvxa6o2oNS0&t=2220s) ARM Cortex-M firmware, \[Dennis Giese\] returns with a walkthrough of how to reverse-engineer Xiaomi IoT devices. He starts off talking about the Xiaomi ecosystem and the drawbacks of reusing firmware across all the different devices connected to the same cloud network before jumping into the walkthrough for accessing the devices.

Targeting the Aquara Smart IP Camera, you first identify the serial port after bricking the device (a necessary step for connecting to the filesystem). Since the JFFS2 filesystem on the MCU (Zigbee NXP JN5169) wasn’t properly cleaned, a fair amount of credentials is leaked, which is essentially enough for rooting the device via telnet. Once you replace telnetd with SSH, change the root password, and change the camera software, you’ve got a modified smart camera!

![](https://hackaday.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-10-at-11.48.56-AM.png?w=400)

For a different device, a WiFi network speaker, even the device teardown was unnecessary. No input validation was found on the firmware update over HTTP – no signatures, with the information packed into an XML format. This makes it even easier to simply overwrite the firmware OTA.

Finally, for a vacuum cleaning robot, a bit more circuitry was needed to root the device. In the usual method, the MMC data lines are shortcut, caused the system to fall into FEL mode. Using a USB connector and a load and execute tool, the MMC flash is dumped. The image can then be modified and rewritten to flash memory.

As it turns out, for many of the devices you don’t even need to resort to bricking the device in order to gain root access. While Xiaomi’s inevitably patched up most of the vulnerabilities since the talk, there’s invariably still more out there.

  
  
from Hackaday https://ift.tt/33Y2STq  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)