---
title: 'Strategies for Long Projects'
date: 2019-09-30T05:22:00+01:00
draft: false
---

28 Sep 2019

Strategies for Long Projects

I’m in the middle of three multi-month to a year projects right now:

*   Writing a book
*   Running a marathon
*   Building a new API

Each I started months ago and have found brutally difficult in unique ways. For each, progress is often times non-visible and the visible progress is incremental. Running is frequently an exercise in watching your pace go up and down with no discernible reason for the zigs and zags. Many days feel like regressions. Direction can and will change - in writing my book, I’ve changed the plot significantly three different times. Each resulted in a substantial rewrite. Project goals are often moving targets. As is the case with almost everything, unexpected obstacles crop up that you didn’t forecast. Software is a living example here - when you have dependencies (and what software project doesn’t?), changes in those dependencies are changes you must adjust to.

The saving grace here is that simply putting in the hours usually moves you closer to the goal. Failure is higher probability when time or effort on a project decreases. As a result, I think time budgeting and attitude make an enormous difference. Most of the ideas below deal with one or both. As I like to point out in all of my blog posts that prescribe behavior, the below is stuff that has worked for me and your mileage may vary. Here we go:

**Relentless, irrational optimism is the only attitude that works**

Something that seems trivial turns out to be nearly impossible. Mile 5 of a 20 mile run hurts like heck. A third party library massively changed its API. That programming language feature you were confident would resolve your issue doesn’t behave the way the docs said. Unexpected events are going to happen, and while you can’t control these events, you can control your response to them.

“In the space between stimulus (whap happens) and response, lies our freedom to choose,” [writes Stephen Covey](https://www.goodreads.com/quotes/459654-in-the-space-between-stimulus-what-happens-and-how-we). Taking the time to craft your response when an unexpected event occurs is the opportunity to frame that event as opposed to letting that event frame you. I can’t stress how important I think this idea is - a bad reaction to new information can kill a project in its tracks. I look back on a few of the side projects I’ve stopped working on because I found some library or business that was doing the same thing. In retrospect, I understand that markets can have a large number of competing participants (check out the 10 different rent-a-cars near any major airport). It’s human nature to react negatively to information that isn’t congruent with our expectations. Taking time to respond to new information in addition to expecting the unexpected are strong defenses against negativity.

Moreover, I believe that choosing to feel something can make you feel that way even if the feeling is artificially manufactured. What I mean by this is that when someone asks us to label how we feel, the label we select is based on how we physically feel at the moment. But what if you said the exact opposite of how you actually felt? Is it possible the re-labeling could become reality? This seems absurd on the face of it, but my experience has been that re-labeling works and causes an actual physical response.

Of course, taking time and choosing a response is only part of the equation. The other part is infusing such responses with optimism, even if the optimism is a little irrational. I’m not advocating here for pie in the sky optimism - I’ll never run a sub four minute mile. What I am advocating for is optimism that represents a reasonable and possible outcome, even if a few things would have to fall into place for that outcome to happen. After all, our negative responses generally _assume_ a few things would have to happen for that outcome to play out, so it’s fair to make assumptions on the upside.

As an example, let’s assume some third party you rely on changed its API and is deprecating the old API in a month. A negative response would implicitly assume that the required changes would take X days and just cause churn in the codebase. A positive response might assume Y days (< X) and that the new API included performance and other improvements AND that doing this refactor could be the subject of a blog post or tech talk that could be used to recruit great engineers or land consulting contracts.

For the relentless optimist, every setback is 1) never as bad as it seems on the surface and 2) an opportunity in disguise. This view is healthier than the alternative, which is guaranteed to sap energy and fail to identify opportunities embedded in the unexpected event.

**Documenting each day shows progress that would otherwise be hidden**

`CHANGELOG`s in software are great. They serve as a living document that traces the life of a project. It answers the question “What have the maintainers of this project been doing?” A personal changelog or journal can answer these same questions and prevent the negative feelings that can arise from feeling that a project is going nowhere.

The reason these feelings arise can be that we just forget the past. For software, I’ve found this is often the time it takes to learn a new technology or understand the source code from a project you’re expected to contribute to. Both take significant time, but once you’ve acquired the skills, it then becomes easy to say “Why did take me so long?" Personal changelogs I think should be extremely detailed and include things like:

