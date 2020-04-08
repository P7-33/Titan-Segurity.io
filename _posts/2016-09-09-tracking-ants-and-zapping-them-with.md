---
title: 'Tracking Ants and Zapping Them With Lasers'
date: 2019-10-06T03:07:00+01:00
draft: false
---

Thanks to the wonders of neural networks and machine learning algorithms, it’s now possible to do things that were once thought to be inordinately difficult to achieve with computers. It’s a combination of the right techniques and piles of computing power that make such feats doable, and [\[Robert Bond’s\] ant zapping project is a great example](https://www.hackster.io/nvidia/how-to-bug-a-bug-e6b3fd).

The project is based around an NVIDIA Jetson TK1, a system that brings the processing power of a modern GPU to an embedded platform. It’s fitted with a USB camera, that is used to scan its field of view for ants. Once detected, thanks to a little OpenCV magic, the coordinates of the insect are passed to the laser system. Twin stepper motors are used to spin mirrors that direct the light from a 5 mW red laser, which is shined on the target. If you’re thinking of working on something like this we highly recommend [using galvos to direct the laser](https://hackaday.com/2018/02/15/laser-galvo-control-via-microcontrollers-dac/).

Such a system could readily vaporize ants if fitted with a more powerful laser, but \[Robert\] decided to avoid this for safety reasons. Plus, the smell wouldn’t be great, and nobody wants charred insect residue all over the kitchen floor anyway. We’ve seen AIs do similar work, too – [like detecting naughty cats for security reasons](https://hackaday.com/2019/07/01/ai-recognizes-and-locks-out-murder-cats/).

[https://hackaday.com/wp-content/uploads/2019/09/intro.mp4](https://hackaday.com/wp-content/uploads/2019/09/intro.mp4)

  
  
from Hackaday https://ift.tt/2oUu06z  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)