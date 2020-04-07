---
title: 'ICYMI: Adafruit IoT Monthly: Learning from IoT Projects, Adafruit Joins
the LoRa Alliance, Ring Ransoms, and
more! #IoT #IoTMonthly #Adafruit #Newsletter'
date: 2020-01-01T20:11:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/AIO-Monthly.png)

ICYMI (In case you missed it) – the IoT Monthly Newsletter from [AdafruitDaily.com](https://www.adafruitdaily.com/) went out today!

**If you missed it, [subscribe now](https://www.adafruitdaily.com/)!** – You’ll get one fab newsletter each Month.

The next newsletter goes out in a week and being subscribed the best way to keep up with all the Internet of Things. _No spam, no selling lists, leave any time._

Over 1,200 subscribers worldwide!

IoT Projects
============

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#face-tracking-and-identification-with-walle-ng)Face Tracking and Identification with Walle-ng
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![OpenCV Robot](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/opencv_robot.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/opencv_robot.jpg)

Anton built a robot inspired by the Pixar Movie Wall-E. If a face is detected (using the OpenCV Facial Recognition Demo), activity is logged and a notification is sent to an Amazon Web Service API Gateway and distributed as an SMS by AWS’s Simple Notification Service. – [Hackster.io](https://www.hackster.io/gr1m/face-tracking-and-identification-using-walle-ng-63b81d)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#data-logging-zero-to-hero-with-circuitpython-and-mqtt)Data Logging Zero to Hero with CircuitPython and MQTT
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![CircuitPython MQTT](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/circuitpython_mqtt.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/circuitpython_mqtt.jpg)

Robin Cole published a tutorial which navigates through the basics of creating a CircuitPython temperature logging device. First, you use the Mu editor to plot your data and verify it’s correct. Then add WiFi Connectivity using a local MQTT broker and CircuitPython’s MiniMQTT module. Finally, add an MQTT sensor to Home Assistant so the data is graphed on a web dashboard. – [Hackster.io](https://www.hackster.io/robin-cole/data-logging-zero-to-hero-with-circuitpython-and-mqtt-05af61)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#iss-tracking-globe-lamp)ISS-Tracking Globe Lamp
---------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Globe](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/globe.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/globe.jpg)

This project uses an Open Notify API notification called [ISS Location Now](http://open-notify.org/Open-Notify-API/ISS-Location-Now/) to track the International Space Station. A WeMos D1 grabs and parses the data. Then it tells a servo where to place a laser-pointer on a 3D-printed globe. – [Instructables](https://www.instructables.com/id/ISS-Tracking-Lamp/)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#disaster-radio---an-off-grid-solar-powered-mesh-network)Disaster-Radio – an off-grid, solar-powered mesh network
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Disaster Flowchart](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/diagram.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/diagram.jpg)

[disaster.radio](https://disaster.radio/) is a work-in-progress long-range, low-bandwidth wireless disaster recovery mesh network powered by the sun.

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#what-i-learned-building-an-indoor-air-quality-monitor-with-adafruit-io)What I Learned Building an Indoor Air Quality Monitor with Adafruit IO
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![AQ Monitor](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/temp_sensor_node.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/temp_sensor_node.jpg)

There are lessons to learn from every electronics project. Even a sensor node can quickly become complicated. Andy Bradford wrote up his experience (and provided [free, open source code on GitHub](https://github.com/andycb/AirQualityMonitor)) in building a logging platform. – [Andy Bradford](https://andybradford.dev/2019/11/29/monitoring-my-indoor-air-quality/)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#pyportal-voice-controlled-smart-switch-and-time-display)PyPortal Voice Controlled Smart Switch and Time Display
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![PyPortal Smart Switch](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/smart_switch.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/smart_switch.jpg)

We’ve written about this project in a previous IoT Monthly before, but it was only a sneak preview. The PyPortal Voice Controlled Smart Switch and Time Display is now on the Adafruit Learning System as a guide – [Adafruit Learning System](https://learn.adafruit.com/pyportal-voice-controlled-smart-switch-and-time-display/)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#sending-arduino-data-to-google-sheets-using-the-google-cloud-platform)Sending Arduino Data to Google Sheets using the Google Cloud Platform
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Arduino Google IoT](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/arduino_google_iot.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/arduino_google_iot.jpg)

Building an Arduino sketch to send data to Google Sheets using the Google Cloud Platform. – [DZone](https://dzone.com/articles/how-to-integrate-arduino-and-google-cloud-platform)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#iot-news-and-more)IoT News and More!
==========================================================================================================================================================

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#adafruit-joins-the-lora-alliance)Adafruit joins the LoRa Alliance
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Adafruit LoRa Alliance](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/lorawan_alliance.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/lorawan_alliance.jpg)

Adafruit is thrilled to announce that we have joined the LoRa Alliance! I asked Ladyada why we joined this alliance…

> _“Humans have done a great job of connecting people in dense populations like cities or buildings – WiFi and Cellular are ubiquitous technologies that connect people, machines and sensors. The future is to connect people wherever they are, and that’s where LoRa has so much promise. We think LoRa and LoRaWAN are the best way to solve last-mile connectivity for Industrial and Agricultural IoT”_ – Limor “Ladyada” Fried.

[Read the full blog post here…](https://blog.adafruit.com/2019/12/05/adafruit-joins-the-lora-alliance-loraalliance-lora-lorawan-adafruit/)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#ring-cameras-are-ransomed)Ring Cameras are Ransomed
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Ring Camera](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/ring_cameras.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/ring_cameras.jpg)

December 2019 was the month of Ring insecurity. [First, videos appeared where hackers spoke to families through their Ring cameras](https://www.wfaa.com/article/news/hacker-says-pay-bitcoin-ransom-or-get-terminated-through-couples-ring-security-cameras/287-226c535c-c765-4b29-91b6-d849fb315e94): “We would like to notify you that your account has been terminated by a hacker.” The voice then says, “Pay this 50 bitcoin ransom…”.  Ring asserted that their investigation found that the family used an email/password combination which was exposed in an unrelated data breach. [@fs0c131y on Twitter did a deep-dive into Ring’s iOS/Android application](https://twitter.com/fs0c131y/status/1208009855149248512). They found the application to leak geographic details of cameras through their API, Ring does not require authentication for video/photo alerts and the application does not implement rate-limiting for logging in. It’s likely that hackers are running automatic bots against the login with exposed usernames/passwords from previous breaches.

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#fbi-releases-a-statement-for-building-a-digital-defense-for-the-internet-of-things)FBI releases a statement for building a digital defense for the Internet of Things
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![FBI Press Release](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/fbi_iot.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/fbi_iot.jpg)

The FBI has suggested network security measurements for those with IoT devices on their network. In short: change factory settings/passwords, isolate IoT devices to their own network, and update your devices regularly. – [FBI](https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/tech-tuesday-internet-of-things-iot)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#lorawan-and-wi-fi-made-for-each-other)LoRaWAN and Wi-Fi: Made for Each Other
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![WiFi and LoRaWAN](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/lorawan_wifi.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/lorawan_wifi.jpg)

Remi Lorrain wrote that “WiFi and LoRaWAN work well together as an end-to-end solution in IoT applications and more.” – [EETimes](https://www.eetimes.com/lorawan-and-wi-fi-made-for-each-other/#)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#project-connected-home-over-ip-an-open-standard-for-smart-home-devices)Project Connected Home over IP: an Open Standard for Smart Home Devices
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Project Connected Home](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/projectconnectedhome.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/projectconnectedhome.jpg)

Amazon, Apple, Google, Zigbee Alliance and board members form a working group to develop an open standard for smart home devices – [Project Connected Home](https://www.connectedhomeip.com/)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#ikeas-2020-smart-home-lineup-is-unveiled)Ikea’s 2020 Smart Home Lineup is Unveiled
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Ikea Smart Home App](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/ikea2020news.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/ikea2020news.jpg)

Ikea is planning on barreling into the smart-home area in 2020 with new bulbs, products and even a ZigBee gateway. – [TheVerge](https://www.theverge.com/2019/12/18/21025798/ikea-home-smart-scenes-shortcut-button-onboarding-upgrade-software-price)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#dzones-iot-predictions-for-2020)DZone’s IoT Predictions for 2020
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![DZone IoT 2020 Stock Photo](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/dzone_graphic.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/dzone_graphic.jpg)

Dzone published their 2020 IoT predictions, among them are: the edge gets smarter, evolving networks and protocols, AI Smart Homes connected to ISPs, increases in DIY Home Security installations, more hard-lined policies for BYOD, and new flexible electronic materials. – [Part 1](https://dzone.com/articles/your-iot-predictions-for-2020-part-one) and [Part 2](https://dzone.com/articles/your-iot-predictions-for-2020-part-2)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#the-2019-state-of-responsible-iot-report)The 2019 State of Responsible IoT Report
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Responsible IoT Report](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/stateofresponsibleiot.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/stateofresponsibleiot.jpg)

“With ThingsCon, we have devoted ourselves to working towards a ‘responsible IoT’. But what does that look like in the light of Surveillance Capitalism? With this years ‘responsible IoT Report’ – RioT for short – we wanted to find out.” – [ThingsCon](https://thingscon.org/small-escapes-riot-report-2019-out-now/)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#hackaday-superconference-talk-on-youtube-basic-device-security-for-basic-needs)HackADay SuperConference Talk on YouTube: Basic Device Security for Basic Needs
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![HackADay Talk Screenshot from Youtube](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/hadconf.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/hadconf.jpg)

Kerry Sharfglass remarks that “In our IoT-ified world, device security is more important than ever, but not every hardware product needs to be secured like an ATM inside a missile. I will discuss basic design practices and implementation tricks which are easy to incorporate into your product and provide a solid baseline of security against casual adversaries.” – [YouTube](https://www.youtube.com/watch?v=o30TAezzorA&feature=youtu.be&t=50)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#five-reasons-to-upgrade-to-mqtt-5)Five Reasons to Upgrade to MQTT 5
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![MQTT 5 Spec Screenshot](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/mqtt5.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/mqtt5.jpg)

The latest version of the IoT’s favorite stateless protocol has been out for a while. Here are five reason to upgrade to it – [IoTforAll](https://www.iotforall.com/mqtt-iot/)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#actinus-environmental-sensor-featherwing-released)Actinus Environmental Sensor FeatherWing Released
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Sensor Featherwing](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/sensorfeatherwing.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/sensorfeatherwing.jpg)

Actinius’ Environmental Sensor FeatherWing measures temperature, humidity, pressure, and air quality. The Feather-compatible environmental sensor add-on also includes a Grove connector for use with any I2C-compatible microcontroller. [It’s available for purchase from the actinius website and is in-stock at the time of writing.](https://www.actinius.com/environmental-sensor-featherwing)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#openmv-cam-h7-plus)OpenMV Cam H7 Plus
-----------------------------------------------------------------------------------------------------------------------------------------------------------

[![OpenMV Cam H7 Plus](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/openmv.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/openmv.jpg)

The OpenMV Cam is a small, low power, microcontroller board which allows you to easily implement applications using machine vision in the real-world. You program the OpenMV Cam in high level Python scripts (courtesy of the MicroPython Operating System) instead of C/C++. It’s currently in-production and will be in stock by March 2020. – [OpenMV](https://openmv.io/collections/products/products/openmv-cam-h7-plus)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#adafruit-iot-updates)Adafruit IoT Updates
===============================================================================================================================================================

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#new-adafruit-io-feature-kiosk-mode-for-dashboards)New Adafruit IO Feature: Kiosk Mode for Dashboards
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Kiosk Mode](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/io_kiosk_mode.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/io_kiosk_mode.jpg)

[Adafruit IO Dashboards](http://io.adafruit.com/) have a new “kiosk mode” URL that will launch the dashboard in a “no browsing mode” without any of the surrounding page. This is super-handy if you’re designing an exhibit or would like to use a [Raspberry Pi + HDMI Display](https://www.adafruit.com/product/2232) to monitor your Adafruit IO Feeds. [Read our blog post to learn how to enable this feature on your dashboard right now…](https://blog.adafruit.com/2019/12/05/new-adafruit-io-feature-kiosk-mode-for-dashboards-adafruitio-dashboard-iot-adafruitio/)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#new-pyportal-sizes-meet-the-pyportal-pynt-and-the-pyportal-titano)New PyPortal Sizes: Meet the PyPortal Pynt and the PyPortal Titano
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![PyPortal Family Picture](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/new_pyportals.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/new_pyportals.jpg)

The PyPortal is our easy-to-use IoT device that allows you to create all the things for the “Internet of Things” in minutes. Adafruit has released the [PyPortal Pynt, the little sister to our popular PyPortal – zapped with a shink ray to take the design](https://www.adafruit.com/product/4465) from a 3.2″ diagonal down to 2.4″ diagonal screen. [We’ve also released the PyPortal Titano, with an ATMEL (Microchip) ATSAMD51J20 plus an Espressif ESP32 Wi-Fi coprocessor with TLS/SSL support built-in](https://www.adafruit.com/product/4444). PyPortal Titano has a bigger 3.5″ diagonal 320 x 480 color TFT with resistive touch screen. Compare that to the original PyPortal’s 3.2″ 240×320, there are twice the number of pixels! Also, Adafruit has updated the connector to be a reverse-friendly USB C connector.

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#build-a-mini-smart-home-with-the-smart-home-kit-for-digi-key-iot-studio)Build a Mini Smart Home with the Smart Home Kit for Digi-Key IoT Studio
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![DigiKey Home Kit](https://github.com/adafruit/io-blog/raw/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/smart_home_kit.jpg)](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/images/01012020/smart_home_kit.jpg)

Automate your own adorable, IoT-enabled papier-mâché house. The small size of this build lets one explore wiring, user interaction, and firmware deployment without having to get a ladder out. [After building this project](https://learn.adafruit.com/digikey-iot-studio-smart-home), you can re-purpose it for your home or apartment. We’ve specifically selected components and sensors which are common in real-world IoT projects. You can also go further with this project, adding sensors to monitor different rooms in your home. [Visit the product page for this kit on the Adafruit Website…](https://www.adafruit.com/product/4450)

[](https://github.com/adafruit/io-blog/blob/1cce63e5e5654ef5f37eba49e0da0ea404583b9b/_posts/2020-01-01-iot-monthly.md#what-is-adafruit-io)What is Adafruit IO?
==============================================================================================================================================================

Adafruit.io has over 14,000+ active users in the last 30 days and 880+ Adafruit IO Plus subscribers. [Sign up for Adafruit IO (for free!) by clicking this link](https://io.adafruit.com/). _Ready to upgrade?_ [Click here to read more about Adafruit IO+, our subscription-based service](https://io.adafruit.com/plus). We don’t have investors and we’re not going to sell your data. When you sign up for Adafruit IO+, you’re supporting the same Adafruit Industries whose hardware and software you already know and love. You help make sure we’re not going anywhere by letting us know we’re on the right track.