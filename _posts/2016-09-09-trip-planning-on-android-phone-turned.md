---
title: 'Trip planning on Android phone turned off for now'
date: 2019-11-05T05:29:00+01:00
draft: false
---

![](https://s0.wp.com/i/blank.jpg "Trip planning on Android phone turned off for now – OneBusAway")  

**tl;dr:**

**What** – Until further notice, we need to turn off trip planning in OneBusAway on Android.

**Why** – Google is charging our non-profit ~$1,000 every month to provide this feature to you and rejected our request for credits because OneBusAway “recreates Google Products or Services.” The OneBusAway app is free to download, volunteer-supported, and doesn’t show you ads or sell your data – as a result, we can’t afford this cost. We’ve tried appealing to Google in as many ways as we can, but have run out of options.

**What’s next** – We are working on finding an alternative to Google’s Places API geocoding service, which converts street addresses into machine-readable latitude/longitude coordinates.

Please read on if you’re interested in more details.

It has been exciting to see OneBusAway grow from a small graduate student effort at the University of Washington to a fully-fledged open-source project that has served over a million users around the world. The [OneBusAway Open-Source Project](https://onebusaway.org), which provides real-time transit information to several cities, including Seattle, Tampa, San Diego, and Washington, D.C., with around 300,000 active users of the native Android and iOS apps, split approximately evenly between the two platforms. OneBusAway has blossomed in a valuable tool for transit riders and researchers trying to better understand the impact of technology on transportation.

In 2019, the OneBusAway community took an important step to create a permanent home for the project – the creation of the non-profit Open Transit Software Foundation (OTSF). This organization consists of members from transit agencies, research universities, companies, non-profits, and individuals who all have the common goal of making transit easier to use. While the creation of an official non-profit is an exciting step for the project, unfortunately 2019 brings some bad news too – we’re going to need to say goodbye to a feature, at least temporarily. Let’s rewind to explain.

In early 2016, contributors to the OneBusAway Android app added the trip planning feature. In the design process, the team was careful to select components to minimize ongoing costs, as no budget for operating expenses was available. To translate points-of-interest names (e.g. “Airport”) and addresses (e.g., “1234 Anywhere Dr.”), the team selected the Google Places SDK, which was free to use for Android apps. In 2017, the Google Summer of Code program sponsored the [addition of bike-share to OneBusAway](https://medium.com/@sjbarbeau/bike-share-launches-in-onebusaway-3452c08c0ed)), making OneBusAway one of the first native apps to offer true multimodal trip planning.

In 2019, Google decided to start charging for use of the Places SDK on Android – a cost of around $35 per day (around $1000 per month). We pleaded our case to Google and were directed to apply to the Google for Nonprofits program (https://ift.tt/2CfiTsp). Several transit agencies funded the incorporation of the Open Transit Software Foundation 501(c)(3) in the state of Washington and submitted the non-profit application to Google. In the meantime, Google’s new pricing went into effect on July 29, 2019. We shut down the trip planner during this time while waiting for approval to avoid racking up additional charges that we couldn’t afford.

On September 19, Google admitted OTSF to Google for Nonprofits and approved our request for credits for the Places SDK. At this point we turned the trip planner back on, thinking the problem was solved.

But the credits never showed up in our account. When we asked Google about this, they asked that we submit another request for the credits. We did, and got back a response on October 11th denying our request, saying:

> _This request is rejected because this app violates our terms of service (https://ift.tt/2HSbnZD)._

…pointing to:

> _3.2.4 Restrictions Against Misusing the Services (d) No Re-Creating Google Products or Features. Customer will not use the Services to create a product or service with features that are substantially similar to or that re-create the features of another Google product or service. Customer’s product or service must contain substantial, independent value and features beyond the Google products or services._

Given that OneBusAway featured real-time transit information and multimodal trip planning long before Google Maps, we are extremely disappointed in Google’s decision. Furthermore, OneBusAway is a laboratory for experimental new features and research studies showing how riders benefit from real-time information, which Google and other apps often use to convince transit agencies to share their real-time data publicly. OneBusAway was never designed to be a competitor to Google Maps or other 3rd party applications – it was created to advance the state-of-the-art in the public transportation industry.

As a result of Google’s decision, we are unfortunately shutting down the trip planning feature in OneBusAway Android until we can evaluate affordable geocoding options. We are just as disappointed as you in this development – in the last 30 days, approximately 7,300 users have planned over 2.3 million trips using OneBusAway.

If you’d like to express your support for OneBusAway to Google, please feel free to reach out to [Google Maps on Twitter](https://twitter.com/googlemaps?s=17).

Sincerely,  
Kari Watkins  
Chair, Open Transit Software Foundation

  
  
from Hacker News https://ift.tt/362kHm5