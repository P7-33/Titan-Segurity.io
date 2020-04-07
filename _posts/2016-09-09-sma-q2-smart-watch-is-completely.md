---
title: 'SMA-Q2 Smart Watch Is Completely Hackable'
date: 2020-01-30T10:23:00+01:00
draft: false
---

The search for the ultimate hacker’s smart watch probably won’t end any time soon. \[emeryth\] has nominated another possible candidate in the form of the [SMA-Q2](https://hackaday.io/project/85463-color-open-source-smartwatch), and has made a lot of progress in making it accessible.

Also known as the SMA-TIME, the watch is based around the popular NRF52832 Bluetooth SoC, with a colour memory LCD, accelerometer, and a heart rate sensor on the back. The main feature that makes it so easy to hack is the stock bootloader on the NRF52832 that works with generic Nordic upload tool, making firmware upgrades a breeze via a smart phone. Unfortunately the bootloader itself is locked, so it must be completely wiped to gain debugging access. The hardware configuration has also been well reverse engineered with all the details available.

![](https://hackaday.com/wp-content/uploads/2020/01/sma-q2-replacement-board.jpg)

Custom main board with a NRF52840 module

\[emeryth\] has most of the basic features working with his [custom firmware](https://github.com/Emeryth/sma-q2-oss), although it’s still in the early stages. He designed a new watch face that includes weather updates and basic audio controls. The 3-bit display’s power consumption has also been reduced by only refreshing the necessary parts. The heart rate sensor outputs the raw waveforms, and it’s pretty accurate after a bit of FFT and filtering magic. Built-in tap and tilt detection is available on the accelerometer, which works well, but strangely doesn’t appear to have been used in the stock firmware.

Unfortunately the original enclosure design that used screws was dropped for glued version. It’s still possible to open without breaking anything, just a bit more difficult. \[emeryth\] has even designed a completely new open-source main board with a NRF52840 module and heart rate sensor on a small flex PCB, with everything up on GitHub.

We really hope the community takes a liking to this watch, and look forward to seeing some awesome hacking. This is an excellent addition to the list of candidates for the [perfect hacker’s smart watch](https://hackaday.com/2019/10/07/ask-hackaday-whats-the-perfect-hacker-smart-watch/) that \[Lewin Day\] has already investigated . We also see a lot of DIY smart watches including one with a [beautiful wood-filled 3D printed housing](https://hackaday.com/2019/05/01/scratch-built-smartwatch-looks-pretty-darn-sharp-with-3d-printed-case-and-round-lcd/) and another with [LED matrix display](https://hackaday.com/2019/12/04/led-matrix-watch-is-the-smart-watch-we-didnt-know-we-wanted/).

  
  
from Hackaday https://ift.tt/3aWsFj1  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)