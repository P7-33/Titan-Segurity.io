---
title: 'DigiKey performs a $17 bench power supply
teardown #PowerSupply #Safety @Digikey'
date: 2019-10-17T17:11:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-67.png)

[Digikey documents](https://www.digikey.com/eewiki/pages/viewpage.action?pageId=90243471) a thorough analysis tearing down and analyzing a $17 Best model PS-1502DD power supply.

> The old axiom “you get what you pay for” is often invoked in discussions of product quality.  It can also inspire curiosity as to what exactly one does get when the price paid for a product is significantly less than asked by others having comparable basic specifications.
> 
> It was this spirit of curiosity that led a colleague to purchase a bench-type adjustable power supply, advertising a 0-15V, 0-2A output from a low-cost supplier for all of $17 USD.  What exactly does that buy a person?  Let’s find out.
> 
> _After completing this write-up, it was found that this same supply is available under maybe a half dozen different brand names, at price points ranging from the $17 USD range mentioned to upwards of $50 USD.  Numerous resources are available demonstrating the basic functionality of the device; this article focuses more on reasons that a person might want to consider spending more on a device of this type._

The standard tests are performed first including output voltage and current and safety tests. The ground was not a true earth ground as the non-polarized European 220V plug had no ground connection.

![](https://www.digikey.com/eewiki/download/attachments/90243471/image2019-9-20_17-47-9.png?version=1&modificationDate=1569019629352&api=v2)

Testing showed some prominent safety concerns:

> (The unit has) single-line fusing in conjunction with that symmetric, reversible AC input plug.  There’s only a 50/50 chance of the fuse being connected between the “hot” line and the appliance, so should an AC-to chassis fault occur, there’s only a 50% chance that the fuse would be in a position to provide any protective effect at all.  In the case where the plug is connected so as to put the fuse in series with the neutral AC conductor, the fuse opening during a fault condition might actually cause an increased hazard, since its doing so would eliminate the only “safe” current return path available.  The diagram at right shows the path of current flow should an AC to chassis fault occur in the supply in question.  Note that the fuse isn’t even part of the current path in this scenario.

Digikey dives into the ripple and other electrical characteristics. They also find some decent features.

[See the whole article for their findings](https://www.digikey.com/eewiki/pages/viewpage.action?pageId=90243471).

_Editor’s Note: In the Adafruit store, Engineer Limor “Ladyada” Fried has personally tested all items, especially electronics like test equipment, to ensure they meet her strict standards. Shopping the [Adafruit store](https://www.adafruit.com/) provides the company assurance of quality and performance._