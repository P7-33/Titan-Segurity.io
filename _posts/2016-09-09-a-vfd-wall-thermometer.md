---
title: 'A VFD Wall Thermometer'
date: 2019-12-28T13:26:00+01:00
draft: false
---

Want to build something using VFD tubes, but don’t need yet _another_ clock project? In that case, this [wall mounted temperature and humidity display created by \[commanderkull\]](https://imgur.com/a/VfKWqYv) might be exactly what you’re looking for. With six IV-11 tubes, this display is a practical way to add some of that gorgeous blue-green glow to your home or office.

The USB powered display uses a XL6009 and an XL7015 to provide the 24 V and 1.8 V needed by the IV-11 tubes, respectively. Both of which can be disconnected with jumpers to shut down the tubes without powering off the entire device, a useful feature when programming and debugging the display’s ATmega328P microcontroller. Each tube is connected to the ATmega with an 74HC595 shift register and a UDN2981 driver. Temperature and humidity data is provided, perhaps unsurprisingly, by the exceptionally common DHT22 sensor.

If you _are_ looking to build another clock with these style tubes, [there’s certainly enough prior art out there to get you started](https://hackaday.com/2013/03/02/vfd-tube-clock-built-using-protoboard-and-free-formed-psu/). We’ve also seen [faux VFDs that you could use for either project](https://hackaday.com/2018/03/26/its-a-nixie-its-a-vfd-no-its-a-custom-led-display-in-a-tube/), just in case you aren’t looking to deal with the voltage requirements and relative rarity of the real thing.

  
  
from Hackaday https://ift.tt/2tZcocm  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)