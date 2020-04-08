---
title: 'You’ve Got Mail?'
date: 2019-12-01T07:04:00+01:00
draft: false
---

Life is full of tough decisions, such as deciding whether you want to go to the end of the drive to check if the mail has arrived. These questions are made even more arduous in the winter months, but \[Catpin\] has a solution. [The Mail Box Alert](https://www.catpin.com/mailalert/) uses an Electric Imp, a solar panel and a proximity sensor to let you know if you’ve got mail.

[![](https://hackaday.com/wp-content/uploads/2019/11/mailboxdone2.jpg?w=400)](https://hackaday.com/wp-content/uploads/2019/11/mailboxdone2.jpg)It’s a neat build, with the brains provided by that [Electric Imp](https://www.electricimp.com/) which handles most of the heavy lifting. This wakes up every five minutes and checks whether the status of a small proximity sensor has changed. If it has, it pings a website. The unit sits at the bottom of the postbox, so if your friendly neighborhood post person has put in any letters, it will have changed. The Imp is powered by a small battery, which is in turn charged by a solar panel. That means that it doesn’t require any power cables or other wiring, as long as it is in the range of WiFi. With the addition of a 15-hours overnight deep sleep, \[Catpin\] found that the whole thing could be run from a couple of 18650 LiPo batteries.

Perhaps the most interesting part of the writeup was discussing the problems that he found with the build, such as the fact that a LiPo battery won’t perform that well in a Wisconsin winter. So, this was replaced with a Lithium Iron Phosphate battery that should be a bit more tolerant of the chill. There is also a writeup on how to create the same project using an ESP8266 if required.

  
  
from Hackaday https://ift.tt/2DyJcKF  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)