---
title: 'The ESP32, Laid Bare'
date: 2019-11-17T13:08:00+01:00
draft: false
---

Most readers will be familiar with the ESP32, Espressif’s dual-core processor with integrated WiFi and Bluetooth. Few of us though will have explored all of its features, including its built-in encryption facilities and secure booting capability. With these, a developer can protect and secure their code, and keep their devices secure.

That sense of security may now be illusory though, thanks to \[LimitedResults\] who has developed a series of attacks on the chip that compromise its [crypto core](https://limitedresults.com/2019/08/pwn-the-esp32-crypto-core/), [secure boot](https://limitedresults.com/2019/09/pwn-the-esp32-secure-boot/), and [flash encryption](https://limitedresults.com/2019/11/pwn-the-esp32-forever-flash-encryption-and-sec-boot-keys-extraction/). This enables both the chance of arbitrary code execution and firmware extraction on locked-down ESP32 devices.

To achieve all this he used a glitching technique on the device’s power supply, inserting a carefully timed glitch in the rail to coincide with a particular instruction being executed. For those of us who are not experts in this technique, he provides a basic primer with [a description](https://limitedresults.com/2019/05/pwn-mbedtls-on-esp32-dfa-warm-up/) of his home-made glitcher made using a CMOS switch chip.

It appears that there is no solution to this attack short of new silicon, however, it should be borne in mind that it’s something that depends upon a specialist hacker with a well-equipped bench, and is thus only likely to be a significant headache to manufacturers. But it undermines a key feature of a major line of microcontrollers, and as such it remains a significant piece of work.

  
  
from Hackaday https://ift.tt/2Xw7fDr  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)