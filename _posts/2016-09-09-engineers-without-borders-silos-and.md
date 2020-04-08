---
title: 'Engineers without borders, silos, and vendor walls'
date: 2019-10-14T05:34:00+01:00
draft: false
---

Engineers without borders, silos, and vendor walls
--------------------------------------------------

I've seen a bit of variety in how different companies handle engineering problems. Some are big. Others are small. Some build things, and others don't. For some places, the tech is the product, but at others, it's a distraction at best. This is just to say that no one solution is expected to solve every problem, but it's still possible to find things that generally work better than others.

Let's talk about communication and teamwork. If you think those are generally good to have in your organization, you might be prone to make decisions to maintain what you already have and perhaps grow more. Keep that in mind as I describe some scenarios.

Scenario number one is a company which has a product which then depends on a bunch of different services. The product isn't important - it could involve cat pictures, influencing elections, or delivering pizzas. We'll say they have hard dependencies on 20 different services which must all be up and running for the business to function. Maybe one service is a database, another one is a cache, a third one is a group of web servers, a fourth tracks "upvotes", "likes" or "stars", and so on.

In this organization, the 20 services are owned by 20 teams in a 1:1 mapping. Team A owns service A, team B owns service B, and so on down the line. Some of these teams are quite good at what they do, and rarely cause trouble for the business. We'll even say that most of them are pretty solid, and generally don't break things.

There are, however, three services which have significant challenges. They fall over a lot. They stop working. They take down the whole operation. It doesn't matter how reliable the other 17 parts are, since one of these "terrible three" will show up and wreck the whole thing.

Fortunately, this company is enlightened, and has embraced a philosophy where people are able to talk about these things openly, and reflect on the problems and not the people involved. More to the point, the best engineers from other parts of the company are able, willing, and allowed to "wander around" into the troubled parts to help out. This kind of knowledge transfer happens, and pretty soon the roughest spots have been smoothed out, and now everything's a lot better. The cat pictures keep going out, the elections keep being hacked, and the pizzas show up on time. Life's pretty good.

Now let's jump into scenario number two. It's another company that has similar hard dependencies. They also have 20 services which must be up and running to make their business "go". Those 20 services are also run by 20 separate teams, as before, with one team owning one service. Most of them are also pretty good, and only a few of them have issues.

Unfortunately, that's the end of the similarities. Company number two has this "siloing" thing going on. If you're not familiar with the term, consider yourself lucky. It's when a company isolates one thing (a system, department, etc) from another. Well, this company has a LOT of siloing happening. People are very possessive of their services, and their team's "turf". Outsiders are to be suspected, since they probably have some nefarious intent in mind. The fact that all of these people nominally work for the same company with the same supposed goal in mind doesn't matter.

The corporate firewalls are up, they're numerous, and they're pretty tough. If a good person is on one side of the wall, and there's an interesting problem on the other that they could fix, the wall is going to prevent it. There will not be any cross-pollination between the teams. The best you might see is a few individuals moving around between teams in a shared silo, but you'll never see anything more than that.

The organization has been set up with defenses against this. People who try to poke their nose in, even if they have the best possible goals in mind, are the enemy. They must be blocked or reported. They definitely must be thwarted. They must not see the weaknesses in the system because it will be used to attack somehow and take over part of the turf!

Imagine running a company this way, where you can get these protected realms where the employees are "untouchable" and also somehow unable to deliver on the same requirements as everyone else. Worse still, you find yourself unable to send in helpers since the immune system will flare up and attack them in every way imaginable.

In such an environment, I'd expect it to become obvious by way of the general sense of malaise, acceptance of the status quo, and a lot of shrugs - "it's always been like that". "They're protected". "Those requirements don't apply to them". Maybe you've heard some of these before.

I'd hope that most people would try to avoid this with their companies, and part of that would involve breaking down the walls between groups which aren't mixing it up enough. The whole notion of engineers moving around and sharing their talents with whoever needs it has to be supported and rewarded.

Now I'm going to throw another complication into the mix with scenario three. This is a third company which amazingly also relies on 20 different services staying up and available the whole time for their business to work.

But, unlike company #1 and company #2, this one has a completely different approach to services. By default, they go out to Hacker News, find the shiniest thing in that space, and then pull out their checkbooks and throw money at whatever products they find on this romp through the web. They end up with 20 different services, sure, but they are coming from 20 different vendors.

Maybe most of the vendors are reasonably competent and so you never notice problems with them. They take your money and you get some level of service in return. It's good enough and so you probably forget about them. This is akin to the 17 or so good ones at the other two companies.

There's always a catch, though. Three of these services are garbage, just like at the other two companies. Their vendors are just not good at doing whatever they are purportedly selling. They're consuming lots of customer money and are delivering fatal errors, timeouts, or worse.

When this kind of thing happens at company 1, there's always the option of retasking some of the better engineers to do a field trip to the troubled teams to bail them out. If it happens at company 2, the silo walls prevent it, but those silo walls can in theory be torn down, and then they can turn into company 1.

But company 3? That's a different kind of trouble. All of their services are on the other side of a vendor relationship. Maybe some of those vendors are best-in-class, and are amazing -- it happens! But, some of those vendors definitely are not. Do you think company 3 can convince the awesome vendors to send engineers over to the terrible vendors to fix things up? Yeah, I don't think so. That's not going to happen. It's the ultimate silo, and you're never going to break it.

Would you ever willingly build a company like #2? I hope not. But, if you build a company like #3, you've basically done it anyway: you get all of the walls and none of the opportunities to tear them down later.

There are plenty of other gotchas which come with each of these three scenarios, but I'll leave it there for now. It boils down to this: the proliferation of interconnected vendors leads to a loss of control, and few things are more depressing than that.

  
  
from Hacker News https://ift.tt/2B9jxqJ