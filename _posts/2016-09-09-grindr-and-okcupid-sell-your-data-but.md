---
title: 'Grindr and OKCupid Sell Your Data, but Twitter’s MoPub Is the Real Problem'
date: 2020-01-28T04:12:00+01:00
draft: false
---

On January 15, a [Norweigian Consumer Council (NCC) investigative report](https://www.forbrukerradet.no/out-of-control/#GDPR) exposed the ways that Grindr, OKCupid, and eight other apps are collecting and sharing extremely sensitive personal data. Grindr in particular was sharing users’ age and location tied to a [_device ID_](https://www.eff.org/wp/behind-the-one-way-mirror#AdvertisingIDs) that would allow trackers to match that information to a real identity.

A third-party advertising company called MoPub, owned by Twitter, was responsible for much of the technology that Grindr used to collect and share data. In response to the NCC report, Twitter [announced](https://adage.com/article/digital/twitter-suspends-grindr-its-ad-platform-it-investigates-privacy-concerns/2227116) that it was suspending Grindr’s ad account pending an investigation into “the sufficiency of Grindr’s consent mechanism.”

Let’s be clear: Grindr was in the wrong. It built a platform that encourages people to be exceptionally open with sensitive, potentially dangerous personal information, then it invited third-party advertisers to harvest and share much of that data with impunity. Twitter likely hopes to paint Grindr as an anomaly, a single bad actor misusing its tracking technology which will be disciplined appropriately. But Twitter’s suspension of Grindr is hypocritical: Grindr was using Twitter’s ad tools almost exactly as intended. Moreover, Grindr is just one of over 55,000 apps using MoPub to collect and share data. When we formulate policy responses to the privacy violations exposed by the NCC report, we need to focus on the adtech systems like MoPub that enable companies like Grindr.

MoPub operates in the vast, convoluted, opaque ecosystem of personal data collection and sharing that powers modern adtech. To understand how that ecosystem works and where Grindr and MoPub fit in, we need to talk about [real-time bidding](https://www.eff.org/wp/behind-the-one-way-mirror#Real-time-bidding), or RTB.  

RTB is the automatic, milliseconds-long data-sharing frenzy that occurs whenever you see a third-party ad on one of your devices. First, an app developer, like Grindr, decides it wants to monetize its app. To do so, it partners with a Supply-Side Platform (SSP) like MoPub. SSPs are companies that app developers and website publishers hire to sell their advertising space. When you install the Grindr app on your phone, part of what you get is a big chunk of code from MoPub, called a [software development kit (SDK)](https://developers.mopub.com/publishers/android/). After some initial configuration, Grindr leaves the details of sharing data and serving ads up to MoPub.

When a user opens the Grindr app, code from the MoPub SDK kicks into action. The process looks like this:

1.  The SDK gathers as much data as it can about the user’s phone. This may include the phone’s advertising ID, its precise GPS-derived location, and data from Grindr itself, like age and gender. The app directs the user's phone to send all this information to MoPub.
2.  MoPub links the data it got from Grindr with what it knows about the user from other sources. This includes the 55,000 other apps that use MoPub, such as The Weather Channel app, Ubisoft games, and Ask.fm.
3.  MoPub packages this data into a “[bid request](https://developers.mopub.com/dsps/integration/openrtb/#3-bid-request-variables--definitions),” a standardized dossier about the user that includes device ID, location, gender, age, and interest keywords.
4.  MoPub sends the bid request to dozens or even hundreds of demand-side platforms (DSPs). DSPs are companies which advertisers hire in order to target and serve their ads, such as Criteo, Rocketfuel, and AppNexus. You may not have heard of them, but those and hundreds of other DSPs have probably handled a lot of your personal information. MoPub partners with over 130 different DSPs, [listed here](https://www.mopub.com/legal/partners/).
5.  Each DSP that receives the bid request can link the included device ID to its own profile of the user, or purchase additional information about the user from data brokers like LiveRamp.
6.  Each DSP submits a bid to serve an ad to that particular user at that particular time.
7.  MoPub determines the winning bidder and notifies all participants in the auction.
8.  The winning advertiser serves its ad to the user’s phone. Often, the ad itself allows the advertiser to collect even more information directly from the device.

_![A diagram shows a mobile phone on the left, a computer scree in the center labeled ](https://www.eff.org/files/2020/01/27/mopub_rtb.png)_

_A diagram from MoPub’s website showing a simplified view of the real-time bidding process._

All of this happens in a fraction of a second. MoPub boasts that its software reaches over 55,000 apps and 1.4 billion devices worldwide.

So while Grindr’s actions definitely violated users’ privacy, it was using MoPub as intended. Twitter’s suspension of Grindr’s ad account pending “investigation” is an attempt to deflect blame, and lawmakers shouldn’t be fooled. MoPub is still operating at full tilt, harvesting and sharing sensitive personal data in at least 54,999 other apps.  

To fix the problems raised by the NCC’s report, we need to fix the adtech ecosystem as a whole. That means [laws](https://www.eff.org/deeplinks/2019/06/effs-recommendations-consumer-data-privacy-laws) that give users the right to know what happens to their data, freedom from processing of their data unless they expressly opt-in, and [minimization](https://www.eff.org/deeplinks/2019/05/consumer-data-privacy-advocates-senate-committee-heres-how-protect-consumers) of processing beyond what the user asked for. These laws must let people [sue companies when their rights are violated](https://www.eff.org/deeplinks/2019/01/you-should-have-right-sue-companies-violate-your-privacy). A better adtech paradigm is possible, but only with strong, enforceable laws to rein in the industry's current privacy-invasive practices.  

  
  
from Hacker News https://ift.tt/36u7UrO