---
title: 'WooCommerce Lead Time v1.1 nulled'
date: 2020-01-05T10:29:00+01:00
draft: false
---

When you read “Arduino wristwatch”, you fall into the trap of envisioning an Arduino UNO clumsily strapped to someone’s wrist. \[Marijo Blažević’s\] [creation is much more polished than that](https://www.hackster.io/marijoblaz/arduino-wristwatch-d4cc92). A round circuit board holds two surface mount ICs and 12 LEDs. The whole thing looks nice fit snugly inside of a watch body. It isn’t a Rolex, but it does have considerable geek cred without being unwearable in polite company.

Once IC is an AVR micro, of course. The other is a DS3231 real time clock with built-in crystal. A CR2032 keeps it all running. The main body, the outer ring, the bottom, and the buttons are 3D printed in PLA. The crystal and the band are the only mechanical parts not printed. The [bill of materials](https://docs.google.com/spreadsheets/d/1dRS8NlPdyWTDZ6p1nXBYItXKkWj21toqLvILf9NTu7Y/edit#gid=0) shows a 36mm crystal and even provides links for all the parts.

You don’t want to run LEDs all the time because it is bad on the battery. When you press the button once, you get one of the LEDs to light to show the hours. Another press reads the minutes in units of 5 minutes. A third press shows you one of five LEDs to show how many minutes to add. For example, if the time is 9:26 you’d get LED 9 (hours), LED 5 for 25 minutes, and the third press would show LED 1 for 1 extra minute. If either of the minute indicators show 12 o’clock, that indicates zero minutes.

The exciting thing, of course, is that you can program it beyond the [code](https://github.com/marijoblaz/iOWatch) on GitHub. Already it can tell time and display the temperature. You don’t have a lot of I/O, but you ought to be able to get some more options and maybe some flashy LED blinking patterns in if you try.

  
  
from Hackaday https://ift.tt/2tup0YM  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)