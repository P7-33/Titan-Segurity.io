---
title: 'Don’t DIY This Surgical Robot At Home'
date: 2020-01-10T04:32:00+01:00
draft: false
---

The LVL1 Hackerspace in Louisville hosted a hackathon for useless and impractical devices a couple of years ago and this makeshift [Duh-Vinci Surgical Robot](http://wiki.lvl1.org/Duh-Vinci_Surgical_Robot) was one of the “successful” results. While it’s not necessarily a project that should ever be used for its intended purpose, its miniature setup is certainly an interesting one.

The project builds on top of the MeArm Open Source Robot and a camera controlled by a Blynk board. Servos are wired into the base of each of the robotic arms for freedom in rotating. A separate microcontroller is used for the motor controllers for the arms and for the camera, partially due to the current draw for the camera power supply. The remote control system runs on an Android tablet and is used to control each of the arms.

The ESP32-Cam supplied video input is configured as a RTSP stream. As for the operation, while the movements are jerky and the range of dexterity limited, the robot is technically able to handle the sharps. Its final setup looks a bit like a deranged game of Hungry Hungry Hippos meets Operation and definitely not something to be making its way to surgical tables anytime soon.

  
  
from Hackaday https://ift.tt/2tGUStk  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)