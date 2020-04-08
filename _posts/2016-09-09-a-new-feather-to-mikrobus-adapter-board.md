---
title: 'A new Feather to mikroBUS adapter board FeatherWing from
BORKA #Feather #mikroBUS #Adafruit'
date: 2019-10-30T15:38:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-105.png)

An interesting board in the [Adafruit FeatherWing format](https://www.adafruit.com/category/943) allows for connection to mikroBUS modules. They are [distributed by BORKA on Tindie](https://www.tindie.com/products/bokra/adapter-for-adafruit-feather/). From the page:

The **BOKRA Adafruit Feather Adapter** module is designed to install Adafruit Feather (or compatible) and mikroBUS modules and provides a device based on this module with non-isolated 5VDC power, up to 1A. The module has slot for installing one Adafruit Feather (or compatible) module and one mikroBUS module of the “S” or “M” format. These two slots organize a common bus. Using the Adafruit Feather slot allows you to design devices based on mikroBUS modules, various BOKRA modules and Adafruit Feather compatible SoM such as:

*   Huzzah32, M0 and M4 Express from Adafruit
*   Xenon, Argon and Boron from Particle
*   MAX32620FTHR and MAX32630FTHR from Maxim Integrated

with all software and services from specified companies.

The MBL (labeled P1) and MBR (labeled P8) connectors are all mikroBUS bus signals. Thus, through these connectors it is easy to connect another module (or even several) with mikroBUS slots, increasing the number of slots on the common bus. Almost all signals not used by mikroBUS from the installed Adafruit Feather are output to the P12 connector, which makes it possible to use almost all Adafruit Feather functions without changing the programs.

The I2C interface is most often used in the design of devices and instruments based on this module. For this, the module has I2C connector through which you can connect external devices and sensors.

The module contains the LM75B chip – a temperature sensor connected via I2C. Temperature measurement accuracy: 2 C for the temperature range from -25 C to +100 C, 3 for the temperature range from -55 C to +125 C.

The module power supply is non-isolated, in the range from 9VDC to 36VDC. The module converts the input power to the output, 5VDC. The maximum current is 1A. There are two connectors for distributing 5VDC to other modules and a connector for transmitting VIN input voltage to other modules.

The **BOKRA Adafruit Feather Adapter** module size 65 x 56 mm. The format of the module corresponds to the popular format of the Raspberry Pi 3A+, which greatly simplifies its use with the Raspberry Pi.

The module comes fully assembled and ready to go. The module is part of the BOKRA universal platform for IoT and IIOT, which was created to simplify users the step from design to implementation of projects and the start of production.

[See the Tindie page](https://www.tindie.com/products/bokra/adapter-for-adafruit-feather/) for more information and buying information.

See the [Awesome Feather List](https://github.com/adafruit/awesome-feather/blob/master/README.md) for all the links on the Feather ecosystem of boards.

[Buy Feather products in the Adafruit shop](https://www.adafruit.com/category/943).