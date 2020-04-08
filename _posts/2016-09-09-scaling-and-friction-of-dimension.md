---
title: 'Scaling and the Friction of Dimension'
date: 2019-12-06T01:40:00+01:00
draft: false
---

If you’ve been in software development for a while, you know that small web applications are ill-suited for massive load. I’m writing this a few days after Black Friday in the US. This year, another large retailer had a site outage, losing tens of millions of dollars in expected sales. The retailer definitely didn’t have a small system, but it is easy to imagine that if their possible load had been much smaller, the system could have been simpler and everything would have gone ok.

Over the past few decades, the industry has gone through a number of cycles of innovation aimed directly at the problem of how to scale systems “up.” There are many approaches, but it’s worth asking why there’s a problem at all? Why don’t _things in the small_ just work when scaled up?

The most immediate answer is: physics. Code that runs in the physical world has a relationship with the physical world. It’s easy to miss this fact _in the small_, much like we can ignore relativistic effects when apples fall from trees, but interactions with the world are inevitable when we scale. Memory size, latency, computational speed, synchronization across distributed nodes.. there are many problems that can be solved with a screenful of code, but once _N grows large_ you have to alter your algorithm (or its packaging) to deal with all of the scaling issues imposed by atoms, photons and electrons.

This, in a nutshell, is why scaling is a problem in software; but we can go deeper.

One of the most important insights about scaling came from [Galileo Galilei](https://en.wikipedia.org/wiki/Galileo_Galilei) in the 17th century. While under house arrest at the end of his life he wrote a book called [Two New Sciences](https://en.wikipedia.org/wiki/Two_New_Sciences) that contained the following observation (sometimes called Galileo’s Scaling Law or the [Square-Cube Law](https://en.wikipedia.org/wiki/Square%E2%80%93cube_law)):

> the surface of a small solid is comparatively greater than that of a large one because the surface goes like the square of a linear dimension, but the volume goes like the cube

It’s such a simple statement but it is profound. In the world of physical objects we can’t build a skyscraper using the same materials, supports and ratios that we would when building a cottage. It would collapse because volume scales faster than surface area. Materials have somewhat fixed strengths — walls we build of brick simply won’t support a 50 story tower.

The same is true, by the way, of [biological structures](https://en.wikipedia.org/wiki/On_Being_the_Right_Size). Cheap sci-fi movies show us ants the size of elephants terrorizing cities, but if an ant actually was the size of a elephant it would collapse and become a puddle of goo. The material of the ant's exoskeleton simply isn’t strong enough to support the weight of the enclosed volume at that scale.

What does this have to do with software? Well, I think we deal with the same problem in software development — but _one dimension down_. In physical systems, volume grows faster than surface area but, in networked systems, there’s a tendency for the number of edges to grow faster than the number of nodes. For a graph of N nodes, the number of edges tends toward N2 as it becomes more connected.

**Galileo’s Scaling Law is about the tension between N2 and N3. In networks, scaling is about the tension between N and N2.**

Where do we see this tension in software development? I can think of two obvious places. One is the tension of team size implied by [Brook’s' Law](https://en.wikipedia.org/wiki/Brooks%27s_law) and the other is the tension of dependency in architecture.

Let’s look at Brook’s’ Law first.

In [The Mythical Man Month](https://en.wikipedia.org/wiki/The_Mythical_Man-Month), [Fred Brooks](https://en.wikipedia.org/wiki/Fred_Brooks) pointed out that adding people to a late project makes it later. It’s a useful observation, but the reasoning behind it is the important part. Brooks realized that number of communication paths in a team grows as the square of number of team members. Each time an additional person is added, potentially N-1 new relationships form — that can be costly. Worse, the cost of adding a team member grows each time we had one. The costs accelerate.

Outside of software development, we can see how communication costs can grow excessively as N grows large. It’s often quicker to reach consensus with smaller groups of people than with larger groups of people. Three people deciding where to go for dinner usually takes far less time than thirty people deciding. This is the [Universal Scalability Law](https://wso2.com/blog/research/scalability-modeling-using-universal-scalability-law) in a social context. It’s also why smaller teams tend to be better. Amazon’s [two-pizza team](http://blog.idonethis.com/two-pizza-team/) model is a good example of advice that aligns with these insights.

Architecture is another place where N2 has brutal effects. In code, we know that circular dependencies are bad, but aside from the directionality of dependencies, it’s better on balance for a component to have fewer dependencies on other components. When systems go bad, every piece starts to depend on every other piece. N components start to develop N2 connections between them. I called this _bad_ but I think it’s important to realize that is not a _sinister_ sort of _bad_, it’s just the natural way that systems grow. No developer is saying “oh, I want to mung up the system today” but there is a tendency toward connection in systems. You are working in component A and you find it needs something from library B. You get the benefit of having that capability from B but now you have a dependency on B. Connection is attractive.

We can see this in social systems too. Adding a person to a team gives the team the benefit of new skills, new perspectives, and another set of hands. But, when you add a person you have one more person to coordinate with. As N grows, you slow down. Then, you start to think about splitting the team. Even if you don’t consciously split teams, they tend to divide internally on an ad-hoc basis. In the social sciences, these subgroups are called _cliques_.

There’s a tension that grows as the number of pieces in a system grows if the pieces can connect. This doesn’t put an absolute bound on the number of pieces but it does increase costs as systems grow. At a certain point, the costs outweigh the benefits. In economics, this is [Ronald Coase’s](https://en.wikipedia.org/wiki/Ronald_Coase) [transaction cost theory of the firm](https://en.wikipedia.org/wiki/Theory_of_the_firm#Transaction_cost_theory). In software, it’s why we modularize. The [7 plus or minus two](https://en.wikipedia.org/wiki/The_Magical_Number_Seven,_Plus_or_Minus_Two)  
of our working memory is an area of reduced cost. The N things that can fit in your mind at once can be connected in N2 ways at low cost. As N grows, you wish for functions, classes and services to bound the scope of what you need to be aware of. [Dunbar’s Number](https://en.wikipedia.org/wiki/Dunbar%27s_number) is another example of the same tension of connection at the organizational level.

All of these tensions can be modeled as functions of the costs of edges in a graph. When the costs are zero and the benefits of connection are positive, N becomes N2 very quickly. As costs grow, systems break apart. They federate or form local hubs, creating the structure that we see.

Let’s go back to Galileo for a moment.

Galileo showed a relationship between N2 and N3. As N grows, structure needs to change when there are costs. The same relationship seems to hold for N and N2.

Maybe we can generalize this and say that there’s a friction between adjacent dimensions that generates structure.

  
  
from Hacker News https://ift.tt/2LjBFDU