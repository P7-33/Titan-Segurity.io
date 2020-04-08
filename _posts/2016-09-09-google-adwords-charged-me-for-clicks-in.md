---
title: 'Google AdWords charged me for clicks in Istanbul while location-targeting the US'
date: 2019-11-30T01:49:00+01:00
draft: false
---

![](https://miro.medium.com/max/1000/1*rd89XPQOjSX9Kycxjv5sxQ.jpeg "Google AdWords charged me for clicks in Istanbul while location targeting the U.S.")  

Google AdWords charged me for clicks in Istanbul while location targeting the U.S.
==================================================================================

Three months ago, I [quit my job](https://medium.com/@siggi/what-ive-been-building-since-leaving-google-8512ef7e25e2) at Google to start my own company. This past week, I decided that I wanted to get a feel for how much it would cost to acquire new users for our app through paid channels. Having been a Googler for over 5 years (2 of which were as a software engineer on the AdWords team), my instinct was to start with Google Ads.

I set up a small search campaign to drive traffic to my subscription page. After what seemed like an eternity waiting for approval on my creatives, my ads were serving and I was ready to go.

My past 3 months have been spent building [an app](http://usehyperlink.com/) that lets you get push notifications when your links get clicked on, so I was excited to start receiving push notifications as the AdWords traffic started to roll in. I put unique url parameters in my creatives so I could distinguish this ad traffic from organic visitors.

I waited — excitedly checking my phone for notifications with the ref=adwords url parameter. A few hours went by and then, when I was least expecting it, I got my first click!

Two more clicks quickly followed. I was excited that my notifications were working properly — but was confused to see that all 3 of the notifications said the clicks came from **Istanbul**.

The location I display in the notification come from Google’s own GCP [request headers](https://cloud.google.com/load-balancing/docs/user-defined-request-headers) which are determined based on the users IP address. My initial reaction was that I must have forgotten to enable location targeting, so I quickly opened up AdWords and checked the settings tab.

The location settings were there — I was only targeting the United States. I was also a little shocked that I was **charged** for all three of those clicks, given that all three of them came from the same IP address in Turkey in very quick succession.

I asked a friend who’d spent more time than I implementing AdWords campaigns what he thought about this (in the meantime, I got a notification for another AdWords click from **Kafr Abu Sir, Egypt**). He mentioned there were some advanced location settings that I should check out. I dug into the advanced Location settings and discovered these three options.

None of these three options would give me the targeting settings that I want (U.S. only). There is enough wiggle-room in the wording of each of these options that I could still be charged for clicks in Turkey and Egypt.

So this is my warning to my fellow advertisers out there — if you think you’re only targeting certain locations, you’re probably getting clicks from outside of those locations. I have a strategy in mind that I might try out if this remains such a high percentage of my clicks (still currently at 100%, but a small sample size). It involves manually going in and excluding all of the countries that are not the United Sates. In the meantime, I’m going to be keeping a close eye on my ad clicks that are coming in with [Hyperlink](http://usehyperlink.com/).

And to the folks back on the AdWords team, it’d be great if there was an option to respect the location targeting settings that we select. At the very least, it seems like the default option shouldn’t allow for such a high percentage of clicks to come from outside of the targeted countries.

  
  
from Hacker News https://ift.tt/2q3npHU