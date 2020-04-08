---
title: 'Modulated Pilot Lights Anchor AR to Real World'
date: 2019-12-17T10:57:00+01:00
draft: false
---

We’re going to go out on a limb here and say that wherever you are now, a quick glance around will probably reveal at least one LED. They’re everywhere – we can spot a quick half dozen from our desk, mostly acting as pilot lights and room lighting. In those contexts, LEDs are pretty mundane. But what if a little more flash could be added to the LEDs of the world – literally?

That’s the idea behind [LightAnchors](https://www.lightanchors.org/), which bills itself as a “spatially-anchored augmented reality interface.” LightAnchors comes from work at \[Chris Harrison\]’s lab at Carnegie Mellon University which seeks new ways to interface with computers, and leverages the ubiquity of LED point sources and the high-speed cameras on today’s smartphones. LightAnchors are basically beacons of digitally encoded data that a smartphone can sense and decode. The target LED is modulated using amplitude-shift keying and each packet contains a data payload and parity bits along with a pre- and post-amble sequence. Software on the phone uses the camera to isolate the point source, track it, and pull the data out of it, which is used to create an overlay on the scene. The video below shows a number of applications, ranging from displaying guest login credentials through the pilot lights on a router to modulating the headlights of a rideshare vehicle so the next fare can find the right car.

[An academic paper](https://karan-ahuja.com/assets/docs/paper/lightanchors.pdf) (PDF link) goes into greater depth on the protocol, and demo Arduino code for creating LightAnchors is thoughtfully provided. It strikes us that the two main hurdles to adoption of LightAnchors would be convincing device manufacturers to support them, and advertising the fact that what looks like a pilot light might actually be something more, but the idea sure beats [fixed markers for AR tracking](https://hackaday.com/2014/08/24/open-source-marker-recognition-for-augmented-reality/).

  
  
from Hackaday https://ift.tt/2PSotY1  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)