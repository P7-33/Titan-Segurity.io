---
title: 'Emulating a Bluetooth Keyboard with the ESP32'
date: 2020-02-13T13:25:00+01:00
draft: false
---

Most people associate the ESP family of microcontrollers with WiFi, which makes sense as they’ve become the solution of choice for getting your project online quickly and easily. But while the WiFi capability might be the star of the show, the ESP32 also comes equipped with Bluetooth; we just don’t see people using it nearly as often. If you’re looking to get started using Bluetooth on the ESP32, [then this simple wireless macro keypad from \[Brian Lough\] would be a great way to get started](https://github.com/witnessmenow/arduino-switcheroonie).

From a hardware standpoint, this project is incredibly straightforward. All you need to do is connect a membrane keypad up to the GPIO pins on the ESP32. Adding in a battery is a nice touch, and you probably would want to put it into a enclosure of some sort, but as a proof of concept it doesn’t get much easier than this. In this case \[Brian\] is using the TinyPICO board, but your personal ESP32 variant of choice will work just as well.

The rest of the project is all software, which \[Brian\] walks us through in the video after the break. There’s a preexisting library for Bluetooth Human Interface Device (HID) emulation on the ESP32, but it needs to be manually installed in the Arduino IDE. From there, he demonstrates how you can build up a functioning keyboard, including tricks such as sending multiple virtual keys at once.

In the past [we’ve seen the ESP32 used to create a Bluetooth game controller](https://hackaday.com/2019/04/29/esp32-adds-bluetooth-to-gamecube-controllers/), but the ability to emulate a keyboard obviously offers quite a bit more flexibility. With a practical demonstration of how easy as it is to turn this low-cost microcontroller into a wireless input device, hopefully we’ll start seeing more projects that utilize the capability.

  
  
from Hackaday https://ift.tt/2HgEtz8  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)