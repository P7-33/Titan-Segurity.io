---
title: 'The Electoral College and the Knapsack Problem'
date: 2019-09-30T03:42:00+01:00
draft: false
---

![](https://mike.place/images/default.png "The Electoral College and the knapsack problem")  

The Electoral College and the knapsack problem
==============================================

2017-02-11

What is the smallest number of Democrats that could have changed the outcome of the 2016 United States presidential election by relocating to another state? And where should they have moved?

It turns out this question is a variant of the [knapsack problem](https://en.wikipedia.org/wiki/Knapsack_problem), an [NP-hard](https://en.wikipedia.org/wiki/NP-hardness) computer science classic.

By solving it, we can show that Democrats win 21st century elections by relative landslides, while Republicans win by very narrow margins. And the 2016 election was the closest since 2000. Code and data is available in [`ecknapsack` on GitHub](https://github.com/williamsmj/ecknapsack).

The Electoral College
---------------------

Imagine that Democrats from California (or any other Democrat-rich state) strategically relocate to states won by the GOP in 2016.

Imagine further that nobody changes their vote: everyone who voted on November 8, 2016 votes again in 2020, and they vote for the same party. And everyone who stayed at home continues to stay at home. And there are no new voters. The only changes are people relocating from California (or any other Democrat-rich state) to states the GOP won in 2016. We’ll also assumes spherical cows and absolute zero for good measure.

Under these (ludicrous) assumptions, if 112,912 Californians move to Florida then the Democratic candidate would win that state by a single vote, and thus also win its 29 Electoral College votes (EVs).

Is Florida an efficient place for Democrats to focus efforts under these assumptions? Sure, it earns the winner a lot of EVs, but the Democrats would have to move have to move a relatively large number of people.

If the goal is to increase the Democrat EV total by at least 38, since Clinton won 232 EVs, and 270 are required to win, while also minimizing the number of people who have to move, this is a variant of the knapsack problem.

The knapsack problem
--------------------

In the vanilla knapsack problem we have a knapsack of capacity `W` and a collection of items, each of which has a weight and value. The goal is to select a subset of the items that can be placed in the knapsack without exceeding its capacity, while maximizing the total value of items in the knapsack.

Think of the “items” as the set of states won by the GOP in 2016. The EVs awarded by a state is its “weight”. The amount by which the Democrats would have to increase their vote in a state is its “value” (or price).

Now we have a problem very similar to the knapsack problem, which we’ll call the _complementary knapsack problem_ for reasons that will become clear.[1](https://mike.place/2017/ecknapsack/#fn:1) The aim is to choose the subset of states whose total “weight” (EVs) _exceeds_ some number (38 in the case of the 2016 election), while _minimizing_ their total “value” (or price, the number of people who have to relocate to change the outcome of the election).

An extremely elegant solution to the complementary knapsack problem (exceed `W` while minimizing total value) in terms of the vanilla knapsack problem (do not exceed `W` while maximizing total value) was [given by Amit Gross on Stack Overflow](http://stackoverflow.com/a/7950524/409879): simply solve the vanilla knapsack problem with the same set of items and a knapsack of capacity `Wtot - W`, where `Wtot` is the total weight of _all_ the items. The items _not_ selected for this knapsack, the _complement_, are the subset whose total weight exceeds `W` while minimizing their total value, so they are precisely those that solve our related problem!

Given a vanilla knapsack solver `knapsack()`, the following function solves the complementary knapsack problem.

```
def complementaryknapsack(items, W): ''' Solve complementary knapsack problem for an iterable of items and knapsack capacity W. Each item is a (label, value, weight) triple. Returns the items selected and their total value. ''' Wtot = sum(weight for label, value, weight in items) picks, _ = knapsack(items, Wtot - W) complement = [(label, value, weight) for label, value, weight in items if label not in [labelp for labelp, _, _ in picks]] complementvalue = sum(value for label, value, weight in complement) return complement, complementvalue 
```

The final piece of the puzzle is the vanilla knapsack solver itself, [`knapsack()`](https://github.com/williamsmj/ecknapsack/blob/master/ecknapsack.py#L71-L109). I won’t reproduce it here, but it’s a standard dynamic programming solution. Like `complementaryknapsack()` it takes an iterable `items`, each element of which is a `(label, value, weight)` triple, and a capacity, and returns the subset of items selected and their total value. I actually wrote this function a couple of years ago while taking [Tim Roughgarden’s algorithms course on Coursera](https://www.coursera.org/specializations/algorithms) (which I cannot recommend highly enough, incidentally).

The answer
----------

Back to the election. First I scraped the results from [Wikipedia](https://en.wikipedia.org/wiki/United_States_presidential_election,_2016).

```
>>> print(results2016) {'AK': {'dem': 116454, 'evs': 3, 'gop': 163387}, 'AL': {'dem': 729547, 'evs': 9, 'gop': 1318255}, 'AR': {'dem': 380494, 'evs': 6, 'gop': 684872}, 'AZ': {'dem': 1161167, 'evs': 11, 'gop': 1252401}, ... 'WA': {'dem': 1742718, 'evs': 12, 'gop': 1221747}, 'WI': {'dem': 1382536, 'evs': 10, 'gop': 1405284}, 'WV': {'dem': 188794, 'evs': 5, 'gop': 489371}, 'WY': {'dem': 55973, 'evs': 3, 'gop': 174419}} 
```

I then set up a couple of simple functions to determine the winner and loser, the states the loser lost, and the EVs required by the loser to change the outcome.

```
def winnerloser(results): '''Return ('gop', 'dem') if GOP won, else return ('dem', 'gop').''' demevs = sum(result['evs'] for state, result in results.items() if result['dem'] - result['gop'] > 0) gopevs = sum(result['evs'] for state, result in results.items() if result['gop'] - result['dem'] > 0) return ('gop', 'dem') if gopevs > demevs else ('dem', 'gop') def loststates(results): '''Return list of states lost by loser.''' winner, loser = winnerloser(results) return {state: result for state, result in results.items() if result[winner] > result[loser]} def evsreqd(results, total=538): '''Returns number of addional EVs required by loser to change outcome.''' lost = sum(result['evs'] for state, result in loststates(results).items()) won = total - lost reqd = total//2 + 1 - won return reqd 
```

Here they are in action:

```
>>> evsreqd(results2016) 38 
```

The function `findflips()` takes the results dictionary and turns it into a list of `(label, value, weight)` triples as required by `complementaryknapsack()`. It does this by computing `result[winner] - result[loser] + 1`, which is the number of additional votes the Democrats would need to change the outcome in that state. In terms of the complementary knapsack problem this is that state’s value (or price).

With the subset of states lost by the Democrats, the votes required to flip them, and their EVs in hand, we can apply `complementaryknapsack()`:

```
def findflips(results): winner, loser = winnerloser(results) items = [(state, result[winner] - result[loser] + 1, result['evs']) for state, result in loststates(results).items()] flips, _ = complementaryknapsack(items, evsreqd(results)) return flips def printresults(flips, loser='Democrats'): for flip in flips: print('Move {} {} to {} for {} EVs'.format(flip[1], loser, flip[0], flip[2])) print('Total of {} people for {} EVs'.format( sum(flip[1] for flip in flips), sum(flip[2] for flip in flips))) 
```

Finally, `printresults()` prints the solution:

```
>>> flips2016 = findflips(results2016) >>> printflips(flips2016) Move 22749 Democrats to WI for 10 EVs Move 44293 Democrats to PA for 20 EVs Move 10705 Democrats to MI for 16 EVs Total of 77747 people for 46 EVs 
```

So that’s the answer to the original question: by relocating 77747 people (22749, 44293 and 10705 Democrats from California to Wisconsin, Pennsylvania and Michigan respectively) you could have changed the outcome of the 2016 election.

Note that `findflips()` is very fast (~10ms according to `timeit`). It’s possible to solve a knapsack problem by brute force simply by trying all 2n subsets of the set of `n` items (i.e. iterating through the [powerset](https://docs.python.org/dev/library/itertools.html#itertools-recipes)). Needless to say, with `n = 30` that approach is not very quick. It does give the same answer though.

Other elections
---------------

The 2016 election was close enough in some big states that you could probably have figured out that the answer was Wisconsin, Pennsylvania and Michigan by eye.

And the same goes for 2000: that election famously hung on an incredibly tight outcome in Florida. Let’s just sanity check the code above:

```
>>> flips2000 = findflips(results2000) >>> printflips(flips2000) Move 538 Democrats to FL for 25 EVs Total of 538 people for 25 EVs 
```

But what about other elections? We can use `findflips()` to figure those out efficiently and correctly too.

### 2004

```
>>> flips2004 = findflips(results2004) >>> printflips(flips2004) Move 5989 Democrats to NM for 5 EVs Move 10060 Democrats to IA for 7 EVs Move 99524 Democrats to CO for 9 EVs Total of 115573 people for 21 EVs 
```

Pretty close! But not as close as 2016.

### 2008

```
>>> flips2008 = findflips(results2008) >>> printflips(flips2008, loser='Republicans') Move 28392 Republicans to IN for 11 EVs Move 68293 Republicans to NH for 4 EVs Move 146562 Republicans to IA for 7 EVs Move 236451 Republicans to FL for 27 EVs Move 262225 Republicans to OH for 20 EVs Move 14178 Republicans to NC for 15 EVs Move 234528 Republicans to VA for 13 EVs Total of 990629 people for 97 EVs 
```

It would be difficult to spot this set of states by eye, but with McCain’s 173 EVs they add up to exactly the 270 required for victory.

### 2012

```
>>> flips2012 = findflips(results2012) >>> printflips(flips2012, loser='Republicans') Move 67807 Republicans to NV for 6 EVs Move 79548 Republicans to NM for 5 EVs Move 39644 Republicans to NH for 4 EVs Move 74310 Republicans to FL for 29 EVs Move 166273 Republicans to OH for 18 EVs Total of 427582 people for 62 EVs 
```

Measuring the closeness of presidential elections
-------------------------------------------------

You can reasonably argue that the popular vote difference is not the right way to measure the closeness of a US presidential because candidates optimize for the Electoral College, not the popular vote. More to the point, for better or worse, it’s simply not how elections are decided.

The total number of people who need to move to change the outcome under our assumptions is an intuitive and much fairer metric of the closeness of a US presidential election.

By this metric, Democrats win 21st century elections by relative landslides, while Republicans win by very narrow margins. And the 2016 election was the closest since 2000, because no election since then could have had its outcome changed by moving fewer voters.

  
  
from Hacker News https://ift.tt/2yJalXW