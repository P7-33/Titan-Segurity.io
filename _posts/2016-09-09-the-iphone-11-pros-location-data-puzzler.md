---
title: 'The iPhone 11 Pro’s Location Data Puzzler'
date: 2019-12-04T06:25:00+01:00
draft: false
---

One of the more curious behaviors of Apple’s new **iPhone 11 Pro** is that it intermittently seeks the user’s location information even when all applications and system services on the phone are individually set to never request this data. Apple says this is by design, but that response seems at odds with the company’s own privacy policy.

The privacy policy available from the iPhone’s Location Services screen says, “If Location Services is on, your iPhone will periodically send the geo-tagged locations of nearby Wi-Fi hotspots and cell towers (where supported by a device) in an anonymous and encrypted form to Apple, to be used for augmenting this crowd-sourced database of Wi-Fi hotspot and cell tower locations.”

The policy explains users can disable all location services entirely with one swipe (by navigating to Settings > Privacy > Location Services, then switching “Location Services” to “off”). When one does this, the location services indicator — a small diagonal upward arrow to the left of the battery icon — no longer appears unless Location Services is re-enabled.

The policy continues: “You can also disable location-based system services by tapping on System Services and turning off each location-based system service.” But apparently there are some system services on this model (and possibly [other iPhone 11 models](https://www.macworld.com/article/3437999/iphone-11-vs-iphone-11-prosspecs-features-colors-price.html)) which request location data and cannot be disabled by users without completely turning off location services, as the arrow icon still appears periodically even after individually disabling all system services that use location.

On Nov. 13, KrebsOnSecurity contacted Apple to report this as a possible privacy bug in the new iPhone Pro and/or in iOS 13.x, sharing a video showing how the device still seeks the user’s location when each app and system service is set to “never” request location information (but with the main Location Data service still turned on).

VIDEO

The video above was recorded on a brand new iPhone 11 Pro. The behavior appears to persist in the latest iPhone operating system (iOS 13.2.3) on iPhone 11 Pro devices. A review of Apple’s support forum indicates other users [are experiencing the same issue](https://discussions.apple.com/thread/250665845). I was not able replicate this behavior on an older model iPhone 8 with the latest iOS.

This week Apple responded that the company does not see any concerns here and that the iPhone was performing as designed.

“We do not see any actual security implications,” an Apple engineer wrote in a response to KrebsOnSecurity. “It is expected behavior that the Location Services icon appears in the status bar when Location Services is enabled. _The icon appears for system services that do not have a switch in Settings” _\[emphasis added\].

Apple has not yet responded to follow-up questions, but it seems they are saying their phones have some system services that query your location regardless of whether one has disabled this setting individually for all apps and iOS system services.

Granted, the latest versions of iOS give users far more granular control over the sharing of this data [than in the past](https://appletoolbox.com/why-is-my-iphones-location-services-icon-is-always-on/), especially with respect to third-party apps. And perhaps this oddity is somehow related to [adding support for super-fast new WiFi 6 routers](https://www.wi-fi.org/discover-wi-fi/wi-fi-certified-6), which may have involved the introduction of new hardware.

But it would be nice to know what has changed in the iPhone 11 and why, particularly given Apple’s [recent commercials](https://www.youtube.com/watch?v=Py0acqg1oKc) on how they respect user privacy choices — including location information. This post will be updated in the event Apple provides a more detailed response.

[![](https://krebsonsecurity.com/b-akamai/15.jpg)](https://www.akamai.com/us/en/security.jsp?utm_source=krebsonsecurity&utm_medium=display&utm_id=F-MC-44701&utm_campaign=unifiedsecurity_digital_2019&utm_content=unifiedsecurity_global&utm_term=unifiedsecurity_ros)

Tags: [Apple iPhone 11 Pro](https://krebsonsecurity.com/tag/apple-iphone-11-pro/), [location privacy](https://krebsonsecurity.com/tag/location-privacy/), [location services](https://krebsonsecurity.com/tag/location-services/)

This entry was posted on Tuesday, December 3rd, 2019 at 10:51 pm and is filed under [A Little Sunshine](https://krebsonsecurity.com/category/sunshine/).  
You can follow any comments to this entry through the [RSS 2.0](https://krebsonsecurity.com/2019/12/the-iphone-11-pros-location-data-puzzler/feed/) feed.  
  
You can skip to the end and leave a comment. Pinging is currently not allowed.

  
  
from Hacker News https://ift.tt/2qhQ63X