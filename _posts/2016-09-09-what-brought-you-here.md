---
title: 'What Brought You Here?'
date: 2019-09-29T01:32:00+01:00
draft: false
---

What brought you here?
======================

Milan Curcic • Sep 28, 2019 • 3 min read

Everybody’s life path is steered by series of seemingly strange coincidences. Like weather, human lives are chaotic and unpredictable. By chaotic, I don’t mean disorderly and in disarray, but rather that [small changes at one time can lead to large changes down the road](https://en.wikipedia.org/wiki/Chaos_theory).

![](https://milancurcic.com/assets/noaa-sahara-dust.png)

_Enhanced color image of Saharan dust plume over the Atlantic ocean as seen from a geostationary satellite GOES-16. Source: NOAA Environmental Visualization Laboratory._

I think about what gets me to make certain turns and decisions in life. For example, co-founding [Cloudrun](https://cloudrun.co) with my friend Josh. What brought me here? On first thought, academic background in meteorology and oceanography, combined with experience in high-performance computing and interest in emerging technologies, made me aware of an unsolved problem in current practice of weather research and prediction and an opportunity for a paradigm-shifting solution.

To some extent, that’s true, but doesn’t tell the whole story — it’s just the setting. Within that setting, however, were a series of events that nudged me in certain directions. In late 2016, I was experimenting with functional programming patterns in Fortran — map, filter, reduce, that kind of stuff (I wrote later about it [here](https://milancurcic.com/2019/05/22/map-filter-reduce-in-fortran-2018.html)). Once I was happy with it, I uploaded the code and posted a link on Hacker News, a popular news board for [hackers](http://www.paulgraham.com/gba.html). To my surprise, the [functional-fortran post](https://news.ycombinator.com/item?id=13024702) gathered quite some attention. It reached #1 spot for almost an hour, and spent most of the day on top of the Show HN board. _Nudge_.

I wasn’t a regular on HN and this was my first post, so I was happy. #1 spot on HN? You’ve got to be kidding me. It was a generous blow of smoke up my ass, and my ego enjoyed it. However, this turned out to be much less important than the fact that I got to spend some more time reading HN in the next few days. A notably more popular post, about a service called [dply.co](https://news.ycombinator.com/item?id=13030603) (short for “deploy”, discontinued since) bubbled up to the top of HN the next day. Dply allowed you to create free, small, 2-hour Linux instances in the cloud with a few clicks of a button and without providing any payment info. I went to try it out, and two minutes later I was in an SSH session of Fedora in the cloud. _Nudge_.

Things felt completely familiar, and yet, this was my first time ever playing with a cloud instance. I’ve been reading about cloud computing, sure, and I’ve been exploring the AWS offerings, but I never knew what cloud computing looked or felt like. Huh, pretty cool — this was the good ole Linux environment I was used to. I had root access, so I could install any package. Fortran compiler? Works. How about a quick and dirty Flask web server? Sure! Digging further: A screen dump of `/proc/cpuinfo` revealed that the hardware was quite recent — latest generation Intel CPUs. Most HPC systems I worked on were one or more generations behind. And yet, these cloud instances had to be cheap enough for a service to offer them for free. _Nudge_.

The next week, I was talking on the phone with my friend and ex-roommate Josh. I was telling him about my experience with tinkering with cloud instances, and what the traditional HPC setting was like in contrast. It blew my mind that we’re still doing weather prediction like this: Bare metal hardware the size of your back yard; graduate students pulling their hair out with compilers, libraries, and job schedulers; setting up weather and ocean models of incredibly high complexity, with incredibly poor documentation. And that wasn’t the only pain point. Large parts of most HPC systems sat idly. Yet, in the cloud, you pay only for what you use. Back of the napkin calculation suggested huge potential savings if one used cloud instances over traditional HPC for weather simulations.

Why aren’t we doing things better than this? All the parts are there, we just need the plumbing and packaging (yeah right, like it’s that easy). I was surprised that nobody has built anything similar to date. I can remember this conversation and everything around it vividly. It was about 6:30pm on December 9, 2016. I was driving back from work and crossing the railroad tracks on NE 61st Street in Miami. It was overcast with a drizzle. Right there and then, Josh asked the question that steered our path: “Is this something I could help you with?” _Nudge_.

A few weeks later, we had the first set of prototype WRF runs in the cloud and a landing page with the email sign-up form. Fast-forward to today, we’re profitable with a few loyal customers, and steadily building our product and user base. No moving fast and breaking things here — just good, clean, fun software development and exceptional customer service. We’re learning by the pound and only getting better every day.

While it’s not surprising in retrospect how chaotic the journey turns out to be, it’s sure a lot of fun to trace back the path. Would we have started Cloudrun if I haven’t tinkered with functional programming in Fortran, posted it on Hacker News, discovered Dply and cloud computing, leading to thoughts about practical problems of weather prediction? Who knows? Maybe we’d do it 6 months later, maybe 3 years. Would I have worked on Cloudrun if I never met Josh? Probably not. No matter what, tracing your path back to what brought you here is helpful. It tells you about the setting and the circumstance that made the difference, what worked and what didn’t. In weather prediction, the uncertainty grows from the smallest scales to the large. Likewise, seemingly random circumstances nudge us toward our path.

So, what brought _you_ here?

  
  
from Hacker News https://ift.tt/2lU22GS