---
title: 'Making A Robotic Dog Better By Adding Springiness Without Springs'
date: 2019-11-09T01:16:00+01:00
draft: false
---

Getting a legged robot to stay upright, especially a quadruped or biped, can be a challenging undertaking. To experiment with different approaches, \[James Bruton\] built robot dog test platform and is playing with “[dynamic compliant simulated springs](https://youtu.be/bHCzrDr-t3w)“, or in other words, using the motors to act as though they were springs and dampers..

When robotic legs are kept stiff, they tend to reduce the stability of the platform due to the sudden erratic movements of the robot, especially on uneven surfaces. With a back drivable joint arrangement, \[James\] is using limited holding current on the motor, and the position of the motor shaft is monitored using an encoder. When a leg experiences a resisting force, with will have some “give” and then the motor will return it to it’s intended position more slowly. Using a IMU on top of the robot, it can detect when it start leaning to a side, and then temporarily soften the other side to balance the robot.

This is quite a common technique in legged robots, but \[James\] does an excellent job of explaining just how it works. He hopes to use the lessons learned from the test platform to improve or redesign his already impressive [OpenDog](https://hackaday.com/2018/06/11/james-bruton-is-making-a-dog-opendog-project/).

We’ve seen a number of quadruped robots on Hackaday recently. Including Boston Dynamics’ very expensive [Spot](https://hackaday.com/2019/09/25/ask-hackaday-what-good-is-a-robot-dog/) as well as a low cost robot dog that giving its [big brothers a run for their money](https://hackaday.com/2019/09/22/watch-legged-robot-run-circles-around-its-bigger-brethren/), and doing some [back flips](https://hackaday.com/2019/05/29/robotic-cheetah-teaches-a-motors-class/) in the process. Check out James’ video after the break.

  
  
from Hackaday https://ift.tt/32vHEuQ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)