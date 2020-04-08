---
title: 'Break before make, abstractions, and sleazy ISPs'
date: 2019-10-06T06:46:00+01:00
draft: false
---

Break before make, abstractions, and sleazy ISPs
------------------------------------------------

Back in July, I [wrote](http://rachelbythebay.com/w/2019/07/21/reliability/) about some of my reliability list items, including a few mentions of "make before break", "A, AB, B" and the like.

Now I'm going to drop a concrete reason as to why you should care about this kind of thing. It's also related to what happens when you've abdicated responsibility to a bunch of magic systems which do things behind your back and you can't see what's going on. Sometimes they pull this "break before make" business on you, and you might not notice it at all. Worse still, someone might decide it's acceptable.

Here's the scenario: someone is using one of these "infrastructure as code" things, because they're hooked on the cloud, and they've started stacking vendor stuff on top of vendor stuff to manage all of it. They decide to make a small change to their DNS. Maybe they want to shift an A record from a.b.c.1 to a.b.c.2.

They're not stupid, so they have servers running at both IP addresses ahead of time. This ensures that even if someone has the .1 version cached for a while, things will still work. They will shut down service on .1 at some later date.

They are also not stupid in the other way. The .2 IP address actually works just fine, and will serve traffic without any sort of side-effects. This is also not the problem I'm writing about.

This isn't even a problem of not having sticky sessions and potentially doing a "pogo" thing between .1 and .2. They handled that, too.

No, this is about what happened to those DNS zone files when they asked their "IaC" thing to make the change from .1 to .2. This is what happened.

First, there was the original zone file with a.b.c.1 in it. That had to go away, so the system sent an RPC to the cloud provider to _delete that A record_. It was acknowledged, and it disappeared as requested. The cloud provider started handing out NXDOMAINs to anyone asking for that A record. It's the DNS equivalent of a 404 - nobody's home.

Then, to get the new IP address in place, the system sent another RPC to the cloud provider to _create the A record_ with a.b.c.2 as the IP address. The cloud provider acknowledged this too, and it appeared as requested, and now anyone asking for it got the new IP address in response.

How long elapsed with the NXDOMAINs going out? Maybe a couple of seconds. Most clients didn't notice, or if they did, they started working again a few seconds later.

But then there was a whole other group of clients that fell off entirely and did not come back. Minutes passed, and they weren't coming back online. It took a while, but someone eventually realized that all of these clients were using the same (very large) ISP. There must have been something in common, and oh yeah, there definitely was.

Someone got a test machine running on the ISP and did a query for the hostname, and got back an IP address which was neither .1 or .2. It was something else entirely, off in a completely different net block, routed by some rando autonomous system. Actually going there in a regular web browser turned up some weird error page.

What happened? First, that particular ISP's resolvers got a NXDOMAIN back during the seconds-long window just like everyone else. But, unlike most places, this ISP happens to be a real piece of crap, and they replace NXDOMAINs with their own A records for their "helpful" ad network. So, instead of getting some kind of DNS error from your browser, app, or device, you get taken for a ride. You end up at a weird ad-laden page, your app goes insane with data it can't handle, or maybe (if you're lucky), it complains about a certificate mismatch and just stops there.

Of course, this malicious injection had a relatively long TTL set, and once it landed in the ISP's resolvers, it stayed there like a bad penny, not going away. All of those clients just kept going to the wrong place. Even though the NXDOMAIN was long gone, the clients were still offline, and people were starting to complain loudly.

Actually fixing it involved pulling some strings to get the scummy ISP to clear the cached records in their recursive DNS resolvers, at which point they'd fetch the real (a.b.c.2) data, and things started working again.

Did the cloud provider offer a way to update the existing record without having to delete it outright? Probably. Did the extra layer of abstraction know that? Maybe, maybe not. Did anyone have any idea what was about to happen? Absolutely not.

This is why I say some of this stuff is entirely too complicated. We've brought this upon ourselves: building breathtakingly high stacks of ridiculous systems where few (if any) people can keep the whole thing in their head. Just like code, configs also have to "run" on people first in order to be written and reviewed honestly, and if you can't know the stack, there's no way to know what will really happen.

I keep asking if people do this on purpose as a job security gambit. The number of companies which exist to just stack things higher and higher and higher seems to confirm that a whole lot of money exists in this space. They keep selling and people keep buying it.

If you're using things which do macro expansion or anything else that involves you writing format A and it generating format B which actually does the work (or worse yet, gets turned into format C), you _really_ owe it to yourself to run a 'diff' on the before-and-after versions of the output from the tool BEFORE it goes and takes any action on your behalf.

Otherwise, you too may get your DNS hijacked by a sleazy ad vendor.

  
  
from Hacker News https://ift.tt/2LNtgsV