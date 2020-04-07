---
title: 'RemoteXY Simplifies Arduino Control'
date: 2020-01-31T04:23:00+01:00
draft: false
---

\[Labpacks\] wanted to build a robot car controlled by his phone. As a Hackaday reader, of course you probably can imagine building the car. Most could probably even write a phone application to do the control. But do you want to? In most cases, you are better off focusing on what you need to do and using something off the shelf for the parts that you can. In \[Labpacks’\] case, he used Visuino to avoid writing ordinary code and [RemoteXY to handle the smartphone interface](https://labpacks.blogspot.com/2020/01/remotexy-controlled-arduino-elegoo.html).

RemoteXY is a website that allows you to easily build a phone interface that will talk to your hardware over Bluetooth LE, USB, or Ethernet (including WiFi). One thing of interest: even though the interface builder is Web-based, the service claims that the interface structure stays on the controller. There’s no interaction with the remote servers when operating the user interface so there is no need for an external Internet connection.

The system supports Arduino and ESP controllers. On the phone side, you can use Android or iOS. The [RemoteXY site has plenty of examples](http://remotexy.com/en/examples/).

We know there are other ways to do this, including just rolling your own. However, it is nice to have different options and RemoteXY has all the usual controls, including a joystick, a color picker, a level, graphs, and more.

We did our own version of this project using [Blynk](https://hackaday.com/2016/12/02/blynk-with-joy/). We’ve also seen [Visuino](https://hackaday.com/2017/11/30/skelly-the-skeleton-is-a-scary-good-musician/) before, too.

  
  
from Hackaday https://ift.tt/2GEr3N3  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)