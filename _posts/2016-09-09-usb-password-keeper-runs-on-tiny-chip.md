---
title: 'USB Password Keeper Runs on Tiny Chip'
date: 2020-02-08T16:13:00+01:00
draft: false
---

The most important rule of password use, especially when used for online logins, is to avoid reusing passwords. From there, one’s method of keeping track of multiple passwords can vary considerably. While memorization is an option in theory, in practice a lot of people make use of a password manager like Lastpass or KeePass. For those with increased security concerns, though, you may want to implement a [USB password keeper like this one](https://github.com/snopf/snopf) based on an ATtiny.

This password keeper, called “snopf”, is a USB device with an ATtiny85 which adds a layer of separation to password keeping that increases security substantially. Passwords are created by the USB device itself using a 128-bit key to generate the passwords, which are physically detached from the computer. Password requests are made by the computer to the USB device, but the user must push a button on the snopf in order to send the password to the computer. It does this by emulating a keyboard, keeping the password information off of the computer’s clipboard.

Of course, snopf isn’t perfectly secure, and the project’s creator \[Hajo\] goes into detail on the project’s page about some of the potential vulnerabilities. For most use cases, though, none of these are of serious concern. Upgrading your password keeper to a physical device is likely to be a huge security improvement regardless, [and one was actually developed on Hackaday](https://hackaday.com/2014/10/30/developed-on-hackaday-the-answer-is-below/) a few years ago.

  
  
from Hackaday https://ift.tt/2SvEqEO  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)