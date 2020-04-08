---
title: 'Unfollowing Everybody'
date: 2019-10-22T03:26:00+01:00
draft: false
---

At this point, there's nothing novel about noticing that social media is often toxic and stressful. But even aside from those concerns, our social networks are not things we generally think of as requiring maintenance or upkeep, even though we routinely do regular updates on all the other aspects of our digital lives.

Keeping in mind that spirit of doing necessary maintenance, I recently did something I'd thought about doing for years: I unfollowed everyone on Twitter. Now, these kinds of decisions are oddly fraught; a lot of people see their following relationships on social media as a form of status, not merely an indication of where information is flowing between people. But I decided to assume that the people I'm connected to know that me unfollowing everyone isn't personal, but really just a response to the overwhelming noise of having more than 5000 accounts sharing info with me on a single network.

* * *

How I did it
------------

Okay, this part is gonna get slightly geeky, if you're not a coder, but I thought I'd explain the process in case anyone wants to repeat it.

Years ago, Twitter used to have a command-line interface for performing bulk or automated actions on an account. They abandoned it after a while, so Erik Berlin created a new command-line tool for power users of Twitter, [simply called "t"](https://github.com/sferik/t). It's written in Ruby (a language I basically can read but not really write) so it's easy enough to get running if you follow the [few simple setup steps](https://github.com/sferik/t#dependencies).

As Erik mentions in that documentation, you'll then need to set up a [new Twitter app](https://apps.twitter.com/) on your account, and get the credentials that will let the `t` tool perform actions on your Twitter account. (Note: I got some errors while updating and authenticating; making [these edits](https://github.com/sferik/twitter/issues/878#issuecomment-349718252) to one of the ruby libraries that `t` depends on fixed the issue immediately.)

The Plan
--------

At that point, I wanted to follow a few simple steps. These took a little longer for me because I was following over 5,000 people on Twitter, but if you're following a more reasonable number, none of these steps should take more than a few minutes to complete. This was my plan:

1.  Copy all the people I was following to a [Twitter list](https://help.twitter.com/en/using-twitter/twitter-lists), so I could still access them in my Twitter apps on all my devices, and I could still see my old timeline at any point if I wanted to.
2.  Archive all of the people I was following into a spreadsheet, so I could sort through them and filter for geography or how many followers they have or whether they were verified or not — basically any criteria that might be interesting when deciding who to follow (or _not_ follow).
3.  Actually unfollow everybody and start over.

As it turns out, each of these steps is pretty easy.

### Copying all your followers to a List

If you want to back up all of your followers, you only need to make a list and then populate it. You can make lists in most regular Twitter apps, but to do it at the command line it's simple: type in ``t list create following-`date "+%Y-%m-%d"` `` to make a list named after the current date, so you can easily remember this was a list of who you were following as of today. You can pretty easily understand the `t` syntax here — commands like `list create` are pretty self-explanatory.

Next, we have a slightly more elaborate command to copy all of your followers to the new list; you'll dump out a list of everyone you follow, and then pipe that into another `t` command to add them to your new list. It works like so: ``t followings | xargs t list add following-`date "+%Y-%m-%d"` ``. (If you're like me, you'll be doing all this stuff around midnight, and the date will change in the middle of it, and you should just type in the current date instead of using `date` variables.)

That's it! Now you've got a list of all your followers, and if you browse that list in your Twitter client app, you should see the exact same thing as your regular timeline. Do note, though, that Twitter lists don't function well with more than a few thousand followers. It took hours for all 5,000+ of my followers to show up on the list, and in the interim the counts of how many people belonged to the list were often incorrect.

### Archiving your followers into a spreadsheet

This one is just a fun thing to do in general, if you like to slice and dice data about your social network. `t` supports exporting a pretty broad set of data about your followers, not just their names and Twitter handles, by allowing for a "long format" export with complete data. You get stuff like how many favorites (likes) they have on Twitter, when their account was created, and how many people they follow or are followed by. Frustratingly, Twitter no longer makes it easy for this data export to include whether that person follows _you_ or not; that requires an additional query.

You'll use CSV (comma-separated values) as the format for exporting your data into a spreadsheet. And good news! `t` supports that natively. So your command will look like this: `t followings -l --csv > followings.csv` which basically says "Export my followings, in long format, to a CSV file named 'followings.csv'." Once you do that, you can open it up in Excel or Google Sheets in a few clicks, and you're all set.

![spreadsheet of people I used to follow on Twitter](https://anildash.com/content/images/2018/07/Screenshot-2018-07-13-11.01.18.png)

After all the people I followed were in a spreadsheet, I was able to sort by how many followers or followings they had, and also their last update, and I found friends who'd passed away whose accounts had been dormant for years, or joke accounts whose relevance had expired, or quiet voices with small networks that had been drowned out amongst the cacophany of the many other voices I was hearing each day. I found this part to be a really worthwhile exercise, and definitely decided to follow fewer people with huge networks and lots of reach.

### Actually unfollowing!

Then, it was time for the main event: actually unfollowing everybody. I don't think this will be as much of a problem for other folks, but trying to run a single process of unfollowing everybody had me repeatedly running into Twitter's rate limits, where they try to keep any app from performing too many actions on your account in too short a period of time. I ended up writing a simple script to do the unfollowing in batches, then pausing for a few minutes, then starting up again.

But with a more reasonable network, the command to unfollow everyone is extremely simple:

`t followings | xargs t unfollow`

It'll chug away for a few minutes, and then that's it! You're not following anybody anymore. Except it might still _look_ like you are.

> A number of people are noticing that my follower count says something other than 5, or that you see incorrect lists of who I follow. This is an artifact of a design called “eventual consistency”, which Twitter & other distributed systems use to help scale. [https://t.co/FGzQ9qR0SG](https://t.co/FGzQ9qR0SG)
> 
> — Anil Dash (@anildash) [July 5, 2018](https://twitter.com/anildash/status/1014695768903413760?ref_src=twsrc%5Etfw)

In my case, my follower count was wrong for _days_, and kept showing wildly inaccurate information like insisting that I was following one of Mike Pence's official accounts. (Needless to say, that was never the case.) All of this is due to a architectural decision called [eventual consistency](https://en.wikipedia.org/wiki/Eventual_consistency), which helps enable Twitter to scale to its massive size, but doesn't do as good a job of handling unusual circumstances like being able to immediately see the correct list of followers for someone who has just unfollowed thousands of accounts.

Nevertheless, the deed was done. I refollowed a few essential accounts (my family, [@Glitch](https://twitter.com/glitch) and [@Prince](https://twitter.com/prince), and was ready to start anew.

Lessons learned
---------------

It's been about a week and a half, and, well... Twitter is a lot more pleasant. I've chosen a handful of accounts to follow each day (most ones that I followed before, some entirely new to me) and it's made a big difference. On the flip side, about 100 people seem to have unfollowed me after I unfollowed everybody, and I hope they hadn't felt obligated just to reciprocate if I was following them before. (That might also just be how many people unfollow me in a given week, I dunno.)

One of the most immediate benefits is that, when something terrible happens in the news, I don't see an endless, repetitive stream of dozens of people reacting to it in succession. It turns out, I don't mind knowing about current events, but it _hurts_ to see lots of people I care about going through anguish or pain when bad news happens. I want to optimize for being aware, but not emotionally overwhelmed.

To that point, I've also basically not refollowed _any_ news accounts or "official" corporate accounts. Anything I need to know about major headlines gets surfaced through other channels, or even just other parts of Twitter, so I don't need to see social media updates from media companies whose entire economic model is predicated on causing me enough stress to click through to their sites.

Similarly, I've focused a _lot_ more on artists and activists and people who write about the stuff I'm obsessed with in general — Prince or mangoes or urban transit or the like. That brings a lot more joy into my life, and people writing about these other topics offer alot more inspiration for the things I want to be focused on. Oddly, given that my job is being the CEO of a tech company, I follow _far_ fewer people in tech, and almost no tech company accounts except for my own. Despite that, I've missed almost nothing significant in the industry since making this change.

The algorithm is learning
-------------------------

Most interesting to me is how the suggested content and accounts on Twitter have changed since I changed my network. Before, much of the suggested headlines or featured Tweets in my Twitter apps would be from categories like "Technology VC"; now they're much more likely to be about "Climate Change" or "Comedians" than about inside-baseball tech talk.

On the less positive side, Twitter _still_ suggests that I follow accounts that are almost entirely men, and overwhelmingly white American men with verified Twitter accounts. This is bizarre to me as I'm [now following nearly 100 accounts](https://twitter.com/following), and they're basically the same mix of races and genders and geographies that I've always been interested in hearing from. I would have expected Twitter's follow-suggestion algorithm to be at least as adaptive as its content-suggestion one, and hope that it'll get updated to feature accounts that don't fit the usual privileged patterns. (I do still follow a lot of verified accounts, but some of that is due to an oddity I've just realized, which is that a lot of my friends have verified accounts. Look, ma — I'm a big-city elite!)

### What Follows

I don't have some grand takeaway about what all this means; obviously, I've been thinking about the design and impacts and best use of social networks on the web for basically as long as they've existed. I strongly believe we should be intentional in how we use our networks, and even spent years building tools to encourage that, though the corporate interest of the major social networks precludes building a business around encouraging healthier use of their platforms.

But I'm happy for making a conscious decision about managing my network, and I lament that it takes a pretty extreme level of technical knowledge to be able to do so. I first [wrote about Twitter](https://anildash.com/2007/02/14/consider_twitte/) when it was only a few months old, talking about its promise and predicting that Twitter would adopt @messaging and adapt to other ways its community was inventing new behaviors. Some of that happened, but of course most of what power users (and vulnerable users) wanted was never created.

I've also written a good bit about the peculiarities of having a large network in social media, like [Twitter's early practice of suggesting which accounts to follow](https://anildash.com/2009/12/29/life_on_the_list/) (including mine!) and what it's like to [have the social network of a famous person](https://medium.com/message/nobody-famous-37790cb4d014) without actually being famous. I think a lot about [why I "favorite" (or like) so many things](http://anildash.com/2011/06/09/all_in_favor/) on various networks. And I also hope people can think more broadly about the ways the design of social networks intersects with how we see ourselves, and how we see social status, as best exemplified by the huge social anxieties around [what it's like being verified on Twitter](http://anildash.com/2013/03/01/what_its_like_being_verified_on_twitter/).

And ultimately, I come back to what I [wrote a few years ago](https://medium.com/the-only-woman-in-the-room/the-year-i-didnt-retweet-men-79403a7eade1) when I first decided to stop retweeting men (a practice I've followed for about half a decade now):

> If you’re inclined, try being mindful of whose voices you share, amplify, validate and promote to others.

It's still a really important point, and to this list I would only add: Also be mindful about who you follow. And don't be afraid sometimes to reset and start over.

  
  
from Hacker News https://ift.tt/2mgNyh6