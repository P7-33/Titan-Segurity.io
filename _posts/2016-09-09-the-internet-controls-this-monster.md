---
title: 'The Internet Controls This Monster'
date: 2020-01-07T07:13:00+01:00
draft: false
---

What’s worse than unleashing a monster on the internet? Allowing the internet to control the monster! But that’s just what \[8BitsAndAByte\] did, [created a monster that anyone on the internet can control](https://www.instructables.com/id/The-Internet-Monster). Luckily for us, this monster only talks.

This is a very simple project and most of the parts are off the shelf. Hardware wise the monster’s body is made out of a plastic flowerpot; its mouth is a bit of wood that covers the top of the flowerpot; its eyes, two halves of a plastic sphere painted white with some felt for irises. And then whole thing is covered in some blue fake fur.

Electronics wise, a Raspberry Pi is running the show and handling the text-to-speech is an AIY Voice Hat. A servo fits inside the flowerpot to open and close the monster’s mouth. On the software end of things, a bit of Python has been written that waits for a bit of text, sends it off to the Voice Hat’s text-to-speech module and moves the servo to open and close the mouth. The scary part, connecting the monster to the internet, is done with [remo.tv](https://github.com/remotv/controller), which is some open-source code hosted on GitHub specifically for allowing control of robots over the internet.

This is a neat little project which is simple enough that kids could build one themselves. The instructions and the python script are up on [the Instructables page](https://www.instructables.com/id/The-Internet-Monster), and you can see the monster in action at its [page](https://remo.tv/join/lwppotv) on remo.tv. Perhaps \[8BitsAndAByte\] could add a couple of these [internet controlled robot arms](https://hackaday.com/2011/11/24/internet-controlled-robotic-arm-2/) to the monster to create a monster that could create some real havoc!

  
  
from Hackaday https://ift.tt/36w01mj  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)