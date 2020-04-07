---
title: 'Sealed lead acid battery testers #Batteries @Brian_Dorey'
date: 2019-12-27T17:29:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-91.png)

[Brian Dorey posts](https://www.briandorey.com/post/12v-sla-battery-testers) about using 12 volt sealed lead acid (SLA) batteries and the need to test them:

> We use 12 Volt sealed lead acid batteries (SLA) for many different uses from shed lighting to running radios and other 12V equipment which needs a portable power supply.
> 
> To check the charge status of the batteries we usually use a multimeter but with some being used as shed lighting on our allotment it would be useful to have a built in voltage tester fitted on the batteries so we don’t need to carry a multimeter with us each time.
> 
> We mainly use the 12 Volt 7 Amp and 12 Volt 12.6 Amp batteries and so Andrew designed a custom PCB which fits direct onto the top of the batteries and has a voltage tester circuit with LED indicators for the charge state.

The circuit uses a Microchip PIC16F1933 with a 5V 78L05 voltage regulator to power the microcontroller and a voltage divider is used to drop the voltage down to a level that can be measured by the internal ADC. A row of 10 LEDs are used to display a voltage range of 11.6V to 12.7V. The LEDs are coloured red, yellow and green to make it quick and simple to see the charge state of the battery. Green means the battery is still charged, yellow means it is getting low and red means it needs recharging.

The PCB design files in Diptrace format and microprocessor code can be downloaded from [GitHub](https://github.com/briandorey/12v-SLA-battery-tester). [Download the schematic in PDF format.](https://www.briandorey.com/docs/2019-11-21-battery-testers/battery-status-indicator-schematic.pdf "Download PDF")

[See the full post here](https://www.briandorey.com/post/12v-sla-battery-testers).

![Plastic cover fitted on the battery](https://www.briandorey.com/docs/2019-11-21-battery-testers/cover-fitted.jpg)