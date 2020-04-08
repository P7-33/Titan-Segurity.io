---
title: 'A Web API For Your Pi'
date: 2019-10-01T12:04:00+01:00
draft: false
---

There are many ways to attach a project to the Internet, and a plethora of Internet-based services that can handle talking to hardware. But probably the most ubiquitous of Internet protocols for the average Joe or Jane is the web browser, and one of the most accessible of programming environments lies within it. If only somebody with a bit of HTML and Javascript could reach a GPIO pin on their Raspberry Pi!

![](https://hackaday.com/wp-content/uploads/2019/09/raspberry-pi-web-api.png?w=400)If that’s your wish, then help could be at hand [in the form of \[Victor Ribeiro\]’s RPiAPI](https://hackaday.io/project/167837-rpiapi). As its name suggests, it’s an API for your Raspberry Pi, and in particular it provides [a simple web-accessible endpoint wrapper for the Pi’s GPIO library](https://github.com/victorqribeiro/rpiapi) from which its expansion port pins can be accessed. By crafting a simple path on the address of the Pi’s web server each pin can be read or written to, which while it’s neither the fastest or most accomplished hardware interface for the platform, could make it one of the easiest to access.

Security comes courtesy of Apache password protected directories via `.htaccess` files, so users would be well-advised to consider the implications of connecting this to a public IP address very carefully. But for non experts in security it still has the potential to make a very useful tool in the armoury of ways to control hardware from the little single board computer. It’s not the first try at this idea as we’ve seen [a PHP example](https://hackaday.com/2012/05/05/controlling-raspberry-pi-expansion-pins-with-a-web-interface/) early in the Pi’s lifetime as well as one [relying upon MySQL](https://hackaday.com/2013/02/02/easy-web-interface-with-gpio-access-runs-on-raspberry-pi/), but it does seem to be a simpler option than the others.

  
  
from Hackaday https://ift.tt/2nqZT6f  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)