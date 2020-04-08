---
title: 'CloudFlare is ruining the internet for me'
date: 2019-10-06T05:36:00+01:00
draft: false
---

[CloudFlare](https://www.cloudflare.com/) is a very helpful service if you are a website owner and don’t want to deal with separate services for CDN, DNS, basic DDOS protection and other (superficial) security needs. You can have all these services in a one stop shop and you can have it all for free. It’s hard to pass up the offer and go for a commercial solution. Generally speaking, CloudFlare service is as stable as they come, their downtime and service interruption are within the same margin as other similar services, at least to my experience. I know this because I have used them for two of my other websites, until recently.

But what about the users? If you live in a First World Country then for the most part you probably wouldn’t notice much difference, other than better speed and response time for the websites using CloudFlare services, you will be happy to know that because of their [multiple datacenter locations](https://www.cloudflare.com/network-map/) mostly in USA, Canada, Europe and China, short downtimes won’t result in service interruptions for you because you will be automatically rerouted to their nearest CloudFlare data center and they have plenty to go around within the first world countries.

But what about the rest of us? I can only talk about my experience, I live in South East Asia (SEA). As it is normally the case for us we are treated as second class citizens on the Internet, often most premium, and sometimes freemium services, are limited to developed nations. We have to resort of Proxies and VPNs to enjoy the same freedom internet users from developed nations are used to. But other than that, for the most part, we enjoy the same basic internet freedom as rest of the most of the world. Unless of course your website is using CloudFlare services.

![cloudflare-facebook](https://i1.wp.com/www.slashgeek.net/wp-content/uploads/2016/05/cloudflare-facebook.png?resize=486%2C376)

You see CloudFlare has these [“Security” features](https://support.cloudflare.com/hc/en-us/articles/203366080-Why-do-I-see-a-captcha-or-challenge-page-Attention-Required-trying-to-visit-a-site-protected-by-CloudFlare-as-a-site-visitor-) which can prompt users belonging to certain IP blocks, countries, blacklists or behavioral patterns and either automatically block you to visit some sites (rare, but often done by Site Owners discretion) or prompt you for [reCAPTCHA](https://www.google.com/recaptcha/intro/index.html) (much better than the ridiculous captcha they had before), before you can visit the site. reCAPTCHA prompts happens a lot, I know its only one click away, but we shouldn’t have to deal with this annoying pseudo security measure. The entirety of the StackExchange sites is under CloudFlare firewall. As it is often the case, a lot of my searches often end up to one of the StackExchange sites and if I visit the link through Google search results I am prompted for captcha, but curiously I don’t get prompted if I directly visit the site. I wish it was only limited to StackExchange, because of CloudFlare’s ludicrous free one-stop shop offering and their [aggressive partnership with cheap hosting service](https://www.cloudflare.com/hosting-partners/), every joe with a website is using CloudFlare. So that one click per site per day often results in 30-40 clicks per day or more.

I wish it was something to do with only my IP. You see I co-own an ISP, we have four /22 IP blocks (4096 IPs) while I didn’t get a chance to test all our IPs but all of them I have personally checked (about 500+) over the last year gets prompted for captchas. It’s not only limited to our IP blocks, It happens on my phone when I am using my telco’s internet or services from a couple of dozen of ISPs I have tried in my country. We often do market research for service quality of our competition, so it happens a lot.  

  
  
  
  
  

![network-map](https://i0.wp.com/www.slashgeek.net/wp-content/uploads/2016/05/network-map-e1463471996476.png?resize=900%2C390)

There is a second part of this CloudFlare annoyance. CF being a CDN, its strength lies in having redundancy all around the world. So, in theory, their service should work even if their closest node goes down. But their data centers or nodes are not evenly distributed around the world, so if my closest CloudFlare node becomes unavailable my traffic get rerouted to a node that could be a lot further from my location, which results in increased latency and invalidating the whole point of having a CDN in the first place. This is exactly what happened on May 13, two of my closest nodes in SEA, **Kuala Lumpur** and **New Delhi**, was down for [scheduled maintenance](https://www.cloudflarestatus.com/). For whatever reason instead of traffic being rerouted to the closest nodes (which wasn’t very close to me in the first place), all CloudFlare hosted sites would either not work or was heavily broken because static files weren’t loading. This includes Reddit and StackExchange. This is not the first time it happened, but this was probably the longest duration so far with approximately 4-5 hours worth of disruption.

The idea that a single company can negatively influence the experience of such a large portion of the internet for users is kinda scary. I would urge everyone to reconsider using CloudFlare as your CDN/DNS/DDOS solution. Being free is not good enough reason to use something, if you are concerned about your site speed there are more important things to look into for optimization before considering a CDN. DDOS might be a good reason to choose CloudFlare, but only small portion of total users probably gets affected by DDOS anyways. Not to mention their free tier doesn’t cover the complex DDOS attacks that you really should be concerned about. So something that you configured because its free to use and relatively easy to setup because of its integration to most cheap hosts, turns out to be a nuisance to a large part of the internet users.

  
  
from Hacker News https://ift.tt/2OloMvc