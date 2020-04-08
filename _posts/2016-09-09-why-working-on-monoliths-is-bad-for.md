---
title: 'Why Working on Monoliths Is Bad for Your Career'
date: 2019-10-22T01:56:00+01:00
draft: false
---

It’s a Tuesday morning and it’s time for another standup. It’s the 3rd time your company has tried to “become agile.” Your “Scrum Master” (and manager) is assigning tasks for the day and checking on why your team has been slipping the next feature release for the last month. Changing 10 modules across the monolith without breaking everything has turned out to be more challenging than expected (well, at least more challenging that management expected: You’d given your honest estimates and had them discounted by 30% because you were “clearly sandbagging” right?) You’re starting to wonder about this whole software development thing. Let me help you out: working on monoliths is bad for your career in the following ways.

### Working on Monoliths is Exciting in the Wrong Ways _And Boring in the Wrong Ones Too_

Deploying a new feature in a monolith is **an exciting time** not because the feature is great but because who knows what’s really going to happen when customers use it? Sure, you’ve got tens of thousands of tests. You have unit tests, systems tests, acceptance tests, smoke tests, but again and again, “surprising” things have happened, like when you didn’t figure out that database writes were silently failing for four hours, or that invoicing for a third of your customers was broken for a couple of months. So, deploys are exciting (in a dreadful kind of way).

Getting a new feature out to meet a customer need certainly starts off as exciting: You’ve heard what they needed and you want to make sure it makes the next monthly deploy. But then the planning process starts, and you discover that you’ll need to coordinate across three teams, best case, to make sure your changes don’t conflict with changes they’re planning to make — a recipe for code review and merge hell. Then comes actually making the changes… No one’s tried to use the data this way before and the object model dependencies are, to put it nicely, daunting. You miss the first deploy, then the second. The excitement of delivering something the customer needs slowly turns into the day-to-day grind of making another change, finding the tests that break after the test suite finishes an hour later, figuring out whether the issue is the tests or code, making another change, waiting another hour. It becomes boring.

A microservices environment, or even service-oriented architecture, is the opposite. Deploys are **boring** (on purpose). You did three today, you’ll do five tomorrow. Maybe you’ll have to rollback one or two, makes some fixes, and deploy again, but the **process** of getting features in front of customers is boring. The exciting thing is that you can hear a customer request, look at the code necessary to make the change, and deploy the change to get feedback in a couple of days if not hours.

Getting used to and internalizing the monolith cycle will make it a lot harder to even understand the microservices cycle, much less successfully get hired at the companies you’d like to work at.

### Working on Monoliths You’ll Miss Out on Modern Tooling and Techniques

![Why Working On Monoliths Is Bad For Your Career - 2](https://lightstep.com/blog/why-working-on-monoliths-is-bad-for-your-career/)  
Working on a monolith, you’ll get very familiar with object inheritance, especially whichever approach your current architects favor. You’ll probably learn a lot about debugging from logs. Perhaps enough about databases and SQL to be truly dangerous. You may learn about some cloud APIs and how to use their clients, perhaps a little bit about metrics. You will likely not learn about RPC frameworks, CI/CD, or distributed tracing.

When the question comes, either in a design meeting or an interview, about how to scale a system, you will not have the context nor the experience to answer it.

Working with microservices, you might end up less familiar with object inheritance or SQL, but you will learn how to rapidly and safely deploy software that spends time communicating with other software over unreliable networks. You’ll learn about thundering herds and circuit breaking. You’ll be able to talk about what’s involved in scaling a feature to 1000x the users. And that will open up many other opportunities not only for success in your career but also for continued growth.

### Working on Monoliths Means Working at Businesses That Have Had or Will Have Limited Success

I’m not going to tell you there aren’t successful businesses that are built on monoliths. I will tell you that being on a monolith has or is going to limit their success. The rate of change in a monolith is so much slower that if a competitor comes along and they’re able to create features at (conservatively) 3x the rate you’re able to, there will be business problems. The longer the business has been on a monolith, the more they’ve embedded how they think about what they sell, how they sell it, how it can be supported, into the object model and the development process. Every month, every year, it will be harder for them to change to stay ahead of, or even catch up to competitors. If or when the decision comes to split the monolith, be ready for years of the exciting/boring cycle and a high likelihood that you’ll end up with a **distributed monolith instead of microservices**.

Working in a microservices environment with (actual) microservice-sized codebases means that, if you need to, you can literally rewrite your business over the course of a couple years. It’s been done. You’ll move faster than your competitors, and, if you’ve hired a good platform / SRE team, with better availability too. Being able to adapt to changing business conditions, both **technologically and organizationally**, simply but dramatically increases the likelihood of the business’ success.

### Working on Monoliths Limits Your Growth

![Why Working On Monoliths Is Bad For Your Career - 4](https://lightstep.com/blog/why-working-on-monoliths-is-bad-for-your-career/)  
When you’re working on the same type of thing all the time, when you’re spending most of your day waiting for tests to run instead of understanding whether you’re meeting customer needs — your growth will be limited. As a team lead, maybe you’ll own a module, or, as an architect, an initiative, but you’ll rarely have the opportunity and challenge to take a perceived need and turn it into a working and highly scalable service. You won’t get to feel that sense of ownership, of success, of confidence, knowing that you have accomplished a serious piece of work and that you can do it again.

When you’re working with microservices, there will certainly be many opportunities to lead the development of a completely new service, to conceive of an API, discuss it with users, refine it, implement it, and scale it. You’ll know that you have the skills, that you know the process, that you can teach it to others. You will grow and you will help others grow. You’ll create connections that will lead to the next thing, and the next thing after that. You will grow, because that’s fundamentally the orientation of the organization.

### Conclusion

There are many good people working on monoliths. You may be one of them.

Microservices are not a magic dust of success, but, all things being equal, you will grow more, learn more, become a better developer, and be more successful at more successful businesses by choosing to work in environments embracing microservices.

  
  
from Hacker News https://ift.tt/2TelLx6