---
title: 'Go on an Adventure with “AI Dungeon
2” #ArtificialIntelligence #MachineLearning #NLP #Gaming @nickwalton00'
date: 2020-01-21T02:32:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/aidungeon-1-600x199.png)

The original “AI Dungeon” logo from aidungeon.io.

Late last year [Nick Walton](https://twitter.com/nickwalton00?ref_src=twsrc%5Etfw) [announced](https://twitter.com/nickwalton00/status/1211006356922101760) the release of “[AI Dungeon 2](https://www.aidungeon.io)” for your browser! In the original “[AI Dungeon](https://ai-adventure.appspot.com/)” game,  users were able to select storylines and choose preselected actions similar to “[Choose Your Own Adventure](https://en.wikipedia.org/wiki/Choose_Your_Own_Adventure)” books. In the current iteration, “AI Dungeon 2”, the responses are freeform text and it is up to the user to drive the game. The second version utilizes [OpenAI’s](https://openai.com/) 1.5B parameter [GPT-2](https://github.com/openai/gpt-2) model fine-tuned on text from [chooseyourstory.com](https://chooseyourstory.com/). The setting, characters and starting prompt are used as a seed but it can be directed from there.

In my test run, I ended up in a never-ending fantasy loop talking to animals, being attacked by wolves and getting poisoned fairies. In the example below, I narrowly escape a wolf attack by ‘hitting wolf with staff’. It’s also [possible to die quickly](https://twitter.com/jonathanfly/status/1216510864762843136) at the hand of a testy skeleton.

![](https://cdn-blog.adafruit.com/uploads/2020/01/Screen-Shot-2020-01-20-at-4.59.14-PM-600x274.png)

Excerpt from “AI Dungeon 2” documenting my wolf attack.

You can test the game out [here](https://play.aidungeon.io/). If you’d like to learn more about the model or the game design check out this [blog post](https://pcc.cs.byu.edu/2019/11/21/ai-dungeon-2-creating-infinitely-generated-text-adventures-with-deep-learning-language-models/). If you’d like to take a look at the code you can check out the [GitHub Repo](https://github.com/AIDungeon/AIDungeon) or the [Colab](https://colab.research.google.com/github/nickwalton/AIDungeon/blob/master/AIDungeon_2.ipynb).

##### _Written by Rebecca Minich, Product Analyst, Data Science at Google. Opinions expressed are solely my own and do not express the views or opinions of my employer._

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/2tE8961  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)