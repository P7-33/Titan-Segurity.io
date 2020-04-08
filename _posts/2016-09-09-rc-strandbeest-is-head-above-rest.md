---
title: 'RC Strandbeest is a Head Above the Rest'
date: 2019-12-09T04:32:00+01:00
draft: false
---

Prolific maker \[Jeremy Cook\] recently put the finishing touches (at least, for now) on [his impressive ClearCrawler remote controlled Strandbeest](https://github.com/JeremySCook/ClearCrawler), which includes among other things a surprisingly expressive “head” complete with LED matrix eyes. For anyone in the audience who was only _mildly_ terrified of these multi-legged robotic beasties before, you may want to avert your eyes from the video after the break.

The [clever locomotive design](https://hackaday.com/2010/03/24/theo-jansen-like-the-professor-from-gilligan/) of \[Theo Jansen\] known as Strandbeest is a legged walker. What makes it special is that the legs themselves are not independent, but work together for a gliding action more akin to wheeled bots. \[Jeremy’s\] work with ClearCrawler has taken this to another level of precision and mechanization.

[![](https://hackaday.com/wp-content/uploads/2019/12/clearcrawler_detail.jpg?w=400)](https://hackaday.com/wp-content/uploads/2019/12/clearcrawler_detail.jpg)Before installation of the electronics, the ClearCrawler had to be tethered to a bench power supply, and could only move forward and backward. Once the locomotion was working as expected, \[Jeremy\] was ready to install some brains into the beast.

The robot is controlled by a dual motor driver and an Arduino Nano socketed in an I/O expansion board. Communication between the Nano onboard the walker and the hand-held remote control is provided by of a pair of nRF24L01 modules. The controller itself is a simple affair, comprised of a joystick shield plugged into an Arduino Uno.

The robot’s head is made up of a chunk of clear polycarbonate tube with a 3D printed internal frame to hold the dual 8×8 LED matrices that serve as its animated eyes. This arrangement is mounted on a servo pan and tilt mount, which is controlled by an analog stick on the controller. While the head doesn’t currently serve any practical function, it does give \[Jeremy\] a chance to emote a bit with his creation; a popular trick when he shows the ClearCrawler off.

A few years ago we covered this robot’s predecessor, [the considerably larger ClearWalker](https://hackaday.com/2017/06/01/watch-the-clearwalker-light-up-and-dip-its-toes/). While that machine was surely a beauty to behold, this smaller and more agile iteration of the concept is quite a bit more practical.

  
  
from Hackaday https://ift.tt/2Pu4ej1  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)