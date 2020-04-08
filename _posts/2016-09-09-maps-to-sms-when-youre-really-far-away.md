---
title: 'Maps to SMS, When You’re Really Far Away'
date: 2019-09-29T03:09:00+01:00
draft: false
---

GPS is available on most smart phones, which is all well and good unless you drive out into a place with weak service. Unless you want to go into the before-time and buy a standalone GPS (and try to update the maps every so often) or go even further back and print out MapQuest directions, you’ll need another solution to get directions. Something like [this project which sends Google Maps directions over SMS](https://medium.com/@ahadcove/bringing-back-google-maps-by-text-messaging-using-a-raspberry-pi-9ca51bc912df).

The project is called RouteMe by \[AhadCove\]. It runs on a Raspberry Pi at his home which is constantly monitoring an email inbox. Using Google Voice to forward incoming text messages as emails to the Pi, the system works when your phone has a cell signal but no data connection. The Pi listens for specific commands in that SMS-to-Email connection and is able to send directions back to the phone via text message. That’s actually a neat hack you may remember from the olden days where you can send email as SMS using the phone number as the address.

If you find yourself lost in the woods with just your phone often enough, \[AhadCove\] has all of the code and detailed directions on how to set this up on [his GitHub site](https://github.com/AhadCove/routeme). But don’t discount this particular task, anything you can script on the Pi can now be controlled via SMS without relying on a service like Twilio.

This maps hack is a pretty ingenious solution to a problem that more than a few of us have had, and it uses a lot of currently-available infrastructure to run as well. If you want another way of navigating without modern tech, have a go at [dead reckoning in a car](https://hackaday.com/2018/06/17/retrotechtacular-car-navigation-like-its-1971/).

  
  
from Hackaday https://ift.tt/2myfqB7  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)