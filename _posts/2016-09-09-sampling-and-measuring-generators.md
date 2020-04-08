---
title: 'Sampling and Measuring Generators: Tutorial'
date: 2019-10-21T02:47:00+01:00
draft: false
---

_[< Back to Index](http://www.possibilityspace.org/index.html)_

![](http://www.possibilityspace.org/tutorial-sampling/header.png)

### Tutorial: Sampling And Measuring Generators

_Posted October 4th, 2019_

[In the first part of this tutorial series we learned about _generative space_ and _possibility space_](http://www.possibilityspace.org/tutorial-generative-possibility-space/), and what the difference between them is. In this part we’ll see how we can understand the generative space of a procedural generator by _sampling_ it. We'll see how we can automate this process, and then talk about what that makes easier (and what it makes harder).

Measuring Our Generators
------------------------

You know, it's important to live healthily especially if you're often stuck at a desk coding. Here’s a simple salad recipe for you, in case you want to make a quick snack while we go through this tutorial. Per person, mix into a big bowl:

*   A handful of cherry tomatoes, roughly sliced
*   A quarter of a lettuce, chopped
*   Half a pepper, chopped
*   4-8 green olives, halved
*   A bit of grated carrot

Whenever I prepare a salad I always make the same mistake - I taste a spoonful, decide there aren’t enough olives, and add in a handful or two more (I really like olives). Then when we sit down to eat, suddenly every spoonful is overflowing with olives. The mistake is thinking that the first spoonful is representative of the whole salad, when in reality the bowl is all jumbled up, and some areas will have more olives in than others.

This might sound familiar if you’ve ever made a procedural generator. For example, suppose we’re making a very simple level generator for a Mario-like platformer, and when we run it for the first time we see this:

  
![](http://www.possibilityspace.org/tutorial-sampling/example1.png)  
  

Notice anything? There aren't any enemies in the level! In our code for this level generator, any space that is empty and has solid ground underneath it has a _random chance_ to spawn an enemy on it. We didn't know what random chance to use at first, so we picked 10%. Given that there aren't any enemies, we probably need to increase that chance to make it more likely to happen. Let's double the chance, from 10% to 20%, and generate another level:

Is this fixed now? It definitely looks _better_, but we can't really know for sure. Just like tasting a spoonful of our salad, this level might not be representative of how our generator behaves. How can we get a better idea of what our generator is doing? Well, if we keep tasting our salad we eventually run out of salad, but fortunately we can test our generator all day long. Let's try that now, with an interactive example:

  
  

### Exercise: Measuring By Eye

Click on the level above or press R to generate a new one (if you're pressing R you might need to click once first). **Question: On average, how many enemies are in each level?** Generate as many or as few levels as you need to before continuing.

How did you do the calculation? Maybe you just estimated by eye a few times, maybe you actually kept a running total in your head, or even reached for a pen and paper? Whatever you did, I imagine you didn't do it for very long - it's quite boring.

Fortunately, calculating something like this is easy for a computer, and so we can automate this process of generating and inspecting levels. We can ask the computer to generate hundreds or thousands of levels, keep a running tally of the number of enemies as it goes, and calculate an average.

If we do that for the above generator, and sample a million levels, we get an average of **3.75** enemies per level. How close was your estimate?

Sampling And Representation
---------------------------

This process, where we study a few things from a larger group, is called _sampling_. The small bunch of things we take to study is called a _sample_ (in our case, the levels we're looking at). Our hope is that our sample resembles the larger group we took it from, and so if we measure something about the sample it will be similar to measuring the entire group. When a sample is small - like looking at a single level - it's not as _representatiive_ of the larger group; we might be looking at an outlier or a special extreme case. But as we increase the size of the sample, any measurements we take from the sample get closer to being what we would see if we measured the original, large group. One level might be an extreme outlier, but ten thousand levels in a row are unlikely to _all_ be outliers.

How big should a sample be before we can trust it? That depends on what we're measuring. In the example above one level wasn't enough, but a million levels was probably overkill. While bigger samples give more accurate results, they also take longer to compute. When you're doing your own sampling, you can experiment with different sample sizes to find a value that's a good tradeoff of accuracy and time.

For the rest of this tutorial, we'll be using a slightly smaller sample size than is ideal, mostly to make sure it doesn't take too long to run in your browser. It'll mean our results are a little less accurate, but it's a good tradeoff here to keep the tutorial interactive.

### Exercise: Sampling & Simple Relationships

Let's look at a live example of sampling and what we can learn from it. The interactive example below automatically samples 200 levels and calculates the average number of enemies, visible in the bottom-left of the window. We also have some buttons that can change settings in the generator, and whenever we do this it resamples it and calculates a new average. Let's try changing these settings, and see how the results of the sampling change!

  
  

Try pressing Q or W to change the chance that an enemy will spawn. Remember that enemies have a chance to spawn anywhere there is solid ground, including crates and powerup blocks. As you press Q and W, keep an eye on the sample average in the bottom left. **Question: What happens to the average number of enemies as you change this setting?**

What we see is that as we increase the chance of an enemy spawning in any tile, the average number of enemies increases in our sample - which makes perfect sense! We didn't really need sampling to know this, we probably had a hunch already, but it's good to confirm our ideas.

As a bonus detail, you can press the E key to resample the current generator without changing anything. Notice how the average enemies per level measurement changes? That's because each sample is slightly different, and so it has a slightly different average. If we had a bigger sample, these differences between measurements would be smaller, because each sample would be more accurate.

### Exercise: Indirect Relationships

The O and P keys change how likely there is to be a gap at any point in the level. The higher the parameter, the more gaps there are. **Question: What do you think will happen to the average number of enemies when you change this parameter?** Take a second to make a quick guess, and then change the parameter.

If you increase the chance of a gap in the level (O/P keys), you should see the average enemy count go _down_. One of the rules for enemy spawning is that they have to be placed on solid ground. More gaps mean less solid ground, which means fewer places an enemy could be spawned. Even though this parameter doesn't _directly_ control enemy spawns, it changes other parts of the generator which indirectly influence enemy placement. This is less obvious than the previous example we looked at!

Okay, just in case you've scrolled down past the example, here it is again so you don't have to keep scrolling back and forth:

  
  

### Exercise: Hidden Relationships

The K and L keys change how likely the height of the level will go up or down. At 0% you get a completely flat level, and at 100% the level spikes up and down with cliffs (with limits to ensure the player can always get over them). **Question: What do you think will happen to the average number of enemies when you change this parameter?** Have another think for a moment, and then change the parameter and see.

If you increase the parameter controlling height changes, you should see the average enemy count go down, just like the increased gaps. This might be surprising because the amount of ground isn't changing, but there's a small detail in this level generator I didn't mention.

When our generator spawns an enemy there's a small bonus chance it will spawn one or two extra enemies in a row. This creates little groups of enemies to challenge the player. However, it only does this if the ground continues in a flat line. That means that if we make the level less flat, there's less chance for these bonus enemies to spawn, and so the average number of enemies goes down, just by a little bit.

Now, in this example I hid that detail from you, but in reality every generative system is full of these accidental connections and hidden links between things. They're often the source of the most exciting and surprising things that these systems do, but they can also make it hard to predict or understand what a generator will do next. Imagine we had sat down to tweak our generator to make mountainous levels, and only discovered a week later that the levels had half as many enemies!

This is why little sampling tools are so useful - they're another tool for testing and understanding what you've build, just like you might write tests to check your software, or show a game to players to check if they like the controls. Software can get big and tangled and messy, and it's easy to miss subtle connections like this. One thing that took me a long time to learn: the time spent writing tools is almost always recovered in time saved using them.

Computer Problems
-----------------

The examples we've seen today show us how useful sampling can be in getting information about how our generator works. We saw how sampling by hand was slow and boring, but how we could improve it by getting the computer to sample for us. We can ask the computer to sample a million levels if we want, or build little tools that let us sample a generator as we edit it, which lets us fix mistakes and explore different possible configurations.

Automating this kind of analysis can be really powerful, but it also brings in new problems to be aware of, too. Before we close out today's tutorial, we'll look at two examples of this, and think about what they mean for us as designers of generative systems. We'll return to these questions in future tutorial episodes, to discuss the more philosophical aspects of making generative things.

### Measuring The Unmeasurable

Writing code to automatically sample a generator saves us a lot of time, as we've seen today, but it has one big requirement: we have to know what we're measuring. For instance, in the examples we saw today we were measuring the number of enemies per level. That's a really simple measurement that's easy to do - we can loop over every tile in the level and see if there's an enemy in it or not.

When we discuss a game we've played with our friends, or talk about an idea in a design meeting, we don't normally talk about things like "the average number of enemies in a level", though. We say things like "This game is so difficulty!" or "The loot you find is so cool!" How do we get a generator to measure how difficult a level is, or how cool an item is?

Ideas like this are subjective, and can't easily be expressed in code. What I find cool might be boring to someone else, and even if I just wanted to define my idea of 'cool' a lot of it will be subjective, emotional or subconscious. When we're automatically analysing generated content, we need to think about what we can actually measure, and always acknowledge the weaknesses of only measuring things with code.

A good thing to practice is to _never rely solely on automatic evaluation_. In our interactive examples, note how I always show you example levels whenever you change the generator, and it's easy to press R to see more. That means that even when you're changing settings and checking analysis, you also get to see a level for yourself. Keeping the person in the loop at all times is a good habit to get into.

We'll discuss the idea of measuring unmeasurable things, and the problems with handing control over to automated systems, in a future tutorial.

### Losing Detail

Even when we know what we're measuring, we can still encounter problems! Sampling normally involves crunching the samples down into a number that's easily digestible. In our case we calculated an average across a sample, but we might also be looking for the highest or lowest value seen in the sample, or finding in what percentage of the sample a certain thing is true.

Sometimes these analysis techniques can hide details from us, or mislead us. For example, below is an interactive example with two generators running side-by-side. Click on it or press R to generate new levels. Both generators average 5 enemies per level, but if you generate a few you'll see a big difference: the right-hand level always has _exactly_ 5 enemies in it, but the left-hand level varies from almost no enemies to ten or more!

  
  

An average is a good rule of thumb, but it can hide important details like how much each level varies from the average. Both of these levels look the same under our average-enemies analysis, but they feel very different to play. As we mentioned in the previous example, building tools that show the user output from the generator can help notice these problems.

Another way we can get around that is to build better tools that help us visualise and understand samples more clearly. We'll be looking at a very important way to do that in a future tutorial, called _Expressive Range Analysis_. Stay tuned for that one!

Summing Up
----------

Today we covered the following topics:

**Sampling**

Sampling is a way of looking at a small part of something to get an idea of what the rest of it is like. We can sample procedural generators by generating lots of outputs randomly. Measuring things about the sample can tell us what the generator is like.

The bigger our sample is, the more accurate our analysis will be. But bigger samples also take longer to generate. This can be really boring to do by hand, but we can write code to automate the process.

**Analysing Samples**

If we sample a generator before and after making a change, we can use the results from the samples to get extra information about what effect the change we made had on the generator.

Sometimes this is useful for confirming something we already knew; sometimes this helps us learn relationships between different parts of our code; and sometimes it totally surprises us with something we didn't expect!

**Sampling Isn't Always Enough**

At the end, we discussed a couple of important things to remember about sampling: that we can't always measure exactly what we want to; and that sampling can also mislead us.

Read More & Thanks
------------------

That's all for this tutorial! Don't forget that this tutorial is part of a larger series - [you can find part one here](http://www.possibilityspace.org/tutorial-generative-possibility-space/). If you want to ask me a question, make a suggestion or submit a correction, you can find ways to contact me [here](http://www.possibilityspace.org/contact.html).

Thanks to Chris, John and Adam for giving feedback on this tutorial!

Here are some handy links related to today's topics:

*   Darius Kazemi's superb [HTML5 Spelunky Level Generator](http://tinysubversions.com/spelunkyGen2/) lets you interactively generate levels and look at how many enemies, treasure or traps are in each level. We'll look more closely at Spelunky in a case study later on.
*   The algorithm for generating platformer levels in this tutorial was inspired by the examples in [the Mario AI framework](http://marioai.org/).
*   You can find a version of the sampling-based generator, with extra controls, in an open-source Processing sketch [here](https://github.com/possibilityspace/tutorial-sampling).

_Posted October 4th, 2019_

  
  
from Hacker News https://ift.tt/35T7Lz8