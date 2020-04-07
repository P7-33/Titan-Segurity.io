---
title: 'A global navigation system logger with Adafruit Feather #Feather #GNSS'
date: 2020-01-28T16:56:00+01:00
draft: false
---

![RAWX_Logger](https://github.com/PaulZC/F9P_RAWX_Logger/raw/master/img/RAWX_Logger.JPG)

Paul Clark [posts on GitHub](https://github.com/PaulZC/F9P_RAWX_Logger) a GNSS PPK RAWX Logger. (Global Navigation Satellite Systems GPS/ etc.) PPK (post processed kinematic) data logger. PPK is [usually better](https://www.altavian.com/blog/use-ppk-not-rtk) for robotic applications. RAWX is a data format.

This project uses an [Adafruit Feather M0 Adalogger](https://www.adafruit.com/product/2796) and a [SparkFun GPS-RTK2 Board](https://www.sparkfun.com/products/15136) which incorporates the [u-blox ZED-F9P](https://www.u-blox.com/en/product/zed-f9p-module) dual band (L1 + L2) GNSS receiver.

> The RAWX files logged by this project can be processed using [rtklibexplorer’s](https://rtklibexplorer.wordpress.com/) version of [RTKLIB](http://rtkexplorer.com/downloads/rtklib-code/)
> 
> [HARDWARE.md](https://github.com/PaulZC/F9P_RAWX_Logger/blob/master/HARDWARE.md) describes how to connect the Adalogger to the SparkFun GPS-RTK2 board
> 
> [UBX.md](https://github.com/PaulZC/F9P_RAWX_Logger/blob/master/UBX.md) describes how the Arduino code communicates with the F9P using the u-blox UBX binary protocol to enable and log the RAWX messages.

The [code](https://github.com/PaulZC/F9P_RAWX_Logger/tree/master/Arduino) is written in Arduino. See the [GitHub repo](https://github.com/PaulZC/F9P_RAWX_Logger) for details.

![Connections](https://github.com/PaulZC/F9P_RAWX_Logger/raw/master/img/Connections.JPG)