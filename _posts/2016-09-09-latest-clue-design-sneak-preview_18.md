---
title: 'Latest CLUE design sneak
preview! @nordictweets @arduino @microbit_edu @circuitpython #clue'
date: 2020-01-18T18:58:00+01:00
draft: false
---

![Clue01](https://cdn-blog.adafruit.com/uploads/2020/01/clue01.jpg)

![Clue02](https://cdn-blog.adafruit.com/uploads/2020/01/clue02.jpg)

Have a look at the latest art for [CLUE](https://www.adafruit.com/clue), images above and a vid with CLUE spinning around ([video](https://youtu.be/x3rbq_yxcYM)). [Sign up here](https://www.adafruit.com/clue) to get an email when CLUE is shipping! [adafruiit.com/clue](https://www.adafruit.com/clue)

What is CLUE? We wanted to build some projects that have a small screen and a lot of sensors. This board has a 1.3″ 240×240 IPS TFT display, two buttons, and a ton of sensors:

*   LSM series 9-DoF motion – LSM6DS33 Accel/Gyro + LIS3MDL magnetometer
*   APDS9960 Proximity, Light, RGB, and Gesture Sensor
*   PDM Microphone sound sensor
*   Humidity, temperature and barometric environmental sensing

There’s a Qwiic / STEMMA QT connector for adding more sensors, like PM2.5 air quality and others that were too big to fit on the board.  
We’ll be primarily using CircuitPython for programming it, but it will also work in Arduino. And of course, we’d love to see MakeCode on it!  
After designing it, the board was close enough to micro:bit-shape-size that we moved a few parts to make it fit in micro:bit robots and some projects – the nrf52840 is a big upgrade chip and can do stuff like Tensorflow Lite for Microcontrollers, BLE central and peripheral, and more.