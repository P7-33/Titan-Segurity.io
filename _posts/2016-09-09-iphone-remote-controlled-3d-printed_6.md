---
title: 'iPhone Remote-Controlled 3D-Printed
Jeep @Raspberry_Pi #PiDay #RaspberryPi'
date: 2019-12-06T09:41:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/uploads2ftmp2f71cff26f-9912-456b-b082-7c14aeb24c862fqd1g4vq1ssgh1ct4rvkdjg_oEnJH8IvYx-600x450.jpg)

from [jim Myracle](https://www.hackster.io/TomatoMan) via [hackster.io](https://www.hackster.io/TomatoMan/wemos-blynk-iphone-remote-controlled-3d-printed-jeep-485f18)

> After viewing the plans for a 3D-printed Jeep Rancher on the [3DSets.com](https://www.3dsets.com/)website I decided it would be a perfect project for my grandson and I (but really for me). The.stl files and instructions supplied by [3DSets.com](https://www.3dsets.com/) are near perfect particularly for original Prusa printers and a real value at $30.00.
> 
> I don’t know a thing about RC (radio controlled) gear. It’s a hobby I have never explored. As I investigated the requirements for RC controller for this project I got intimidated by the wide assortment of transmitters, receivers, esc’s (electronic speed controllers) and motors involved in RC. I also don’t have a group of RC knowledgeable people around that I could rely on for advice.
> 
> Rather than investing in a traditional RC hardware I decided to create my own using Blynk on my iPhone as the ‘remote control’ and a Wemos D1 Mini and Cytron MD13S as the receiver/motor controller onboard the Jeep. I knew from other projects I have made that I could make this work. I just wasn’t sure if I could make it small enough to fit in the same area as the 3D Sets Jeep designers had set aside for the RC hardware.
> 
> **Desired** **features** **for the electronics:** The design of the Jeep evolved during the development of the electronics. The original build had only one motor, a 21T, 540 high torque brushed dc motor providing the forward and reverse motion. It requires a high current reversible motor controller. During my design process 3DSets added a winch for the front bumper. It is specified as a 3-5V geared to 150 rpm. It also requires a separate reversible controller. The steering is actuated by a 180 degree servo. The suggested battery for this project is a 2S Shorty Lipo 7.4V 100C 4600 mAh hardcase. To be safe I used BEC’s (battery elimination circuits) for the microcontroller and motor controller. I also wanted a circuit to monitor the charge level of the battery to protect it from over-discharge. Since it was possible that I would operate the Jeep in a location where cellular internet service was unavailable I decided to host the communication between the iPhone and Jeep with a Blynk local server on a Raspberry Pi.

[See project!](https://www.hackster.io/TomatoMan/wemos-blynk-iphone-remote-controlled-3d-printed-jeep-485f18)