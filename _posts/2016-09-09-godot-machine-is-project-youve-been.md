---
title: 'Godot Machine is the Project You’ve Been Waiting For'
date: 2019-10-30T09:07:00+01:00
draft: false
---

Are you waiting for something that may never happen? Maybe it’s the end of your ennui, or the release of Half Life 3. While you wait, why not build a Godot Machine? Then you can diversify your portfolio and wait for two things that could happen today, tomorrow, or at sunrise on the 12th of Never.

[The Godot Machine](https://www.instructables.com/id/The-Godot-Machine/) is a functional art piece that uses a solar panel and a joule thief to charge a bank of capacitors up to 5V. Whenever that happens, the Arduino comes online and generates a 20-bit random number, which is displayed on an LED bar. If the generated number matches the super-secret number that was generated at first boot and then stashed away in EEPROM, the Machine emits a victory beep and lights a green LED. Then you can go back to complaining about whatever.

We like that \[kajnjaps\] made his own chaos-based random number generator instead of just calling `random()`. It uses a guitar string to collect ambient electronic noise and an entropy generator to amplify it. Then the four least significant digits are used to seed the logistical map, so the initial value is always different.

You don’t have to create your own entropy for truly random numbers, though it’s probably more fun that way. [Did you know that someone wrote an Arduino entropy library](https://hackaday.com/2018/01/08/entropy-and-the-arduino/)?

  
  
from Hackaday https://ift.tt/2BQOiBj  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)