---
title: 'Building a Cyberpunk Multi-Touch Input Device'
date: 2019-10-06T15:07:00+01:00
draft: false
---

This [multi-touch touch panel built by \[thiagesh D\]](https://hackaday.io/project/167866-led-touch-matrix-raspberry-pi) might look like it came from the retro-futuristic worlds of _Blade Runner_ or _Alien_, but thanks to a detailed build video and a fairly short list of required parts, it could be your next weekend project.

[![](https://hackaday.com/wp-content/uploads/2019/10/touchpanel_detail.jpg?w=400)](https://hackaday.com/wp-content/uploads/2019/10/touchpanel_detail.jpg)The build starts with a sheet of acrylic, which has a grid pattern etched into it using nothing more exotic than a knife and a ruler. Though if you _do_ have access to some kind of CNC router, this would be a perfect time to break it out. Bare wires are then laid inside the grooves, secured with a healthy application of CA glue, and soldered together to make one large conductive array. This is attached to a capacitive sensor module so it’ll fire off whenever somebody puts a finger on the plastic.

With RGB LED strips added to the edges, you could actually stop here and have yourself a very cool looking illuminated touch sensitive panel. But ultimately, it would just be a glorified button. There’s plenty of interesting applications for such a gadget, but it’s not going to be terribly useful attached to your computer.

To turn this into a viable input device, \[thiagesh D\] is using a Raspberry Pi and its camera module to track the number and position of fingertips from the other side of the acrylic with Python and OpenCV. His code will even pick up on specific gestures, like a three finger drag which changes the colors of the LEDs accordingly in the video below. The camera’s field of view unfortunately means the box the panel gets mounted to has to be fairly deep, but if recessed into the surface of a desk, we think it could look incredible.

Custom multi-touch panels have been a favorite project of hackers for years now, and we’ve got examples [going all the way back to the old black and white days](https://hackaday.com/2007/12/16/diy-led-multi-touch-panel/). But [larger and more modern incarnations](https://hackaday.com/2017/11/04/diy-multi-touch-all-the-surfaces/) like this one have the potential to [change how we interface with technology](https://hackaday.com/2010/12/03/benddesk-multi-touch-furniture/) on a daily basis.

  
  
from Hackaday https://ift.tt/2ItJbux  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)