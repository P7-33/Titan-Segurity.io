---
title: 'Prusa Unveils New Mini 3D Printer, Shakes Up The Competition'
date: 2019-10-13T15:04:00+01:00
draft: false
---

For the last couple of years, consumer desktop 3D printer choices in the under $1,000 USD range have fallen into two broad categories: everything bellow $500 USD, and the latest Prusa i3. There are plenty of respectable printers made by companies such as Monoprice and Creality to choose from on that lower end of the scale. It wasn’t a luxury everyone could justify, but if you had the budget to swing the $749 for Prusa’s i3 kit, the choice became obvious.

Of course, that was before the Prusa Mini. [Available as a kit for just $349](https://www.prusa3d.com/original-prusa-mini/), it’s far and away the cheapest printer that Prusa Research has ever offered. But this isn’t just some rebranded hardware, and it doesn’t compromise on the ideals that have made the company’s flagship machine the de facto open source FDM printer. For less than half the cost of the i3 MK3S, you’re not only getting most of the larger printer’s best features and Prusa’s renowned customer support, but even capabilities that presumably won’t make it to the i3 line until the MK4 is released.

Josef Průša was on hand to officially unveil his latest printer [at the 2019 East Coast Reprap Festival](http://eastcoastreprapfestival.com/), where I got the chance to get up close and personal with the diminutive machine. While it might be awhile before we can do a full review on the Mini, it’s safe to say that this small printer is going to have a big impact on the entry-level market.

A Simplified Design
-------------------

Considering the huge price drop, you might expect the Prusa Mini to have removed many of the features that made the recent entries into the i3 family so popular. But for the most part, the Mini should deliver more or less the same experience Prusa owners have come to expect.

[![](https://hackaday.com/wp-content/uploads/2019/10/miniprusa_extruder.jpg?w=536)](https://hackaday.com/wp-content/uploads/2019/10/miniprusa_extruder.jpg)

The Prusa Mini uses a 3:1 geared Bowden extruder

That means automatic mesh bed leveling via inductive probe, a magnetic spring steel print bed (in both smooth and textured variants), near-silent operation thanks to the Trinamic stepper drivers, [out of the box support in PrusaSlicer](https://hackaday.com/2019/05/24/3d-printering-the-past-and-future-of-prusas-slicer/), and the self-checks and safety features that far too often are missing on lower-cost printers.

Of course, there has to be some cuts somewhere. For one, the Prusa Mini does away with the sensor (though it’s available as an option) that pauses the printer if it runs out of filament. [This was one of the key upgrades made in the i3 MK3](https://hackaday.com/2018/10/22/a-close-look-at-the-prusa-i3-mk3/), and is undeniably a nice feature to have on long prints. But considering how few other printers even offer this capability, the fact that it doesn’t come standard on the Mini certainly doesn’t put it at a disadvantage. The fact that it’s even available as an official option and not something you have to hack together yourself is actually an improvement over other printers in this price range.

To reduce weight, the Prusa Mini also switches from a direct drive to a Bowden style extruder. Again, this is not particularly unusual at this price, and is very reminiscent of the [arrangement used on the Monoprice Mini](https://hackaday.com/2016/06/13/review-monoprice-mp-select-mini-3d-printer/). But it will certainly be an adjustment for Prusa owners that are used to a direct drive extruder. For example, Bowden extruders tend to be somewhat more finicky and are notoriously difficult to get working with flexible filaments. Incidentally, the switch to a Bowden extruder also means the Prusa Mini is not compatible with the company’s Multi Material Upgrade (MMU).

Finally, it’s worth noting that the Prusa Mini forgoes an integrated power supply and instead uses a laptop-style “power brick”. While a somewhat unglamorous change, this isn’t likely to be a deal-breaker for anyone. But certainly something to consider when thinking of where you’ll put the machine, or when designing an enclosure for it.

[![](https://hackaday.com/wp-content/uploads/2019/10/miniprusa_psu.jpg?w=800)](https://hackaday.com/wp-content/uploads/2019/10/miniprusa_psu.jpg)

Printrbot called, they want their power supplies back.

Now You’re Playing with Power
-----------------------------

While the mechanical aspects of the Prusa Mini have been simplified compared to its larger predecessor, the electronics have gone in the opposite direction. At least in that respect, the new printer is actually quite a bit more advanced than the i3 MK3S. It stands to reason that the Mini will serve as something of a test bed for the electronics that will go into the next generation of Prusa printers, so perspective buyers would be wise to expect some growing pains.

[![](https://hackaday.com/wp-content/uploads/2019/10/miniprusa_display.jpg?w=361)](https://hackaday.com/wp-content/uploads/2019/10/miniprusa_display.jpg)

The display is bright and easily visible from a distance.

The Mini features a completely revamped control board and accompanying user interface. The new 32-bit ARM STM32F407 equipped “Buddy” controller is vastly more powerful than the 8-bit board Prusa uses in the i3, and thanks to its onboard Ethernet and USB, can perform all the tasks you’d currently have to do with a Raspberry Pi running OctoPrint.

Or at least, it will in the future. Prusa says those more advanced features, including webcam support, are coming down the line as a software update. Speaking of which, the Buddy board is able to pull its own firmware updates down over the Internet; so no more plugging it into the computer to manually flash the latest hex file. With the DIY addition of an ESP module, it’ll even be able to do that over WiFi.

Increased computational capabilities in the controller also enable some relatively flashy graphics on the printer’s 2.8 inch LCD. Not only does the 320×240 screen look worlds better than the i3’s rather dated display during normal operation, but it allows for 3D rendered previews of the selected STL. Users will be able to visually confirm what they’re about to print, rather than having to remember the file name of a particular object.

Though for all the new capabilities of the Buddy board, there is at least one omission that long-time Prusa owners might find odd: there’s no support for SD cards. STLs are now loaded either over the network or from USB Mass Storage. Arguably this is an improvement, but still somewhat unexpected given that nearly every desktop 3D printer since the MakerBot Cupcake has had an SD slot.

A New Member of the Family
--------------------------

One thing made abundantly clear was that the Prusa Mini is not intended to compete with the i3 line, much less serve as a replacement for it. Josef Průša says that the i3 MK3S is still going strong, and will continue to be updated as time goes on. He also says the team is working on a new CoreXY printer codenamed “Prusa XL”, but that we’ll have to wait until next year before we see anything concrete on that one.

The Mini is envisioned as an ideal starter printer, or perhaps even as a secondary printer so you can start tackling big jobs in parallel. Prusa says its small size and integrated remote control capabilities also make it an ideal choice for print farms. Whatever people will be buying them for, at this price, we expect the Prusa Mini is going to be in high demand for the foreseeable future.

  
  
from Hackaday https://ift.tt/2ottv3L  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)