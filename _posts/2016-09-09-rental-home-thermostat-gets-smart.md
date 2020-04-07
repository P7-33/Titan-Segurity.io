---
title: 'Rental Home Thermostat Gets Smart Upgrade Without Modifying the Dumb
Controller'
date: 2020-02-09T16:13:00+01:00
draft: false
---

A problem facing those who live in rental properties comes with two prongs: that such properties rarely have up-to-date facilities such as heating controllers, and that landlords tend to take a dim view of tenants installing their own alternatives. \[Andy\] wanted to upgrade the heating controller in his home and was in this situation, so [he came up with a smart controller add-on for the existing mechanical timer](https://andybradford.dev/2020/02/01/how-i-made-my-heating-smart-without-damaging-or-replacing-anything/) that does not irreversibly modify anything and is easily removable when he moves on.

This sounds like an impossible task, but it’s one he’s done very well by mounting a stepper motor on a 3D-printed frame over the timer switch. It’s the type with a motorised ring onto which plastic fingers can be placed to flip a switch on or off; he’s simply removed the plastic fingers and designed a shaft extension for the motor that simulates their passing the switch. He can now turn his heating on and off at will from an ESP8266, in this case on an Adafruit Feather Huzzah.

Behind it all lies [Adafruit IO](https://io.adafruit.com/) with a custom dashboard — Hackaday’s \[Sean Boyce\] [took this service for a trial run](https://hackaday.com/2017/10/31/review-iot-data-logging-services-with-mqtt/) if you’d like his take on it’s features. For this project, Adafruit IO delivered exactly what \[Andy\] was after but still left a few teething troubles. The stepper needed to be told not to try to hold its position, and moving a stepper very slowly generated wait periods long enough to trigger the ESP’s watchdog timers. Adding in [IFTTT](https://ifttt.com/) gave him the ability to schedule, as well as Alexa control. All in all he’s replicated some commercial offerings with a lot less cost and all without annoying his landlord. You can see it in action in the video below the break.

  
  
from Hackaday https://ift.tt/2OH4jk5  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)