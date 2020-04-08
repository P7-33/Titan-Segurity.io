---
title: 'Open Source solar panel charge controller with an ESP32 and Adafruit
IO #IoT #ESP32 #AdafruitIO @AdafruitIO'
date: 2019-11-11T16:02:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/roof.jpeg)

[Tim O’Brien](https://github.com/opensolarproject/OSPController/wiki) built an “internet-connected, privately hosted smart solar MPPT power system”. This system, designed to charge his eWheel for free, costs less than $40 in parts and can power your eBike/eScooter, lights, laptop or your router/modem.

The open source firmware which sits at the center of the project, OSPController, supports forwarding variables “out to [adafruit.io](https://io.adafruit.com/) for really nice charts and dashboards”. We agree, these charts look _great_, especially with the updated data visualization blocks (such as the Gauge block) on Adafruit IO.

![](https://cdn-blog.adafruit.com/uploads/2019/11/charts2-1.png)

On the hardware side, an ESP32 (running the OSPController firmware) is connected to a DC-DC converter over serial UART. This DC-DC converter takes 18-82VDC input from a solar panel and has a programmable output of 3-60VDC to charge eBike batteries or laptops.  
![](https://cdn-blog.adafruit.com/uploads/2019/11/layed_out.jpeg)

[Read more about the OSPController on its GitHub repository…](https://github.com/opensolarproject/OSPController/wiki)