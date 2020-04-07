---
title: 'Unlocking SIM Cards with a Logic Analyzer'
date: 2020-01-02T13:47:00+01:00
draft: false
---

\[Jason Gin\] wanted to reuse the SIM card that came with a ZTE WF721 wireless terminal he got from AT&T, but as he expected, it was locked to the device. Unfortunately, the terminal has no function to change the PIN and none of the defaults he tried seemed to work. The only thing left to do was [crack it open and sniff the PIN with a logic analyzer](https://ripitapart.com/2019/12/21/recovering-the-sim-card-pin-from-the-zte-wf721-cellular-home-phone/).

This project is a fantastic example of the kind of reverse engineering you can pull off with even a cheap logic analyzer and a keen eye, but also perfectly illustrates the fact that having physical access to a device largely negates any security measures the manufacturer tries to implement. \[Jason\] already knew what the SIM unlock command would look like; he just needed to capture the exchange between the WF721 and SIM card, find the correct byte sequence, and look at the bytes directly after it.

Finding the test pads on the rear of the SIM slot, he wired his DSLogic Plus logic analyzer up to the VCC, CLK, RST, and I/O pins, then found a convenient place to attach his ground wire. After a bit of fiddling, he determined the SIM card was being run at 4 MHz, so he needed to configure a baud rate of 250 kbit/s to read the UART messages passing between the devices.

[![](https://hackaday.com/wp-content/uploads/2019/12/simpin_detail.png)](https://hackaday.com/wp-content/uploads/2019/12/simpin_detail.png)

Once he found the bytes that signified successful unlocking, he was able to work his way backwards and determine the unlock command and its PIN code. It turns out the PIN was even being sent over the wire in plain text, [though with the way security is often handled these days](https://hackaday.com/2019/01/29/dont-toss-that-bulb-it-knows-your-password/), we can’t say it surprises us. All \[Jason\] had to do then was put the SIM in his phone and punch in the sniffed PIN when prompted.

Could \[Jason\] have just run out to the store and picked up a prepaid SIM instead of cracking open this wireless terminal and sniffing its communications with a logic analyzer? Of course. But where’s the fun in that?

  
  
from Hackaday https://ift.tt/2FfdWBm  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)