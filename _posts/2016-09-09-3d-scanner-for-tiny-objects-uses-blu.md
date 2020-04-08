---
title: '3D Scanner For Tiny Objects Uses Blu-Ray Parts'
date: 2019-10-30T12:02:00+01:00
draft: false
---

There’s plenty of different methods to build a 3D scanner, with photogrammetry being a particularly accessible way to do it. This involves taking a series of photos from different angles to build up the geometry of the model. If you want to do this with something small, instead of a camera, just substitute a microscope! [\[NoseLace’s\] LadyBug does just that.](https://www.instructables.com/id/LadyBug-a-Motorized-Microscope-and-3D-Scanner-for-/)

It’s a 3D scanner built in a very hacker fashion. The X-Y stage that moves the sample is from a KES-400a Blu-Ray drive, salvged from the original “fat” Playstation 3. The Z axis is then created using the linear stepper motor from the optical pickup of the same drive. A rotary stepper motor is added on to the Z-axis to allow the sample to be rotated. It’s all combined with a basic USB microscope to take the images, and a Raspberry Pi which handles running all the stepper motors with some add-on driver boards.

\[NoseLace\] uses the device to create 3D models of insects, but it would work just as well with other small objects. The benefit of this approach is that it creates both the 3D model and the requisite texture, too. [There’s plenty of open-source tools available if you’d like to try it for yourself.](https://hackaday.com/2019/04/07/get-great-3d-scans-with-open-photogrammetry/) Video after the break.

  
  
from Hackaday https://ift.tt/2JzhXDg  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)