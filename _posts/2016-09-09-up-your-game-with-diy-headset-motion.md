---
title: 'Up Your Game With DIY Headset Motion Tracking'
date: 2020-02-03T07:02:00+01:00
draft: false
---

While there’s been a lot of advancements in VR gaming over the last couple of years, plenty of folks are still happy enough to just stare at their monitor. But that’s not to say some of those fancy head-tracking tricks wouldn’t be a welcome addition to their repertoire. For players who are literally looking to get their head in the game, [\[Adrian Schwizgebel\] has created qeMotion](https://www.instructables.com/id/QeMotion/).

[![](https://hackaday.com/wp-content/uploads/2020/01/qemotion_detail.jpg?w=337)](https://hackaday.com/wp-content/uploads/2020/01/qemotion_detail.jpg)The idea here is simple enough: attach a motion sensor to a standard gaming headset (here a MPU-6050 IMU), and use the data from it to virtually “press” keys through USB HID emulation. Many first person shooter games offer the ability to lean left or right by pressing Q or E respectively, so all \[Adrian\] had to do was map the appropriate accelerometer readings to those keys for it to work seamlessly with popular titles such as _Tom Clancy’s Rainbow Six Siege_ and _Insurgency._

The concept might be basic, but the execution is anything but. Rather than just duct taping an Arduino to his headset, \[Adrian\] designed a very slick 3D printed enclosure for the electronics that sits on his desk. While they haven’t all been implemented yet, the devices features indicator lights and buttons to switch through various modes. The sensor on the headset has similarly been encased in a very professional looking 3D printed box, complete with a nice braided cable to link it to the desk unit.

It’s been awhile since we’ve seen a head tracking project, and [most of those utilized something like the Wii Remote](https://hackaday.com/2007/12/21/wiimote-head-tracking-desktop-vr-display/). Adding sensors to a person’s head normally wouldn’t be an ideal situation, but if you’re going to be wearing the headset anyway to listen to the game and chat, it’s not really a problem. If your hair is too nice for the qeMotion, [you could always try doing something similar with computer vision](https://hackaday.com/2015/09/14/head-gesture-tracking-helps-limited-mobility-students/).

  
  
from Hackaday https://ift.tt/2OnCQUb  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)