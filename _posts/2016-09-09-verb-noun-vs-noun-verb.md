---
title: 'Verb-Noun vs. Noun-Verb'
date: 2019-10-17T06:02:00+01:00
draft: false
---

Friday, October 11, 2019

I went to the [Roguelike Celebration over the weekend](https://roguelike.club/event2019.html) and enjoyed Thomas Biskup's talk about Ultimate ADOM. Among the _many_ interface improvements they're making based on user testing is they're simplifying the controls from the traditional roguelike controls to W A S D + E F. I don't know how roguelike game players will respond to that but I'm a fan! This reminded me of two things from my past, so I thought I'd say a little about those.

Sometime in my teens I got to meet Lord British (Richard Garriott) and Iolo the Bard (David Watson). My mom was shopping, and I went to the computer aisle to browse the games I couldn't afford. Richard and Iolo were talking about Ultima 6. Nobody else was there, so I got to talk to them for half an hour! I learned about OOP, UI, testing, systems thinking, and more. Really cool!

They told me about how they coded puzzles to look for the _state of the world_ (nouns) instead of the _player actions_ (verbs). For example, there was a puzzle where they expected players to cast [Telekinesis](http://wiki.ultimacodex.com/wiki/Telekinesis) (ᚩᚣᛕ `ORT` `POR` `YLEM`) on a lever on the other side of a chasm. Instead, during playtesting, they saw that one player killed a party member, tossed the body over the chasm, cast [Resurrect](http://wiki.ultimacodex.com/wiki/Resurrect) (ᛁᛗᚳ `IN` `MANI` `CORP`), then have the party member pull the lever.

Wow! That wasn't something I had ever thought of in the simple games I had written at that age.

Another thing they told me about was the simpler control scheme. [Previous Ultimas had a control scheme](https://strategywiki.org/wiki/Ultima_V:_Warriors_of_Destiny/Controls) similar to what roguelike games have. W to wear armor, I to ignite a torch, K to klimb a ladder, D to descend a ladder, B to board a ship, etc. You specify the _verb_ such as J to jimmy a lock and then after that you can choose a noun such as the lock to jimmy.

[In Ultima 6](https://strategywiki.org/wiki/Ultima_VI:_The_False_Prophet/Controls) they reversed the order so that the noun came first and then the verb. This meant the game could tell whether you were trying to J jimmy a lock or B board a ship or K klimb a ladder because the game knew that it was a lock or a ship or a ladder. And that meant they didn't need separate keys for these verbs, but instead one key, U use object. There are times when they had multiple verbs for a noun but for the most part they could get away with just one.

I haven't closely followed Ultimate ADOM but I'm guessing they're doing something similar.

The noun-verb thing comes up in another context. After I stopped making games for a living I went into programming language research. My main topic was studying how functional programming languages and object-oriented programming languages can be combined. Something I noticed at the time was that the _syntax_ for functional languages tends to be _verb_ then _noun_: `f(x)`, whereas the syntax for object oriented languages tends to be _noun_ then _verb_: `x.f()`. At some level these can be considered equivalent. You can express with one what you can express with the other. There's a big difference in usability though: auto-complete.

What happens when we auto-complete `f(x)`? First we need to know all possible `f` that are valid in this context. Since the programmer has just started typing in the expression, _any_ function is valid, and that means there's a very long list to choose from. It takes many keystrokes to pick one. Second we need to know all possible `x` that are valid in this context. These are usually local names, so there aren't that many. Knowing the type of `f` narrows down the list but the list was already small, so there's not much to gain.

What happens when we auto-complete `x.f()`? First we need to know all possible `x`. The programmer has just started typing, so any local name is valid, but there aren't many. Typing just one character can narrow down the list to one or two elements. Second we need to know all possible `f` that are valid in this context. These are methods defined on the type of `x`, so there aren't that many compared to all possible functions. Knowing the type of `x` narrows down the list substantially, so there's a lot gained.

The two syntaxes seem equivalent in theory but they aren't in practice. I wonder if people who use regular text editors end up believing the two syntaxes are equivalent, whereas people who use IDEs prefer the object-oriented syntax, even if they're not taking advantage of object-oriented programming (inheritance, subtyping, etc.).

This asymmetry is orthogonal to whether you're using functional or object-oriented programming. It is better for programmers if they can choose from two medium length lists than to have to choose from a very long list (where a lot has to be typed before it's useful) and then a very short list (where not much is gained). You see this in other contexts too. Command line interfaces like DOS, VMS, and Unix shell typically specify a verb first and then the noun(s). GUIs such as Mac and Windows typically specify a noun first by clicking an icon, and then the verb by choosing from the right click menu. In text editors, vim's commands like `d0` are verb then text selection (noun), whereas in more conventional text editors (including Emacs) you'd first select some text (the noun) and then invoke a verb like delete. [Kakoune](http://kakoune.org/why-kakoune/why-kakoune.html) is a modal editor that uses noun-verb instead of verb-noun.

In games it seems like it'd be better for players to first choose an object from the environment and then choose from a small set of actions, than to first choose from a large set of actions and then choose from a set of objects. However I haven't surveyed enough games to see what's more common. The next time you're playing a game, look at the structure of commands to see if it's verb-noun or noun-verb.

Labels: [structure](https://simblob.blogspot.com/search/label/structure)

–

[Amit](http://www.redblobgames.com/)

– Friday, October 11, 2019

  
  
from Hacker News https://ift.tt/2OH0dcm