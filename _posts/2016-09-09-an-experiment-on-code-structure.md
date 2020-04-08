---
title: 'An Experiment on Code Structure'
date: 2019-11-10T04:31:00+01:00
draft: false
---

Let’s say you want some software built. So you hire a team of smart developers, tell them what to build, and leave them alone. Inputs will be needed in the form of computer hardware, pizza and coffee. Of course, you expect outputs in the form of status updates (no one outside the team will understand the updates, but that’s beside the point). Since you hired smart developers and gave them everything they need, you can be sure they’ll do a good job in no more time than necessary, so you don’t to bother them with schedules and such. Time passes and the hardware requests shift from desktop PCs to servers. Pizza and coffee are required at all hours. The status updates are more frequent and more cryptic. And you just know that it must be close to done. Finally there’s a knock on your office door. It’s the lead dev. He apparently hasn’t slept in days, and hygiene was set aside long before that. He must be here to give you a demo of the shiny new software toy. But it’s not that, the codebase has deteriorated to the point that further development has become nearly impossible. The development team will need a few months “for refactoring”.

Unfortunately, something like this hypothetical scenario plays out over and over again. A decent group of programmers is given all they need, they make a mess, then they start talking about “technical debt” and “refactoring”.

A couple years ago, I was a developer on a team writing a REST API in Go. We had what we needed, there was no significant pressure, we were probably not idiots, and we tried to do a good job. It should have been perfect. But after a few months, development slowed considerably, and seemingly simple changes took great effort.

It’s hard to pin down where exactly we went wrong, but a few statements stick out in my mind:

*   _“This main package seems a little big. I think I’ll move all the code that converts data into a conversions package.”_ Consequently, `conversions` was intimately aware of every data structure in the project.
*   _“protobufs look cool._ This was hacked in, not as an isolated serialization method, but the existing data structures were replaced with auto-generated `protobuf` ones. Everything now knew about `protobufs`.
*   _“This is too slow, we need to add caching.”_ This was also hacked in without being isolated. Everything now knew about caching.

These weren’t all my decisions, but I did go along with them. The rest of the team left about that time (semi-voluntarily). So there I was with a messy codebase, no one to blame but myself, and not much help to fix it. I’m sure we’ve all experienced a failure that snowballs into some ridiculous thoughts, but life got a bit dark around this point. Clearly I didn’t have future in software development, and the next logical step was to prepare myself for my inevitable new life in subsistence farming. But the man at the bank was unimpressed with my plan of repaying the mortgage with produce grown in the backyard. With no other leads for a lord that would accept me as a vassal, I had no choice but to fix the mess.

