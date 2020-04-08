---
title: 'It''s Not Sabotage, They''re Drowning'
date: 2019-11-15T05:09:00+01:00
draft: false
---

![](https://s0.wp.com/i/blank.jpg "It’s Not Sabotage, They’re Drowning – Sherman On Software")  

As you gain visibility into system problems, you’ll often experience push back like this:

> I refactored the code from untested and untestable, to testable with 40% test coverage. The senior architect is refusing to merge because the test coverage is to low.

> Me: I instrumented the save process. Saving takes between 10-25s, with the average around 16s!  
> Other Developer: That’s crazy! Wait! How much time does the metric system add?  
> Me: About 500ms.  
> OD: That’s over a 3% increase! You have to turn the metrics off!

> Me: Good news, I can make the system 15% faster and support jobs about 6x our current max. Bad news, it uses short lived DB table, which will increase disk usage by up to 1GB/client.  
> Different Developer: You need to find another way, we can’t have that much additional disk usage.  
> Me: What about all those orphaned short lived tables lingering about due to bugs and errors? Would cleaning those up get us enough space?  
> DD: I don’t know, we don’t have any visibility into the magnitude of that problem. You’re going to have to find another solution.

I used to believe that this kind of push back was intentional sabotage. That the people responsible for creating the problems were threatened by exposure.

It took me many years to learn that most of the time, it’s not sabotage, it’s drowning people sinking the lifeboat in an attempt to save themselves.

When you add visibility to a system, the numbers are always bad. That’s why you’re putting in the effort to add visibility to an existing system. When the initial steps towards fixing your problems make that number worse, that’s when the fear of drowning sets in.

I don’t have a solution for dealing with your colleagues’ reactions. Just remember, they aren’t trying to sabotage you, they’re drowning, and you’re manning the lifeboat.

If you’ve got similar stories of metrics bringing pushback, I’d love to hear from you!

  
  
from Hacker News https://ift.tt/33V7eeE