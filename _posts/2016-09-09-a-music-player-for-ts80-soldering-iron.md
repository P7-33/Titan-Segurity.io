---
title: 'A music player for the TS80 soldering iron'
date: 2020-01-01T01:55:00+01:00
draft: false
---

[](https://github.com/joric/ts80player/#ts80player)TS80player
=============================================================

Audio player for the TS80 soldering iron

[](https://github.com/joric/ts80player/#video)Video
---------------------------------------------------

[![](https://camo.githubusercontent.com/c423c1f86fc81f8da23e6f0af94d100924cc67b8/687474703a2f2f696d672e796f75747562652e636f6d2f76692f616f7365377a575631664d2f302e6a7067)](https://youtu.be/aose7zWV1fM)

[](https://github.com/joric/ts80player/#installation)Installation
-----------------------------------------------------------------

Download .hex file in the [releases section](https://github.com/joric/ts80player/releases).

Connect to USB while holding button A, copy .hex to USB drive, wait it renames to .rdy, unplug USB.

There's no firmware backup, just revert to the official firmware the same way.

[](https://github.com/joric/ts80player/#hardware)Hardware
---------------------------------------------------------

*   STM32F103T8U6 (ARM Cortex M3, clock frequency 72 MHz, 20K RAM, 64K FLASH)
*   MMA8652FC (3-Axis, 12-bit Digital Accelerometer)
*   SSD1306 (White 96x16 OLED Display)

Name

TS100

TS80

KEY\_A

A9

B1

KEY\_B

A6

B0

PWM\_OUT

B4

A6

TIP\_TEMP

B0

A3

TMP36

A7

A4

OLED\_RST

A8

A15

SCL

B6

B6

SDA

B7

B7

[](https://github.com/joric/ts80player/#debugging)Debugging
-----------------------------------------------------------

You could use a cheap Bluepill board for debugging. Upload [TS80-Bootloader.hex](https://github.com/Ralim/ts100/blob/master/Development%20Resources/TS80-Bootloader.hex) to the Bluepill the usual way, e.g. [via UART](https://github.com/joric/bluetosis/wiki/Uploading). Connect B1 to GND for the USB Mass Storage bootloader, use pins B6/B7 for I2C display. You can upload your own firmware in hex format (use 0x08004000 offset and 0x4000 start vector) and file extension will change to .RDY. You can press reset instead of unplugging USB each time. Stock TS80 firmware works as well.

[![](https://camo.githubusercontent.com/4036b8066f9aa3f2ea61c1f8405eca87168d326d/68747470733a2f2f692e696d6775722e636f6d2f316a4d4862344a2e6a7067)](https://camo.githubusercontent.com/4036b8066f9aa3f2ea61c1f8405eca87168d326d/68747470733a2f2f692e696d6775722e636f6d2f316a4d4862344a2e6a7067)

[](https://github.com/joric/ts80player/#documentation)Documentation
-------------------------------------------------------------------

[](https://github.com/joric/ts80player/#references)References
-------------------------------------------------------------

  
  
from Hacker News https://github.com/joric/ts80player/