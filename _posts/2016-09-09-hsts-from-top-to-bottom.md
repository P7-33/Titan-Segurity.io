---
title: 'HSTS from Top to Bottom'
date: 2019-11-10T03:31:00+01:00
draft: false
---

We're pretty much at a "secure by default" internet these days, at least that's the assumption with most websites, particularly so in the financial sector. [About 80% of all web pages are loaded over an HTTPS connection](https://letsencrypt.org/stats/), [browsers are increasingly naggy when anything isn't HTTPS](https://www.wired.com/story/google-chrome-https-not-secure-label/) and [it's never been cheaper nor easier to HTTPS all your things](https://httpsiseasy.com/). Which meant that this rather surprised me:

![](https://www.troyhunt.com/content/images/2019/11/Xero-redirect.png)

Let me break down what's happening here: I'm in (yet another) hotel and on complete autopilot, I start typing "xer" into the address bar which Chrome then dutifully auto-completes for me:

![](https://www.troyhunt.com/content/images/2019/11/image.png)

Because it's hotel wifi I expect it to be slow, so I flick over to another tab to do other useful things before switching back to the Xero tab ready to log myself in. Now, imagine for a moment that I'd been confronted with this page:

![](https://www.troyhunt.com/content/images/2019/11/image-2.png)

I've doctored this image to represent what could easily have been a rogue Xero homepage, but would I have hit the login button if I'd seen it? Would I then have entered my credentials on the resulting page, even if still served insecurely? Possibly, although a saving grace would have been [Chrome's red indicator once I started typing the password](http://http-password.badssl.com/) (although in my case, I would have tried to autofill from 1Password and I'd have 2FA to protect me if someone else grabbed it, but you get the point). No really, I pay a lot of attention to this stuff and I'll admit that I could easily have missed the absent padlock. And why is there no [HSTS](https://www.troyhunt.com/understanding-http-strict-transport/) which would have avoided this situation altogether? So I decide to check out the response headers on the login page and behold, there's HSTS:

![](https://www.troyhunt.com/content/images/2019/11/image-4.png)

That's one year's worth of seconds and I visit the site regularly, so what's the problem? Well the obvious one is a combination of the domain being different to the one I originally went to and the HSTS setting not specifying that it should include subdomains. With no such header being returned on the apex domain coupled with my mental autopilot then Chrome autocompleting to xero.com and defaulting to the insecure scheme (as all browsers presently do), meant no HTTPS and the local network effectively MitM'ing the request.

The irony with all this is that Xero obviously recognises the value of HSTS or they wouldn't have used it anywhere, yet by failing to use it on the landing page they leave customers vulnerable to precisely the sort of risk they added HSTS on the login page to prevent. So the moral of the blog post is that HSTS must exist across the entire route of navigation and ideally, also include subdomains _and be_ preloaded. And hey, it's free, easy and one of the best defences going for precisely this threat.

[SSL](https://www.troyhunt.com/tag/ssl/)

  
  
from Hacker News https://ift.tt/32nRhMl