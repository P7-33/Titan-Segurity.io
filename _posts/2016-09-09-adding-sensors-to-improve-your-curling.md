---
title: 'Adding Sensors to Improve Your Curling Game? Turns Out It’s Really Hard'
date: 2019-11-13T10:01:00+01:00
draft: false
---

Sometimes, a project turns out to be harder than expected at every turn and the plug gets pulled. That was the case with \[Chris Fenton\]’s efforts to gain insight into his curling game by adding sensors to monitor the movement of curling stones as well as the broom action. Luckily, [\[Chris\] documented his efforts](http://www.chrisfenton.com/2019/07/01/lightly-documented-projects-part-1-adventures-in-curling/) and provided us all with an opportunity to learn. After all, failure is (or should be) an excellent source of learning.

The first piece of hardware was intended to log curling stone motion and use it as a way to measure the performance of the sweepers. \[Chris\] wanted to stick a simple sensor brick made from a Teensy 3.0 and IMU to a stone and log all the motion-related data. The concept is straightforward, but in practice it wasn’t nearly as simple. The gyro, which measures angular velocity, did a good job of keeping track of the stone’s spin but the accelerometer was a different story. An accelerometer measures how much something is speeding up or slowing down, but it simply wasn’t able to properly sense the gentle and gradual changes in speed that the stone underwent as the ice ahead of it was swept or not swept. In theory a good idea, but in practice it ended up being the wrong tool for the job.

The other approach \[Chris\] attempted was to make a curling broom with a handle that lit up differently based on how hard one was sweeping. It wasn’t hard to put an LED strip on a broom and light it up based on a load sensor reading, but what ended up sinking this project was the need to do it in a way that didn’t interfere with the broom’s primary function and purpose. Even a mediocre curler applies extremely high forces to a broom when sweeping in a curling game, so not only do the electronics need to be extremely rugged, but the broom’s shaft needs to be able to withstand considerable force. The ideal shaft would be a clear and hollow plastic holding an LED strip with an attachment for the load sensor, but no plastic was up to the task. \[Chris\] made an aluminum-reinforced shaft, but even that only barely worked.

We’re glad \[Chris\] shared his findings, and he said the project deserves a more detailed report. We’re looking forward to that, because [failure is a great teacher, and we’ve celebrated its learning potential time and again](https://hackaday.com/tag/fail-of-the-week/).

  
  
from Hackaday https://ift.tt/33Ixhph  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)