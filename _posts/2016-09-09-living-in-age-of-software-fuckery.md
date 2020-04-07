---
title: 'Living in the Age of Software Fuckery'
date: 2020-01-06T01:38:00+01:00
draft: false
---

![](https://web.archive.org/web/20160308032127im_/https://cdn-images-1.medium.com/max/800/1*xImxcl149ZX5gkRhZCFF-A.png "Living in the Age of Software Fuckery — Medium")  

### Living in the Age of Software Fuckery

_Ten Anti-patterns and Malpractices in Modern Software Development_

Your hopes? Your sanity? Your next code base.

#### 1) Business Thinking Favors the Short-Term — To an Extreme

According to Alan Kay, there are legislative problems in the US that effectively force businessmen to make myopic decisions — [https://www.youtube.com/watch?v=NdSD07U5uBs#t=36m12s](https://web.archive.org/web/20160308032127/https://www.youtube.com/watch?v=NdSD07U5uBs#t=36m12s)

Some propose that the phenomenon of easy credit and low-interest rates make it economically nonviable for a company to act in its longer-term interests.

Some people just blame capitalism for its inherently exploitative nature.

Whose opinion is most accurate is immaterial for this discussion. What matters is that your manager, and all the way up to the CEO, spend no time thinking about, much less preparing for, future engineering concerns. This is for the same reason that a Firefighter blasting a water cannon doesn’t think how much water damage he may be causing — _the goddamn building is on fire_.

Anyone whose eyes are not glued to an IDE for 50+ hours a week is effectively blind to the company’s metastasizing engineering problems.

The ‘business view’ of the engineering problems.

But software works in the opposite way. The longer-term you can think about your software, the more robust and less costly and painful its development will be. The more time you put up front into building simplicity into the system with intelligent layering, the less of a nightmare it will be to develop.

The Business Team addresses a technical issue.

Sorry to say, but because of the short-sighted way in which management must think (again, likely due to the incentives provided by the larger economic environment), the integrity of your software system isn’t even on their radar. If they notice it at all, they’ll more likely see it as an obstacle to work around rather than a constraint to respect.

#### 2) You Will be Crucified for Not Being a ‘Team Player’

It won’t matter how productive you are, how many late nights you invest, or even how well you actually collaborate with your fellow engineers. The moment you engage in thinking misaligned with management’s above view, you will be up for crucifixion on this cross. And if you’re the type of person who relents to plain reason, you will eventually find yourself voicing legitimate engineering concerns.

You will feel the room temperature rise every time you do so, for you are stepping into the fire.

Ultimately, your job is to help management meet expectations for the next quarter. This means that most of your time will be spent fighting fires lit from the previous quarters, hunting bugs that could have been easily prevented, or refactoring several unrelated pieces of code just enough implement the next broken feature.

“Next. Crucifixion? Good…”

#### 3) The Software Architect is a Politician

Ever wonder why you never find yourself in a maintainable commercial code base? Surprisingly, it’s not at all due to a lack talent in the software world. There are tons of great software architects just biting at the chance to build the next great system.

The problem is that the main qualification for being a software architect is not technical wherewithal. The qualification for being a software architect is in having the ability to coerce front line engineers to implement functionality at an unsustainable pace. For this is what is required to satisfy our short-sighted management.

When it comes to building a coherent, understandable, and well-designed system, the software architect will not have this as his top priority, or likely anywhere near it. This is true regardless of the long-term necessary benefits of doing so.

Two legs good, four legs bad.

The architects job is to a) appease the business people to whom he is beholden, and b) engage in any manner of political fuckery needed to coerce the engineering team to follow suit.

If our architect were ever to grow sufficient backbone to stops producing at the rapid-fire, unsustainable pace as demanded by short-term interests, he’ll eventually be replaced by someone with sufficiently less integrity. Someone who can _‘get the job done, bygod…’_

#### 4) Suffering is the Commodity That you Provide

You might be under the impression that what makes you qualified for various positions in software development is primarily your technical acumen and ability to work with other technically-capable engineers.

You’d be wrong.

While a certain minimum of capability is required to do your day-to-day work, what your value really consists of is in grinding yourself against the piercing pincers of elusive bugs and razor-wire bundles of bullshit code until something resembling progress is made. You are not a problem-solver, you are a problem-endurer.

This is what you went to college to do.

Oh sure, you can solve the endless little meaningless problems that plague the day-to-day life of programmers everywhere, but the source of these problems — defects at the engineering level — are effectively untouchable. Also untouchable are the systemic issues that cause each of these should-be-trivial-to-fix problems into 5–8 hour tasks. The interesting problems that have long-term engineering and business impact, the problems you went to college to solve, might as well not be on your radar.

