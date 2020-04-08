---
title: 'Building IoT Devices The Easy Way'
date: 2019-10-11T06:02:00+01:00
draft: false
---

Do you have a Raspberry Pi? What is it being used for right now? If you’re like the majority of people who replied to \[Michael Hall’s\] poll on Twitter, it’s likely yours is sitting on a shelf doing nothing too. So why not just [turn it into an IoT device for your home](https://mhall119.com/blog/turn-your-raspberrypi-into-an-smart-iot-device-no-coding-required/)?

\[Michael\] wrote an easy-to-follow guide focusing on getting the EdgeX Foundry IoT platform running on the Raspberry Pi. It is designed to be a unified multi-platform base for IoT devices hosted by the Linux Foundation, making it easy to control and integrate them into other systems. The framework for this consists of two parts, a Device Service running on your Pi, and the rest of the services running on a desktop or laptop where you’ll be monitoring it.

His guide goes into detail on how to get both parts working on your computer and your Pi using Docker for ease of installation. As for the IoT device, he uses the built-in PIR sensor example to show how to configure it without having to write any programming. You can then monitor the device’s sensors, which you can just connect straight to the Pi’s GPIO pins, from your desktop. Since the EdgeX software is designed to run on any flavor of Linux, this should make it easy to repurpose any forgotten single-board computer into the beginnings of a home automation system.

However, if you are confident in your programming skills, you’re probably looking for something slimmer such as the ESP8266 family of microcontrollers to do your bidding. Why not try an [energy monitor](https://hackaday.com/2019/07/27/building-a-safe-esp32-home-energy-monitor/) or a [smoke detector](https://hackaday.com/2019/07/26/building-a-smarter-smoke-alarm-with-the-esp8266/) project with them?

  
  
from Hackaday https://ift.tt/2B0pMwS  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)