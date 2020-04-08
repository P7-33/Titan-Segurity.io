---
title: 'Google Creates Debuggable iPhone'
date: 2019-11-04T04:05:00+01:00
draft: false
---

Apple is known for a lot of things, but opening up their platforms to the world isn’t one of those things. According to a recent Google post by \[Brandon Azad\], there do exist [special iPhones](https://googleprojectzero.blogspot.com/2019/10/ktrw-journey-to-build-debuggable-iphone.html) that are made for development with JTAG ports and other magic capabilities. The port is [in all iPhones](https://www.theiphonewiki.com/wiki/Baseband_JTAG) (though unpopulated), but is locked down by default. We don’t know what it takes to get a magic iPhone, but we are guessing Google can’t send in the box tops to three Macbook Pros to get on the waiting list. But what is locked can be unlocked, and \[Brandon\] set out to build a debuggable iPhone.

Exploiting some debug registers, it is possible to debug the A11 CPU at any point in its execution. \[Brandon’s\] tool single steps the system reset and makes some modifications to the CPU after key instructions to prevent the lockdown of kernel memory. After that, the world’s your oyster. [KTRW](https://github.com/googleprojectzero/ktrw) is a tool built using this technique that can debug an iPhone with a standard cable.

The name is a play on KTRR which is the Kernel Text Readonly Region. The work follows the example of some earlier exploits that did similar things. Those methods, though, didn’t have the flexibility that KTRW offers.

Honestly, we don’t really care about debugging the iPhone but the cat and mouse story of how to work around all the Apple protection is a pretty good read. Of course, it really is cat and mouse. KTRW doesn’t work on A12 devices. Curiously, \[Brandon\] thinks other people already knew this or similar methods to compromise the phone, but didn’t publish it to discourage Apple closing the door that lets them in.

Apple phones have a reputation as being safe, but they [do get hacked](https://hackaday.com/2019/09/06/this-week-in-security-mass-iphone-compromise-more-vpn-vulns-telegram-leaking-data-and-the-hack-of-jack/). And if you want to just disable some of them, you only need [a kid’s balloon](https://hackaday.com/2018/10/31/helium-can-stop-your-iphone-maybe-other-mems-too/).

  
  
from Hackaday https://ift.tt/2PKnL0K  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)