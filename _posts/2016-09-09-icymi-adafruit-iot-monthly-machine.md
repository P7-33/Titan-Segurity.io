---
title: 'ICYMI: Adafruit IoT Monthly: Machine Learning 101, PWNing the ESP32,
and more! #IoT #Adafruit #CircuitPython #AWS #AdafruitIO'
date: 2019-12-01T09:03:00+01:00
draft: false
---

The** monthly Adafruit IOT newsletter** from [AdafruitDaily.com](https://www.adafruitdaily.com/) went out this morning – **if you missed it, [subscribe now!](https://www.adafruitdaily.com/)**

IoT Projects
============

Running ML on Particle Hardware, ML 101
---------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/11/TFLite-running-on-particle-featured.jpg)Tensorflow Lite now runs on newer Particle devices! Brandon Satrom published a tutorial for running TFLite on Particle devices. – [Particle](https://blog.particle.io/2019/11/08/particle-machine-learning-101/)

Do your chores or else I’ll cut off the internet!
-------------------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/11/Gallery___DO_YOUR_CHORES______Hackaday_io.png)AccidentalRebel is creating a device “that monitors and logs if my kids have done their chores and daily tasks. If not, their devices won’t have access to the internet.”. When their chores for the day are complete, their device will automatically re-connect them to the internet. – [Hackaday.io](https://hackaday.io/project/168628-do-your-chores)

ESPRing Clock![](https://cdn-blog.adafruit.com/uploads/2019/12/Gallery___EspRing_Clock___Hackaday_io.png)
---------------------------------------------------------------------------------------------------------

ESPRing is a NeoPixel ring with an onboard ESP module. The ESP connects to WiFi and fetches the NTP time. – [Hackaday.io](https://hackaday.io/project/168619-espring-clock)

AutoHome – Universal Home Automation with Raspberry Pi
------------------------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/11/EKEhmHPWoAAZrcx-1.jpeg)

[rirozizo is building a home automation system](https://twitter.com/rirozizoXDA/status/1198306803223797760) powered by a Raspberry Pi “to remotely control any possible home appliances without the use of proprietary hardware and apps”. They’re using [the (_free_) Adafruit IO service](https://io.adafruit.com/) as the MQTT broker and for data visualization. – [Github](https://github.com/rirozizo/AutoHome)

Voice-Controlled PyPortal Smart Switch
--------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/11/EKQrf4nXYAADVLB-1536x1152-1.jpeg)[Dan the Geek](https://twitter.com/cogliano/status/1199131236549218306) is improving their PyPortal-based Smart Switch. They connected it to Adafruit IO’s IFTTT integration so they can turn a light on or off using voice commands over Alexa or Google Assistant. – [Twitter](https://twitter.com/cogliano/status/1199131236549218306)

Evaluating Motion Sensors, Microwave v.s. PIR
---------------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/3_NN27q6KO5p.jpeg)Akarush wrote a detailed log of his evaluation for two motion sensors – a RCWL-0516 and a PIR motion sensor. The results? Each sensor has unique advantages and disadvantages. – [Hackaday.io](https://hackaday.io/project/168608/instructions)

Bluetooth-based Costume Props using Arduino and ESP32
-----------------------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/11/PCYoZlj.jpg)Juan Carlos Jiménez hosted a costume party and integrated their costume with the house decorations. This BLE-powered costume prop is spooky. – [JCJC-Dev](https://jcjc-dev.com/2019/11/11/esp32-arduino-bluetooth-halloween-costume/)

RGB Weather Strip
-----------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/Gallery___Weather_Color_Strip___Hackaday_io.png)This RGB LED Strip changes color based on the weather forecast outside. – [Hackaday](https://hackaday.io/project/168579-weather-color-strip)

Code-less IoT Projects with Node-RED on Raspberry Pi
----------------------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/Peek-2019-11-18-20-51-1.gif)

[Les Pounder posted a tutorial](https://bigl.es/tooling-tuesday-node-red/) about using the Node-RED development tool…

> Node-RED is an awesome tool and anyone, yes anyone can make something with it. All you need is a web browser and a device with Node-RED. Node-RED uses JavaScript syntax, but we do not have to write any code, rather we link nodes together.

Around the Internet – IoT News
==============================

PWNing MBEDTLS on ESP32
-----------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/bench-1024x686.png)LimitedResults found [vulnerabilities](https://limitedresults.com/2019/05/pwn-mbedtls-on-esp32-dfa-warm-up/) with the ESP32 which allows an attacker to compromise the cryptographic library on the ESP32, MbedTLS**. **It’s important to note that an adversary will need _physical_ access to the ESP32 module as it’s been compromised using a voltage-glitching attack. While this doesn’t impact hobbyists, it is a an attack on the hardware module (you can not roll out new software to patch it). If you have an ESP32 module in the field, it is potentially vulnerable to this type of attack, given an attacker’s resources and time. It looks like Espressif is following this report. They [tweeted](https://twitter.com/EspressifSystem/status/1197827007268061184) “after ESP32 was pwned a couple of months ago, we have upgraded the hardware; stay tuned for ESP32v3 with improved security and performance!”. We are unsure if this impacts the ESP8266 or the upcoming ESP32-S2 module.

Adafruit joins the Zephyr Project![](https://cdn-blog.adafruit.com/uploads/2019/12/zephyr_linux_adafruit.jpg)
-------------------------------------------------------------------------------------------------------------

The Zephyr Project is a scalable real-time operating system (RTOS) supporting multiple hardware architectures, optimized for resource constrained devices, and built with safety and security in mind, and we’re thrilled to announced we’ve joined the project. – [Adafruit](https://blog.adafruit.com/2019/11/26/adafruit-joins-the-zephyr-project-and-linux-foundation-zephyriot-zephyriot-linuxfoundation-linux-adafruit/)

Mozilla is building a “Web of Things”
-------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/web_of_things_illustration.png)Mozilla is building an “open platform for monitoring and controlling devices over the web”.

> The idea of the Web of Things is to create a decentralized Internet of Things by giving things URLs on the web to make them linkable and discoverable, and defining a standard data model and APIs to make them interoperable.

[Read more on Mozilla IoT…](https://iot.mozilla.org/)

Amazon’s long-term plan for Alexa
---------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/alexa-convo.jpg)An interview with Rohit Prasad, Alexa’s head scientist, revealed details about where Amazon wants to head with their powerful voice assistant. – [TechnologyReview](https://www.technologyreview.com/s/614676/amazon-alexa-will-run-your-life-data-privacy/)

Hackable Smart Watch powered by Espruino
----------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/bangle-leaf.jpg)Bangle.js is a hackable, open-source smartwatch that can be easily customized. It’s currently crowdfunding on Kickstarter and may fill the space on our wrists from Pebble’s acquisition by Fitbit. The bangle packs more of a punch than a pebble with a nRF52832, 64kB RAM, heart rate monitor, accelerometer, magnetometer and a 350mAh battery. – [Kickstarter](https://www.kickstarter.com/projects/gfw/banglejs-the-hackable-smart-watch)

Best Buy discontinues Insignia IoT Products
-------------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/Insignia_Connect.png)Insignia, Best Buy’s generic hardware brand, has shut down every product which replies on their app (including a _freezer_). Each time this happens, we think about how many products in our lives rely on “other peoples servers”. _Do you have a contingency plan for the IoT devices in your life?_ – [Hackaday](https://hackaday.com/2019/11/14/best-buys-iot-goes-dark-leaving-some-smart-products-dumbfounded/)

Recognizing AI Snake Oil
------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/MIT-STS-AI-snakeoil_pdf.png)AI has been intertwined with IoT (AIOT). But, “Much of what’s being sold as ‘AI’ today is snake oil — it does not and cannot work.”. This paper addresses the important questions of “Why is this happening? How can we recognize flawed AI claims and push back?” – [Princeton](https://www.cs.princeton.edu/~arvindn/talks/MIT-STS-AI-snakeoil.pdf)

Analyzing NB-IoT and LoRaWAN Sensor Battery Life
------------------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/image-5.png)Low power wide area network (LPWAN) technologies like NB-IoT and LoRaWAN are perfect for your projects requiring small packets, long battery life, and long distances. But how long will the batteries in your IoT project _really _last? – [Semtech Developer Journal](https://tech-journal.semtech.com/analyzing-nb-iot-and-lorawan-sensor-battery-life)

Adafruit IoT Updates
====================

Promotion: 1 Year of Adafruit IO Plus Free with $250 Adafruit Purchase
----------------------------------------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/3980-03.jpg)We’re running a special promotion! [_As of November 20th, 2019 5:30pm, if you place an order of $250 or more at Adafruit, you’ll receive a 1 year subscription to Adafruit IO+._](https://www.adafruit.com/free) You’ll receive a minimal yet elegant[ **Adafruit IO+ Subscription Card**! This card comes with a code on the back and when typed into your Adafruit IO account, will activate a full year of Adafruit IO+ service for all the IoT projects you can dream up](https://www.adafruit.com/product/3980).

Promotion: Google AIY Voice Kit for Black Girls CODE
----------------------------------------------------

![](https://cdn-blog.adafruit.com/uploads/2019/12/alsdkfj.png)For a limited time, whenever you buy a Google AIY Voice Full Kit the regular price of $59.95 here, on this page, Google will automatically donate one to [Black Girls CODE](http://blackgirlscode.org/). Black Girls CODE goal is to empower young women of color ages 7-17 to embrace the current tech marketplace as builders + creators. [Check out the bundle on Adafruit’s website](https://www.adafruit.com/product/4427).

What is Adafruit.IO?
====================

Adafruit.io has over 14,000+ active users in the last 30 days and 850+ Adafruit IO Plus subscribers. [Sign up for Adafruit IO (for free!) by clicking this link](https://io.adafruit.com/).

_Ready to upgrade?_ [Click here to read more about Adafruit IO+, our subscription-based service](https://io.adafruit.com/plus). We don’t have investors and we’re not going to sell your data. When you sign up for Adafruit IO+, you’re supporting the same Adafruit Industries whose hardware and software you already know and love. You help make sure we’re not going anywhere by letting us know we’re on the right track.

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/2LaZPR3  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)