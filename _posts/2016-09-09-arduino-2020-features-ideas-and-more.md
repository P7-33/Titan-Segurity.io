---
title: 'Arduino 2020: features, ideas, and more … post
yours! @arduino @adafruit #arduino'
date: 2019-12-31T01:33:00+01:00
draft: false
---

![Arduino Featured](https://cdn-blog.adafruit.com/uploads/2019/12/arduino_featured.jpg)

Adafruit has been part of the Arduino community from the start, making and sharing open-source libraries, code, and hardware. We’ve put together a list of updates and suggested features based on community feedback, things we are re working on, and requests we have received. Here’s the list we came up with!

Post up in the comments with what you want to make, share, build, or see in Arduino in 2020. We’ll also post this to the [Arduino developer list](https://groups.google.com/a/arduino.cc/forum/#!forum/developers).

* * *

DOWNLOAD STATS FROM ARDUINO FOR COMMUNITY AND DEVELOPERS
--------------------------------------------------------

Currently, there is no way (unless you work at Arduino) to get the download stats for libraries. The way the Arduino Library manager works is that once a copy is moved to Arduino, stats for developers are not available and are not published. The site: [arduinolibraries.info](https://www.arduinolibraries.info/) is an attempt at that, but it can only get data from GitHub and public sources.

Having the download stats of the library you have contributed to Arduino would help software developers and community to know what’s popular, what development resources are needed, and encourage developers to contribute their libraries to Arduino. Download stats were mentioned in April of 2019. We got a top 10 from the presentation and [have a post about it here](https://blog.adafruit.com/2019/03/16/top-10-arduino-library-downloads-arduino-arduinolibs-arduino-arduinod19/).

* * *

TINYUSB SUPPORT IN ARDUINO-CORE
-------------------------------

The Arduino low level hardware support was recently “chainsaw”-ed to make adding new hardware cores easy and keep them all compatible. [TinyUSB](https://github.com/hathach/tinyusb) is an open-source cross-platform USB Host/Device stack for embedded systems, and it is a perfect fit as a default USB stack (when none is provided by the hardware port). It allows developers to add USB support to their hardware quickly and easily. The supported boards include: MicroChip SAMD, Nordic nRF5x, NXP iMX RT, NXP LPC, Sony, ST STM32, Tomu and more.

If Arduino replaced the current USB stack with TinyUSB, more hardware makers and software developers would be able to contribute to the Arduino ecosystem. This would make it  easier to add new chipsets, and open up the peripherals available. (For example, mass storage which is an oft-requested but unavailable class for Arduino). Best of all, the same USB interfaces would work across all ports!

* * *

UF2 BOOTLOADER SUPPORT FROM ARDUINO
-----------------------------------

UF2 is an open-source file format and bootloading specification, developed by Microsoft for PXT (also known as Microsoft MakeCode) that makes it super-easy to flash microcontrollers. It shows up as a USB drive and new/updated software can be flashed to the device eliminating much of the frustration for users. Even better you can drag existing firmware OFF the device, for backup and distribution. It solves many problems with serial port drivers/identification, tricky command line tools like bossa, and project setup.There are bootloaders for Microchip ATSAMD21 and ATSAMD51, Arduino UNO, STM32F103, STM32F4, Nordic NRF52840, Linux (RPi Zero), Cypress FX2 and more!

Microsoft [has a great post about it](https://makecode.com/blog/one-chip-to-flash-them-all), and [check it out on GitHub](https://github.com/microsoft/uf2).  
   
Being able to flash devices immediately without special cables or software, and being able to run Arduino (or Python, tinyGo, uLisp, etc) on your hardware gives users the maximum choice for what they want to do. It’s the easiest way to send updates to  users if they are developers or hardware makers. Arduino supporting UF2 would allow more people to contribute to the Arduino ecosystem and participate with their hardware innovations.

* * *

ARDUINO LIBRARY STANDARDS & AUTOMATION
--------------------------------------

Writing software is like gardening – the flowers are beautiful but you’re going to spend a lot of time weeding! Except instead of weeding, it’s keeping up to date with new frameworks, operating systems and dependencies. It’s a ton of work! Automation makes this easy – there are free continuous integration services like Travis and GitHub actions. It would be really great if there was an Arduino CI system check/prerequisite for inclusion into the Arduino library manager. Stuff like dependencies, clean formatting, documentation, and other ‘linting’ that could be done to promote good quality libraries and coding styles. There’s been more work on this recently, in compilation-testing, which is a great start. It would be great to have the CI script do even more common-error checking like -Wall, or clang-format.

* * *

UNIFORM TRANSFER OF STRUCTURED DATA OF UART, SPI, ETC. IN ARDUINO
-----------------------------------------------------------------

Related to library standards checking with automation – it would be a great help when creating better libraries and examples if there were some lightly-structured helpers for the common bus interfaces like UART/SPI/I2C, so folks don’t have to copy-and-paste the same code over and over for transmitting data. This would be a big boon for library writers who can have small bugs slip in and also will keep code updated as the interfaces improve – for example when the I2C buffer size changes, SMBus-style register reading, bitmask twiddling, or when transactions are improved/added. Adafruit created – [Adafruit\_BusIO](https://github.com/adafruit/Adafruit_BusIO). Having a universally-available toolset would also keep hardware forks from adding or changing the bus interfaces.

* * *

SUPPORT FOR GROVE / QWIIC / STEMMA ON ARDUINO HARDWARE
------------------------------------------------------

On the Arduino MKR there is a 5-pin JST SH connector, with +5V, ground, and SDA/SCL. This is great because we’re definitely seeing a big shift over to I2C as its the one and only ‘universal’ interface for sensors and mainboards, it’s even supported in Linux and there’s USB to I2C adapters that cost $1.50. However, given it’s a 5V power supply not 3V, it risks having I2C pullups to 5V on the ‘client’ device if its plugged into something like a Grove sensor – or possibly trying to connect it to a non-regulated sensor and frazzling it. It’s not a big issue but it would be great if the power supply was 3V so it would work with SparkFun QWIIC, Seeed Grove, DF Robot Gravity, or Adafruit STEMMA / STEMMA QT. If everyone making breakouts would be interested in committing to a standard, it would make customers very happy!

* * *

Post up in the comments with what you want to make, share, build, or see in Arduino in 2020.

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/39AOjsK  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)