So I re-read [Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/) and [Refactoring](https://www.amazon.com/Refactoring-Improving-Design-Existing-Code/dp/0201485672) and did what I could. This [post from Ben Johnson](https://medium.com/@benbjohnson/standard-package-layout-7cdbc8391fc1), gave some specific ideas that helped a lot. It took a while, but eventually the project got back on track and it’s been mostly successful.

I’ve followed the structure from that blog post for every Go app I’ve begun since. It makes it pretty easy to follow the [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle). Organizing code around dependencies means the dependencies isolated and easy to replace. That isolation makes tests pretty easy to write. Overall it’s been good.

My only real complaint is the vigilance required keep people from mixing the layers together. Let’s say, someone needs some data in an HTTP handler. I haven’t met a programmer who’s first instinct is to add a function to the `app#Foobar` interface, implement the function in `app/mock#Foobar`, and `app/mysql#Foobar` (and perhaps `app/postgres#Foobar`, or something else), then call that new function from the HTTP handler. Everyone tries to find the MySQL client in the HTTP package. But they can’t find it, and if I don’t catch them in time, they’ll add it. Then they polish it up, take a deep breath of satisfaction and behold their creation. Which is about the time I waltz up and ask them to rewrite it.

The trouble is that code is structured for people, and if the people who have to use the structure don’t understand it, then the structure is no good. It’s a code equivalent of a [Norman door](https://99percentinvisible.org/article/norman-doors-dont-know-whether-push-pull-blame-design/).

So what can I do? Code structure seems largely subjective. But if the code I have now is like a song on the radio that no one likes, then the mess I had before was like a first-year violin student playing “Mary had a little lamb.” Which is to say, that even though what I have now is subjectively bad, what I had before was objectively worse.

There must be a better option, but I don’t know what it is. There’s been a lot written about what makes good code, which certainly has some good insights, but much of it is just expert opinion. Unfortunately, opinions are often wrong, and opinions are especially bad when there’s no immediate feedback, like in the case of software design (see Daniel Khaneman’s [Thinking Fast and Slow](https://www.amazon.com/Thinking-Fast-Slow-Daniel-Kahneman/dp/0374533555)). I wish there was a “code theory” similar to music theory or color theory that could tell us what people actually need in code.

An experiment
-------------

I’d really like to get away from the opinions and be able to say with confidence that one design is better than another. Or, at the very least, understand the trade-offs being made. So I decided to do an experiment. The goal is to find out if the style of program that I’ve been writing is really any better than an ad-hoc program that’s just kinda thrown together. The plan was to write the same program in two different ways, extend them both with the same features and see which one held up better. One would be in a “natural” style, which is whatever happened to fall out of the keyboard. The other would be structured in the style I’ve been using lately.

I needed a project which was moderately complicated. There wouldn’t be much to learn from two versions of “Hello, World!” And I’m just one guy without a lot of spare time, so I couldn’t do anything too complicated. I settled on a simple web app that displays historical stats on airplane flights. You can see it live at [flightranker.com](https://flightranker.com). The back-end code is on [github](https://github.com/pboyd/flightranker-backend) (the front-end code is an abomination I created while trying to learn React that will probably never see the light of day). The flight data came from the [US Bureau of Transportation Statistics](https://www.transtats.bts.gov/), and therefore the project is limited to domestic US flights.

The two back-ends are:

They both produce identical output, and take the same config. As close as I can make it they are functionally equivalent. They have a GraphQL interface, and all data is stored in the same MySQL database. Most of the work happens in SQL queries. The most complicated computation is probably calculating a percentage. But there’s lots of code to glue everything together, which is mostly what I’m interested in.

The first version just displayed the percentage of flights which were on time for a origin and destination airport. It’s easy to organize software when you know exactly what it will do when you start. I think the true test comes when software is extended in a way that wasn’t initially intended. So I picked some new behavior to implement.

Metrics
-------

I wanted to get some data about how the back-end was performing. So I instrumented the code with [Prometheus](https://prometheus.io/). This is the type of code tends to be sprinkled through a codebase and can make quite a mess.

The [`backendA` metrics implementation](https://github.com/pboyd/flightranker-backend/commit/4eb87ce2530f8f41656b5ca65eb9f2318adc0514) was straight-forward. I wrapped every GraphQL resolver function in another function to capture metrics. It’s not isolated, but it isn’t too hard to follow either.

[`backendB` metrics](https://github.com/pboyd/flightranker-backend/commit/6d21281cff2ee9dc78c362472d682eff86f6b7f2#diff-8067f538d9c8992c9e784a709cf08c78) weren’t much different. The diff is perhaps a little easier to follow, but it’s basically the same. Perhaps I should have made a new package to hold the metrics code? I did isolate the dependency on Prometheus, but only as a function not as a package.

Neither version is clearly better in this case.

Rollup
------

The flight data came as one record for each individual flight. I left it that way when I imported it into the database. Not surprisingly, asking MySQL to produce summary statistics for, say, every flight from LAX to JFK for a few years is a bit slow. It was almost OK for total stats, but I knew I wanted some graphs and that would slow it down beyond a reasonable level. So I rolled up that granular flight data into daily buckets that was faster to query ([cd81b](https://github.com/pboyd/flightranker-backend/commit/cd81b2bc591bd53578dde54059bd12f230dd35ec#diff-8067f538d9c8992c9e784a709cf08c78)).

The original version in both back-ends made two queries for the data before then merged the results. Now they just needed one query, so there was no merging required. Consequently this simplified the code and didn’t really tell me anything.

Daily charts
------------

Knowing that your flight is on time 80% of the time is neat, but people waiting in airports will need a little more info to fight off boredom. To that end, I wanted to plot the on-time percentages. For the back-end, that meant creating a new GraphQL query that produced stats grouped by day and airline.

The [code](https://github.com/pboyd/flightranker-backend/commit/4e64f5842b389c078edc19ced17695a4e8b58af0#diff-8067f538d9c8992c9e784a709cf08c78) is not too surprising. `backendA` has a new resolver function which queries the database itself and some configuration.

`backendB` required a bit more work. The `app#FlightStatsStore` interface got a new `DailyFlightStats` function, which was implemented in `app/mysql#Store`, and called by the (also new) `app/graphql#dailyFlightStatsQuery`.

I wrote unit tests for the `backendB` version, but not `backendA`. I could have written unit tests for `backendA`, but they wouldn’t have been much better than the integration test suite which runs for both back-ends, and it would have been a hassle.

I’m not which version is really better here either. `backendB` has a lot of parts, so the feature is spread over a few packages, but those parts were easy to test. Adding a new query like this would probably be a common task, and in `backendA` that was quick and straight-forward.

Monthly charts
--------------

The daily charts looked awful on the front-end. A line for each day was just visual noise and made me want to close the tab, not keep clicking around. I still liked the idea of a chart, so I decided to group flights by month instead. A flexible GraphQL query that let me group the results by any amount of time would be nice, but I don’t really need it. A simple monthly query will do for now.

I didn’t _need_ the daily query anymore, but I thought there might still be some value in it (especially if I add a date filter to it later), so I left it in. I did the same thing to add the monthly endpoint as I did for the daily endpoint. The [code](https://github.com/pboyd/flightranker-backend/commit/7e3653a4eeb45d4c94c530e657f843e337da0267#diff-8067f538d9c8992c9e784a709cf08c78) mostly was the same for both back-ends.

Cleanup
-------

I didn’t work on this all at once. I picked it up and put it down several times. I also worked on it when I should have been sleeping and when I couldn’t really focus on it. Consequently the code for both back-ends was beginning to be a mess.

`backendA`’s file names weren’t making sense to me anymore and some of the files had grown too large, so I [split them up](https://github.com/pboyd/flightranker-backend/commit/8791dce56f0e2a195f500ceb464dad4969b85c53#diff-0fc738ac862257f2d4fc2debc3e36085). It also acquired some duplicated code, which was simple enough to [fix](https://github.com/pboyd/flightranker-backend/commit/5831e2d862b23fc80f2b39935574605111b3b2ad#diff-0fc738ac862257f2d4fc2debc3e36085).

`backendB` had the same problems and was no easier or harder to [fix](https://github.com/pboyd/flightranker-backend/commit/85abc9f074ce3b398dbb130cdf8cfc5db181ab49).

I have to call this a toss-up too.

Results
-------

This experiment has been running a bit longer than I wanted it to, so I need to wrap it up. Unfortunately, I can’t really say which version is better. I could easily pick a feature that would be to the advantage of `backendB`, such as supporting Postgres, or adding a REST API. But in my experience big changes like that are rare, so I don’t think it’s fair to judge a codebase by them.

I suspect if I carried this on a while longer that `backendA` would eventually crack into an unmaintainable mess. But right now it’s a small program that’s easily understood and not hard to extend. It isn’t perfect, but neither is `backendB`. If I’ve learned anything from this experiment, it’s that I shouldn’t jump straight to a hierarchical structure. Especially when the program is well understood from the beginning and has a limited scope.

I don’t think this will change the way I write software. I like code that’s easy to unit test, and I think there’s enough value with that alone to make it worthwhile. I still don’t think `backendB` is very good, it’s just the best I know to do right now. I might try to improve the design in a `backendC` someday, but for now `backendB` will have to do.

Code quality is largely subjective, so if you’re willing to look this code over, and perhaps even hack on it a bit, I’d love to hear how it goes.

  
  
from Hacker News https://ift.tt/2NlTG5Y