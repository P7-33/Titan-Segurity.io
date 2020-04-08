---
title: 'Robot Joints Go Modular With This Actuator Project'
date: 2019-10-22T12:06:00+01:00
draft: false
---

\[John Lauer\] has been hard at work re-thinking robot arms. His project to create [modular, open source actuators that can be connected to one another to form an arm](https://github.com/chilipeppr/robot-actuator-esp32-v8) is inspiring, and boasts an impressively low parts cost as well. The actuators are each self-contained, with an ESP32 and a design that takes advantage of the form factors of inexpensive modules and parts from vendors like Aliexpress.

![](https://hackaday.com/wp-content/uploads/2019/10/Anti-backlash-flex-spline.gif?w=400)

Flex spline in action, for reducing backlash

Each module has 3D printed gears (with an anti-backlash flex spline), an RGB LED for feedback, integrated homing, active cooling, a slip ring made from copper tape, and a touch sensor dial on the back for jogging and training input. The result is a low backlash, low cost actuator that keeps external wiring to an absolute minimum.

Originally inspired by a design named [WE-R2.4](https://www.thingiverse.com/thing:3327968), \[John\] has added his own twist in numerous ways, which are best summarized in the video embedded below. That video is [number three](https://youtu.be/4o3d7_WZ_DQ) in a series, and covers the most interesting developments and design changes while giving an excellent overview of the parts and operation (the video for [part one](https://www.youtube.com/watch?v=tEbJV32GyYU) is a basic overview and [part two](https://www.youtube.com/watch?v=RdmdFIhCo4M) shows the prototyping process, during which \[John\] 3D printed the structural parts and gears and mills out a custom PCB.)

Is your interest piqued? If so, head over to [the GitHub repository](https://github.com/chilipeppr/robot-actuator-esp32-v8) for all the details, including Fusion 360 models, PCB design files, and a complete bill of materials with online sources. While [not all robotic actuators require motors or gears](https://hackaday.com/2019/06/14/pneumatics-for-the-masses/), one thing that is undeniable is that the availability of 3D printing, PCB fabrication, and access to electronic components has been a tremendous boon to projects like this.

  
  
from Hackaday https://ift.tt/2BvN7qE  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)