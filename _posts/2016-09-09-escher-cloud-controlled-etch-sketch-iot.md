---
title: 'Escher – a cloud-controlled Etch-a-Sketch #IoT #InternetOfThings @Medium'
date: 2019-12-20T16:07:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-74.png)

[Matt Welsh writes on Medium](https://medium.com/@mdwdotla/escher-the-worlds-first-cloud-controlled-etch-a-sketch-f2d5b7f1bd44) about Escher, the world’s first cloud-controlled Etch-a-Sketch.

> For the last year, I’ve been working on a side project at home which I call **Escher**. It’s a robotic Etch-a-Sketch that can be controlled over the Internet from anywhere in the world. It’s made possible by the [Adafruit Feather HUZZAH32](https://www.adafruit.com/product/3405) development board, and [Google Firebase](https://firebase.google.com/) to provide the control between the Etch-a-Sketch and a web client.
> 
> While there are a bunch of Arduino and Raspberry Pi-controlled Etch-a-Sketch projects out there, I wanted to build something that anyone could walk up to and use just by visiting a web page from their phone.

**Hardware**

Escher is controlled by an [Adafruit Feather HUZZAH32 development board](https://www.adafruit.com/product/3405), which features an ESP32 processor running at 240MHz, 520KB of SRAM, 4MB of flash, and integrated 802.11b/g/n and Bluetooth. This is a great little development board that is fully supported by the Arduino programming environment.

Escher uses two NEMA17 stepper motors to control the knobs of the Etch-a-Sketch. These are controlled using the [Adafruit Motor Featherwing](https://www.adafruit.com/product/2927) board, making it easy to control each stepper motor either independently or together.

See the whole project in [the post here](https://medium.com/@mdwdotla/escher-the-worlds-first-cloud-controlled-etch-a-sketch-f2d5b7f1bd44).![](https://miro.medium.com/max/2652/1*i8jWErtwM6RAQufMN4NvsA.png)