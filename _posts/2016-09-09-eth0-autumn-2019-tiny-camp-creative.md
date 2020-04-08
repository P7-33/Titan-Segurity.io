---
title: 'Eth0 Autumn 2019: Tiny Camp, Creative Badge'
date: 2019-11-03T16:05:00+01:00
draft: false
---

The Dutch organisation [eth0](https://wiki.eth0.nl/index.php/Main_Page) has run a series of informal small camps over the years, never with an attendance too far into three figures, and without pre-planned events or entertainment. What happens is at the instigation of the attendees, and the result is a weekend of much closer socialising and working together on projects than the large camps where you spend your time running around to catch everything.

The largest of hacker camps offer all the lights, robots, tschunk, and techno music you can stomach; they can be a blast but also overwhelming. I made my way eth0 over the past week weekend, enjoying the more intimate size and coming away having made friendships from spending time with great people at a large private camping hostel near Lichtenvoorde. This is in the far east of the country near the German border, to which in the company of a British hardware hacker friend I traveled in the tiny European hatchback. Netherlands roads are so easy to navigate!

[![A prototype tensegrity structure. Image: Igor Nikolic.](https://hackaday.com/wp-content/uploads/2019/10/eth0-igor-tensegrity.jpg?w=354)](https://hackaday.com/wp-content/uploads/2019/10/eth0-igor-tensegrity.jpg)

A prototype tensegrity structure. Image: Igor Nikolic.

At the event was the usual array of activities, though since it was a restricted photography affair I’m short on wider shots that would include people. This year’s hit came from [surplus flipdot displays](https://twitter.com/FauthNiklas/status/1184974318784122880?s=20%EF%BF%BD) from retired German buses, with plenty of glitches as their quirks were figured out by our friends Nilkas Fauth and Jan Henrik. Something tells me I’ll be seeing a lot of those fluorescent circles in the future.

I’d brought along the nucleus of a textile village, and [RevSpace](https://revspace.nl/Main_Page) in the Hague had added their embroidery machine to my overlocker and sewing machines. Its operator was Boekenwuurm from [Hackalot](https://hackalot.nl/Hoofdpagina) in Eindhoven who was kind enough to embroider a Wrencher for me, and now I want one of these 600-Euro machines even if I can’t afford one. She and RevSpace’s Igor Nikolic were experimenting with inflatables and tensegrity structures, creating prototypes with an eye to more impressive installations at future camps.

An entertaining tale of a couple of days hanging out with friends in the Netherlands countryside could probably be spun into a reasonable tale, but there was something more interesting still at this camp. It had [a badge](https://github.com/badgeteam/eth0-2019-badge), courtesy of the prolific badge.team Dutch badge crew. It didn’t come with their trademark ESP32 firmware though, instead in keeping with the budget of the event it was a prototyping board on which attendees could create their own badges. What came forth from that was extremely impressive, and continued after the event.

A Badge For Creatives
---------------------

[![](https://hackaday.com/wp-content/uploads/2019/10/eth0-NR17-badge.jpg?w=250)](https://hackaday.com/2019/11/03/eth0-autumn-2019-tiny-camp-creative-badge/eth0-nr17-badge/) [![](https://hackaday.com/wp-content/uploads/2019/10/eth0-bernadski-badge.jpg?w=250)](https://hackaday.com/2019/11/03/eth0-autumn-2019-tiny-camp-creative-badge/eth0-bernadski-badge/) [![](https://hackaday.com/wp-content/uploads/2019/10/eth0-kartoffel-badge.jpg?w=212)](https://hackaday.com/2019/11/03/eth0-autumn-2019-tiny-camp-creative-badge/eth0-kartoffel-badge/)

The badge itself has an interesting layout, because aside from a bit of badge.team and event related artwork it uses a multipurpose layout from [Electronic Eel](https://github.com/electroniceel/protoboard), that’s designed for both SMD and through-hole parts. This proved to be extremely versatile, but came with the slight burden that the through-hole pads were closely surrounded by the ground plane, making soldering a bit tricky. Despite this there was an enthusiastic take-up from camp attendees, with offerings that went well beyond the mundane.

For the majority of the attendees there was a badge bar, with plentiful supplies of LEDs ad other components. Some attendees made do with a pair of colour changing LEDs and a CR2032, but others made CMOS astable oscillators using 4093 Schmitt AND gates for the full flashing effect. It’s almost unexpected today when so much is done by microcontrollers to see people hacking logic gate oscillators, but there was a circuit bending element to it all that made for a more enjoyable experience.

[![A fully functional event badge built upon an event badge. Fuchsia's Tamafoxi runs the badge.team firmware.](https://hackaday.com/wp-content/uploads/2019/10/eth0-tamafoxi-badge.jpg?w=400)](https://hackaday.com/wp-content/uploads/2019/10/eth0-tamafoxi-badge.jpg)

A fully functional event badge built upon an event badge. Fuchsia’s Tamafoxi runs the badge.team firmware.

One or two badges sported extra lighting in the form of Neopixels and similar. This staple of the LED badge is the obvious choice for one like the eth0 badge, even with its relative lack of space. The _piece de resistance_ of the eth0 winter 2019 badges though did not feature any LED lights, instead it came with a small OLED display and a set of buttons. Fuchsia’e [Tamafoxi](https://pixie.garden/~/Thingies/tamafoxi) is a fully functional tamagotchi clone that runs under [the badge.team badge firmware](https://github.com/badgeteam/ESP32-platform-firmware), for which a Wemos ESP32 board had been fitted to the back of the badge. Power wasn’t quite so elegant, requiring a small protoboard and LiPo cell sandwiched to the back of the badge, but for the feat of getting a badge that wouldn’t disgrace a much larger event running on what was in effect a fancy protoboard, we’ll forgive all that. Plenty of event badge teams have set out to achieve this level of functionality and not quite made it, so to do so on an event badge like this one is a very significant feat indeed.

This was a short camp by the standards of some others, starting on a Friday evening and wrapping up at Sunday lunchtime. We left in the drizzle of a damp autumn afternoon for the easy trip to the overnight ferry across the billiard-table-smooth Dutch motorways, without some of the stress of limited access while packing that comes with the larger camps. It had been everything we’d wanted from a small hacker camp and more, so speaking personally I’d certainly head back to this one if the opportunity arose.

This raises another point that [we’ve touched on before](https://hackaday.com/2019/06/15/the-smallest-hacker-camps-are-the-most-satisfying-and-you-can-do-one-too/) here at Hackaday. We Brits had gone to the Netherlands for eth0 because it was an opportunity to hang out with friends at a hacker camp, but also because in our part of the world there aren’t any events quite like it. But as our Dutch friends have proven, an event like this isn’t in the same league as one of the large camps when it comes to organising, and need not necessarily be impossible to put on. If you have a hankering for an event like eth0 you can always make your way to the Netherlands someday, but that’s not essential. Perhaps the best small event for you is one that you are part of organising wherever you come from.

  
  
from Hackaday https://ift.tt/2JIUu2q  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)