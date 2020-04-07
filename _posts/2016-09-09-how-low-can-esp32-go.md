---
title: 'How Low Can An ESP32 Go?'
date: 2020-01-07T10:09:00+01:00
draft: false
---

Many of us have experimented with the ESP32 microcontroller, attracted by its combination of WiFi and a powerful processor core, but how many of us will have explored all of its many on-board features? One of the more interesting capabilities of this chip comes in the form of its ultra-low-power (ULP) co-processor, an extra core that allows an ESP32 to function while sipping tiny quantities of power with the ever-hungry main cores turned off.

It’s a feature that \[Max.K\] has used to great effect in his [low power ESP32 handheld computer,](https://hackaday.io/project/169103-low-power-esp32-handheld) where he’s paired the chip with a low-power [Sharp Memory LCD](https://www.sharpsma.com/products?sharpCategory=Memory%20LCD&p_p_parallel=0) and used the ESP32’s ULP core to keep the display alive while the ESP cores are sleeping. Software wise the device sports basic PDA and clock functionality including an RSS parser, all of which can be seen in the video below the break. Its inspiration came from Panic’s crank-equipped Playdate console, with which it shares the Sharp display.

Seeing this device reminds us of some of the badges featuring ESP32 power that we’ve seen over the last few years. An event badge creator has a constant battle to give the device enough battery life to last the distance. It’s a problem the designers of the [SHA 2017 badge](https://hackaday.com/2017/08/14/hands-on-with-the-shacamp-2017-badge/) solved with an e-ink unit, but perhaps the Sharp display could offer a cost-effective alternative for new designs.

  
  
from Hackaday https://ift.tt/35s7lxV  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)