Rich Hickey gave one of the most powerful and beautiful talks on how to elegantly engineer 90–95% of these bullshit day-to-day problems out of existence — [http://www.infoq.com/presentations/Simple-Made-Easy](https://web.archive.org/web/20160308032127/http://www.infoq.com/presentations/Simple-Made-Easy). Watch it in full; you’ll be inspired. But despair, for these are the engineering techniques you won’t get to apply. The business team can’t or won’t see the value of putting in even the smallest amount of up-front work into anything you do.

#### 5) Your Peers Won’t Support Change

Businesses and management are short-sighted. But if you’re like me, their shortsightedness is dwarfed only by your coworkers. Whereas your manager can’t think beyond the next reporting period, your co-workers probably can’t think beyond the next pay period.

Because human beings are a coping species, within them lies a mechanism for swallowing lies that help them justify reaching their primary goal of… well… getting paid. They are genetically programmed to gobble up lie after lie as long as it suits their most immediate purposes.

There is a whole class of literature of self-deception and what motivates it, but I’ll just leave couple choice links here -

[http://discovermagazine.com/2013/june/01-lying-to-yourself-helps-you-lie-to-others](https://web.archive.org/web/20160308032127/http://discovermagazine.com/2013/june/01-lying-to-yourself-helps-you-lie-to-others)

[http://www.cleanlanguage.co.uk/articles/articles/27/1/Self-Deception-Delusion-and-Denial/Page1.html](https://web.archive.org/web/20160308032127/http://www.cleanlanguage.co.uk/articles/articles/27/1/Self-Deception-Delusion-and-Denial/Page1.html)

[https://www.psychologytoday.com/blog/evil-deeds/200811/essential-secrets-psychotherapy-truth-lies-and-self-deception](https://web.archive.org/web/20160308032127/https://www.psychologytoday.com/blog/evil-deeds/200811/essential-secrets-psychotherapy-truth-lies-and-self-deception)

Your peers from left to right — The one you confide in, the one who speaks up for you, and the one who looks out for you.

#### 6) Someone is Always Ready to Undercut You

And the guy who is going to replace our newly-spined software architect? He’s the guy sitting across from you who never complains about the code, never ‘wastes his time’ cleaning things up, and is always the first to shut down ‘toxic’ discussion. He’s the one whose ego has him up to his eye-balls in debt on consumer goods. As to thinking in terms of the next pay-period, he’s already adjusted his spending habits for his next _promotion!_

If you think your team’s code base is fucked now… just you wait till Douchbag McGee is put in charge.

Ya, he’s pretty much all that — at your expense.

#### 7) The Conscientious are Disenfranchised

It stands to reason that an engineer with sufficient seniority could put a stop to this circus. After all, code is as much about experience as it is about expertise.

Perhaps this used to be the case, but not any more. Today, we have something called ‘collective code ownership’. The reason given for this practice is at once a truth and a lie. Collective code ownership is to keep people from being ‘blocked’. After all, as we are constantly ‘coached’ by people who traded their spines for three weeks of management training, everyone is allowed to change any code, in any way, so long as it helps them meet their short-term goals.

If our dilapidated, ruined code bases can do anything well, they can teach us viscerally the meaning of the term ‘the tragedy of the commons’ — [https://en.wikipedia.org/wiki/Tragedy\_of\_the\_commons](https://web.archive.org/web/20160308032127/https://en.wikipedia.org/wiki/Tragedy_of_the_commons)

A pictorial representation of how much fun remains in working in collectivized code.

Putting even that valuable lesson aside, let us consider that being ‘blocked from making changes’ can actually be a very good and necessary thing. It’s something that the senior engineers of yesteryear once had the power to do. They sometimes did it out of spite, yes, but more often to keep code over which they had stewardship from being compromised by short-term thinking. Blockers were put up to ensure that software could be developed at a sustainable pace with the minimum of human suffering involved, and to be used as a check and balance against a management team not in a position to understand or learn about engineering trade-offs at stake.

No longer.

Our long dead (or at least retired) heroes, who slayed dragons in business suits with little more than cunning and guile, have finally been cut down by systematic disenfranchisement. The stewards of our lands and balancers of power have been lain waste by top-down collectivization, the business-engineering equivalent of Mao’s Great Leap Forward. Collective code ownership may be the most pernicious thing to happen to code since the advent of Javascript.

What all methodologies eventually revert to.

#### 8) Methodologies Are Management Tools

Which brings me to my next point. They’re not there to help you create better software, and if they are, they will be warped into the opposite.

Agile has been the perfect example of this. What started out as a reasonable means to develop software has been turned into, as Mike Judge calls ‘Psych 101 MBA Bullshit’ -

[https://www.youtube.com/watch?v=oyVksFviJVE](https://web.archive.org/web/20160308032127/https://www.youtube.com/watch?v=oyVksFviJVE)

#### 9) You Will Think your New Team / Project is the Exception

Sometimes naivety is good, especially if you’re behind on bills from being out of work. In fact, lying to yourself can have serious short-term benefits. Such habits are probably so ingrained in you that you often decide to do so unconsciously. The term for this is being on one’s ‘Honeymoon’.

But if you’re going to lie to yourself, at least admit that’s what you’re doing! The more deeply you believe a lie, the more rude your eventual awakening will be. And then you’ll find yourself spending hours writing articles like this and raging against the whole blind stupid world on Twitter.

The sum of my recent productivity.

#### 10) It’s a Race to the Bottom — and No One Gives a Shit

The truth is, commercial software development is a race to the bottom. Whoever can trade away the optimal amount of personal integrity and endure the most suffering wins.

Management thinks you’re just paying your dues to be a part of their club (even if you have no interest in management), so they don’t give a shit.

Your peers adopt a macho attitude against it all, and will see your frustration as a liability, or in D-Bag McGee’s case, weakness upon which they can capitalize.

The average Joe thinks your life is puffery compared to his, so he doesn’t give a shit. He gives even less of a shit because you and your hipster brethren are jacking up his landlord’s property values.

In fact, you’re lucky to find a person who can admit to the above problems in the first place. Most people delude themselves into thinking nothing’s wrong, so that they don’t have to carry the burden of giving a shit. Few dare broach subject in public, much less at work.

### What is to be Done?

#### Pull requests welcome.

But in all seriousness, we can start by telling the truth about the situation, to others and especially ourselves. At the very least, it should help to lessen the shock of the reality to people entering our field. The people most affected by this shock are the honest young people who are least suspicious of this type of chicanery. In other words, the people we lose the earliest are the people we may need the most.

#### We can stop deluding ourselves, and stop putting our energies into the impossible.

However, the recognition of these truths do put us in a precarious position. To be employable for more than a week means acting in accordance with these ugly facts. But to become employed in the first place, we must act mostly oblivious to them! I suspect that most discrimination that happens against older programmers is not, in fact, age discrimination, but is, in fact, ‘wisdom discrimination’.

In order to work in a dishonest system, we must become like it, if only a little bit, if only temporarily. But go too far toward in that direction, and you become the problem.

As I said, precarious.

#### Like any radioactive substance, limit your exposure to the software industry.

Another thing is to prefer only short-term contract work, or to treat their full-time positions as anything but. If you need to, lie about your intended level of loyalty — they’re already lying about theirs.

You may think that this is a problem due to introducing gaps in your resume. Maybe this was a problem when your father was slinging code, but it’s not going to be for you. Again, companies are thinking short-term. Due to their shortsightedness, they cycle through employees as fast as your local burger joint. The last thing they care about is whether you will be at their company 5 years from now. Their only question is — can this guy help us meet our next quarters’ expectations?

So go ahead, negotiate for that extra $50k / year, and leave as soon as your bank account is ready for your next 3 month vacation. I personally consider myself semi-retired since the age of 30. Though it is a life of seeming instability, they’ve done all they can to make long-term engagement unsustainable.

#### Act to change the laws and stimulus-induced environment that force businesses to act shortsightedly?

Sounds promising, until you realize it was the businesses themselves that wrote these rules. Things are precisely as they are intended to be.

Remember all those stupid wacky idiots who railed endlessly against government regulation and the federal reserve, and spammed up your internet chat rooms with Ron Paul or Ralph Nader’s talking points? LOL, right? Well, we’re living out their nightmare, one software fuckery at a time.

#### ADDENDUM:

After many months and nearly 35,000 views of this article (thanks, everyone!), I’ve decided to forward-link my most important articles detailing proposed solutions to many of the above issues.

While the ideas I propose are new and untested - and potentially difficult to implement due to their marginally political nature - I think they’re reasonable enough for people who are interested in this article to explore.

[Part 1: Sharing is the Root of All Contention](https://web.archive.org/web/20160308032127/https://medium.com/@bryanedds/sharing-is-the-root-of-all-contention-f1ba6b9b82fc)

[Part 2: The Civilized Alternative to Agile Tribalism](https://web.archive.org/web/20160308032127/https://top.fse.guru/the-civilized-alternative-to-agile-tribalism-4c60d01428c0)

[Part 3: An Unexpected Inquisition](https://web.archive.org/web/20160308032127/https://medium.com/@bryanedds/an-unexpected-inquisition-c4776bdedbb8)

While these ideas may be imperfect and non-trivial to execute in practice, I’m hoping that this type of ‘post-agile’ thinking will kick into gear the changes we all know we need!

  
  
from Hacker News https://ift.tt/36vtdK8