---
title: 'Who are you trying to impress with your deadlines?'
date: 2020-01-02T07:06:00+01:00
draft: false
---

New year, new me! Of course I start the year by cribbing about tech companies because I didn't do enough of that in 2019. When I started this blog, the plan was to criticize less. It's easy being the crtitic! But a quick look at the post history would tell you that's all I do. I convince myself that criticizing is good because realizing that there is a problem is the first step towards solving a problem.

Though sometimes it starts [conversations like these](https://twitter.com/jackiehluo/status/1110588043251974145) and that's valuable. So in the spirit of see something, say something I'll go ahead and write this.

Raise your hand if your company has _"customer obsession"_ or some variant of it as a leadership principle. For people who are watching this on video and can't see the crowd, almost all the people raised their hands except couple folks in the back.

They work at Oracle.

Oracle does have "Customer Satisfaction" as a company value. Leadership pricinciples are like gym memberships, just having one is not enough.

Obsessing over customers is important, but there is another thing a lot of companies obsess over internally - deadlines. And deadlines are good. "It gets done when it gets done" might be a great (and even recommended) strategy for 2 people working on an app but when you are a 200+ employee company, you need some sense of where things are; a rough idea of when your users will actually get to use the new fart app in their cars.

But I'd argue that hard - set in stone - deadlines are bad and if you have those in your company you should probably go ahead and remove the "customer obsession" bullet from your leadership principles. Because believe it or not, your users don't care about a missed sprint.

Hard deadlines are not user first, they are management first.

the goal is the goal
--------------------

or why locking your sprints is a terrible process
-------------------------------------------------

Deadlines are good, they create a sense of urgency, bring predictability to your processes and for these reasons you should have them.

But there are good deadlines and there are bad deadlines. There are companies where those deadlines are set in stone, and a missed deadline is next to fire. That's when the problem starts.

I am talking about engineering cultures who freeze their sprints, where everyone gets together at the start of sprint and gives an estimate for a task that must be a Fibonacci number, whatever is decided at the start of sprint is all that's done - nothing moves in/out of sprint. It theory, that sounds good but I think such a process is lose/lose:

1.  The developer beats the Parkinson's law and gets done with her sprint's tasks early. As this point they either lie about still working on it in next morning's stand up because hey, they can't say they have nothing to do, _or_ their manager assigns them more tasks effectively unlocking the sprint, because hey they can't have a person doing (gasp) _nothing_.
    
2.  The developer, being a developer, is lagging behind the schedule. Some environment setup issue took more time than anticipated and they are not sure if they can get it done in the sprint.
    

They mention the same in the next project sync up, and their manager says "Hmm, I see. But we have committed to it, could you still try to wrap it up by end of sprint?". While what they are actually thinking is "I'll have a hard time explaining this to VP, Engg in the weekly sync up \[1\] who will have a helpful "Can we just get it done?" suggestion, so might as well try to get it done".

So the developer, being a developer, pulls a couple all nighters, maybe works over the weekend and does get it done. Their manager _deeply_ appreciates their effort in the next stand up. No biggie.

Wrong, it is biggie. And mind you, this is the happy case - the deadline was met, the work was appreciated. But a wrong precedent was set. The new starry eyed campus hire who just joined the company got the message that working over weekends is A Good Thing.

And we are not even talking about the sad path here, where the deadline is not met, the task moves over to next sprint, the manager has to justify a delay in his next weekly update meeting. (It's a sync up)

* * *

You see the problem? At no point did someone ask "Sure, what happens if we move this to next Sprint and don't have to justify it to anyone? Does it affect the user?". And more often than not, these deadlines would be self imposed. And that's how they should be treated.

An ideal solution to this would have been to just go _talk_ to the stakeholders - product/sales team - ask them if the delay could be potentially customer losing. And if it is, by all means put in the extra hours, work those weekends. Because in that case the new campus hire gets the message that the company really care about it's customers, rather than it's sprints.

There is another problem with locking your sprints. Say you get a new customer ask, it's a potentially trivial but low priority bug. The developer could fix it in a day. But you follow The Process TM, the task gets added to your team's backlog, maybe gets picked couple sprints down the line and does get fixed. But you lost the opportunity to delight the user! You could have solved it in couple days, and emailed the user that their issue if fixed. That's what they remember and makes them recommend your product to their peers.

Don't be so busy following the process, that you miss the goal. \[2\]

I also think locking your sprints or any similar autonomy inhibiting process is a sign of inherent lack of trust in the team and there are more fundamental cultural problems you should be tackling but that's a topic for some other day

what's so terrible about deadlines
----------------------------------

1.  They set wrong expectations for what's _good_ and you don't want that in a culture because your leadership principles are not your real principles, the unwritten expectations and biases (good or bad) are your company's real principles.
2.  People _are_ going to cut corners if you put them to tough deadlines. Someone is going to skip a test, or the documentation is going to be in complete. You shipped on time, but at what cost?
3.  No one is going to experiment with new ways of doing things if you fetishize finishing under deadlines. We'd still be doing MVC in frontend apps if someone at Facebook didn't miss a deadline.

so don't have deadlines?
------------------------

Don't be silly! Have deadlines, but fuzzy. How fuzzy should be decided by your goals. If missing a deadline could potentially lose you a million dollars, the fuzziness factor for that should be zero. If it's a new feature, there's always more scope of fuzziness. Another idea is to experiment with more elaborate probabilistic ways of setting shipping estimates rather than gut based estimates. \[3\]

But locking your sprints is not the way to go.

* * *

\[1\] Tech companies love syncing up and touching bases

\[2\] Jeff Bezos said that better in [2016 Letter to Shareholders](https://ir.aboutamazon.com/static-files/e01cc6e7-73df-4860-bd3d-95d366f29e57). His advice is "Resist Proxies"

\[3\] Joel Spolsky wrote about better estimates [https://www.joelonsoftware.com/2007/10/26/evidence-based-scheduling/](https://www.joelonsoftware.com/2007/10/26/evidence-based-scheduling/) _(2007)_

  
  
from Hacker News https://ift.tt/2Fdl0yu