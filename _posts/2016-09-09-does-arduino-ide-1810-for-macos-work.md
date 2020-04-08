---
title: 'Does the Arduino IDE 1.8.10 for macOS work with
Catalina? @arduino #arduino #macos #Catalina'
date: 2019-10-13T21:38:00+01:00
draft: false
---

![Adafruit 2019 2794](https://cdn-blog.adafruit.com/uploads/2019/10/adafruit_2019_2794.jpg)

Does the [Arduino IDE 1.8.10](https://www.arduino.cc/en/Main/Software) for macOS work with [macOS Catalina](https://www.apple.com/macos/catalina/)? [From Gian on the Arduino developer list](https://groups.google.com/a/arduino.cc/forum/#!msg/developers/77_NmlJ-sqs/ZTflzZ9RAwAJ) –

> IDE 1.8.10 for macOS comes with (avr toolchain) 64-bit support and should be working as expected.
> 
> We tracked the efforts in [https://github.com/arduino/Arduino/pull/8976](https://github.com/arduino/Arduino/pull/8976) and included all the fixes in 1.8.10.
> 
> You can download it directly from our website or via homebrew (cask).
> 
> What we found out instead is that Catalina update broke the bootloader recognition for atmega32u4-based Arduino boards (Micro, Leonardo) and are escalating this to Apple as we speak. We’re tracking it in [https://github.com/arduino/Arduino/pull/9303](https://github.com/arduino/Arduino/pull/9303)