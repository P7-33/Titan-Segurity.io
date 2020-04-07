---
title: 'Home Safety Monitoring With IoT'
date: 2020-01-18T07:17:00+01:00
draft: false
---

Home automation is a popular project to undertake but its complexity can quickly become daunting, especially if you go further than controlling a few lights (or if you’re a renter). To test the waters you may want to start with something [like this home safety monitor](https://hackaday.io/project/169289-home-safety-monitor-using-arduino-and-ubidots), which is an IoT device based on an Arduino. It allows remote monitoring of a home for things such as temperature, toxic gasses, light, and other variables, which is valuable even if you don’t need or want to control anything.

The device is built around an Arduino Nano 33 IOT which has WiFi and Bluetooth capabilities as well as some integrated security features. This build features a number of sensors including pressure/humidity, a gas/smoke detector, and a light sensor. To report all of the information it gathers around the home, an interface with Ubidots is configured to allow easy (and secure) access to the data gathered by the device.

The PCB and code for the project are all provided on the project page, and there are a [number of other options available](https://hackaday.com/2017/10/31/review-iot-data-logging-services-with-mqtt/) if Ubidots isn’t your preferred method of interfacing with the Internet of Things. You might even give [Mozilla’s WebThings](https://hackaday.com/2019/10/29/mozilla-webthings-an-open-platform-for-building-iot-devices/) a shot if you’re so inclined.

  
  
from Hackaday https://ift.tt/2sAaGh8  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)