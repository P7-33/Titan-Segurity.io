---
title: 'When Goodharting Is Optimal'
date: 2020-01-17T04:32:00+01:00
draft: false
---

In this post, I'll argue that some of the behaviours that seem to be clear examples of the [Goodhart problem](https://www.lesswrong.com/posts/EbFABnst8LsidYs5Y/goodhart-taxonomy#Extremal_Goodhart), are in fact not. And they are, in some sense, perfectly optimal.

And, somewhat conversely, that the reason we fear Goodharted results are because we implicitly know that there is some key information about the reward functions that we have not been able to include.

Intro: a Goodhart example?
==========================

Consider the following situation, with a robot that can go left or right one square each turn (or stay put):

![](https://www.dropbox.com/s/qmu73xqplq7poxm/simple_robot.png?raw=1)

The reward function UL rewards the robot by 1 each turn it spends in the L (left) square, while UR similarly rewards the robot for each turn spend in the R square.

Suppose the robot puts 50.1% probability on UL being correct, and 49.9% probability on UR. Its optimal policy is then to go left, and stay in the left square forever.

So far, so Goodhart; this feels wrong that, because of such a small probability different, UR is essentially completely irrelevant. **But, in fact, both UL and UR think that that policy is optimal!**

That statement needs clarification, obviously. The reward UR would much prefer that the robot went right; failing that, it would prefer the robot alternated between L and R. But still, in a sense, it sees that the policy of going left is optimal.

To see how, define two reward functions to be mutually exclusive if one is always zero when the other is non-zero, like UL and UR are. Then, suppose you asked the following question to a UR\-optimiser:

*   "Suppose that a robot is uncertain between UR and one other reward function, which is mutually exclusive with UR. The robot has no further way of distinguishing between the two. The UR may be the most probable function or the least probable, both options are equally likely. Is it optimal for the robot to maximise the highest probability reward function (equivalently, to maximise the weighted sum of the reward functions)?"

And the answer to that, from the UR\-optimiser, is a bold **YES!!** That is an optimal policy, and better, from UR's expected perspective, from moving back and forth between L and R (since that looses reward while on the centre square).

Given those constraints, both reward functions would agree that policy is optimal _ex ante_ (before knowing the probabilities); UR would only disagree with it _ex post_ (after knowing the probabilities).

When to Goodhart, when not to
=============================

There are two other optimal policies for UR and UL. One is to optimise the least likely reward function; the third is to optimise a randomly chosen reward function. Note that, since it's not known in advance which reward function is the most likely, these three policies are essentially the same: pick a reward function at random and maximise that.

Still, the point remains: both reward functions agree (ex ante) that Goodharting is better than being "fair" between the options. Why do **we** then expect that Goodharting will be a disaster; and why do we so often want the AI to be more "fair" between the reward functions?

It's because the situations we consider are typically very different from the situation above. This post will explore the various reasons that this might be:

1.  Naive, maximum likelihood maximisation
2.  Ideal reward function unlikely
3.  Ideal reward function difficult to optimise (including extremal Goodhart)
4.  Diminishing returns

There is also the somewhat distinct situation of:

5.  Gains from trade between reward functions

But still, it needs to be repeated that:

*   **The reason we think Goodharting is bad, is because of some features we know about the reward/utility functions that we want**.

So let's start with one bad move: only maximising a single proxy.

1 Naive, maximum likelihood maximisation
----------------------------------------

In the description of the optimal policy above, I asked "Is it optimal for the robot to maximise the highest probability reward function (equivalently, to maximise the weighted sum of the reward functions)?"

But that is only "equivalent" because the different reward functions are mutually exclusive - you have to maximise one at the cost of the other. Combined with the fact that its equally easy to maximise either function, this means that maximising their weighted sum is the same as maximising the most likely.

But in general, that equivalence will not hold. Call maximising the highest probability reward function "maximum likelihood maximisation". In general, doing the Bayesian thing and maximising the probability-weighted sum of the reward functions, will be better than "maximum likelihood maximisation". You can see that as the contrast between the first and second options in [this post](https://www.lesswrong.com/posts/urZzJPwHtjewdKKHc/using-expected-utility-for-good-hart).

One of the reasons that "[regressional Goodhart](https://www.lesswrong.com/posts/EbFABnst8LsidYs5Y/goodhart-taxonomy#Regressional_Goodhart)" can often feel so tractable, is because the two approaches are often the same: the mean of the different possible reward functions is almost identical to the most likely reward function (ie mean ≈ mode). So the simpler, maximal likelihood maximisation, is often the correct approach.

So from now on, I'm assuming we'll be Bayesian about everything.

2 Ideal reward function unlikely
--------------------------------

Note that accepting the optimality of Goodharting relies on it being equally likely that UR and UL be the most probable or least probable. But this fails if we feel that, for some reason, our ideal reward function is likely to be given a lower probability.

And this is typically the case when we worry about AIs Goodharting a learning process. We typically think that the typical "proxy reward" will be over-simple, and will [neglect some crucial key features](https://www.lesswrong.com/posts/GNnHHmm8EzePmKzPk/value-is-fragile) of the ideal reward function. Then if there is any sort of complexity penalty, implicit or explicit, the ideal reward function is going to be given a lower probability than unsuitable alternatives.

In that case, it would be foolish to just be Bayesian about the reward function; we have a genuine problem, and we need to make the ideal reward function more likely somehow, or, as a second best option force the the AI to be more "fair" between the different reward functions.

An extreme version of this is when the ideal reward function is completely absent from the space of possible reward functions. This is typically the case when we rely on a few simple proxy functions that are somewhat aligned with what we want, on the test distribution. We know that there is going to be some Goodharting, maybe disastrous Goodharting, as we move on to new distributions, because the ideal reward function is just not a candidate there.

Solving this issue is probably the most important in this area.

3 Ideal reward function difficult to optimise
---------------------------------------------

The reward functions UL and UR are equally easy to optimise. But we might suspect that the ideal reward function could be difficult to optimise. This might be because we think it has complex requirements (making humans have genuinely flourishing lives), while many proxy candidates are much easier to optimise (increasing the "humans have flourishing lives" variable).

In that case, a Bayesian optimiser will divert resources to the easy-to-optimise reward functions, putting little effort into the other ones.

Note that we expect this to happen even if the ideal reward function is not particularly hard to optimise. If the AI considers many reward functions, it will find some that are easier to optimise, some harder. Similarly to the [winner's curse](https://en.wikipedia.org/wiki/Winner%27s_curse) in auctions, the AI's efforts will go to the few functions that are a) easy to optimise, and b) not too unlikely.

Note that _some_ versions of "[extremal Goodhart](https://www.lesswrong.com/posts/EbFABnst8LsidYs5Y/goodhart-taxonomy#Extremal_Goodhart)" come under this category. This is when the reward function can reach extremely high values in unforeseen and unusual situations - and thus will get optimised more than an "honest" reward function that extrapolates better.

This kind of problem has a clear solution: [re-normalisation](https://www.lesswrong.com/posts/qudmaMyRuQk2pHxtj/normalising-utility-as-willingness-to-pay) of all the reward functions. None of the [standard](https://www.lesswrong.com/posts/hBJCMWELaW6MxinYW/intertheoretic-utility-comparison) re-normalisation methods is [fully ideal](https://www.lesswrong.com/posts/GfMGa9e79AfDMLj36/best-utility-normalisation-method-to-date) (they all introduce their own small distortions), but they remove this problem entirely.

4 Diminishing returns
---------------------

In [this post](https://www.lesswrong.com/posts/urZzJPwHtjewdKKHc/using-expected-utility-for-good-hart) I showed that it can make a big difference if reward functions have diminishing returns.

The same applies here. Let's define U′L and U′R as UL and UR with mild diminishing returns. If the robot has spent nL turns on L, then then next time it is there, U′L will get 1/(log(nL)+1) rather than 1 (and similarly for U′R with nR, the number of turns the robot has spent on R).

This a very weakly diminishing return - the returns are almost linear (especially for large nL and nR).

To ensure that the robot actually reaches a decision, let's also give it a discount[\[1\]](https://www.lesswrong.com/posts/megKzKKsoecdYqwb7#fn-2rydkdsqWnGst24vB-1) rate γ<1 (this can also be seen as having a probability 1−γ that the experiment will end, at each turn).

Assume that the robot believes that U′L is correct with probability p′L\>0, and U′R with probability p′R\=1−p′L\>0.

Then for any γ, p′L, and p′R satisfying the above constraints, the optimal policy involves spending infinitely often on L and on R.

That behaviour seems a lot less... Goodharty. And it's also why we feel afraid of the standard Goodhart outcomes. If our ideal preferences were linear (and the issues above were solved), then there'd nothing to fear in a Goodhart outcome, just as UR found the robot's behaviour optimal ex ante.

It's because they are not linear that we fear Goodhart. We know that a universe with twice as much friendship but no fun - or the opposite, twice as much fun but no friendship - is not exactly equivalent with an ideal universe. A universe empty of humans or human-like beings is a failure, not just the zero of a linear scale.

To be more precise, since "non-linear" is a somewhat vague term ("non-linear in what, precisely?") I expect that if there are small changes a and b to a world w so that w+a+b is as good as w, then typically w+106a+106b will be (much) worse than w.

Thus part of our fear of Goodhart outcomes seems to me, to be that we are tacitly aware that our reward functions have diminishing returns while considering only linear reward functions in the problems we are working on.

The final section looks at a quite different issue, examining when we should allow Goodharting, even if the we haven't fully resolved the issues above.

5 Gains (and losses) from trade between reward functions
--------------------------------------------------------

As stated above, UL and UR are mutually exclusive, and there is no gains from trade between them: optimising one sacrifices optimising the other.

Let's assume a slightly more complicated setup, where gains from trade are possible:

![](https://www.dropbox.com/s/dus40v0f77j0jat/simple_robot_gains_from_trade.png?raw=1)

The top row is as before, but the UL gets 0.7 reward from LR and 0.5 reward from RL; UR gets the reverse, 0.7 from RL and 0.5 from LR.

In that case, despite the fact that 0.7 is quite a bit lower than 1, and the robot still finds UL the most likely reward function, the optimal policy is to go to LR and stay there.

Therefore, if there are many gains from trade between the different reward functions, Goodharting effects are not so bad. Even if we don't manage to solve all the issues mentioned above, we might be ok with a naive Bayesian approach.

Conversely, negative interactions between utilities make everything worse. Consider:

![](https://www.dropbox.com/s/840njoqsyy1d0nf/simple_robot_losses_from_trade.png?raw=1)

In this case, UL gets 1.5 from L−R and −0.1 from R−L, while UR does the opposite, getting 1.5 from R−L and −0.1 from L−R.

Then the optimal policy is to go for L−R, and thus punish the reward function UR. Though note that this is still what UR would agree to, ex ante.

So our tolerance for Goodhart-like effects depends on how we see the interactions between the reward functions. In practice, this is about the [shape of the Pareto boundary](https://en.wikipedia.org/wiki/Pareto_efficiency) - the set of policies such that you can't improve one reward function without making another worse. If this boundary is nice and rounded, then we expect that a "middle" outcome will be one where all reward functions get something, so small errors have small impacts:

![](https://www.dropbox.com/s/3nglkgzb0f3xxm1/rounded_pareto.png?raw=1)

The opposite happens when the Pareto boundary is flat, where "middle" outcomes are mixes between extremes; in that case, small errors are likely to throw the outcome to one end or the other:

![](https://www.dropbox.com/s/1zp664u67cqk4da/spiky_pareto.png?raw=1)

This worse case happens more often when the reward functions are antagonistic, such as "keep people happy" vs "negative utilitarianism", rather than just independent rewards competing over limited resources. This is especially relevant if we think there are "[fates worse than extinction](https://foundational-research.org/s-risks-talk-eag-boston-2017/)" possible in the future, given some of the possible reward functions.

Conclusion
==========

So, as long as:

1.  We use a Bayesian mix of reward functions rather than a maximum likelihood reward function.
2.  An ideal reward function is present in the space of possible reward functions, and is not penalised in probability.
3.  The different reward functions are normalised.
4.  If our ideal reward functions have diminishing returns, this fact is explicitly included in the learning process.

Then, we shouldn't unduly fear Goodhart effects (of course, we still need to incorporate as much as possible about our preferences into the AI's learning process). The second problem, making sure that there are no unusual penalties for ideal reward functions, seems the hardest to ensure.

If not all those conditions are met, then:

5.  The negative aspects of the Goodhart effect will be weaker if there are gains from trade and a rounded Pareto boundary.

* * *

1.  Without a discount rate, there is no optimal policy; the AI would want to "spend infinitely many turns on L, and **then** spend infinitely many turns on R", similarly to the "[heaven and hell problem](https://www.lesswrong.com/posts/PpTN7GP2FsPyHfKrs/naturalism-versus-unbounded-or-unmaximisable-utility-options)". [↩︎](https://www.lesswrong.com/posts/megKzKKsoecdYqwb7#fnref-2rydkdsqWnGst24vB-1)
    

  
  
from Hacker News https://ift.tt/373o2Bo