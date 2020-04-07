---
title: 'Demos, Prototypes, and MVPs'
date: 2020-01-19T08:32:00+01:00
draft: false
---

Demos, Prototypes, and MVPs
---------------------------

Much of my work at [Hangar](https://hangar.is/) involves early product development,  
helping our startups "break ground" on their products. We're starting with little  
more than an idea, and maybe some theories from the research, and taking the first steps towards  
a marketable product. I'm usually building one of three things: a **demo**, a  
**prototype**, or a **minimum viable product** (MVP).

I've seen some confusion over these terms — some people seem to use them somewhat  
interchangeable. But they're not the same thing, and building one when you need another can  
cause problems.

I mean something very specific when I use these terms:

### Demo

Demos are essentially functional sales collateral. They're a bit of functional code perhaps  
backed up with static work like mockups or slides. They face potential customers: they exist to  
help close a deal.

Demos are designed to _demo_nstrate some specific flow through an app, or an important  
feature, etc. In the context of a fully-built product, a demo could is more like a tutorial or  
walkthrough, showing off how to use the product. In the context of early product development  
demos are usually only semi-functional: they're often a combination of some working code,  
some mocked up interfaces, and some static collateral like slides.

When I'm building a demo, I'm building to throw away. Speed is the most important  
factor; I want to ship something to unlock a deal, and do it as efficiently as possible. I choose  
technologies based on expediency, and rarely put much time into testing or QA.

### Prototype

Prototypes, on the other hand, are _internally-facing;_ they exist to help the business  
answer key questions like "can we even build this?" or "should we build X or Y?"

A prototype is similar to a demo in scope. But the audience and the goal make them fundamentally  
different. A prototype is used to prove that a product, feature, or approach is viable. They can  
be very rough, even barely working, as long as they serve their purpose. Demos, the other hand,  
usually need to look good; they're part of a sales pitch.

A concrete example: an iPython notebook makes a fine prototype. It's totally sufficient to  
prove the technical feasibility of some approach. But they make lousy demos. They're  
visually unappealing, very confusing to non-technical users, and I've never seen a notebook  
help close a deal.

Technology-wise, prototypes are similar to demos. Code's usually written to throw away, and  
testing/QA is an afterthought. But technology choice is more intentional: since the goal is to  
prove an approach, I'll usually want to use the toolset that I'd expect to use for a  
real product (or, failing that, something close). And sometimes the goal of a prototype is  
actually to try out a new toolset to see if it's viable.

### Minimum Viable Product

I wrote this whole essay to get to this point.

An MVP is completely unlike a demo or a prototype: an MVP is  
**a fully functional product** — albeit a "minimal" one. It's a  
complete product that an real customer can use, with minimal training or guidance.

There's a common **but** **totally wrong** analogy that "if  
you're building a car, the MVP is a skateboard". That's totally not accurate! If I  
want a car, and you give me a skateboard, I'm going to be really disappointed. An MVP should  
never disappoint.

[Nikki Lee](https://twitter.com/nkkl) has a much better analogy: if your product is a  
wedding cake, your MVP is a single layer:

> OK HERE SATISFIED? [pic.twitter.com/9gDW11oItP](https://t.co/9gDW11oItP)
> 
> — Nikki Lee (@nkkl)  
> [November 25, 2018](https://twitter.com/nkkl/status/1066571295784022016?ref_src=twsrc%5Etfw)

Don't take this to mean that if your product has a complex architectural design you should  
build it one (technical) layer at a time (e.g. the data store, then business logic, then views).  
Cakes and software are constructed differently. You almost certainly want to build your MVP so  
that it's a "vertical" slice through your software (a bit of data store, a dash of  
business logic, a couple-three views).

Figuring out the "minimum" version of your product is an art to itself, and out of  
scope for this article. Suffice to say that MVPs should be fully functional, and capable of  
delivering real value on their own. As such, MVPs require significantly more investment (time,  
mostly, but also money) than demos or prototypes. Think **months** (or years!) for  
an MVP, vs days/weeks for demos/prototypes.

I'll rarely plan to throw away code produced for an MVP; I'd hope that, if successful,  
we'd iterate and gradually evolve the MVP into the full vision of the product. So I'll  
choose my toolset much more carefully, and I'll invest the normal amount of effort into  
better practices like testing, CI, CD, and so forth.

Demos, prototypes, and MVPs all have their place in early product development. But they're  
not interchangeable, and trying to use one where you need the other is a recipe for failure.

  
  
from Hacker News https://ift.tt/2u73xFt