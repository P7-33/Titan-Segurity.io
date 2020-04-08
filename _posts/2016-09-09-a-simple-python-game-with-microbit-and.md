---
title: 'A simple Python game with micro:bit and OLED
display #OLED #Gaming #Python #microbit @blogmywiki'
date: 2019-12-13T15:38:00+01:00
draft: false
---

[blogmywiki posts](http://www.suppertime.co.uk/blogmywiki/2019/11/python-game-microbit-oled/) about using an OLED display with a micro:bit and programming a game using Python.

> I’ve managed to get a simple game working on my micro:bit OLED display, and I ditched the breadboard at the same time, meaning that it should be possible to build this into a small case. I may even add some external buttons and perhaps some sound?
> 
> (For micro:bit interface), a Pimoroni pin:bit edge connector (the [Adafruit DragonTail ](https://www.adafruit.com/product/3695)would work well, with the Kitronik one you have to solder extra pins to get to the i2c interface pins).
> 
> I added the extra Python modules using the new micro:bit Python editor’s feature to add extra files to your projects. It supports WebUSB, so using a recent version of Chrome you can flash Python projects straight onto your micro:bit without having to drag and drop HEX files.

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-40.png)

> The program works by creating ‘stamps’ – like crude sprites – for 3 hazards (a duck, a ghost and a tortoise), all using graphics from the micro:bit’s own built-in 5×5 icons. This is a neat touch that avoids having to create your own bitmap graphics.
> 
> You move left and right using A and B buttons, and press A+B together to move forward – you can’t move backwards! When you reach the top you level up, complete 10 levels to win.

See [the post](http://www.suppertime.co.uk/blogmywiki/2019/11/python-game-microbit-oled/) for the build details and the [video](https://youtu.be/82gQ105goaQ) above.

![](http://www.suppertime.co.uk/blogmywiki/wp-content/uploads/2019/11/vlcsnap-2019-11-25-07h49m05s155-1024x576.png)