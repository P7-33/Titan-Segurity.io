---
title: 'The least common divisor and the greatest common multiple'
date: 2019-11-27T04:54:00+01:00
draft: false
---

  
  
from Hacker News https://ift.tt/33bcw4k

  
Sun, 24 Nov 2019

[The least common divisor and the greatest common multiple](https://blog.plover.com/math/gcm.html)  

One day Katara reported that her middle school math teacher had gone into a rage (whether real or facetious I don't know) about some kids’ use of the phrase “greatest common multiple”. “There is no greatest common multiple!” he shouted.

But that got me thinking. There isn't a greatest common multiple, but there certainly is a least common divisor; the least common divisor of !!a!! and !!b!! is !!1!!, for any !!a!! and !!b!!.

The least common multiple and greatest common divisor are beautifully dual, via the identity $$\\operatorname{lcm}(a,b)\\cdot\\gcd(a,b) = ab,$$ so if there's a simple least common divisor I'd expect there would be a greatest common multiple also. I puzzled over this for a minute and realized what is going on. Contrary to Katara's math teacher, there _is_ a greatest common multiple if you understand things properly.

There are two important orderings on the positive integers. One is the familiar total ordering by magnitude: $$0 ≤ 1≤ 2≤ 3≤ 4≤ \\ldots.$$ (The closely related !!\\lt!! is nearly the same: !!a\\lt b!! just means that !!a\\le b!! and !!a\\ne b!!.)

But there is another important ordering, more relevant here, in which the numbers are ordered not by magnitude but by divisibility. We say that !!a\\preceq b!! only when !!b!! is a multiple of !!a!!. This has many of the same familiar and comforting properties that !!\\le!! enjoys. Like !!\\le!!, it is reflexive. That is, !!a\\preceq a!! for all !!a!!, because !!a!! is a multiple of itself; it's !!a\\cdot 1!!.

!!\\preceq!! is also transitive: Whenever !!a\\preceq b!! and !!b\\preceq c!!, then also !!a\\preceq c!!, because if !!b!! is a multiple of !!a!!, and !!c!! is a multiple of !!b!!, then !!c!! is a multiple of !!a!!.

Like !!\\le!!, the !!\\preceq!! relation is also _antisymmetric_. We can have both !!a≤b!! and !!b≤a!!, but only if !!a=b!!. Similarly, we can have both !!a\\preceq b!! and !!b\\preceq a!! but only if !!a=b!!.

But unlike the familiar ordering, !!\\preceq!! is only a partial ordering. For any given !!a!! and !!b!! it must be the case that either !!a\\le b!! or !!b \\le a!!, with both occurring only in the case where !!a=b!!. !!\\preceq!! does not enjoy this property. For any given !!a!! or !!b!!, it might be the case that !!a\\preceq b!! or !!b\\preceq a!!, or both (if !!a=b!!) or neither. For example, neither of !!15\\preceq 10!! and !!10 \\preceq 15!! holds, because neither of !!10!! and !!15!! is a multiple of the other.

The total ordering !!≤!! lines up the numbers in an infinite queue, first !!0!!, then !!1!!, and so on to infinity, each one followed directly by its successor.

![as described in the previous paragraph](https://pic.blog.plover.com/math/gcm/regorder.png)

The partial ordering !!\\preceq!! is less rigid and more complex. It is not anything like an infinite queue, and it is much harder to draw. A fragment is shown below:

![one node for thirty of the first 42 positive integers, arranged in a complex graph; further description in the main text](https://pic.blog.plover.com/math/gcm/preorder.svg)

The nodes here have been arranged so that each number is to the left of all the numbers it divides. The number !!1!!, which divides every other number, is leftmost. The next layer has all the prime numbers, each one with a single arrow pointing to its single divisor !!1!!, although I've omitted most of them from the picture. The second layer has all the numbers of the form !!p^2!! and !!pq!! where !!p!! and !!q!! are primes: !!4, 6, 9, 10, 14, \\ldots!!, each one pointing to its prime divisors in the first layer. The third layer should have all the numbers of the form !!p^3, p^2q, !! and !!pqr!!, but I have shown only !!8, 12, 18, !! and !!20!!. The complete diagram would extend forever to the right.

In this graph, “least” and “greatest” have a sort-of-geometric interpretation, “least” roughly corresponding to “leftmost”. But you have to understand “leftmost” in the correct way: it really means “leftmost _along the arrows_”. In the picture !!11!! is left of !!4!!, but that doesn't count because it's not left of 4 along an arrow path. In the !!\\preceq!! ordering, !!11\\not \\preceq 4!! and !!4\\not \\preceq 11!!. Similarly “greatest” means “rightmost, but only along the arrows”.

A divisor of a number !!n!! is exactly a node that can be reached from !!n!! by following the arrows leftward. A common divisor of !!n!! and !!m!! is a node that can be reached from both !!n!! and !!m!!. And the greatest common divisor is the rightmost such node. For example, the greatest common divisor of !!12!! and !!16!! is the rightmost node that can be reached from both !!12!! and !!16!!; that's !!4!!. !!8!! is right of !!4!! but can't be reached from !!12!!. !!12!! is right of !!4!! but can't be reached from !!16!!. !!2!! can be reached from both, but !!4!! is right of !!2!!. So the greatest common divisor is !!4!!.

Is there a _least_ common divisor of !!n!! and !!m!!? Sure there is, it's the _leftmost_ node that can be reached from both !!n!! and !!m!!. Clearly, it's always !!1!!, regardless of what !!n!! and !!m!! are.

Going in the other direction, a multiple of !!n!! is a node from which you can reach !!n!! by following the arrows. A common multiple of !!n!! and !!m!! is one from which you can reach both !!n!! and !!m!!, and the least common multiple of !!n!! and !!m!! is the leftmost such node.

But what about the greatest common multiple, angrily denied by Katara's math teacher? It should be the rightmost node from which you can reach both !!n!! and !!m!!. The diagram extends infinitely far to the right, so surely there isn't a rightmost such node?

Not so! There is a rightmost node! !!0!! is a multiple of !!n!! for _every_ !!n!!, we have !!n \\preceq 0!! for every !!n!!, and so zero is to the right of _every_ other node. The diagram actually looks like this:

![The same as the previous, but with zero added on the right margin. There are no explicit connections with any of the other nodes, because in every case there are (infinite many) nodes on the path between, which are omitted from the diagram.](https://pic.blog.plover.com/math/gcm/preorder0.svg)

where I left out an infinite number of nodes in between !!0!! and the rest of the diagram.

It's a bit odd to think of !!0!! by itself there, all the way on the right, because in every other case, we have !!m \\preceq n!! only when !!m≤ n!!, and !!n=0!! is the exception. But when you're thinking about divisibility, that's how you have to think about it: !!1!! is least, as you expect, not because it's smallest but because it's a divisor of every number. And dually, !!0!! is greatest, because it's a multiple of every number.

So that's the answer. Consideration of the seemingly silly question of the greatest common multiple has led us to a better understanding of the multiplicative structure of the integers, and we see that there _is_ a greatest common multiple, which is exactly dual to the least common divisor, just as the least common multiple is dual to the greatest common divisor.

  

_\[[Other articles in category /math](https://blog.plover.com/math)\] [permanent link](https://blog.plover.com/math/gcm.html)_