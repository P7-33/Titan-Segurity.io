---
title: 'Haptic Glove Controls Robot Hand Wirelessly'
date: 2019-10-26T03:01:00+01:00
draft: false
---

\[Miller\] wanted to practice a bit with some wireless modules and wound up creating a [robotic hand he could teleoperate with the help of a haptic glove](https://www.youtube.com/watch?v=nOafy9IheYE). It lookes highly reproducible, as you can see the video, below the break.

The glove uses an Arduino’s analog to digital converter to read some flex sensors. Commercial flex sensors are pretty expensive, so he experimented with some homemade sensors. The ones with tin foil and graphite didn’t work well, but using some bent can metal worked better despite not having good resolution.

The wireless communications set up was pretty easy thanks to the NRF24L01 modules. The hard part was sewing the flex sensors into the glove. We thought some of the circuitry looked precarious on the glove, too.

For the robot hand, he used balsa wood and hinges for each joint. Flexible thread provided the return power like a spring. The hand was surprisingly artistic in a primitive sort of way.

While this is a cool demo, the hand isn’t likely to be practical for much as it is. [Nerve impulses](https://hackaday.com/2016/12/31/move-a-robotic-hand-with-your-nerve-impulses/) are better but harder. The glove reminded us a little of one we’d [seen before](https://hackaday.com/2013/12/10/a-kinect-controlled-robotic-hand/).

  
  
from Hackaday https://ift.tt/2NhMt5u  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)