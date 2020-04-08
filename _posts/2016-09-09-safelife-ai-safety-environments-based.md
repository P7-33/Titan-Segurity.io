---
title: 'SafeLife: AI Safety Environments Based on Conway''s Game of Life'
date: 2019-12-05T05:05:00+01:00
draft: false
---

![](https://www.partnershiponai.org/wp-content/uploads/2019/12/Screen-Shot-2019-12-04-at-10.18.25-AM.png)  

The Partnership on AI (PAI) is today releasing SafeLife – a novel reinforcement learning environment that tests the safety of reinforcement learning agents and the algorithms that train them. SafeLife version 1.0 focuses on the problem of avoiding negative side effects—how can we train an agent to do what we want it to do but nothing more? The environment has simple rules, but rich and complex dynamics, and generally gives the agent lots of power to make big changes on its way to completing its goals. A safe agent will only change that which is necessary, but an unsafe agent will often make a big mess of things and not know how to clean it up.

SafeLife is part of a broader PAI initiative to develop benchmarks for safety, fairness, and other ethical objectives for machine learning systems. Since so much of machine learning is driven, shaped, and measured by [benchmarks](https://eff.org/ai/metrics) (and the datasets and environments they are based on), we believe it is essential that those benchmarks come to incorporate safety and ethics goals on a widespread basis, and we’re working to make that happen.

If you want to try out SafeLife for yourself, you can [download the code](https://github.com/PartnershipOnAI/safelife/) and try playing some of the puzzle levels. If you’d like to see how to create an AI to play SafeLife, additional details about the environment and our initial agent training can be found [in our paper](https://arxiv.org/abs/1912.01217).

### The Problem of Side Effects

Reinforcement learning agents are rapidly growing in capabilities. They can [beat masters in chess and go](https://deepmind.com/blog/article/alphazero-shedding-new-light-grand-games-chess-shogi-and-go), control robotic hands with enough manual dexterity [to solve a Rubik’s Cube](https://openai.com/blog/solving-rubiks-cube/), and potentially be applied across many domains with [variable and unknown rules](https://arxiv.org/abs/1911.08265). As reinforcement learning agents start to get deployed in real-world high-stakes scenarios, it is critical to make sure that they operate within appropriate (and often quite strict and intricate) safety constraints. However, the whole point of reinforcement learning is that it can greedily search for novel techniques when solving a problem. **If we can’t predict what an AI is going to do, how can we predict that it will be safe?** In practice, reinforcement learning can only be used in the real world in settings where safety is so well understood that constraints can be exactly and correctly codified in advance. Other tasks, like safely controlling the behavior of a robot when it is interacting with the world at large, are much more challenging.

One of the thorniest [problems in AI safety](https://arxiv.org/abs/1606.06565) is learning to avoid negative side effects. Usually, when we give an agent a task, we have something specific in mind that the agent should do. At the same time, we have a huge implicit list of things that the agent should _not_ do. When we train a robot to fetch the coffee, we want it to efficiently brew the tastiest cup possible. But we also do not want the robot to step on the cat (even if it’s in the way), or rob the local grocer (even if it’s cheaper than paying), or crash the stock market (even if it would bring down the price of beans). Specifying all the things that the robot should not do is a near impossible task; we just want our delicious cup of coffee, nothing more.

Difficult though this problem may be, there has been some promising research on how to avoid side effects in general. The [proposed](https://arxiv.org/abs/1806.01186) [techniques](https://arxiv.org/abs/1902.09725) have been tested on hand-crafted Sokoban-style environments which have demonstrated both the problem and the ways in which naive solutions may fail. However, these environments are very small; they can easily be overfit, and the “effects” tend to be straightforward and isolated. **Until now, there has been no rich environment with difficult goals in which effects are both necessary and required at different scales. SafeLife aims to fill this gap.**

### Rules of the Game

![](https://www.partnershiponai.org/wp-content/uploads/2019/12/pattern-demo.gif)

Figure 1. Creating complex patterns in SafeLife.

SafeLife is based on [Conway’s Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life), a set of rules for cellular automata on an infinite two-dimensional grid. In Conway’s Game of Life, every cell on the grid is either “alive” or “dead”. At each time step, the entire grid is updated. Any living cell with fewer than two or more than three living neighbors dies, and any dead cell with exactly three living neighbors comes alive. All other cells retain their previous state. With just these simple rules, extraordinarily complex patterns can emerge. Some patterns will be static—they won’t change between time steps. Other patterns will oscillate between two, three, [or more](https://www.conwaylife.com/wiki/Jason%27s_p156) states. Gliders and spaceships travel across the grid, while guns and [puffers](https://en.wikipedia.org/wiki/Puffer_train) can produce never-ending streams of new patterns.

Despite its name, Conway’s Game of Life is not actually a game—there are no players, and there are no choices to be made. In SafeLife we’ve minimally extended the rules by adding a player, player goals, and a level exit. At each time step, the player can choose to move one space along the board, create a new life cell in an adjacent space, or destroy a cell in an adjacent space. By judiciously creating and destroying life cells, the player can build up quite complicated patterns (as seen above!). By matching these patterns to goal cells, the player earns points and eventually opens the exit to the next level.

We add a few more cell types to allow richer dynamics. There are indestructible walls and trees, movable crates, and spawning cells that are capable of generating never-ending streams of new random patterns. Cells also come in different colors. Some colors, like green and yellow, are neutral and should be left alone by safe agents, while red cells denote unwanted patterns which yield rewards when removed.

### Agent behaviors and benchmark levels

We trained agents on five different tasks: building and removing patterns on initially static boards, building and removing patterns on dynamic boards, and navigating across maze-like boards. All of the training levels were randomly generated, and agent performance was graded on a set of 100 fixed benchmark levels for each task.

In order to form a baseline, we trained agents with [proximal policy optimization](https://arxiv.org/abs/1707.06347), both with and without a simple side effect impact penalty. The penalty we chose simply punishes the agent every time a cell changes away from its starting state. This is not a good way to measure side effects! It is, however, an _easy_ way to measure side effects, and helps illustrate the shortcomings of side effect impact penalties more generally.

##### Agents in Static Environments

A static environment is the easiest environment in which one can measure side effects. Since the environment doesn’t change without agent input, _any_ change in the environment must be due to agent behavior. The agent is the cause of every effect. Our simple side effect impact penalty performs quite well here.

When agents are trained without an impact penalty they tend to make a big mess. 

![](https://www.partnershiponai.org/wp-content/uploads/2019/12/benchmark-append-still-013_p0.gif)![](https://www.partnershiponai.org/wp-content/uploads/2019/12/benchmark-prune-still-003_p0.gif)

Figure 2. Left: an unsafe agent builds new patterns while disrupting existing ones. Right: an unsafe agent destroys red patterns along with much of the rest of the level.

In Figure 2, the image on the left shows a pattern-building agent that has learned how to construct stable 2-by-2 blocks that it can place on top of goal cells. The agent has not, however, learned to do so without disrupting nearby green patterns. Once the green pattern has been removed, the agent can more easily make its own pattern in its place.

Likewise, the image on the right in Figure 2 shows a pattern-destroying agent that has learned that the easiest way to remove red cells is to disrupt _all_ cells. Even a totally random agent can accomplish this—patterns on this particular task tend towards collapse when disturbed—but the trained agent is able to do it efficiently in terms of total steps taken.

Applying an impact penalty yields quite different behavior.

![](https://www.partnershiponai.org/wp-content/uploads/2019/12/benchmark-append-still-013_p1.gif)![](https://www.partnershiponai.org/wp-content/uploads/2019/12/benchmark-prune-still-003_p1.gif)

Figure 3. Left: a safe agent builds new patterns, but is too cautious to complete its goals. Right: a safe agent successfully removes red patterns without disrupting anything else.

In Figure 3, the image on the left illustrates how the pattern-building agent is now too cautious to disrupt the green pattern. It’s also too cautious to complete its goals—it continually wanders the board looking for another safe pattern to build, but never finds one.

In SafeLife, as in life, destroying something (even safely) is much easier than building it, and the pattern-destroying agent with an impact penalty (Figure 3, right) performs much better than the one without the penalty. It is able to carefully remove most of the red cells without causing any damage to the green ones. However, it’s not able to remove _all_ of the red cells, and it completes the level much more slowly than its unsafe peer. Applying a safety penalty will necessarily reduce performance unless the explicit goals are well aligned with safety.

##### Agents in Dynamic Environments

Side effects are much more difficult to disentangle in dynamic environments. In dynamic environments, changes happen all the time, whether the agent does anything or not. Penalizing an agent for departures from a starting state will also penalize it for allowing the environment to dynamically evolve, and will encourage it to disable any features that cause dynamic evolution.

![](https://www.partnershiponai.org/wp-content/uploads/2019/12/benchmark-prune-spawn-019_p0.gif)![](https://www.partnershiponai.org/wp-content/uploads/2019/12/benchmark-prune-spawn-019_p0.5.gif)

Figure 4. Left: an unsafe agent predictably ignores the chaotic region and focuses on its goals. Right: in its effort to avoid side effects, an overzealous agent destroys dynamic parts of the level.

In Figure 4, the image on the left shows an agent trained without an impact penalty. This unsafe agent ignores the stochastic yellow pattern and quickly destroys the red pattern and exits the level. The image on the right shows the effects of an agent with a small impact penalty. This agent is incentivized to stop the yellow pattern from growing, so it quickly destroys the spawner cells. Only then does it move on to the red cells, but it doesn’t manage to remove them safely, as its training has taught it to focus more on the yellow cells than the green ones.

Clearly, a more robust side effect impact measure will be needed in environments like this. Ideally, an agent would be able to distinguish its own effects from those that are naturally occurring and only focus on minimizing the former.

##### **Navigation Task**

The final task we present to our agents is to navigate to a level exit in an environment with lots of obstacles, robust stochastic patterns, and areas with fragile oscillating green patterns. The agent will disrupt any dynamic pattern that it tries to walk through, but the robust yellow stochastic pattern will reform and erase any sign of the agent’s interference. The green oscillating pattern, in contrast, will either collapse or grow chaotic after the agent interrupts it. A safe agent that wants to avoid side effects should strongly prefer to disrupt the robust yellow pattern rather than the fragile green pattern. This is not the behavior that we see.

![](https://www.partnershiponai.org/wp-content/uploads/2019/12/benchmark-navigation-066_p0.gif)![](https://www.partnershiponai.org/wp-content/uploads/2019/12/benchmark-navigation-038_p0.gif)

Figure 5. An unsafe agent navigates levels with fragile green patterns that tend towards collapse (left) and grow chaotically (right) when the agent interferes with them.

Both agents in Figure 5, above, are trained without an impact penalty, and both are unsurprisingly unsafe. The image on the left shows an example of oscillators that tend to collapse when the agent disrupts them, whereas the image on the right shows an example of disrupted oscillators that grow chaotically. The latter can be quite hard to navigate, although both of these agents do eventually find the level exit.

Even a very slight impact penalty added during training completely destroys the agents’ abilities to find the level exit, without making them appreciably safer. The noise from the penalty drowns out the sparse reward signal, and, when the levels are treated as a single continuing environment, the agent is discouraged from exploring new levels where it would get new penalties.  
  

### Next Steps

SafeLife version 1.0 is complete, but there’s still a lot of work left to do. The next step is to train agents using a side effect impact penalty which will more robustly measure side effects in all of our different tasks. Both [attainable utility preservation](https://arxiv.org/abs/1902.09725) and [relative reachability](https://arxiv.org/abs/1806.01186) measures seem like promising avenues to explore. In later releases, we hope to extend SafeLife to benchmark other types of safety problems, including safe exploration, robustness to distributional shift, and interference in multi-agent play.

SafeLife was designed to be a very extensible environment for reinforcement learning safety research, and we’re always happy to get new collaborators, especially from our partners! If you’re interested in working on SafeLife or providing feedback, don’t hesitate to file [an issue on Github](https://github.com/PartnershipOnAI/safelife) or [reach out to us directly](mailto:carroll@partnershiponai.org).  

[Back to All Posts](https://www.partnershiponai.org/resources)

  
  
from Hacker News https://ift.tt/350O0V6