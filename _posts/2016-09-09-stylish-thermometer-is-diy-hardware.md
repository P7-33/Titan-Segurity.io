---
title: 'Stylish Thermometer is DIY Hardware Perfection'
date: 2020-01-29T13:14:00+01:00
draft: false
---

Over the last few years, we’ve seen a steady improvement in the sort of custom hardware a dedicated individual can produce. With affordable desktop 3D printers and PCB fabrication services, the line between store bought and home built can get _very_ blurry. This slick [MQTT-connected thermometer created by \[Martin Cerny\]](https://github.com/mcer12/Temper-ESP8266) is a perfect example.

The case for the device, which \[Martin\] calls Temper, is printed in a stone-look PLA filament and has been carefully designed so that LEDs shining behind it illuminate perfect square “pixels” on the front. There’s a living hinge button on the left side, and on the right, an opening for the SHT30 temperature and humidity sensor. Some may say that the look of the sensor aperture could be improved with a printed grille, but there was likely a concern about reduced airflow.

Inside the case is a 13×7 array of SMD LEDs, a few 74HC595 shift registers, a TP4054 charging chip to keep the internal 250 mAh battery topped off via USB, and some passives to round out the party. The ESP-12E module that brings it all together and the battery are on the flip side of the PCB. At a press of the button, the display fires up for 5 seconds and Temper publishes temperature, humidity and battery percentage through MQTT. If you’re looking for more granular data, it can also be configured to publish regular updates at the cost of increased energy consumption.

[![](https://hackaday.com/wp-content/uploads/2020/01/temper_detail2.jpg?w=800)](https://hackaday.com/wp-content/uploads/2020/01/temper_detail2.jpg)

The physical product is gorgeous on its own, but we’re happy to report that the firmware and documentation have been handled with a similar attention to detail. The project’s GitHub repo has a Wiki to help others build and configure their very own Temper, and the device’s web configuration portal is easily just as nice as anything you’d find in a piece of modern consumer electronics (if not moreso).

[We’ve seen plenty of ESP8266-based](https://hackaday.com/2020/01/08/an-esp8266-environmental-monitor-in-your-usb-port/) environmental [monitoring devices here at Hackaday](https://hackaday.com/2019/05/31/freeform-esp8266-network-attached-data-display/), but we think this one really pushes the state-of-the-art forward. This is a device that wouldn’t be out of place on the shelf at a Big Box electronics retailer, and while \[Martin\] says he has no interest in building and selling them himself, we don’t doubt that folks out there will be spinning up their own Temper clones before too long.

  
  
from Hackaday https://ift.tt/37BOz9b  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)