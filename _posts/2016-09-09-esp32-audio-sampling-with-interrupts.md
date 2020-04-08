---
title: 'ESP32 Audio Sampling with Interrupts and IRAM'
date: 2019-12-08T01:32:00+01:00
draft: false
---

Interrupting while someone is talking is rude for humans, but smart for computers. \[Ivan Voras\] shows how to use interrupts to [service the ESP32 analog to digital converters when sampling sound](https://www.toptal.com/embedded/esp32-audio-sampling). Interestingly, he uses the Arduino IDE mixed with native ESP-IDF APIs to get the best performance.

Like most complex interrupt-driven software, \[Ivan’s\] code uses a two-stage interrupt strategy. When a timer expires, an interrupt occurs. The handler needs to complete quickly so it does nothing but set a flag. Another routine blocks on the flag and then does the actual work required.

Because the interrupt service routine needs to be fast, it has to be in RAM. \[Ivan\] uses the IRAM\_ATTR attribute to make this work and explains what’s going on when you use it.

> …the CPU cores can only execute instructions (and access data) from the embedded RAM, not from the flash storage where the program code and data are normally stored. To get around this, a part of the total 520 KiB of RAM is dedicated as IRAM, a 128 KiB cache used to transparently load code from flash storage.The ESP32 uses separate buses for code and data (“Harvard architecture”) so they are very much handled separately, and that extends to memory properties: IRAM is special, and can only be accessed at 32-bit address boundaries.

This is very important because some ESP-IDF calls — including adc1\_get\_raw — do not use this attribute and will, therefore, crash if they get pushed out to flash memory. At the end, he muses between the benefit of using an OS with the ESP32 or going bare metal.

If you want to know more about the [Arduino on ESP32](https://hackaday.com/2016/10/31/whats-new-esp-32-testing-the-arduino-esp32-library/), we covered that. We also [dug deeper into the chip](https://hackaday.com/2016/10/04/how-to-get-started-with-the-esp32/) a few times.

  
  
from Hackaday https://ift.tt/351fo5E  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)