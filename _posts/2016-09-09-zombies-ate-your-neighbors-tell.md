---
title: 'Zombies Ate Your Neighbors? Tell Everyone Through LoRa!'
date: 2019-12-04T13:02:00+01:00
draft: false
---

As popular as the post-apocalyptic Zombie genre is, there is a quite unrealistic component to most of the stories. Well, apart from the whole “the undead roaming the Earth” thing. But where are the nerds, and where is all the apocalypse-proof, solar-powered tech? Or is it exactly this lack of tech in those stories that serves as incentive to build it in the first place? Well, maybe it doesn’t have to be the end of the world to seek for ways to cope with a collapse of our modern communication infrastructure either. Just think of natural disasters — an earthquake or hurricane causing a long-term power outage for example. The folks at \[sudomesh\] tackle exactly this concern with their [fully open source, off-grid, solar-powered, LoRa mesh network, _Disaster Radio_](https://disaster.radio/).

The network itself is built from single nodes comprising of a battery-backed solar panel, a LoRa module, and either the ESP8266 or ESP32 for WiFi connectivity. The idea is to connect to the network with your mobile phone through WiFi, therefore eliminating any need for additional components to actually use the network, and have the nodes communicate with each other via LoRa. Admittedly, LoRa may not be your best choice for high data rates, but it is a good choice for long-range communication when cellular networks aren’t an option. And while you can built it all by yourself with everything available on [\[sudomesh\]’s GitHub page](https://github.com/sudomesh/disaster-radio), a TTGO ESP32 LoRa module will do as well.

If the idea itself sounds familiar, we did indeed cover similar projects like [HELPER](https://hackaday.com/2019/03/29/emergency-neighbourhood-communications-courtesy-of-helper/) and [Skrypt](https://hackaday.com/2019/07/11/adding-lora-long-range-radio-to-smartphones-and-connected-devices/) earlier this year, showing that LoRa really seems to be a popular go-to for off-grid communication. But well, whether we really care about modern communication and helping each other out when all hell breaks loose instead of just primevally defending our own lives is of course another question.

  
  
from Hackaday https://ift.tt/362vR9C  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)