---
title: 'ATtiny Running Lisp #Lisp @MicrochipMakes @technoblogy'
date: 2019-10-10T14:39:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-41.png)

[Technblogy](http://www.technoblogy.com/show?2R5C) posts about placing uLisp on the small ATtiny 3216 microcontroller costing about a dollar.

> Previously the smallest microcontroller that would run my uLisp interpreter was the ATmega328P, the basis for the popular Arduino Uno. This provides 32Kbytes of flash memory, 2Kbytes of RAM, and a 16MHz processor.
> 
> When I saw the specifications of Microchip’s new ATtiny 0-series and 1-series ranges of microcontrollers I realised that it might be possible to run uLisp on the ATtiny3216 and ATtiny3217, which have 32Kbytes of flash and 2Kbytes of RAM, making these the lowest cost processors capable of running Lisp; see [Getting Started with the New ATtiny Chips](http://www.technoblogy.com/show?2OCH).
> 
> For this project I chose the ATtiny3216 which has 20 pins in an SOIC package, and so is relatively easy to solder onto a breakout board. You could also use the ATtiny3217, which has 24 pins in a QFN package, but you would need surface-mount skills.

![Tiny3216Lisp.gif](http://www.technoblogy.com/pictures/kvm/tiny3216lisp.gif)

With uLisp running on an ATtiny3216 you can upload programs directly from the Arduino IDE Serial Monitor. Just type or copy-and paste the program into the field at the top of the **Serial Monitor** window, and click the **Send** button or press Return.

You can control the I/O ports directly, access I2C and SPI peripherals, and write programs to automate functions. You can also save small programs to EEPROM so they are retained when the power is disconnected, and they can be configured to run automatically on restart.

See all the details on the [Technblogy](http://www.technoblogy.com/show?2R5C) blog.