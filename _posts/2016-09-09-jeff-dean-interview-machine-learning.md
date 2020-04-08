---
title: 'Jeff Dean interview: Machine learning trends in 2020'
date: 2019-12-16T08:11:00+01:00
draft: false
---

![](https://venturebeat.com/wp-content/uploads/2019/12/jeff-dean-google-ai.jpg?w=1200&strip=all "Google AI chief Jeff Dean interview: Machine learning trends in 2020 | VentureBeat")  

At the Neural Information Processing Systems (NeurIPS) conference this week in Vancouver, Canada, machine learning took center stage as 13,000 researchers explored things like neuroscience, how to interpret neural network outputs, and how AI can help solve big real-world problems.

With more than 1,400 works accepted for publication, you have to choose how to prioritize your time. For Google AI chief Jeff Dean, that means giving talks at workshops about how machine learning can help confront the threat posed by climate change and how machine learning is reshaping systems and semiconductors.

VentureBeat spoke with Dean Thursday about Google’s early work on the use of ML to create semiconductors for machine learning, the impact of [Google’s BERT](https://venturebeat.com/2019/09/26/google-ais-albert-claims-top-spot-in-multiple-nlp-performance-benchmarks/) on conversational AI, and machine learning trends to watch in 2020.

_This interview has been edited for brevity and clarity._

**VentureBeat****_:_** **So you’re going to be talking at the** [**Tackling Climate Change with Machine Learning workshop**](https://www.climatechange.ai/NeurIPS2019_workshop.html) **Saturday. Anything you can share ahead of your speech?**

**Jeff Dean:** That’s obviously a very broad space, and there’s a lot of potential for using machine learning to help tackle climate change-related topics or mitigate some of the effects. So we’re pretty excited about this. I think Google and the \[AI\] community in general \[are\] excited because it’s a serious problem, and also … one that has a lot of technical meat behind it. Like, how can we actually apply machine learning \[to\] some of these subproblems?

**VentureBeat: Do you get to go through the work that’s here \[at NeurIPS\]? I mean, I presume you didn’t sift through all the posters, but outside of stuff that was shown by Google was there anything that you were particularly excited about?**

**Dean:** Well, probably not quite all of the posters, but we have internal discussions about things people have seen that seem interesting. And I think the ML field as a whole is fairly prolific in its research output these days so it’s really hard to keep up, but one way is having lots of collective opinions about things that people see that seem important.

I just arrived yesterday, so I haven’t actually seen with my own eyes a lot of stuff, but I know other people have been interested in lots of other things.

**VentureBeat: I saw your** [**remarks last month on arXiv about the evolution of hardware**](https://arxiv.org/abs/1911.05289) **for machine learning that you’ll expand upon at the** [**ISSCC**](http://isscc.org/) **next month. What do you think are some of the things that in a post-[Moore’s Law](https://en.wikipedia.org/wiki/Moore's_law) world people are going to have to keep in mind?**

**Dean:** Well I think one thing that’s been shown to be pretty effective is specialization of chips to do certain kinds of computation that you want to do that are not completely general purpose, like a general-purpose CPU. So we’ve seen a lot of benefit from more restricted computational models, like GPUs or even TPUs, which are more restricted but really designed around what ML computations need to do. And that actually gets you a fair amount of performance advantage, relative to general-purpose CPUs. And so you’re then not getting the great increases we used to get in sort of the general fabrication process improving your year-over-year substantially. But we are getting significant architectural advantages by specialization.

**VentureBeat: You also got a little into the use of machine learning for the creation of machine learning hardware. Can you talk more about that?**

**Dean:** Yeah, the other talk I’m giving on Saturday is in the [ML for Systems workshop](http://mlforsystems.org/). And so one of the things I’ll talk about there is \[how\] we’ve been doing some early work on machine learning for ASIC chip design, in particular placement and routing. So you have a chip design, and then you have lots and lots of transistors and how they’re connected.

Basically, right now in the design process you have design tools that can help do some layout, but you have human placement and routing experts work with those design tools to kind of iterate many, many times over. It’s a multi-week process to actually go from the design you want to actually having it physically laid out on a chip with the right constraints in area and power and wire length and meeting all the design roles or whatever fabrication process you’re doing.

So it turns out that we have early evidence in some of our work that we can use machine learning to do much more automated placement and routing. And we can essentially have a machine learning model that learns to play the game of ASIC placement for a particular chip.

**VentureBeat: That’s pretty cool.**

**Dean:** Yeah, and we have, you know, good results on some of the internal chips that we’ve been experimenting with.

**VentureBeat: One of the things that’s come up a lot lately, you know, in the question of climate change — I was talking with Intel AI general manager Naveen Rao recently and he mentioned this idea \[that\] compute-per-watt should become a standard benchmark, for example, and some of the organizers here are talking about the notion of people being required to share the carbon footprint of the model that they trained for submissions here.**

**Dean:** Yeah, we’d be thrilled with that because all the stuff we trained in our Google Data Center — the carbon footprint is zero. Because … basically, all of our energy usage [comes from renewable sources](https://venturebeat.com/2018/11/20/google-to-invest-685-million-in-green-danish-datacenter/). So that would be great. I think other people might not be as excited.

**VentureBeat: I guess a criticism of larger models like** [**XLNet**](https://venturebeat.com/2019/06/21/google-brains-xlnet-bests-bert-at-20-nlp-tasks/) **or models of that nature is the amount of energy required to make and deploy them. I guess if it’s in a Google datacenter it would be carbon neutral, but outside of that context if somebody was using a large model …**

**Dean:** Yes, I think there’s a general point, which is \[that\] some of these large models are computationally intensive, and they’re reasonably expensive in terms of energy usage. And so I think it’s important for the community to look at what are more efficient algorithmic techniques we can have that make a particular model or outcome that we want … be achievable with less compute and less … energy input.

I think things like multitask learning and transfer learning are actually pretty effective algorithmic tools that we have that can improve energy usage, because you can train one model and then fine-tune it, or do multitask learning on a relatively small number of examples for a new task that you want to be good at. And that’s much better than starting from scratch every time, which is sort of mostly the current practice.

**VentureBeat: Something I know you’re passionate about is making sure that** [**researchers from Africa or Asia who were having issues with travel visas**](https://venturebeat.com/2019/11/09/canada-is-denying-travel-visas-to-ai-researchers-headed-to-neurips-again/) **getting here are able to do so, and the organizers talked a little bit about that earlier. But I was talking to someone who was still unable to get here earlier this week, and he suggested the idea of having at least one of the major conferences — like ICML or CVPR — in open border-type countries, places that have fewer issues as relates to getting a visa. What are your thoughts on that idea?**

**Dean:** I think we actually do want these conferences to be accessible to more people. I think there are sometimes issues with — no matter where you put a conference, there’s always going to be constraints on that. For example, sometimes students studying in the U.S. have trouble leaving the U.S. to go to a conference. So if you hold it outside the U.S. in a particular place, that sometimes creates complications.

Different countries have different policies, but I think having the major conferences rotate around where they’re held is a pretty sensible thing, so that not everyone is facing the same visa issues from the same places. But also, I think \[we need to be\] helping inform governments about why scientific exchange is important and why they should be willing to let people come to scientific conferences for a week or whatever.

**VentureBeat: This was a big year for BERT. BERT all over the place, and all different kinds of BERT. What are some of the variations of BERT that people should expect to see next, or what’s on the horizon?**

**Dean:** BERT is interesting because it builds on sort of a progression of other research results. So, BERT sort of depends on the Transformer work that was done the year before. Transformer work is really kind of a take on the same problem that the earlier sequence LSTM-based models were looking at. And that whole research thread I think has been, you know, quite fruitful in terms of actually yielding machine learning models that \[let us now\] do more sophisticated NLP tasks than we used to be able to do. And the fine-tuning of BERT that’s pretrained on a bunch of text — arbitrary text — and then fine-tuned on a particular NLP task you care about is a nice paradigm for a lot of NLP problems that we would like to be able to solve. And so within Google, we’re sort of looking at lots of different kinds of applications in our products. You know we just [rolled out some in the search stack to improve search quality.](https://www.blog.google/products/search/search-language-understanding-bert)

And I think you’re seeing that in the broader community, as well. We’d still like to be able to do much more contextual kinds of models. Like right now BERT and other models work well on hundreds of words, but not 10,000 words as context. So that’s kind of \[an\] interesting direction. I think multimodal kinds of models are pretty interesting — like can you combine text with imagery or audio or video in interesting ways? That’s something we’ve done a little bit of work on, the rest of the community has done a little bit of work on, but I think that’s going to become more important in the future. And I’m sure people will find improvements to the basic approach that BERT is taking. We have some minor or maybe even major improvements.

So the basic research thrusts will continue. The use of what we now know how to do will continue to be sort of a good set of applications, both within Google and outside. We’re pretty excited.

**VentureBeat: Yeah, I followed a lot of the sort of** [**MT-DNN**](https://venturebeat.com/2019/05/16/microsoft-makes-googles-bert-nlp-model-better/)**,** [**RoBERTta**](https://venturebeat.com/2019/07/29/facebook-ais-roberta-improves-googles-bert-pretraining-methods/)**, all that.**

**Dean:** Yeah, everyone has a cute play on the name. It’s hard to keep them all straight and remember exactly what wrinkle is here or there. I do kind of think there’s a bit of an overemphasis on — in the community — on sort of achieving ever-so-slightly better state-of-the-art results on particular problems, and a little underappreciation of completely different approaches to problems that maybe don’t get state of the art because it’s actually super hard and a pretty explored area.

**VentureBeat: Like robustness?**

**Dean:** Yeah, or like “What are completely different ways of solving a problem that we think is important, and show promise?” And if people then pursued those kinds of rough directions, it would be interesting.

**VentureBeat: Instead of trying to get to the top of the GLUE leaderboard?**

**Dean:** Yeah.

**VentureBeat: What do you feel are some of the technical or ethical challenges for Google in the year ahead?**

**Dean:** In terms of AI or ML, we’ve done a pretty reasonable job of getting a process in place by which we look at how we’re using machine learning in different product applications and areas consistent with the AI principles. That process has gotten better-tuned and oiled with things like model cards and things like that. I’m really happy to see those kinds of things. So I think those are good and emblematic of what we should be doing as a community.

And then I think in the areas of many of the principles, there \[are\] real open research directions. Like, we have kind of the best known practices for helping with fairness and bias and machine learning models or safety or privacy. But those are by no means solved problems, so we need to continue to do longer-term research in these areas to progress the state of the art while we currently apply the best known state-of-the-art techniques to what we do in an applied setting.

**VentureBeat: What are some of the trends you expect to emerge, or milestones you think may be surpassed in 2020 in AI?**

**Dean:** I think we’ll see much more multitask learning and multimodal learning, of sort of larger scales than has been previously tackled. I think that’ll be pretty interesting.

And I think there’s going to be a continued trend to getting more interesting on-device models — or sort of consumer devices, like phones or whatever — to work more effectively.

I think obviously AI-related principles-related work is going to be important. We’re a big enough research organization that we actually have lots of different thrusts we’re doing, so it’s hard to call out just one. But I think in general \[we’ll be\] progressing the state of the art, doing basic fundamental research to advance our capabilities in lots of important areas we’re looking at, like NLP or language models or vision or multimodal things. But also then collaborating with our colleagues and product teams to get some of the research that is ready for product application to allow them to build interesting features and products. And \[we’ll be\] doing kind of new things that Google doesn’t currently have products in but are sort of interesting applications of ML, like the chip design work we’ve been doing.

**VentureBeat: Like** [**everyday robots**](https://venturebeat.com/2019/11/21/alphabets-trash-sorting-robots-have-reduced-office-waste-contamination-to-less-than-5/)**?**

**Dean:** Yeah, we have a pretty extensive robotics research effort. I think robotics is a really hard problem — to make robots that operate in sort of arbitrary environments, like a big conference room with chairs and stuff. But, you know, the fact that we’ve been making a fair amount of progress on that in the last few years, I think that’s an interesting research direction as well. We have a pretty big research effort.

  
  
from Hacker News https://ift.tt/2YLVVUb