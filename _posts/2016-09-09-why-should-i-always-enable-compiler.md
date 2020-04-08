---
title: 'Why should I always enable compiler warnings?'
date: 2019-10-04T03:56:00+01:00
draft: false
---

![](https://cdn.sstatic.net/Sites/stackoverflow/img/apple-touch-icon@2.png?v=73d79a89bded "c++ - Why should I always enable compiler warnings? - Stack Overflow")  

C is, famously, a rather low-level language as HLLs go. C++, though it might seem to be a considerably higher-level language than C, still shares a number of its traits. And one of those traits is that the languages were designed by programmers, for programmers -- and, specifically, programmers who knew what they were doing.

\[For the rest of this answer I'm going to focus on C. Most of what I'll say also applies to C++, though perhaps not as strongly. Although as Bjarne Stroustrup has famously said, ["C makes it easy to shoot yourself in the foot; C++ makes it harder, but when you do it blows your whole leg off."](http://www.stroustrup.com/bs_faq.html#really-say-that)\]

If you know what you are doing -- _really_ know what you are doing -- sometimes you may have to "break the rules". But most of the time, most of us will agree that well-intentioned rules keep us all out of trouble, and that wantonly breaking those rules all the time is a bad idea.

But in C and C++, there are surprisingly large numbers of things you can do that are "bad ideas" but which aren't formally "against the rules". Sometimes they're a bad idea some of the time (but might be defensible other times); sometimes they're a bad idea virtually all of the time. But the tradition has always been _not_ to warn about these things -- because, again, the assumption is that programmers know what they are doing, they wouldn't be doing these things without a good reason, they'd be annoyed by a bunch of unnecessary warnings.

But of course not all programmers _really_ know what they're doing. And, in particular, every C programmer (no matter how experienced) goes through a phase of being a beginning C programmer. And even experienced C programmers can get careless and make mistakes.

Finally, experience has shown not only that programmers do make mistakes, but that these mistakes can have real, serious consequences. If you make a mistake, and the compiler doesn't warn you about it, and somehow the program doesn't immediately crash or do something obviously wrong because of it, the mistake can lurk there, hidden, sometimes for years, until it causes a _really_ big problem.

So it turns out that, most of the time, warnings are a good idea, after all. Even the experienced programmers have learned (actually, it's "_especially_ the experienced programmers have learned") that, on balance, the warnings tend to do more good than harm. For every time you did something wrong deliberately and the warning was a nuisance, there are probably at least ten times you did something wrong by accident and the warning saved you from further trouble. And most warnings can be disabled or worked around for those few times when you really want to do the "wrong" thing.

(A classic example of such a "mistake" is the test `if(a = b)`. Most of the time, this is a mistake, so most compilers these days warn about it -- some even by default. But if you _really_ wanted to both assign `b` to `a` and test the result, you can disable the warning by typing `if((a = b))`.)

The second question is, why would you want to ask the compiler to treat warnings as errors? I'd say it's because of human nature, specifically, the all-too-easy reaction of saying "Oh, that's just a warning, that's not so important, I'll clean that up later." But if you're a procrastinator (and I don't know about you, but I'm a _terrible_ procrastinator) it's easy to put off the necessarily cleanup for basically ever -- and if you get into the habit of ignoring warnings, it gets easier and easier to miss an _important_ warning message that's sitting there, unnoticed, in the midst of all the ones you're ignoring.

So asking the compiler to treat warnings as errors is a little trick you can play on yourself to get around this human foible.

Personally, I'm not as insistent about treating warnings as errors. (In fact, if I'm honest, I can say that I virtually never enable that options in my "personal" programming.) But you can be sure I've got that option enabled at work, where our style guide (which I wrote) mandates its use. And I would say -- I suspect most professional programmers would say -- that any shop that doesn't treat warnings as errors in C is behaving irresponsibly, is not adhering to commonly-accepted industry best practices.

  
  
from Hacker News https://ift.tt/2oDt46g