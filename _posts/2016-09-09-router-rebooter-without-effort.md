---
title: 'Router Rebooter Without The Effort'
date: 2019-11-02T12:05:00+01:00
draft: false
---

It’s one of the rituals of our age, rebooting the family router when the bandwidth falters. Flip the power, and after half a minute or so your YouTube video starts up again. Consumer-grade router hardware is not the most reliable computing equipment you will own, as \[Nick Sayer\] found out when the router at his vacation home wasn’t reliable enough to support his remote monitoring equipment. His solution is [an auto-reboot device](https://hackaday.io/project/168150-reboot-o-matic), that power-cycles the offending device on command.

An obvious method might be to switch the mains supply, but instead he’s taken the simpler option of switching the DC from the router’s wall wart power supply with a cunning arrangement of three MOSFETs to keep the router defaulting to on under all conditions except when it is commanded to power down by the ATtiny microcontroller overseeing it. This chip provides extra fail-safe and debouncing functions to ensure no accidental rebooting.

Driving the circuit is a Raspberry Pi that handles the house monitoring, on which a Python script checks for Internet access and asks for a reboot if there is none. For extra safety it requires access to be down for a sustained period before doing so in case of a router firmware upgrade.

This isn’t the first router rebooter, for a mains-switching ESP8266 [take a look at this one](https://hackaday.com/2018/01/31/router-rebooter-eliminates-hassles/).

Router picture: Asim18 \[[CC BY-SA 3.0](https://commons.wikimedia.org/wiki/File:ADSL_router_with_Wi-Fi_(802.11_b-g).jpg)\]

  
  
from Hackaday https://ift.tt/36Biv5w  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)