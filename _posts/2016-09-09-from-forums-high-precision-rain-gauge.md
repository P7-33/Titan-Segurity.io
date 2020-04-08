---
title: 'From the Forums: a high precision rain gauge #Adafruit @Adafruit'
date: 2019-09-26T14:18:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/09/Untitled-28.png)

Via the [Adafruit Forums](https://forums.adafruit.com/viewtopic.php?f=59&t=156729&p=772942#p772923), user Govner shares a build of a high precision rain gauge:

> I have never been happy with the resolution or operation of “rocker-type” rain gauges. Moving parts and constricted water entry openings are inevitable sources of problems. Why not have a no-moving-parts, water-proof detector. “Waterproof” ? How can that be? Enter stage left, a piezo crystal detection unit.
> 
> This unit is capable of counting rain drops at a rate (about 2 usec between drops, est.) that far exceeds the world’s record rainfall rate (Google: South America 1.5-inches/minute). In any case, my goal was not worrying about the fact that research assigns 1 uL/drop or some such thing. I just wanted to get the big picture so I could inhibit irrigation pumps when enough rain warranted that. And with a simple evaporation algorithm, re-enable the pumps. All control had to be wireless so I just added another NRF24L01+ 2.4Ghz transceiver ($2 USD) to my existing network. Piece of cake. I used a glass mason jar which is used for preserving foodstuffs and is completely waterproof. I used a glass one (as you can see) but plastic would have been easier for drilling the small hole in the bottom for DC power. I used a diamond drill bit and it took all of about 30 seconds. No biggie.
> 
> Happy to share anything/everything done on this project. I used Pro Mini, 4 piezo elements, differential amplifier, Buck power supply (I like the buffering between my solar panel system), BME280, NRF24L01, DS3231 RTC.
> 
> I just wire-wrapped the assembly on a PCB that I designed for general purposes like this. I recommend using electrical contact grease around the lip of the glass jar just to get a great, lasting seal. (That’s another reason why I chose not to use plastic. Glass has a far superior long-term reliability in this regard).
> 
> The unit works far better than I expected and has other applications. The processing speed is so nice that, when I did the “shower stall test”, I could increase the droplet rate and see the drop-to-drop LED response. At the maximum rate, the LED just can’t keep up with the rate and appears to be lit steady.

See the [forum post](https://forums.adafruit.com/viewtopic.php?f=59&t=156729&p=772942#p772923) for more and pictures below. Nice work!

![Completed_piezo_rainGuage.jpg](https://forums.adafruit.com/download/file.php?id=70374)

![Completed_PiezoRainGuage_nSolar.JPG](https://forums.adafruit.com/download/file.php?id=70376)