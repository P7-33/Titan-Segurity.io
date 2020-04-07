---
title: 'Testing CircuitPython on Teensy 4.0 – IoT made easy
IoTeensy! @adafruit @CircuitPython @arturo182 @tannewt @NXP @PaulStoffregen'
date: 2020-01-11T04:19:00+01:00
draft: false
---

Testing CircuitPython on Teensy 4.0 – IoT made easy IoTeensy ([video](https://youtu.be/ICg_3I4jvKo))! [Scott and Artur have done an amazing job](https://twitter.com/adafruit/status/1215691877674049536) bringing CircuitPython to the NXP iMX RT1062, this chip holds a lot of promise! I threw together a quick IoT project to test I2C and SPI – the OLED is an I2C device, and the AirLift Featherwing provides WiFi over SPI. This demo connects to my AP, then queries the adafruit quote service to get an inspirational quote every 3 seconds. The JSON is parsed, split, and displayed on the OLED by scrolling. Was really fast to put together, only about 20 minutes and 100 lines of code.