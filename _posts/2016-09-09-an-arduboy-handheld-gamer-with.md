---
title: 'An Arduboy handheld gamer with a removable flash cart #Arduboy #Gaming'
date: 2019-10-21T14:18:00+01:00
draft: false
---

The [FacelessTech blog posts](https://facelesstech.wordpress.com/2019/10/12/arduboy-with-removable-flash-cart/) about building an Arduboy game platform with a removable flash cartridge.

> I’ve been meaning to get round to doing a Arduboy but never got round to it. I’m quite glad I waited because there seams to be a resurgence in the platform as of late. Also they have added the ability to add a flash cart to your build. What makes all this so easy is its all open source with lots of documentation.
> 
> I wanted to make a small Arduboy that anyone with basic soldering skills could make. I don’t think it’s the easiest of boards to solder but it’s the only way I could make it small enough and have all the features I wanted. I just went with the standard SSH1106 0.96″ screen that most people use in their homemade builds. The buttons I went with are the ones I’ve been using on my other RetroPie builds in the past. They are soft touch but they are not mushy like some are and have a small footprint. I used a SMD piezo speaker with a hardware mute switch because not all games have music toggle.

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-71.png)

The design is a 2 board sandwich, All the Arduboy is on the front board then all the power parts on the back board. It uses a tp4056 lipo charging board but this one had a USB C port on it instead of a micro USB port. A DC DC boost board is used to step the battery up to 5V. There is a power switch between the battery and the DC DC boost so that it wouldn’t slowly discharge the battery but more importantly allowing to charge the Arduboy when it was off.

Flash cart
==========

> I definitely wanted a flash memory chip but I decided to go with a removable one because I wanted to make a few different types of Arduboy and that way I could move this cart between builds. This idea sounds good but in theory it wont really work. The reason behind this is some games need to be patched to work with different screens.
> 
> I used the info from this forum post [HERE](https://community.arduboy.com/t/flash-cart-ridge/5840) to make the flash cart. You will need to flash a flashcart version of the bootloader onto the Arduino before you can use the flashcart. The bootloader can be found [HERE](https://github.com/MrBlinky/Arduboy/tree/master/cathy/hexfiles) its called “cathy 3k” you will need to flash the correct .hex file depending on which Arduino and screen you are using. I flashed “[arduboy-bootloader-sh1106.hex](https://github.com/MrBlinky/Arduboy/blob/master/cathy/hexfiles/arduboy-bootloader-promicro-sh1106.hex "arduboy-bootloader-promicro-sh1106.hex")” onto mine because I’m using a Arduino pro micro and the sh1106 0.96″ SPI screen. I used a USBtiny to flash mine using these instructions [HERE](https://facelesstech.wordpress.com/2019/09/08/flashing-cathy-3k-bootloader-to-arduboy-auduino-pro-micro-using-usbtiny-on-linux/).

See [the entire post here](https://facelesstech.wordpress.com/2019/10/12/arduboy-with-removable-flash-cart/) and the video (also above) [here](https://youtu.be/Y-BO8HTmY7o).

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-72.png)

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/2W0F2Uh  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)