---
title: 'Sorry macOS users, but Apple has gone too far for some of us devs'
date: 2019-09-30T01:22:00+01:00
draft: false
---

Years ago when Cogmind was first released, I kept an open mind about the future prospect of releasing an official Mac version. Cogmind is my first commercial game, after all, and having only previously released hobby projects as freeware, and only on Windows, I couldn’t be too sure what supporting additional platforms would entail. So I took a wait-and-see approach about whether to provide some form of official support for Macs.

In the meantime I’ve just ensured that Cogmind (and my other software) works perfectly via Wine and similar third-party solutions, but on Steam of course I could never mark it as having Mac support since it’s not a separate download that runs on its own, and whether or not to put together something that would fit that requirement stayed on the backburner as I worked towards 1.0.

Well, by now I’ve definitely waited long enough, and seen enough, to come to a reasonable decision: Officially supporting macOS is simply not feasible for me.

Regarding the timing of this decision, if you follow [indie](https://itch.io/t/562055/macos-will-no-longer-be-supported "Worthless Bums Steam Marines 2: MacOS will no longer be supported") [game developers](https://twitter.com/McFunkypants/status/1174332424932622337 "Twitter: Christer Kaitila and replies to Apple's changes"), communities, or [news](https://www.theinquirer.net/inquirer/news/3033545/game-developers-fume-as-apple-deprecates-opengl "The Inquiter: Game developers fume as Apple deprecates OpenGL"), you might’ve heard a lot of noise lately about Apple, and sadly I’m here to add another voice to that chorus.

[![twitter_christer_kaitila_macOS_thread](https://www.gridsagegames.com/blog/gsg-content/uploads/2019/09/twitter_christer_kaitila_macOS_thread.png "Dev Twitter talking about Apple's latest moves (macOS app notarization)")](https://www.gridsagegames.com/blog/gsg-content/uploads/2019/09/twitter_christer_kaitila_macOS_thread.png)

Dev Twitter talking about Apple’s latest moves

Clearly I was already on the fence about the whole Mac thing before, otherwise it might’ve happened earlier (I did spend a while researching and testing the potential for a solution on Macs, in preparation for a potential future public release), but Apple has time and again taken actions which are clearly hostile to developers as they continue the trend of building and reinforcing their own walled garden.

Among their latest moves, [Apple’s newest OS drops support for 32-bit applications](https://www.rockpapershotgun.com/2019/09/04/macos-catalina-update-is-about-to-punt-32-bit-games-off-the-platform/ "Rock, Paper, Shotgun: MacOS "), which will unnecessarily render a huge library of software and games unusable on Macs, compared to Microsoft which does a great job of maintaining Windows backwards compatibility in that area even as most modern software tends to be 64-bit. This makes it far easier to hold together Cogmind’s existing tech so I can focus on things players actually care about, like more features.

More importantly, Apple will require developers to register, pay an annual fee, and [_notarize every build_](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution "Apple notarization process") they want to distribute, altogether drawing devs yet closer into the tightly controlled black box of Apple’s world.

So not only would I have to buy, learn, and update their ridiculously expensive hardware, I’d also have keep paying them money, and force both myself and players to suffer a slower build turnaround time and other issues all so Apple can tighten their grip on their users and developers. Nope.

Unreasonable Burden
===================

Making games is already challenging enough without platform holders adding to that burden without anything to offer for it.

The notarization requirement is especially terrible for games that get lots of updates (roguelikes! Early Access!), when I might even want to put out several builds in a single day. My normal release process? Simply compile a build here, copy the files into the Steam backend and \*bam\*, everyone has access just like that--I don’t need to insert a third-party black box into that arrangement.

[![cogmind_uploaded_steam_builds_beta_8.1](https://www.gridsagegames.com/blog/gsg-content/uploads/2019/09/cogmind_uploaded_steam_builds_beta_8.1.png "Cogmind Steam build upload records (Beta 8.1)")](https://www.gridsagegames.com/blog/gsg-content/uploads/2019/09/cogmind_uploaded_steam_builds_beta_8.1.png)

The Steam backend showing Cogmind builds uploaded with modifications and fixes in short order for one of this year’s releases. This is pretty common!

_(Note: My DRM-free release process is more or less the same: Simply zip up a new build and upload it to the release site.)_

So yeah there are more hoops to jump through, but beyond the burden is something more worrisome: Basically I _don’t trust Apple_ to care about my interests as a developer.

They have a history of dev-hostile actions that are pushing developers away from their ecosystem, which I guess is an inevitable side effect of having built a successful business around walled gardens and trying to lock everyone inside--some will stay, but those with good options elsewhere won’t.

Uncertainty is already a huge risk factor in game development, from design issues and technical hurdles to market forces and life in general, we don’t need more uncertainty coming from high places that we don’t have any hope of influencing, much less companies with a poor record in the first place.

Non-Apple Roadblocks
====================

Apple aside, I should also cover the reasons that originally had me on the fence to begin with, one of which I’m sure the average Mac user will also be quite familiar with: economics.

Naturally there’s a non-negligible additional cost to developing and supporting an additional platform, one that varies depending on tech and know-how. Assuming time isn’t a factor, sufficient sales volume might make it worth the investment to support other platforms, although this is harder to do without a more mainstream game (_that also sells well!_) where the inevitably tiny ratio\* of players using Macs is still a respectable number, as opposed to working on niche games like I do :P

_(\*Approximately 5% for your average roguelike, based on the data I have.)_

To me, even more important are the non-financial calculations, since Mac players also tend to require a [greater amount of post-release customer support](https://www.reddit.com/r/Games/comments/376qki/less_than_1_linux_users_according_to_steam_survey/crk5t1q/ "u/NobleKale on the difficulty of non-Windows support for solo indie devs"), and I’m just one guy…

[![halfway_support_stats](https://www.gridsagegames.com/blog/gsg-content/uploads/2019/09/halfway_support_stats.png "tk")](https://www.gridsagegames.com/blog/gsg-content/uploads/2019/09/halfway_support_stats.png)

Mac players account for 4% of sales but 50% of support requests, [one of](http://robotality.com/blog/one-year-of-halfway/ "Robotality: One Year of Halfway") many such examples I’ve seen from dev data over the years, including from other roguelike devs.

Of course Mac support request ratios will vary by game due to architecture and player base, but there’s little question that they’re higher in general, which for me is a problem because I’m only really familiar with Windows. Being able to remotely troubleshoot issues is already challenging enough on a system I’m quite familiar with, but at least the years of learning are behind me, that and I can manage a reasonable number of requests. I wouldn’t be able to offer the same level of help to those using other systems, in which case it’s better to not put myself in that position in the first place.

It’s somewhat easier for a team to handle multiplatform support, whereas I’m mostly on my own here doing all the design and programming (in my custom engine--this isn’t “push button to release to platform B” xD) and marketing and all sorts of other things.

What now?
=========

What does this mean for the future? Unfortunately given Apple’s trajectory here, I can’t see doing anything official for macOS. I’m all for accessibility and making it possible for more people to enjoy the results of my work, but this one’s beyond me. Gotta stay sane, and Apple sure doesn’t make is easy!

I will continue to make sure Cogmind (etc.) is compatible with Wine itself, especially since it also works nicely on Linux (and Proton under Steam), so for as long as it’s possible to run it through Wine on a Mac that will still be an option.

Of course, you can also try to stay on an older macOS, though I guess that will only get you so far. It will, however, enable you to use all the other software that’s about to be deprecated as well xD

In any case, hopefully everyone can understand my choices here. Not easy choices to make, but it’s important to stay realistic…

  
  
from Hacker News https://ift.tt/2mJGcqg