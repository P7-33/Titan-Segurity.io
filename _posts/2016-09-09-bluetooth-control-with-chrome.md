---
title: 'Bluetooth Control With Chrome'
date: 2019-10-18T03:04:00+01:00
draft: false
---

All the cool projects now can connect to a computer or phone for control, right? But it is a pain to create an app to run on different platforms to talk to your project. \[Kevin Darrah\] says no and shows how you can use Google Chrome to do the dirty work. He takes a garden-variety Arduino and a cheap Bluetooth interface board and then [controls it from Chrome](https://www.youtube.com/watch?v=w_mRj5IlVpg). You can see the video below.

The HM-10 board is cheap and could connect to nearly anything. The control application uses Processing, which is the software the Arduino system derives from. So how do you get to Chrome from Processing? Easy. The p5.js library allows Processing to work from within Chrome. There’s also a Bluetooth BLE library for P5.

Once you know about those libraries, you can probably figure the rest out. But \[Kevin\] shows a nice example that you could easily replicate. The Arduino and Bluetooth code aren’t very hard to follow.  The Processing program looks a lot like an Arduino program with a setup and loop function, but it also has canvases, buttons, and other things you don’t usually have in an Arduino.

It is surprisingly easy to create a Chrome app that talks to the hardware. Our usual go to for phone apps is [Blynk](https://hackaday.com/2016/03/10/app-control-with-ease-using-blynk/). We even [used it as a joystick for a robot](https://hackaday.com/2016/12/01/the-joy-of-the-esp8266-and-blynk/#more-231533).

  
  
from Hackaday https://ift.tt/33Lp7vX  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)