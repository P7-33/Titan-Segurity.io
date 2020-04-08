---
title: 'Prism Core boards design into a constrained package #PCB #Design'
date: 2019-10-23T16:49:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-81.png)

How does one fit their design into a form factor for deployment? On [Il blog di Mastro Gippo](http://www.mastrogippo.it/2019/09/prism-core-boards/), that form factor is a 3DIN size box.

> Having a lot of stuff going on, it was pretty clear that I had to spread all the electronics on at least two PCBs. How do we split functionality? The constraints of this problem are to keep connections to a minimum and put the high voltage stuff all together with good isolation.
> 
> ![](http://www.mastrogippo.it/wp-content/uploads/2019/09/Prism_block.png)
> 
> It’s clear that a good option would be to separate everything along the yellow line, leaving the High Voltage stuff on the bottom board and putting everything else on the top one. However, while designing this board I found that there was a lot of space left so I started including more and more stuff, like the STM32 and driving circuitry for the Pilot signal, so I ended up placing almost everything there.

The post details the design decisions used and is a great case on how to get everything to fit and maintain electrical integrity.

All the design files, the board templates for the enclosure and the cables diagrams are on [a github repo](https://github.com/mastrogippo/Prism-Core-DIN). The firmware for the base STM32 handling the charge process is [here](https://github.com/mastrogippo/Prism-Core-firmware)​.

[See the post here](http://www.mastrogippo.it/2019/09/prism-core-boards/).

![](http://www.mastrogippo.it/wp-content/uploads/2019/09/dinbox-1024x722.png)