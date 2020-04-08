---
title: 'Mbed OS on Arduino Nano 33 BLE #Arduino #BLE #Mbed'
date: 2019-11-06T16:08:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-16.png)

[Djynet posts](http://djynet.net/?p=976) about using the Mbed OS on the Arduino Nano 33 BLE microcontroller board.

> Arduino released several new boards including the Nano 33 BLE which piqued my interest due to the fact that it is based on the [nRF52480 chip](https://www.nordicsemi.com/Products/Low-power-short-range-wireless/nRF52840) which should be compatible with Bluetooth MESH. I decided to give it a try…
> 
> This is the first (Arduino) board based on the nRF52840 and thus there is no existing Arduino core for this board which means one would face some challenge to have Arduino running on it. They went for a smart solution by deciding to run Arduino Core on top of MBED OS to be able to use all the works already done by MBED OS to integrate the nRF52840 chip. This is explain on their blog if you are curious: [https://blog.arduino.cc/2019/07/31/why-we-chose-to-build-the-arduino-nano-33-ble-core-on-mbed-os/](https://blog.arduino.cc/2019/07/31/why-we-chose-to-build-the-arduino-nano-33-ble-core-on-mbed-os/)

The article is excellent in going through the process and use of bossac to upload code (unsuccessful) vs. using a [Segger J-Link](https://www.adafruit.com/product/3571) which is less than $20 US.

[See the entire article here](http://djynet.net/?p=976).

[![SEGGER J-Link EDU Mini - JTAG/SWD Debugger](https://cdn-shop.adafruit.com/970x728/3571-05.jpg)](https://www.adafruit.com/product/3571)