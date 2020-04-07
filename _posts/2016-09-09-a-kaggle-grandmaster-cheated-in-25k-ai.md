---
title: 'A Kaggle Grandmaster cheated in $25k AI contest with hidden code'
date: 2020-01-23T03:35:00+01:00
draft: false
---

**Special report** A Google-backed competition to develop machine-learning software to help abandoned animals find loving homes turned ugly – when it was revealed the winning team cheated.

PetFinder.my – a non-profit that lists profiles of dogs, cats, and other small creatures for people to adopt – devised the contest to “save homeless animals with creative AI solutions." The goal was to create an algorithm that could predict how quickly a pet would be adopted based on its profile details, from its photo to its breed, sex, size, age, and whether it had been vaccinated or not.

These predictions would be used to optimize and tweak future critters' profiles so that they are adopted as soon as possible. The algorithm would be trained using a set of profiles and how long each animal was listed on the web before it was adopted. Thus, the model should be able to work out from a given profile when the pet will likely be selected for adoption. If it's too long, changes can be made to make the pet more attractive, if possible.

A $25,000 (£19,000) prize pool was established to reward the best solutions, and the competition was hosted on Kaggle – a Google-owned platform used by more than a million netizens to build AI models, find and share datasets, and collaborate with fellow Kagglers.

### Euthanization

"In this competition you will be developing algorithms to predict the adoptability of pets – specifically, how quickly is a pet adopted,” the competition rules [said](https://www.kaggle.com/c/petfinder-adoption-prediction/overview). “If successful, they will be adapted into AI tools that will guide shelters and rescuers around the world on improving their pet profiles' appeal, reducing animal suffering and euthanization.”

