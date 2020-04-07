---
title: 'Happy 50th Birthday to All You Epoch Birthers'
date: 2020-01-01T16:17:00+01:00
draft: false
---

Good morning everyone, and what a lovely start to the new year it is, because it’s your birthday! Happy birthday, it’s your 50th! What’s that you say, you aren’t 50 today? (Looks…) That’s what all these internet databases say, because you’ve spent the last decade or so putting 1970-01-01 as your birth date into every online form that doesn’t really need to know it!

It’s been a staple for a subset of our community for years, to put the UNIX epoch, January 1st 1970, into web forms as a birth date. There are even rumours that some sites now won’t accept that date as a birthday, such is the volume of false entries they have with that date. It’s worth taking a minute though to consider UNIX time, some of its history and how its storage has changed over the years.

Don’t Use Up That 32 Bit Int Too Quickly
----------------------------------------

[![How doyou turn a 1960s minicomputer into a clock? Digital pdp8f.jpg: Simon Claessen from The Netherlandsderivative work: User:Clusternote [CC BY-SA 3.0]](https://hackaday.com/wp-content/uploads/2020/01/1280px-Digital_PDP-8F.jpg?w=800)](https://hackaday.com/wp-content/uploads/2020/01/1280px-Digital_PDP-8F.jpg)

How do you turn a 1960s minicomputer into a clock? Digital pdp8f.jpg: Simon Claessen \[[CC BY-SA 3.0](https://commons.wikimedia.org/wiki/File:Digital_PDP-8F.jpg)\]

Most readers will be familiar with the UNIX timestamp that the date command will return on UNIX-like operating systems. It’s an integer value representing the number of whole seconds that have elapsed since January 1st 1970, and it’s easy enough to write a little script that scrolls it up the screen so you can watch it increment second by second. But the interesting things about it are that the epoch date preceded its inception by several years, and the earliest UNIX versions used a rather different timing system.

We’re used to generating any clock signal we please using any of a huge number of available clock chips. If we need an odd frequency, there will be a PLL chip somewhere that can do it. In the early 1970s though the designers of the DEC minicomputers used by those primordial UNIX developers did not have that luxury, as complex clock generation would have required costly extra logic chips. The earliest UNIX time was thus measured in terms of the American mains power frequency,  60ths of a second with an epoch at the start of 1971. Since a 32 bit number at that rate would have meant a very short time before roll-over it was decided to use seconds instead with an epoch at the start of the decade. The latest distributions might have switched to using a 64-bit integer because the original 32-bit one would roll over in 2038, but otherwise the timing scheme remains unchanged.

Face It, We’re All Growing Older One Second At A Time
-----------------------------------------------------

The 50-year anniversary, whether real or assumed, hides another impact of that early UNIX. For our youngest readers it’s possible that the start of the 1970s now represents as remote a date as possible, but for many adults it has still been possible to cling to the notion that it’s not too long ago even if we weren’t personally around to see it. The five-decade mark is a definitive point that puts it firmly in the historical, and should remind us that [UNIX is no longer the relative new kid it might have been when we first used it](https://hackaday.com/2019/11/05/will-the-real-unix-please-stand-up/).

You can still get away with claiming it for a fake birthday (at least for a a few more decades) perhaps it’s time to reflect that much of the technology we like to think of as cutting-edge and exciting is in fact now mature  and middle-aged. It’s likely we’ll be still measuring time in some way from the same UNIX epoch in a century’s time, and by then how shall we express a fake birthday?

  
  
from Hackaday https://ift.tt/37sjV1H  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)