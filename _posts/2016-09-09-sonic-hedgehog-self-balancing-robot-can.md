---
title: 'Sonic The Hedgehog Self-Balancing Robot Can Bend At The Knees'
date: 2020-01-31T13:23:00+01:00
draft: false
---

Building your own self-balancing robot is a rite of passage for anyone getting into the field of robotics. Master of robots, \[James Bruton\] has been there, done that, and collected a few T-shirts. Now he’s building a large [Sonic the Hedgehog self balancing robot](https://www.youtube.com/watch?v=yF14N03rkS4&feature=emb_title) that can bend at the knees and hip, allowing it to lean while turning and handle uneven terrain. Check out the first video embedded after the break.

Standing about 1 m tall, the robot is inspired by Boston Dynamic’s box handling bot, [Handle](https://hackaday.com/2017/02/27/i-am-science-fiction-incarnate-i-am-handle/). It’s “skeleton” consists of 20×20 aluminium extrusions, bolted together using a bunch of 3D printed fittings in the signature blue and red of Sonic. The wheels and tyres are also 3D printed, and driven by brushless motor via a toothed belt. The knee/hip mechanism is actuated using a ball screw, also driven by a brushless motor.

\[James\] intends to implement an active shock absorption system into the leg mechanism, using the same technique he [tried on his OpenDog robot](https://hackaday.com/2020/01/04/opendog-adding-force-sensitive-feet/). It works by bolting a load cell onto one of the leg extrusion to sense when it flexes under load, and then actuating the knee mechanism to absorb the force. His first version of the system on OpenDog used PWM signals to send the load cell data to the main controller, but the motors on the legs induced enough noise in the signal wires to make it unusable. He has since started experimenting with the CAN bus protocol, which was specifically designed to work reliably in noisy systems like modern automobiles. If he gets it working on the two legs of this Sonic robot, he plans to also implement it on the quadruped OpenDog.

This is another very ambitious project from \[James\], and we’re really looking forward to the next instalments. With a bunch of complex projects under his belt, like a [series of  full size Star Wars robots](https://hackaday.com/2016/12/10/speed-run-james-brutons-star-wars-builds/), we have high hopes for success.

  
  
from Hackaday https://ift.tt/2S4JQXk  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)