---
title: 'Rule of Three (Computer Programming)'
date: 2020-02-02T04:13:00+01:00
draft: false
---

**Rule of three** (_"Three strikes and you refactor"_) is a [code refactoring](https://en.wikipedia.org/wiki/Code_refactoring "Code refactoring") [rule of thumb](https://en.wikipedia.org/wiki/Rule_of_thumb "Rule of thumb") to decide when similar pieces of code should be refactored to avoid duplication. It states that two instances of similar code don't require refactoring, but when similar code is used three times, it should be extracted into a new procedure. The rule was popularised by [Martin Fowler](https://en.wikipedia.org/wiki/Martin_Fowler_(software_engineer) "Martin Fowler (software engineer)") in _Refactoring_[\[1\]](https://en.wikipedia.org/wiki/Rule_of_three_(computer_programming)#cite_note-1) and attributed to Don Roberts.

[Duplication](https://en.wikipedia.org/wiki/Code_duplication "Code duplication") is considered a bad practice in programming because it makes the code harder to [maintain](https://en.wikipedia.org/wiki/Software_maintenance "Software maintenance"). When the rule encoded in a replicated piece of code changes, whoever maintains the code will have to change it in all places correctly.

However, choosing an appropriate design to avoid duplication might benefit from more examples to see patterns in. Attempting premature refactoring risks selecting a wrong abstraction, which can result in worse code as new requirements emerge[\[2\]](https://en.wikipedia.org/wiki/Rule_of_three_(computer_programming)#cite_note-2) and will eventually need to be refactored again.

The rule implies that the cost of maintenance certainly outweighs the cost of refactoring and potential bad design when there are three copies, and may or may not if there are only two copies.

See also
--------

References
----------

External links
--------------

<img src="https://en.wikipedia.org/wiki/Special:CentralAutoLogin/start?type=1x1" alt="" title="" />

  
  
from Hacker News https://ift.tt/1PyBDoT