---
title: 'Declarative assembly of web applications from pre-defined concepts'
date: 2019-12-06T03:40:00+01:00
draft: false
---

[Declarative assembly of web applications from predefined concepts](https://spderosso.github.io/onward19.pdf) De Rosso et al., _Onward! 2019_

I chose this paper to challenge my own thinking. I’m not really a fan of low-code / no-code / just drag-and-drop-from-our-catalogue forms of application development. My fear is that all too often it’s like jumping on a motorbike and tearing off at great speed (rapid initial progress), only to ride around a bend and find a brick wall across the road in front of you. That doesn’t normally end well. I’ve seen enough generations of CASE (remember that acronym?), component-based software development, reusable software catalogues etc. to develop a healthy scepticism: lowest-common denominators, awkward or missing round-tripping behaviour, terrible debugging experiences, catalogues full of junk components, inability to accommodate custom behaviours not foreseen by the framework/component developers, limited reuse opportunities in practice compared to theory, and so on.

The thing is, on one level I know that I’m wrong. To start with, there’s Grady Booch’s observation that “_the whole history of computer science is one of ever rising levels of abstraction_” [1](https://blog.acolyer.org/2019/12/04/declarative-assembly-of-web-applications-from-pre-defined-concepts/#fn-9385-1). Then there’s the changing demographic of software building. Heather Miller recently gave a great presentation on this topic, ‘[The times they are a changin’](https://speakerdeck.com/heathermiller/the-times-they-are-a-changin)‘. To quote from her presentation:

> There’s a tidal wave of newcomers entering our profession, and it’s not going to slow down. It’s going to pick up speed. – Heather Miller.

We’re also doing a pretty good job at reuse, and messy catalogues full of junk components don’t actually seem to be a problem in practice, so long as the ‘good stuff’ is readily identifiable (think package managers / ‘there’s a gem for that’). Another data point from Miller’s presentation: in 2018 57-70% of the average software project comprises open source components, and that fraction is rising fast. “_We largely glue together open source components now (we didn’t do this as much, not even like 3 years ago)_.”

As a final data point, low-code companies have been able to build sizeable businesses, e.g. Appian valued at $2.89B as I write, and Mendix acquired by Siemens for $700M in 2018.

So, it’s important on a number of levels to keep pushing on rising the level of abstraction. For me, the winning hand will have to combine both technical and social frameworks – supporting, encouraging, and growing a healthy ecosystem is a necessary ingredient of success here.

### The paper!

Onto the paper! Let’s find out what De Rosso et al, have to say about the ‘Declarative assembly of web applications from predefined concepts.’

> A new approach to web application development is presented, in which an application is constructed by configuring and composing concepts drawn from a catalog developed by experts.

The platform (framework) for building these applications is called Déjà Vu, and the unit of abstraction in Déjà Vu is a _Concept_. Concepts are more closely aligned with _application features_ than with e.g. class-level components. Examples are commenting, scoring, and so on. Concepts are embodied as microservices:

> A Déjà Vu application is a set of concept instances that run in parallel. Each instance is a full stack service in its own right, with front-end GUI components, a back-end server and data storage, and all the code necessary to coordinate them. By default these services run entirely independently of one another, in complete isolation.

I’ve called them microservices here, but the authors are at pains to point out that concepts are more fine-grained that traditional plug-ins or microservices.

> Abstractly, a concept instance is a state machine that changes state only in response to actions issued by the user through the front-end.

A bit like actors-with-front-ends then? And surely we’d want to generalise to event sourcing patterns where not all events have to originate in a user action?

The integration of two or more concepts is achieved by defining a common identifier to bind the distinct views. That’s going to present challenges with atomic changes across concepts. The more fine-grained your ~components~ concepts are, the more that matters. The authors include a transaction mechanism, but it’s not clear to me how it coordinates updates across the independent concept backends.

> What’s new in this work is what the parts are — full-stack implementations of concepts — and how they are put together — by declarative synchronization.

Here’s an example configuration file for a Hacker News clone called _Slacker News_.

![](https://adriancolyer.files.wordpress.com/2019/12/deja-vu-figure-2.jpeg?w=480)

Alongside pre-defined concepts, an application may include components of its own. Authoring application components involves the creation of a web component using a templating language for property binding. Application components may in turn be composed of other application components and concepts.

![](https://adriancolyer.files.wordpress.com/2019/12/deja-vu-figure-3.jpeg?w=520)

A key distinction between application components and concepts is that application components are front-end only, all back-end functionality is pushed to concepts. (Make those concept instances shared across apps, and it starts to look a lot like a back-end-as-a-service play…).

The special `tx` application component is used to wrap concept actions (across concepts) in a transaction. When every concept is its own independent full-stack implementation, we’re going to need each concept back-end to be able to act as a resource manager in a distributed transaction for this to work? The paper is silent on this issue.

### Déjà Vu in action

There’s a bit more detail about the Déjà Vu programming model in the paper, but not much. The prototype implementation is built in TypeScript, Angular, and Node.js, and includes a concept library with the following concepts:

![](https://adriancolyer.files.wordpress.com/2019/12/deja-vu-table-1.jpeg?w=520)

There are both monolith (all concept backends in a single Node.js app?) and microservice based backends. So I guess we should infer that concepts are logically independent, but can be physically deployed in the same app and fate-sharing.

To test building applications using Déjà Vu, the authors attempted to reproduce 12 student applications originally created as part of a Fall’16 undergraduate course.

![](https://adriancolyer.files.wordpress.com/2019/12/deja-vu-table-2.jpeg?w=520)

The median number of concept types used to implement the apps was 6, with a median of 9 concept _instances_ (some apps use multiple instances of a concept).

![](https://adriancolyer.files.wordpress.com/2019/12/deja-vu-table-3.jpeg?w=520)

The original projects each represented 200-400 person-hours of work. I was looking for some data to see how much effort it took to rebuild these projects with Déjà Vu, but couldn’t find it in the paper. Instead the main evaluation results seem to focus on the fact that it was possible.

The old chestnut of behaviour not foreseen by the framework / component developer raises its head, with a classic framework developer response too!

> We noticed that it becomes evident when some project deviates from what you’d expect the normal behavior of certain functionality to be… it raises an interesting research question — which we have yet to explore — about whether deviations from the norm (where “norm” is functionality that can be built by combining concepts Déjà Vu-style) represent design flaws in the application or the invention of a novel concept.

Yep, you read that right. If the thing you’re trying to build doesn’t fit with our framework, you probably have a design flaw!

Another classic question concerns the curation and evolution of the concept catalog. Is this an open repository that will gradually fill up with noise, or a carefully curated catalog — in which case who curates it and how does this scale?

> To avoid overlapping functionality between concepts, we only add a new concept to the catalog if there is no other concept with a similar purpose, and we only add functionality to a concept if such functionality cannot be obtained by combining the concept with other concepts. But having simpler and more orthogonal concepts can mean more work combining them.

Future work for Déjà Vu includes building a graphical programming environment to allow developers to build applications without explicitly having to write any binding or configuration code.

I still have nearly all the questions I started this piece with. At the same time, by engaging with the paper and the topic I’m getting clearer in my own mind as to what my requirements for a future application composition system would be. To quote Grady Booch one more time: “_the whole history of computer science is one of ever rising levels of abstraction_.”

  
  
from Hacker News https://ift.tt/2DGEpXx