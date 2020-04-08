---
title: 'Show HN: I created an algorithm to help me achieve Product-Market Fit'
date: 2019-10-30T04:12:00+01:00
draft: false
---

The **Main()** method is at the bottom of this post, and builds upon the preceding methods:

**synthesize.ks**

```
**synthesize(topic, timeToPeriodicallySynthesize){ while(\_uncertain OR timeToPeriodicallySynthesize){ **** var creativity = synthesizeNewResearchIntoKarma(topic); generateAndTestNewIdeas(creativity); timeToPeriodicallySynthesize = false;  
** **} }**
```

**hasAchievedProductMarketFit.ks**

```
**hasAchievedProductMarketFit(){ return ( 40%+ of users would be _highly_ disappointed if your product did not exist AND most users use your product daily AND the product is financially sustainable AND it feels like the market is pulling the product out of you AND you're almost dying from the organic exponential growth ); }**
```

**getCompatibleTraitsBehaviorsValues.ks**

```
**Consider who I personally connect with and enjoy associating with: getCompatibleTraitsBehaviorsValues() { return \[  
    "optimistic", "friendly", "compassionate", "shares content online", "reads nonfiction", "finds joy in learning and teaching", "wants to improve themselves", "wants to improve the world", "identifies as a lifelong learner", "disciplined", "creative", "unhostile", "enjoys reading and writing", "loves themselves", "appreciative", "gemeinschaftsgefühl", "acknowledges many of society's issues", "imagines that there are solutions to many of the society's issues", "sees education as a cure for many of society's issues" "enjoys empowering others", "healthy communicator", "growth mindset", "motivated to help other people", "has experienced a lot of pain", "desires data rights and privacy", "problem-centered", "autonomous", "high empathy", "technologist", "early adopter", "enjoys exercising intellect", "activism-curious"  
 \] }**
```

**getPersonas.ks**

```
**Consider what types of people generally align with my values: getPersonas(traitsBehaviorsValues){ **** return \[ "actively enrolled students", "educators", "volunteers", "educational bloggers", "frustrated Medium users", "any educational content producers", "authors", "self-educators", "activists", "technologists". "academics", "minority groups", "strategically introverted" \]  
****}**
```

  
**getAudiences.ks**

```
**Consider where I can access the people who I want to help: getAudiences(personas){ return \[ "university campuses", "university forums", "alumni networks", "educational blogs", "blogs for nonfiction writers", "blogs for teachers", "blogs for lifelong students", "teachers unions",** **"student unions", **** "study groups", "teacher forums", "self-educator forums", "activist forums", "student activists", "TED talk forums", "Khan Academy forums", "educational YouTube channels", \] }**
```

**getPainsIFeel.ks**

```
**Think about what pains emotionally resonate with me: getPainsIFeel(){ return \[ "I forget what I study", "I don't have time to read", "I hate doing academic work alone", "I wish I could improve my life and the lives of others", "I want to be a member of a vibrant, positive community", "My work isn't meaningful", "I want to have an impact", "I'm tired of unfair treatment and discrimination at work", "I feel a subtle sense of crisis about the world and its future", "I want to make my partner/children proud", "I want to self-actualize" \]  
}**
```

**karmaCanDefinitelyHelp.ks**

```
**karmaCanDefinitelyHelp(user){ return ( User NEEDS a place to connect with like-minded peers online OR User NEEDS a place to accelerate their self-education OR User NEEDS a place to generate social value OR User NEEDS a community that treats them with respect OR User NEEDS a place to compose and share long-form content with their peers OR User NEEDS a place to store and share their notes as they study )  
}**
```

  

**createValuableContent.ks**

```
**createValuableContent(painsIFeel, targetAudience){ var karmaContent = synthesize(getTrend(painsIFeel.union(targetAudience))); if (gainedTrust(targetAudience)) { shareKarmaContent(targetAudience); } else { copyKarmaContent(targetAudience); } }**
```

**innovateSolutions.ks**

```
**innovateSolutions(painsIFeel, audiences, traitsBehaviorsValues){ foreach(targetAudience in audiences){**   
 **var peopleWhoLikeMyContent = createValuableContent(painsIFeel, targetAudience);**  
 **foreach (potentialUser in peopleWhoLikeMyContent){ var theirPains = performUserTherapy(potentialUser); if (theirPains.union(painsIFeel) AND karmaCanDefinitelyHelp(potentialUser) AND potentialUser.isCompatible(traitsBehaviorValues)){ inviteAndDelight(potentialUser); } } } if (hasMeaningfulInsights()){ var dataDrivenEssay = authorInsightEssay(); shareValueWithJournalists(dataDrivenEssay); }  
}**
```

**productMarketFit.ks**

```
**while(!hasAchievedProductMarketFit()){ var traitsBehaviorsValues = getCompatible****TraitsBehaviorsValues****(); **** var personas = getPersonas(traitsBehaviorsValues); var audiences = getAudiences(****personas****);**  
 **var painsIFeel = getPainsIFeel(); innovateSolutions(painsIFeel, audiences, traitsBehaviorsValues); synthesize(getTrend(painsIFeel), true); synthesize(getJustInTimeTopic(), true);  
}**
```

Algorithm Inspirations:
-----------------------

  
  
from Hacker News https://ift.tt/2BZHRM1