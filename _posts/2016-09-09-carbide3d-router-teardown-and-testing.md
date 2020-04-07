---
title: 'Carbide3D Router Teardown and Testing'
date: 2020-01-28T01:44:00+01:00
draft: false
---

On the face of it, you’d think a small router would be pretty simple. After all, what is it other than a spinning motor? However, that motor has to handle some pretty serious torque depending on what you are routing. \[Baki1\] had his Carbide3D router die in the middle of a project, so he did what any of us would do. He [tore it open](https://www.youtube.com/watch?v=PLuOmIOzqaI&feature=youtu.be).

In addition to showing off its insides, he also tried to figure out what was wrong with it. It looks like a blown triac was the culprit, and we assume that part 2 will be the repair and how that actually worked out.

The motor was skipping steps, and in fact, wouldn’t start spinning without a few love taps from a pair of pliers. Once freed from the housing, you can see a surprising amount of circuitry in the relatively small space.

A triac mostly broke off the PC board when exposed. Some testing showed that the router was mechanically intact. However the triac tested bad, and we’ll have to wait for part 2 to see if that really fixes it or not.

This couldn’t help but remind us of the [Dremel triac repair](https://hackaday.com/2013/11/26/simple-dremel-triac-hack-repair/) we saw in 2016. It also reminded us that we wanted to build our [big red switch](https://hackaday.com/2018/02/11/push-big-red-button-receive-power/).

  
  
from Hackaday https://ift.tt/311onlT  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)