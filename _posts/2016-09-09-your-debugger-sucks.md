---
title: 'Your Debugger Sucks'
date: 2019-11-27T04:54:00+01:00
draft: false
---

_**Author's note**: Unfortunately, my tweets and blogs on old-hat themes like "C++ sucks, LOL" get lots of traffic, while my messages about [Pernosco](https://pernos.co/about), which I think is much more interesting and important, have relatively little exposure. So, it's troll time._

**TL;DR** Debuggers suck, not using a debugger sucks, and you suck.

If you don't use an interactive debugger then you probably debug by adding logging code and rebuilding/rerunning the program. That gives you a view of what happens over time, but it's slow, can take many iterations, and you're limited to dumping some easily accessible state at certain program points. That sucks.

If you use a traditional interactive debugger, it sucks in different ways. You spend a lot of time trying to reproduce bugs locally so you can attach your debugger, even though in many cases those bugs have already been reproduced by other people or in CI test suites. You have to reproduce the problem many times as you iteratively narrow down the cause. Often the debugger interferes with the code under test so the problem doesn't show up, or not the way you expect. The debugger lets you inspect the current state of the program and stop at selected program points, but doesn't track data or control flow or remember much about what happened in the past. You're pretty much stuck debugging on your own; there's no real support for collaboration or recording what you've discovered.

If you use a cutting-edge record and replay debugger like [rr](https://rr-project.org), it sucks less. You only have to reproduce the bug once and the recording process is probably less invasive. You can reverse-execute for a much more natural debugging experience. However, it's still hard to collaborate, interactive response can be slow, and the feature set is mostly limited to the interface of a traditional debugger even though there's much more information available under the hood. Frankly, it still sucks.

Software developers and companies everywhere should be very sad about all this. If there's a better way to debug, then we're leaving lots of productivity — therefore money — on the table, not to mention making developers miserable, because (as I mentioned) debugging sucks.

If debugging is so important, why haven't people built better tools? I have a few theories, but I think the biggest reason is that developers suck. In particular, developer culture is that developers don't pay for tools, especially not debuggers. They have always been free, and therefore no-one wants to pay for them, even if they would credibly save far more money than they cost. I have lost count of the number of people who have told me "you'll never make money selling a debugger", and I'm not sure they're wrong. Therefore, no-one wants to invest in them, and indeed, historically, investment in debugging tools has been extremely low. As far as I know, the only way to fix this situation is by building tools so much better than the free tools that the absurdity of refusing to pay for them is overwhelming, and expectations shift.

Another important factor is that the stagnation of debugging technology has stunted the imagination of developers and tool builders. Most people have still never even _heard_ of anything better than the traditional stop-and-inspect debugger, so of course they're not interested in new debugging technology when they expect it to be no better than that. Again, the only cure I see here is to push harder: promulgation of better tools can raise expectations.

That's a cathartic rant, but of course my ultimate point is that we are doing something positive! [Pernosco](https://pernos.co/about) tackles all those debugger pitfalls I mentioned; it is our attempt to build that absurdly better tool that changes culture and expectations. I want everyone to know about Pernosco, not just to attract the customers we need for sustainable debugging investment, but so that developers everywhere wake up to the awful state of debugging and rise up to demand an end to it.

  
  
from Hacker News https://ift.tt/2KWzTZe