---
title: '6 Causes for a Raspberry Pi That Won’t Boot (And How to Fix Them)'
date: 2020-02-04T05:27:00+01:00
draft: false
---

![raspi-wont-boot-fix](https://static.makeuseof.com/wp-content/uploads/2018/06/raspi-wont-boot-fix.jpg)

You’ve got your Raspberry Pi all hooked up, ready to run… but when you connect the power, nothing happens. Something, somewhere is wrong, but what? And what can you do about it?

Here is what you need to check to troubleshoot a Raspberry Pi that won’t boot.

1\. Raspberry Pi 4 Not Booting? Try This
----------------------------------------

If you’re using the most recent version of the Raspberry Pi, you would rightly be expecting superior performance. But if the Raspberry Pi 4 isn’t booting, you might not be so excited.

Three common issues can result in the Raspberry Pi 4 not booting or appearing to not turn on

### Raspberry Pi 4 Power Issues

The Raspberry Pi 4 uses a different power supply unit (PSU) to other models. Power is via a USB Type C connector, preferably from the official 5.1V 3A PSU. As with older Raspberry Pi models, a mobile phone or tablet charger is inadequate.

### Raspberry Pi 4 Won’t Boot? Use the Right OS

The Raspberry Pi 4 requires a fresh installation of the latest Raspbian version. In fact, regardless of what your preferred Raspberry Pi OS is, you’ll need a version released post-June 2019.

Operating systems compatible with older Raspberry Pi models will not work reliably with the latest device. Using an older or unsupported operating system will result in a red LED light when the Raspberry Pi is powered up. It simply won’t boot an OS that isn’t designed to run.

A fresh installation of the latest OS will solve many booting issues with the Raspberry Pi 4.

### Raspberry Pi 4 Has No Picture

Trouble seeing output from the Raspberry Pi 4 on your monitor? The Pi 4 has two HDMI outputs. Specifically, these are micro-HDMI ports, labelled HDMI0 and HDMI1.

Most Raspberry Pi 4 booting issues are due to the HDMI cable being connected to the wrong port. Be sure to use the left-hand connector, HDMI0.

It isn’t only the Raspberry Pi 4 that can have problems booting. The following steps will help you fix other Raspberry Pi models that won’t boot.

2\. Check the Raspberry Pi’s Red and Green LED Lights
-----------------------------------------------------

When a Raspberry Pi boots, one or more LEDs will activate. One is red, indicating power (PWR); the other is green, and indicates activity (ACT). (There is also a trio of green Raspberry Pi LED lights indicating the Ethernet status, if connected.)

So, what do these LEDs indicate? Well, there’s the normal status, which is both PWR and ACT LEDs activated. ACT flashes during SD card activity. Therefore, if there’s no green light on your Raspberry Pi, there’s a problem with the SD card.

Meanwhile, PWR blinks when power drops below 4.65V. As such, if the Raspberry Pi’s red light doesn’t light up, there’s no power.

If only the red PWR LED is active, and there is no flashing, then the Pi is receiving power, but there is no readable boot instruction on the SD card (if present). On a Raspberry Pi 2, ACT and PWR LEDs lit up means the same.

When booting from an SD card, the Raspberry Pi’s green ACT light should have an irregular blink. However, it can blink in a more regulated manner to indicate a problem:

*   3 flashes: start.elf not found
*   4 flashes: start.elf cannot launch, so it’s probably corrupted. Alternatively, the card is not correctly inserted, or card slot is not working.
*   7 flashes: kernel.img not found
*   8 flashes: SDRAM not recognized. In this case, your SDRAM is probably damaged, or the bootcode.bin or start.elf is unreadable.

If any of these indicators occur, try a fresh SD card with a newly [installed Raspberry Pi operating system](//www.makeuseof.com/tag/install-operating-system-raspberry-pi/). No joy? Keep reading for an alternative fix.

3\. Is the Power Adapter Good Enough?
-------------------------------------

As noted above, power issues can cause a Raspberry Pi to fail. It might switch off or hang when running, or it might simply fail to boot at all. To read the SD card accurately, a stable power supply unit (PSU) is required.

To ensure your PSU is good enough, check that it meets the specification of your Raspberry Pi model. Similarly, confirm that the micro-USB from the PSU to the Pi is up to scratch. A lot of people use smartphone chargers to power their Raspberry Pis. This usually isn’t the best idea; a dedicated, suitable PSU is the preferred approach.

The Raspberry Pi has a resettable fuse. This polyfuse can reset itself, but it can take up to a couple of days. If you have accidentally blown the polyfuse, you’ll only find out when you try booting later. While you wait, shop for a suitable Raspberry Pi PSU; try the [CanaKit 5V 2.5A Adapter on Amazon](https://www.amazon.com/CanaKit-Raspberry-Supply-Adapter-Listed/dp/B00MARDJZ4/).

[CanaKit 5V 2.5A Adaptor](https://www.amazon.com/CanaKit-Raspberry-Supply-Adapter-Listed/dp/B00MARDJZ4?SubscriptionId=AKIAIO22DD3AFUSKXUKQ&tag=makeusw-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B00MARDJZ4) [CanaKit 5V 2.5A Adaptor](https://www.amazon.com/CanaKit-Raspberry-Supply-Adapter-Listed/dp/B00MARDJZ4?SubscriptionId=AKIAIO22DD3AFUSKXUKQ&tag=makeusw-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B00MARDJZ4) [Buy Now On Amazon](https://www.amazon.com/CanaKit-Raspberry-Supply-Adapter-Listed/dp/B00MARDJZ4?SubscriptionId=AKIAIO22DD3AFUSKXUKQ&tag=makeusw-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B00MARDJZ4) $9.99

4\. Is the Operating System Installed?
--------------------------------------

Your Raspberry Pi will not boot if there is no operating system installed. Alternatively, you can use a boot script that lets you install an OS ([such as NOOBS or BerryBoot](//www.makeuseof.com/tag/noobs-vs-berryboot-installing-raspberry-pi/)).

As such, if there is no OS installed on the SD card, you’ll get no joy from your Raspberry Pi. Deal with this by ensuring an OS is available. Install Raspbian or use NOOBS to get the Pi up and running and choose an OS to download and install.

5\. Confirm the microSD Card Works
----------------------------------

A working Raspberry Pi will rely on a good quality SD card for booting and running the OS. If the SD card isn’t working, then your Raspberry Pi will be erratic, or simply fail to boot.

Start by checking the card works. You can do this by powering down the Pi and inserting the SD card into your PC. Use a reliable flash drive formatting tool, and attempt to reformat (on Windows and Mac, use the [SDFormatter tool](https://www.sdcard.org/downloads/formatter_4/) from the SD Association). If formatting fails, then the card is corrupt (SD cards from SanDisk can be returned under warranty).

When setting up a new Raspberry Pi OS, always format the SD card prior to writing the image. This means using a reliable card reader/writer, as well as suitable media. Look for media with a high write speed, too, and superior error checking, to ensure a fast, efficient Raspberry Pi.

Only buy SD cards from reputable suppliers, such as this [Sandisk 64GB microSD Card on Amazon](https://www.amazon.com/Sandisk-Ultra-Micro-UHS-I-Adapter/dp/B073JYVKNX/). Other reputable brands include Samsung and PNY, both of which are also on Amazon.

[SanDisk 64GB Ultra MicroSDXC](https://www.amazon.com/SanDisk-Ultra-MicroSDXC-Memory-Adapter/dp/B073JYVKNX?psc=1&SubscriptionId=AKIAIO22DD3AFUSKXUKQ&tag=makeusw-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B073JYVKNX) [SanDisk 64GB Ultra MicroSDXC](https://www.amazon.com/SanDisk-Ultra-MicroSDXC-Memory-Adapter/dp/B073JYVKNX?psc=1&SubscriptionId=AKIAIO22DD3AFUSKXUKQ&tag=makeusw-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B073JYVKNX) [Buy Now On Amazon](https://www.amazon.com/SanDisk-Ultra-MicroSDXC-Memory-Adapter/dp/B073JYVKNX?psc=1&SubscriptionId=AKIAIO22DD3AFUSKXUKQ&tag=makeusw-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B073JYVKNX) $11.75

6\. No Video Output?
--------------------

Your Raspberry Pi cannot display any video without an SD card present. There is no on-board BIOS, so there’s no way to display anything. Therefore, you need to ensure that you’re using a reliable, working HDMI cable.

Meanwhile, the Pi itself needs to detect the display. Similarly, the display device needs to be capable of detecting the signal from the Raspberry Pi. If the Pi appears to be failing to boot because nothing appears on screen, you’ll need to force HDMI detection.

You can do this on your computer by inserting the SD card and browsing to the /boot/ partition. Open the **config.txt file**, and add the following to the end:

```
hdmi_force_hotplug=1
```

Save and exit the file, safely remove the SD card, return it to your Raspberry Pi, then power up again.

Meanwhile, if you’re using NOOBS with the aim of installing an operating system on your Raspberry Pi, and nothing appears on the display, you can try some keyboard shortcuts. Within the first ten seconds of booting, tapping 1, 2, 3, and 4 on your keyboard will force the display output signal to switch between ideal HDMI, safe HDMI, PAL composite, and NTSC composite.

Other video options are also possible. However, recent Pi models use TRRS, which means you need the correct cable. This should be capable of translating the RCA (red and white connectors) and composite (yellow connector) signals.

You can find a suitable [TRRS A/V Cable on Amazon](https://www.amazon.com/Camcorder-Composite-Panasonic-Samsung-Camcorders/dp/B079DDX1N9). This should work for you if HDMI is not an option.

[BRENDAZ 3.5mm Plug to RCA](https://www.amazon.com/BRENDAZ-Camcorder-Composite-Panasonic-Camcorders/dp/B079DDX1N9?SubscriptionId=AKIAIO22DD3AFUSKXUKQ&tag=makeusw-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B079DDX1N9) [BRENDAZ 3.5mm Plug to RCA](https://www.amazon.com/BRENDAZ-Camcorder-Composite-Panasonic-Camcorders/dp/B079DDX1N9?SubscriptionId=AKIAIO22DD3AFUSKXUKQ&tag=makeusw-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B079DDX1N9) [Buy Now On Amazon](https://www.amazon.com/BRENDAZ-Camcorder-Composite-Panasonic-Camcorders/dp/B079DDX1N9?SubscriptionId=AKIAIO22DD3AFUSKXUKQ&tag=makeusw-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B079DDX1N9) $7.99

Raspberry Pi Not Booting? How Tell If It’s Dead or Defective
------------------------------------------------------------

If you’ve got this far and the Raspberry Pi is not booting, there is a chance the device is defective. It looks like you’ve been unlucky—Raspberry Pi’s are all tested following manufacture.

Own a Raspberry Pi B, B+, 2B, 3B, or 3B+ ([what are the differences between Raspberry Pi boards?](//www.makeuseof.com/tag/raspberry-pi-board-guide/))? You can check if it is broken is to compare it with an identical model that you know is working. This is pretty much the only way. From the suspect device, remove the SD card, Ethernet cable, power lead, and HDMI cable. Remove anything else that is connected—and substitute the working device with the same cables, peripherals, and SD card.

If the device boots, your other Pi is faulty; if not, then your cables, power supply, or SD card are causing the problem. See above.

Meanwhile, for Raspberry Pi A, A+, and Zero devices, there is different way to check suspect devices. Remove all cables, and the SD card, and connect the device via USB cable to your Windows PC. (Use USB-A to USB-A for the Raspberry Pi A and A+, micro-USB to USB-A for the Pi Zero models).

If working, the device will be detected and an alert will sound. You’ll find the Raspberry Pi listed in Device Manager as “BCM2708 Boot”. On Linux and Mac, a working Raspberry Pi A or Zero will be listed in response to the **dmesg** command.

Raspberry Pis have a 12-month warranty, but don’t return it without first [checking the terms and conditions](http://www.farnell.com/datasheets/1627216.pdf).

Raspberry Pi Boot Problems: Fixed!
----------------------------------

So, that’s six things you need to check to fix Raspberry Pi boot issues. Here’s a recap:

1.  Using a Raspberry Pi 4? Check the power cable, operating system, and HDMI cable
2.  Check the LEDs
3.  Is the power adapter suitable?
4.  Have you installed the operating system?
5.  Is the microSD card reliable?
6.  Is HDMI output disabled?

Meanwhile, if your Raspberry Pi is one of the few that are genuinely defective, use the steps above to confirm this. Managed to get everything up and running? Great! Now take a look at these [awesome Raspberry Pi projects to get started](//www.makeuseof.com/tag/different-uses-raspberry-pi/).

Read the full article: [6 Causes for a Raspberry Pi That Won’t Boot (And How to Fix Them)](https://www.makeuseof.com/tag/raspberry-pi-wont-boot-fix/)

  
  
from MakeUseOf https://ift.tt/2N7qKfW  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)