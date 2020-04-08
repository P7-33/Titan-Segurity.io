---
title: 'A push gone wrong in the name of what, exactly?'
date: 2019-10-26T08:17:00+01:00
draft: false
---

A push gone very wrong in the name of what, exactly?
----------------------------------------------------

Some time back, I had the opportunity to witness a particularly bad release of some random software gunk that does stuff over a network connection. It's one of those things that talks to other instances of itself, and so sometimes you have an older one talking to a newer one, and that sort of thing.

Anyway, this particular release (version B) had an amazing quirk: it would emit data on the network that would _kill_ instances of itself running the older release (version A). This was something to do with B sending out something that A couldn't handle. The exact problem wasn't particularly interesting, but it boiled down to "if B talks to A, then A segfaults and drops all of its clients".

Obviously, for a multi-tenant system with long-lived sessions, this was a very bad thing. As B would roll out to more places, more and more of the A instances would die. This was causing service disruptions all over the place.

What happened next is kind of amazing. Instead of stopping there and doing something useful about it, the team decided to double down and just kept on pushing. They figured that the only real problem was when B talked to A, so they "just needed to get rid of all of the A instances".

So, what did they do? They rushed that push out just as fast as they could, slaughtering A instances all over the place. Eventually, B wound up everywhere, and the mayhem stopped. They declared victory and went on with life.

Nobody else really found out about what was going on with this until it was much too late, so there were no opportunities for saner heads to prevail.

What could have happened instead? Many things.

You'd think they would have noticed that new feature killed old instances when they wrote it. After all, if you just wrote it in your local working copy, who else do you have to talk to but old instances? Somehow, they didn't, or they did, and committed it anyway.

They could have stopped the push of B, rolled back to being 100% A, and then removed the new crash-inducing feature from the code base. Then they could have fixed the crash and created a new non-crash-inducing AND non-crashing version C. That would then need to go out everywhere.

Now, just having this intermediate state is not an excuse to rush things and push C into production super quickly. It would need to be treated as just another normal release and should have gone out as such.

Then, once C was everywhere, only at that point could the new feature be added back to the code. That would be committed and released as version D, and then that could go out to production, same as before, with a properly measured pace and not rushing things.

Or, you know, they could have not enabled a feature with a code push alone, and put it behind some kind of feature flag. Then they could have shipped B, noticed the problem while doing a _partial rollout_ of the flag, and left it disabled until A was gone everywhere. At that point it would have been possible to resume the flag push.

Do yourself a favor. Don't rush pushes. Don't ship features with code deploys. Use feature flags if your service works that way, or "percent of user base" knobs if it works the other way.

And hey, when you know your push is breaking the world, stop!

When you're already in a hole, QUIT DIGGING.

  
  
from Hacker News https://ift.tt/32Il7vX