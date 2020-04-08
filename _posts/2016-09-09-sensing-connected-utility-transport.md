---
title: 'Sensing, Connected, Utility Transport Taxi for Level Environments'
date: 2019-11-09T16:06:00+01:00
draft: false
---

If that sounds like a mouthful, just call it [SCUTTLE – the open-source mobile robot designed at Texas A&M University](https://mxet.github.io/SCUTTLE/). SCUTTLE is a low cost (under $350) robot designed for teaching Aggies at the Multidisciplinary Engineering Technology (MXET) program, where it is used for in-lab lessons and semester projects for the MXET 300 – Mobile Robotics undergraduate course. Since it is designed for academic purposes, the robot is very well documented, making it easy to replicate when you follow the instructions. In fact, the team is looking for others to build SCUTTLE’s and give them feedback in order to improve its design.

Available on the SCUTTLE website are a large collection of videos to walk you through fabrication, electronics setup, robot assembly, programming, and robot operation. They are designed to help students build and operate the mobile robot within one semester. Most of the mechanical and electronics parts needed for the robot are off-the-shelf and easy to procure and the rest of the custom parts can be easily 3D printed. Its modular design allows you the freedom to try different options, features and upgrades. SCUTTLE is powerful enough to carry a payload up to 9 kg (20 pounds) allowing additional hardware to be added. To keep cost low and construction easy, the robot uses a simple, two wheel drive system, using a pair of geared motors. This forces the robot to literally scuttle in a “non-holonomic” fashion to move from origin to destination in a sequence of left / right turns and forward moves, so motion planning is interestingly tricky.

The SCUTTLE robot is programmed using Python3 running under Linux and has been tested working on either a BeagleBone Blue or a Raspberry Pi. The [SCUTTLE software guide](https://github.com/MXET/SCUTTLE/blob/master/docs/supplemental/SCUTTLE%20Software%20Architecture%20Slides.pdf) is a good place to get acquainted with the system architecture.

The standard configuration uses ultrasonic sensors for collision avoidance, a standard USB camera for vision, and encoders coupled to the wheel drive pulleys for determining position with respect to the starting origin. An optional USB LiDAR can be added for area mapping. The additional payload capability allows adding on extra sensors, actuators or battery packs.

To complement information on the [website](https://mxet.github.io/SCUTTLE/), additional resources are posted on [GitHub](https://github.com/MXET/SCUTTLE), [GrabCAD](https://grabcad.com/library/scuttle-robot-v2-1-1) and [YouTube](https://www.youtube.com/playlist?list=PLeVnRAuL1kMk5i01CC8kCIVRevEhVnU1J). Building a SCUTTLE robot ought to be a great group project at maker spaces wanting to get hackers started with Robotics. We have covered many [Educational Robot](https://hackaday.com/?s=educational+robot) projects in the past, but the SCUTTLE really shines with its ability to carry a pretty decent payload at a low cost.

  
  
from Hackaday https://ift.tt/2NxJLdJ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)