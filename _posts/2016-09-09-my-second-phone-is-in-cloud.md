---
title: 'My Second Phone Is in the Cloud'
date: 2020-02-01T03:43:00+01:00
draft: false
---

You know what I want? I want my own private server, to run my own private software, and I want everyone else to have one as well. Let me explain:

I’ll start with privacy; it’s at the forefront of a lot of people's minds these days. Down with centralization of power! Embrace web-style topology over the hub and spoke model!

Trust me, I get it. I believe that users data should be secure, private, and easily manageable. When it comes time to actually _implement_ this, however, these little things like “practicality” and “feasibility” keep getting in the way. It’s just far _simpler_ to have a central hub. Both in an implementation, but also, **critically**, in user adoption.

An example: [Matrix](https://matrix.org) advertises itself as “an open network for secure, decentralized, communication”. It’s a very cool idea, and I encourage you to check it out! There’s just one problem: to truly own your data, you’d better be running your own matrix server. This _immediately_ vetoes _just about everyone_ from ever using matrix as intended. Instead, they’ll connect to someone else’s server, and inevitably, provided Matrix grows in adoption, that “someone” will be some centralized giant. User’s want convenience, and trade true privacy for convenience time and time again.

Run-your-own email server, private backup, photo collection… all of these _have_ open source solutions. You are entirely able, for _free_, to run a myriad of services yourself instead of delegating to some centralized solution. You just “simply” download the software, read the instructions, provision hardware, upload, install, configure, configure some more, debug, and Tada! Luckily this “only” takes a few hours because you have the requisite knowledge to know that when the instructions say \`$ mycoolproject run\`, you should type that into your terminal. Good luck onboarding anybody outside of software.

Problems with roll-your-own exist in other places as well; gamers have been wrestling with servers ever since games had networked multiplayer. A young kid wants to run their own minecraft server? They’ll spend an entire weekend figuring out wtf a .jar file is, only to find that nobody can join because McCafe blocks the port that the clients connect on. I’m sure they’ll figure it out. Also, if they do, the server is only up when they specifically run it, so no playing your save file if your buddy isn’t also playing.

This also shows a second problem, that of uptime.

Teamspeak is (was) a popular VoIP for gamers, but it required someone to run the server on their computer. Also, they’d have to setup port forwarding on their router. Then you could only chat when the hosts computer was up. Discord came along and said “woah we’ll just host the server for you! (and also collect all your info but ignore that)” and _to nobody's surprise_ become wildly popular.

A lot of SaaS companies provide software that _could_ run locally, except that whatever software is running has to be available 24/7. These companies are usually of the “personal assistant” flavour. Personal finance apps, time tracker apps, photos apps, ect ect. Users must submit personal information to these apps because the app server needs some sort of “authority” to act on the user's behalf, and, to function properly, they have to be ready to use that authority at any moment in time.

I’m part of [HodlBot](https://www.hodlbot.io), where we provide high level automation software to help our users better invest their cryptocurrencies. To do that, we need users private API keys to whatever exchange they happen to be using. Trust me when I saw that _**I don’t want to have to store those keys**_. But we _have_ to, so that we can make trades for our users. We thought about putting all the trade execution on the client side, but ultimately rejected it. Part of our value proposition is “set it and forget it” style wealth management; if we can’t do anything for you because your computer is off, that’s a _big_ problem.

This leads me to my conclusion: _a ton_ of centralized solutions don’t inherently need to be, but they are because 1) they must be available and 2) it’s too complicated for users to roll-their-own. Both of these problems are solved with the advent of a new software platform: the personal server. For legibility reasons, I’m going to henceforth abbreviate the personal server as PCC (personal/private cloud computer).

I want you to imagine your PCC as a smartphone, but in the cloud. There’s a sleek traditional phone app to interface with your PCC. There’s an app store for applications to run on your PCC. PCC apps are all standardized to run on the PCC model, much like phone apps today. Some are pay to use, some are free. Anybody can make PCC apps, so long as they conform to certain specifications. On installing an app, the app will download, install, and automatically run. Updates install automatically. Apps can register servers at any subdomain of \*.appname.yourdomain.com, so that they can expose web UIs/APIs/anything really.

Your PCC is of course automatically secured. Only your phone has admin access. All network communication between your phone and PCC is automatically encrypted. Apps are containerized and sandboxed, just like traditional smartphones.

It really would be just like a second phone, except in the cloud. Phones today are phenomenal, but are necessarily handicapped by virtue of 1) intermittent connectivity and 2) being a slave to low power consumption. A PCC is always up and holds no such power requirements. These two differences alone have a _huge_ impact in what software is viable to run on your phone, and what isn’t.

I want to take _all_ the difficulty out of run-your-own solutions. Give everybody a PCC. The compute providers might be centralized, but they only provide “dumb” compute/network/storage resources for a monthly subscription.

The same amount of effort that it takes to download Flappy Birds can be used to start running your own pi-hole DNS server. Download a blogging application and run your own blog at blog.yourdomain.com, where users can read your content in peace without getting modal-blasted to sign in with Google. Host your own tweets at new-twitter.yourdomain.com, and push them to activity pub. You have your friends domains in your contact book, so easily subscribe to their twitter feeds in a decentralized way. Same goes for a next-gen instagram.

The technology for this already exists, nothing is groundbreaking. Compute, storage, and networking resources are cheap and continue to only get cheaper. Users could be in complete control of all their data for the price of a netflix subscription.

The world _could_ be more decentralized today, but it _won’t_ be until you make it hassle-free to do so. Make it easy by giving developers a promising decentralized platform to build on. I promise you, If you build it, they will come.

  
  
from Hacker News https://ift.tt/2GGP2LD