A little more than 2,000 teams signed up in the challenge and submitted more than 3,000 entries: each group was given a training dataset of 15,000 PetFinder.my profiles and the time it took for the animals to be adopted after their information was posted online. After a few months, the teams were asked to submit their code. Each model was then tested on a second dataset made up of about 4,000 profiles that the models hadn’t previously seen before: their predictions for time-to-adoption were compared to the actual time taken. The entries were then [scored](https://www.kaggle.com/c/petfinder-adoption-prediction/overview/evaluation) by prediction performance.

In April 2019, the winning team was announced. It was a group called Bestpetting, led by a familiar name: Pavel Pleskov. He was a well-known Kaggler, ranked third in the leaderboard for all Kaggle competitions, and held the lofty title of [Grandmaster](https://www.kaggle.com/progression). He was described as “the best of the best.”

Bestpetting nabbed the highest prize of $10,000. The second-best team received $7,000, the third-placed team bagged $5,000, fourth place got $2,000, and fifth placed won $1,000.

Nobody batted an eyelid until a teenage student volunteered to put Bestpetting’s code into production for PetFinder.my. Then things went south.

### Enter the super-sleuth

Benjamin Minixhofer, a 19-year-old from Austria, had taken part in the challenge and finished sixth. After hopping on a call with Andy Koh, founder and CEO of Malaysia-based PetFinder.my, the teen agreed to work with the top teams to combine their techniques to create one overarching machine-learning-based system.

“I thought it'd be an interesting thing to do because I had never put a model into production before,” Minixhofer told _The Register_ this month. “I thought it’d be a good challenge.”

PetFinder.my’s ultimate goal was to take the best competition models and use them to develop tools that could be used to optimize profiles for pets in need of homes. To do that, Minixhofer needed to figure out what made, in the models' view, profiles more likable or unlikable: the photo, the text, and so on.

“I took a closer look at the winning model, obviously," he told us. "There was a big difference in score between the first and second place.”

When he started poking around in Bestpetting’s source code, he was troubled by a particular portion that made other models' performance dip when added to their code – an odd result. He realized that the function `majority_voting` was secretly hiding snippets of Python code that allowed Bestpetting to cheat.

### What's the best way to cheat? Ah, just look at the answers

The winning team had scraped and hashed thousands of pet profiles from PetFinder.my along with how long it took for each animal to get adopted. This table of hints was stashed among hashes of profiles from a Pixabay data set.

During testing by the competition judges, if the machine-learning system realized it was being shown a profile that matched one of the scraped PetFinder.my profiles, the software would, using the profile hash, look up the actual time taken for the animal to find a home in its table rather than predict it. Its prediction therefore wasn't a prediction: it was fact. Of all the profiles scraped, 3,500 were present in the testing dataset. Not bad coverage.

Here's a [full technical breakdown describing the cheat](https://www.kaggle.com/bminixhofer/how-bestpetting-cheated) for those who know Python.

![](https://regmedia.co.uk/2015/05/20/terminator_2_t1000_liquid_metal.jpg?x=174&y=115&crop=1)

You've been a Baidu boy! Tech giant caught cheating on AI tests
---------------------------------------------------------------

[READ MORE](https://www.theregister.co.uk/2015/06/05/youve_been_a_baidu_boy_tech_giant_caught_cheating_on_ai_tests/)

Pleskov and his teammates were clever enough to make sure their model wasn’t too good, and thus avoided raising suspicions. The code only peeked at the answers ten per cent of the time, enough to gain a competitive edge.

“They just encoded all the images they scraped, and incidentally 3,500 of them appeared in the test dataset. I guess they knew it was going to be from PetFinder.my’s website so there had to be some overlap,” Minixhofer explained to _El Reg_. He realized if Bestpetting hadn’t cheated, the team would have placed about a hundred or so in the leaderboard, nowhere close to first.

Perhaps the scandal would have been uncovered if Kaggle had scrutinized Pleskov’s code more closely. It was not the first time Pleskov had pulled such tricks.

Over a year ago, in a Kaggle competition to detect and flag bogus questions posted on Quora, a Q&A website, he described how he and his team achieved such a good score. “The solution is quite straightforward: we just scraped the answers,” he brazenly [boasted](https://www.kaggle.com/c/quora-insincere-questions-classification/discussion/80665).

Minixhofer alerted Koh, who then contacted Kaggle to report the fraud. Kaggle has since removed Pleskov’s account and banned him from the platform for violating its terms of use.

Pleskov was subsequently fired from his job at H2O.ai, a Silicon Valley software company, where he had been a data scientist for about four months.

Achieving a Grandmaster title on Kaggle is a prestigious achievement that engineers proudly show off in their CVs to get jobs. In fact, companies such as H2O.ai like to hire top Kagglers for specific projects, such as [building tools](https://www.h2o.ai/blog/ai-automatic-machine-learning-feature-engineering-interpretability/) for data scientists working on self-driving cars.

When it was publicly revealed this month that Pleskov and his team had been disqualified, he apologized and promised to return the $10,000 prize:

> 1\. We, as a team, would like to apologize to [@myPetFinder](https://twitter.com/myPetFinder?ref_src=twsrc%5Etfw) [@kaggle](https://twitter.com/kaggle?ref_src=twsrc%5Etfw) and the DS community for all the wrongdoings. I would also like to apologize to [@h2oai](https://twitter.com/h2oai?ref_src=twsrc%5Etfw) and all the Kaggle competitors for putting their reputation at risk.
> 
> — Pavel Pleskov (@ppleskov) [January 11, 2020](https://twitter.com/ppleskov/status/1215983188876709888?ref_src=twsrc%5Etfw)

“For me, it was never about the money but rather about the Kaggle points: a constant struggle of becoming #1 in rating had compromised my judgement,” Pleskov [continued](https://twitter.com/ppleskov/status/1215983328043708417). “Now, after the ban, I feel almost relieved that the race is over, and there are still a lot of thoughts to process and reflect upon. I hope at least some of you forgive me and hope other competitors will learn from my mistakes.”

Pleskov and Kaggle declined to comment for this piece.

“The Bestpetting team has issued an apology and offered to refund the prize money. We are currently awaiting their updates on the remittance,” PetFinder.my's Koh told _The Register_. ®

_**PS:** Have you spotted wrongdoing or data misuse in machine learning? Help us share your story: [drop us a line](mailto:kquach@theregister.co.uk)._

Sponsored: [Detecting cyber attacks as a small to medium business](https://go.theregister.co.uk/tl/1889/-8120/detecting-cyber-attacks-as-a-small-to-medium-business?td=wptl1889)

  
  
from Hacker News https://ift.tt/2NLq1mg