> Spent five hours going through source of repo Y and looking at Stack Overflow and documentation. Tried and failed several times to refactor code - got some cryptic errors with a stack trace I didn’t understand. Finally talked to Bob and found out some this is expected behavior and the workaround is to use a forked version of library XYZ AND to set some environment variables to specific values. This isn’t documented anywhere, so I took the time to document it. Still working on refactoring code.

The fact of the matter is that starting a project is extremely difficult - perhaps more difficult than the middle and end stages of long projects. Learning new things and creating new ideas and patterns requires time, often far more time than implementing the ideas and pattern.

When a project is a group project, this time might even have some multiplier on it. _Agreeing_ on new patterns and ideas is perhaps no less difficult than thinking of those ideas and patterns in the first place. A mentor of mine also showed me recently that new groups often regress a bit in the early stages of forming new practices and adjusting to each others’ work patterns - [these stages are called “forming” and “storming”](https://en.wikipedia.org/wiki/Tuckman%27s_stages_of_group_development). Group dynamics take time to get right.

Changelogs are a way to document things that are easy to forget. When I get discouraged at the pace of a project, looking at my changelog / journal often helps me understand why things have played out the way they have.

**Compounding matters a lot**

Compounding generally is discussed in a financial context where interest accrues interest. For software, the equivalent here is developer tools you took time to write being used by you and your teams (code gen, scripts, deploy orchestration, etc.). For running, it’s increasing your V02max and being able to sustain the same effort for a longer time. In each case, the initial time investment saves time down the line and results in new opportunities that may save even more time. Time saved results in new work that saves more time that results in more new work and so on. This is a positive feedback loop.

David Goggins in his book [_Can’t Hurt Me_](https://www.amazon.com/Cant-Hurt-Me-Master-Your/dp/1544512287) talks about a memory bank that can be drawn on in times of adversity (or really any time). For each obstacle conquered in pursuit of your goal, you have created a memory that can help you overcome future obstacles. I’ve found this most evident in running - continually doing long runs has made it easier to push through pain. “I can’t believe I have four miles to go” over time has slowly become “I only have four miles to go”. The memory bank re-frames what mileage means. Just like compound interest, positive memories help accrue more positive memories which accrue more positive memories. Some athletes call this “building a base”. The base sets what is normal. By continually increasing the floor that is normal behavior, long-term projects can deliver compounding.

**Finding the time means being extremely defensive of your time**

Time is finite. It can be uncomfortable to accept this and act as a fierce guardian of your own time, as doing so may include declining social invitations. I recommend watching [Tim Urban’s TED talk](https://www.youtube.com/watch?v=arj7oStGLkU) on procrastination. Tim envisions time as a series of 10 minutes blocks - giving up any of those blocks mean that block is lost forever.

I think when I’ve talked about this point with friends and family, their reaction is that doing this means becoming an anti-social hermit and making some tradeoff that’s harmful to you. That hasn’t been my experience when I’ve acted in defense of my long-term projects. In fact, _not_ acting in defense of my long-term projects has felt harmful to me. Falling behind on a project that’s important to me introduces feelings of guilt and frustration.

Importantly, I think life’s many priorities can be balanced with long-term projects. It has been written that Walter Isaacson wrote many of his books on vacations with friends and family. He would slip away for a few hours at a time, and no one really noticed. He had a great time on these vacations and it seems like nobody was negatively impacted by his small absences.

* * *

I wanted to conclude by saying I truly believe long-term projects can lead to transformative returns, even if they fail. Trying to run a marathon, for instance, has brought me into contact with dozens of runners at work and in a running club I go to I probably never would’ve met otherwise. Meeting these runners has led to relationships that have helped me on non-running projects. It’s obviously helped me a ton with my running. I think I’ve witnessed first hand that ambitious projects generate supportive responses from people - on the marathon, the book and the new API, countless people have offered their support, and I’ve been glad to take it.

I want to encourage myself and anyone reading this to keep trying things that are hard and take a long time. It will be tempting to quit, but overcoming that temptation could be the best decision you ever make.

  

![scribble](http://benbrostoff.github.io/images/scribble3.png)

  
  
from Hacker News https://ift.tt/2nvvbJ6