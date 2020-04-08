---
title: 'Long Live Jibo, Our Adorable Robot Companion'
date: 2019-10-17T09:05:00+01:00
draft: false
---

Jibo, the adorable robot made by Jibo, Inc., was getting phased out, but that didn’t stop \[Guilherme Martins\] from using his robot companion for [one last hack](https://medium.com/artica/long-live-jibo-b4aabdc9f9e0).

When he found out that the company would be [terminating production](https://hackaday.com/2019/03/08/uncertain-future-of-orphaned-jibo-robots-presents-opportunities/) of new Jibos and shutting down their servers, he wanted to replace the brain of the robot so that it would continue to live on even after all of its software had become deprecated. By the time the project started, the SDK downloads had already been removed the from developer’s site, so they looked at other options for controlling Jibo.

The first challenge was to not break the form factor in order to disassemble Jibo. They only managed to remove the battery from the bottom, realizing that the glass frame held the brain room. From within the robot, they were able to find the endless rotation joint for the head and the heart of the electronics. Jibo uses a DC motor, encoder, and IR sensor at each of three distinct levels to detect reference points.

![](https://hackaday.com/wp-content/uploads/2019/10/jibo-brain.jpeg?w=400)

They decided to use Phidgets modules to interface with these devices. While the DC motor controller handles 2A and has an encoder port, the Phidgets are able to provide software with the encoder and PID built-in. The 4x Digital Input Module was used for detecting the IR switch and connecting the modules to the computer.

\[Martins\] decided to use LattePanda, a hackable Windows 10 development board, for the brain of the new Jibo. The board was luckily able to fit inside the compartment for Jibo, but since it requires more power the unit is powered with 12V regulated to 5V in order to have less current passing through the wires. The DC motors, meanwhile, run at 12V and the IR switches and encoders at 5V.

A program developed in Unity3D plays the eye animations, and a C# program interfaces with the Phidgets. The final configuration was to fit Jibo onto a robotic arm to augment its behaviors. We previously wrote about [Toppi](https://hackaday.com/2019/05/25/humanizing-industrial-robots-by-sticking-a-jibo-on-top/), the robotic arm artist, that was used as the base for Jibo’s new home.

You can check out the result in the video below.

  
  
from Hackaday https://ift.tt/33H2c4W  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)