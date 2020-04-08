---
title: 'Burned-Out Flash Trips Up Older Teslas'
date: 2019-11-29T04:24:00+01:00
draft: false
---

According to several Tesla repair professionals, the embedded NAND-based eMMC memory found in older Model S, X units are wearing out and bricking the in-vehicle displays. With the Flash memory down, drivers no longer have access to some of the vehicle's features, including climate control, autopilot, and lighting control. While owners can still technically drive the affected EVs (electric vehicles), they will not be able to charge them, effectively making the cars inoperative.

The problem with the embedded eMMC chips is that they regularly update Tesla’s vehicle logs, and over time, the storage medium begins to lose space and thus will have to overwrite new data over the old. These constant updates wear out the Flash memory faster than normally expected, which ultimately leads to failure. 

The issue has been known since May of this year when a YouTube video popped-up from [Rich Benoit](https://youtu.be/o-7b1waoj9Q) (Tesla repair specialist) who interviewed Phil Sadow (another Tesla specialist) on the matter. In the video, Phil states, “Well, Tesla’s got a problem. On these things, there’s a chip here called an eMMC, and it’s basically an SSD drive, like a Flash drive, or like in your Android phone you can find the same thing. They create so many logs in the car, they write to the chip so fast that it burns them out.”

VIDEO

According to an article from [InsideEVs](https://insideevs.com/news/376037/tesla-mcu-emmc-memory-issue/) in October, that eMMC issue continued to be a growing problem as reports from three Tesla repair professionals at several different locations- Jason Hughes (@ [057 Technology](https://057tech.com/), North Carolina), Robert Cotran (@ [Cotran Consulting](https://057tech.com/), Quebec), and Pete Gruber (@ [Gruber Motors](https://gruberpower.com/ev-performance-products), Arizona) experienced the same issue concerning the memory on the MCUv1 (Media Control Unit).

![Tesla, early model](https://m.eet.com/media/1314430/TeslaSX.jpg)

_The embedded eMMC Flash storage in  
older Tesla Model S and X units are failing  
due to constant log updates, which causes  
a myriad of problems, including the ability  
to charge the vehicle. (Source: Tesla)_

The problem became compounded when new firmware updates were introduced that brought additional features to the EVs, which acted as fuel to further fire on the wearing progress. The firmware wasn’t an issue at the beginning, the logged data had plenty of memory to handle the load, but each firmware upgrade brought new features along with it, lessening the amount of storage space via each update. Flash memory in any form (eMMC, NAND, NOR, etc.) are only rated for a finite amount of write cycles (program/erase cycles), with most commercial offerings estimated at [100,000](http://www.ni.com/product-documentation/10126/en/) before becoming unreliable.

The MCUv1 units supplied for the Tesla Model S and X, up until 2018, feature an Nvidia Tegra Arm-based SoC with 8Gb of eMMC integrated into the same board, which is hosted on a mainboard. Tesla’s firmware size over the years went from a paltry 300Mb to a full 1Gb over an estimated four year period, which consumes much of the storage space in that Flash. Add on the constant vehicle log updates, and the failure rate of those chips increased exponentially.

The firmware is essentially competing for space with data logs, and when that happens, the Flash controller uses a mechanism known as wear-leveling technique that spreads out write operations across the chip instead of in isolated sectors. It’s intended to extend the number of write cycles of the memory before it becomes degraded. Tesla’s firmware utilizes nearly 100% of that space available, so it’s almost impossible to use wear-leveling for the vehicle logs.

When eMMC failure occurs, Tesla replaces the entire MCU if it’s still under its warranty period, and if it no longer is, it’s up to the owner to pay for a replacement, which can cost up to $1,800 at Tesla’s service centers for parts and labor. This brings another problem, as most Tesla service centers have limited stock on parts for older models, and independent Tesla repair professionals usually have to rely on salvaged parts from wrecks.

![Twitter capture](https://m.eet.com/media/1314435/Twittercapture2019Teslastory.png)

_Independent Tesla repair professional Jason Hughes tweeted Elon Musk  
about the eMMC wear problem, to which Elon replied that the issue  
“should be much better now.” (Image credit: Jason Hughes via Twitter)_

Hughes took to Twitter to address that fact in an October [Tweet](https://twitter.com/wk057/status/1182047438577774593) stating, “In the past month I've done repairs/replacements on over a dozen [@Tesla](https://twitter.com/Tesla) MCUv1 units for customers suffering from eMMC flash failure. [@elonmusk](https://twitter.com/elonmusk), you really need to tell the engineers to fix the logging wear in /var. It's literally killing a huge percentage of these units.” It’s unknown how many Tesla Model S and X owners have encountered this issue if it’s widespread or just a few isolated incidents. Tesla has yet to make a public statement on the matter, however Tesla CEO Elon Musk did reply to Hughes Tweet stating, “Should be much better at this point.” 

  
  
from Hacker News https://ift.tt/2Y35jCF