---
title: 'Selling Juicer'
date: 2019-12-05T01:55:00+01:00
draft: false
---

The first commit for [Juicer](https://www.juicer.io) was on August 14th 2014, and we closed on selling it to [SaaS.group](https://saas.group) on June 29th 2018. So me and my partner [Amit](http://amitpatel.me) started, grew, ran and sold it in just under 4 years.

A few months before we decided to sell I read this amazing article by [Tyler Tringas](https://tylertringas.com/selling-my-bootstrapped-saas-business/) that described the process in such great detail that I’m sure at the very least it had a subconscious effect on my deciding to sell. I wanted to give back in a similar way, so almost exactly a year after the completion of the sale I wanted to write about the entire lifespan of Juicer.

**The Motivation**

In December of 2013 I quit the last real full time job I had at [GOOD](https://www.good.is/) and spent [6 months traveling through Asia](https://www.goddamnyouryan.com/blog/off-i-go/). I have never not had a full time job since I graduated from university, so during the first few weeks of travel I was having a lot of thoughts like “Why would you quit your high paying, remote friendly job and give up your amazing New York City apartment, you moron? You’re going to run out of money and no one will ever hire you again.” Then, after a few weeks the thoughts switched to “Not having a job is reaaaaaaaaally nice.” Then when it was almost time to come back the thoughts were changing to “Oh god no, I don’t want to get a job. How can I avoid ever getting a job again?!”.

When I arrived back in the States I still had a little bit of a cushion saved up, but not much. I started freelancing / consulting again because I had already done quite a bit of that in the past and it seemed like a decent way to start making money. After helping run a [workshop](https://www.mesa.do/) in Brazil for a week, I took the bus from São Paulo to Rio de Janeiro. On the bus, I read a book called [The Millionaire Fastlane](https://www.amazon.com/Millionaire-Fastlane-Crack-Wealth-Lifetime-ebook/dp/B004BDOUAI), which, despite it’s regrettably cringy title, I actually found to be very illuminating. The two lessons from the book that really stuck out to me were that:

*   No one (with the exception of a few very elite lawyers and heart surgeons and probably a few others that I am forgetting) has become wealthy working for someone else, and;
*   Being employed by someone is by its very definition, an exploitative relationship, even if your job is great. Your employer can only afford to hire you if you make more money than you cost (again, with a few exceptions of course) so no matter what you are getting paid less than your true value.

I didn’t have a big yank to become wealthy, but not having to worry about money any more (or at least less) sounded pretty nice. The book also described a career progression that resonated with me:

*   Working for someone else.
*   Working for yourself, but you are the limiting factor in terms of growth.
*   Working for yourself but there is no upper ceiling on growth.

At the time I read the book I was on the second step. Freelancing is great but you can really only work on one or two projects at a time, which really puts an upper limit on your maximum value. Really, you’re really still trading time for money. You want to break this paradigm.

So I started thinking about business ideas that could scale with only indirect input on my part.

(**AUTHORS NOTE**: I don’t actually remember the specifics from this book at all, so the ideas above are taken directly from my own, extremely fallible memory. Considering I completely forgot the name of this book I read almost 5 years ago, and it took me, no joke, over an hour of searching through old emails to find it, it’s highly likely that the above is just my own interpretation of the lessons from the book.)

**The Idea**

When you’ve been building websites on a freelance basis for several years you will oftentimes find yourself getting stuck in a “rut” where you end up building a bunch of similar sites one after another. For me, this rut was building production company websites (I did live in LA for a long time, after all) for commercial directors. I did one, then one of the directors who worked for that production company saw the new site, liked it, wanted me to do their site as well, then another “friendly-competitor” production company would see the new site, and want me to do theirs, etc. etc., on and on until it’s been a year and you’ve made 7 sites thats are all basically a bunch of thumbnails of videos and portraits of directors.

The very first production company I built a site for had asked me if it was possible to have a big feed of all their companies social media posts on a part of their site. I knew it was possible doing it via the social media providers API’s but I had no desire to build that myself, so I just googled “Social Media Feed” and found a company that already offered this service. They charged $10 a month so it was a no brainer for the production company. Setup was a breeze, we just created an account, connected their social media accounts, and copied an embed code onto their site. BAM! Done.

Every successive production company website that I would build would see the social media feed on the previous production companies site and want one for their own site. So I’d send them to that social feed company.

So when I got back to the US after a few weeks in Brazil, another production company asked me to build them a website. This was a few years after my initial run of production company websites, so when they asked me to put a social media feed on their site I went right back to the social media feed company. In the intervening years they had raised their prices from $10/month to $250/month (they have since increased it to $500/month). It seemed they had started to go more after big brands, so smaller companies were left in the lurch. This seemed a bit expensive to me for what it was (or at least what I needed it for). Naturally the production company didn’t want to / couldn’t pay this much. They asked me if I could build them a custom integration to their social media posts. With the lessons of _The Millionaire Fastlane_ still in my head I told them to save their money: I would build that feature as a standalone service and they could just sign up for it. Juicer already had one customer and I hadn’t written a line of code.

**The Minimum Viable Product (MVP)**

The next morning (or another morning relatively soon thereafter) I woke up at like 5am and couldn’t sleep (probably still jet lagged) and I had the idea for a logo that was an [orange](https://assets.goddamnyouryan.com/blog/development/old.png). I really liked that imagery for some reason, so I just had to come up with a name that fit it. A few hours later I had it.

I liked Juicer as a name because it was simple, an already existing word, could be vaguely interpreted as we were “squeezing the juice out of social media posts” and the domain juicer.io was available.

I actually find it necessary to name a product before I start working on it. This is for a few reasons:

*   I’m going to have to type the name a lot while I am coding the project
*   I work on the backend and frontend and design and UI/UX all at the same time and the branding and colors and name can all play into how that all shakes out.
*   Naming it makes it more real in your head and makes it easier to talk about.
*   You can then find the domain and buy it before you code anything so you can launch right away when you are finished.

The MVP of Juicer was everything I needed to get the feed on the production companies site and get them signed up as a customer and nothing else:

*   A way to sign up for an account
*   A way to connect your social media accounts (in the beginning only supporting Facebook, Twitter and Instagram)
*   A way to embed the posts from those accounts
*   A way to pay me (Stripe!) via credit card

Presumably there was a little description on the homepage that said what it was, but that was about it. I got the whole thing launched in two weeks. I got the production company signed up, and got their Juicer feed embedded in their site. I charged them $10 a month (thanks old Tint!).

**The Partnership**

Around the same time I had made dinner plans with my high school / college friend Amit Patel. One of the first things I did after I launched it was post about it on Facebook. Mostly as a crappy first attempt at marketing it to people I already knew. Thank god I did. Amit saw it there, and was pretty surprised I was launching companies:

![Amit sees Juicer on Facebook](https://assets.goddamnyouryan.com/blog/juicer/amit-facebook.png)

Amit was interested in chatting since he has tried launching a few things himself in the past with little success but he liked that he could understand the concept behind Juicer immediately and found it super compelling. At our dinner we decided to be business partners. This ended up being great for a few reasons:

*   Amit is great and I was (and still am) very happy that I got to work with him all the time.
*   Amit could do all the stuff I didn’t want to do, like incorporating a company, negotiating contracts, and doing sales. Not that Amit had much experience doing anything like this, he’s a Physicist by trade; but he’s a generally smart and motivated guy who can figure just about anything out.
*   A partner is great for bouncing ideas off of.
*   I didn’t know it at the time, but once I found out how self-motivated Amit was I realized I couldn’t have had it any other way. Finding a partner who did everything that needed doing without having to be told to was a huge game changer and maybe the biggest contributor to the success of our partnership.
*   The only thing that was maybe more important: Amit was motivation in the beginning to keep going. My usual MO when launching a new project was to post it on a few places online, and then when it didn’t immediately become super successful and get bought for a billion dollars, give up. Having Amit as a partner gave me the motivation to keep working even though progress after launch is almost always non-existent.
*   We have different backgrounds and ways of thinking - different approaches to things like finances and risk, but we are still on the same wavelength. Somehow, as a combo, we’re better than the sum of the parts.

**How We Got Customers**

I posted it to a few relevant [subreddits](https://www.reddit.com/r/socialmedia/comments/2ftlmy/im_a_developer_and_i_created_a_site_that_allows/) which got a little discussion and traffic, and the next day it was posted to Product Hunt (which was pretty much brand new at the time, I had never heard of it), which got us a bit more traffic. After a few days the traffic slowed down significantly.

At the time the Juicer pricing structure was as follows:

*   Accounts could get unlimited feed and unlimited sources for those feeds. Accounts cost $10 a month
*   You got a two week free trial upon signing up, after that you had to pay $10 a month.

With all the traffic the first few days we got a lot of free-trial signups, but after two weeks, none of them had signed up for the paid account. It’s at this point that I definitely would have given up if not for Amit.

We had the realization that we would need a more sustainable method of getting people to the site than from posting it to other websites; the traffic just dies off after a few days. We started thinking about who our customer was, which was easy: people like me! Developers who were tasked with putting social media posts on their clients site, and who didn’t want to build that themselves. What did I do when put in that position? I googled it! So we should work on SEO for Juicer and get it onto the first page of google. The problem was, I had no idea how to do that and had never done so. Information about it is not super easy to find online because most people either a) don’t know or b) want to charge you lots of money to “help” you.

The only real “genius” revelation I would say I had during this entire Juicer journey was as follows. I understood on a basic level that google would rank sites higher that had a high amount of links to them from reputable sites. So how could we get a lot of sites to link to us? We changed the pricing model. Instead of there being a 2 week trial, we would make three pricing tiers: Small, Medium and Large. Medium and Large were paid plans, but Small was free forever. The catch was, if you used the Small plan, your feed, when embedded on your site, would have a small “Powered by Juicer” link on it that linked back to us. So while we technically wouldn’t make any money from Small plan customers, we would get valuable SEO ‘Juice’ from them which would push us up in the rankings.

Of course, the next problem was getting people to the site so they could sign up for the Small plan! I posted about it a few more times, and we also discovered that if you searched “Social Media Feed” on google, one of the top results was a directory of Wordpress plugins. I personally didn’t like using wordpress that much, but it is massively popular. We decided to build a Wordpress plugin. The benefit of doing this was two fold:

*   Many people building wordpress sites will search directly in the wordpress plugin directory for what they are looking for;
*   It’s much, _much_ easier to get to the top, or near the top of the wordpress plugin directory than it is google (essentially it’s making sure the description of your plugin has the right keywords, and then you’ll be there essentially instantly).

Of course, if you google “Social media feed” and the wordpress plugin directory for the term “social media feed”, then if you can get to the top of the wordpress plugin directory for the search term it’s kind of like being on the top of the google searches as well, just with one extra click.

Building a wordpress plugin was kind of a pain, since it’s PHP but I was able to bang out a simple one that just made embedding in a wordpress site slightly easier and get it submitted to the plugin directory (I’d say figuring out how to do all of that took longer than actually building it). Pretty soon thereafter we started getting traffic from wordpress.org signing up for Small accounts.

We did a few other things, like posting to relevant Quora questions, and submitting to a few other business and online tool directories, but it in the early days most of our traffic came from wordpress, and then eventually, google searches directly.

Around 6 months after launch, through these inbound marketing techniques, we got our second paying customer (after the production company). This customer, however, we didn’t know. 6 months is a long time to work on something for $20 a month, but we were elated. A week or two after that we got our 3rd customer, then the next week a 4th. Eventually it accelerated and it seemed we had struck upon a viable and reliable method for getting consistent traffic.

The best part about going after SEO and google searches is that while not too many people search for terms like “Social Media Feed” those that do are usually extremely in need of the product you are offering.

This worked so well in fact that we really never had to do too much more and we _almost_ had more customers than we knew what to deal with by the time we sold a few years later. We never paid for ads, so really our CAC was essentially $0.

**Growing and Burning Out**

Our original goal with Juicer was to be able to pay our rents with it. Since Amit and I were 50/50 partners this worked out to being about $3000 per month. We didn’t really expect to actually be able to achieve this, but it was good to have a goal. We managed to hit this goal in the next few months after we got our first customer. When it rains it pours. It was a very strange feeling after spending 6 months working for essentially 0 return.

Of course then, a funny thing happened, that neither of us expected or predicted. It kept growing. Even though we had hit our goal.

So we kept working on it! We kept improving the product, making it easier to use and capable of doing more. The primary thing I worked on, on a daily basis, was customer service. Every day more and more customers would contact us, that, after a year or so, it got to be a fulltime job in an of itself.

It was really nice to be this close with our customers as well as being the main developer on the codebase, as it allowed me to really see the problems and issues with the platform they were having through their eyes, and it allowed me to notice trends with customer service issues, and improve the platform to prevent those issues from reoccurring.

Eventually this started to burn me out. I was answering questions all day as well as keeping an increasingly popular website online (in the end we were getting 100s of millions of requests a month) all the while also trying to add useful features and improve the User Experience. Yet another reason it’s a good idea to have a partner: he was able to point out to me that I was burning myself out, and he was right.

So we hired a customer service person. We were recommended an overseas resource by some friends who was supposedly good and cheap. They didn’t end up working out because while they were on top of things, they were unable to do the thing that I really needed them to do: think for themselves. Essentially they needed us to write a script: if the customer asks question a), respond with answer b). The problem was, if there was even a slight variation in the question, they didn’t know how to answer it and would come back to me and I would have to answer it. This resulted in me not really saving anytime and in fact spending more, because I was still answering all the customer service queries but also teaching a person how to do it who fundamentally didn’t get better or learn.

So we decided to spend a lot more money and hire our friend Bryan. He was, and still remains, the best. I can’t emphasize enough how important it is to spend a lot of money on customer service. It’s worth it both in terms of your customer satisfaction and therefor bottom line, but for your mental health. Bryan is personable to the extent of being a people pleaser. He almost habitually wants to make the customer happy. And he’s smart. So you never have to tell him the same thing twice. Bryan is so good at helping the customers that he could probably build Juicer from scratch now, even though he has no idea how to develop things. Hire someone like Bryan. He likely saved me from a mental breakdown.

**Thinking About Selling**

I originally came across Patrick McKenzie (aka Kalzumeus aka patio11) right when I got back from Japan the first time when I read his amazing article on [Japanese Salaryman](https://www.kalzumeus.com/2014/11/07/doing-business-in-japan/) which blew my mind and really opened my eyes to Japanese culture. So I looked into him a bit more deeply and it turns out that he is in the Bootstrapped Startup world. And it also turns out there is a term for what I was doing (that is to say, starting a startup without venture capital). So we had a lot in common so I started following him more closely.

In 2017 I came across an episode of his podcast where [he interviewed Thomas Smale](https://www.kalzumeus.com/2016/08/26/kalzumeus-podcast-episode-13-selling-online-businesses-with-thomas-smale/), one of the founders of [FE International](https://feinternational.com/) and thought it was very interesting. I had never given too much thought to selling, mostly because it seemed almost impossible to do, but here was a company that made it significantly easier.

I mentioned this all to Amit and we started vaguely thinking about the idea of selling. A few people contacted us around this time with interest in buying us, but we always found that as soon as we started discussing revenue numbers, they could no longer afford us, which was okay because we weren’t pursuing the deals seriously, just seeing what was out there.

Juicer had been chugging along pretty reliably and consistently for the last 2 or 3 years, and had really been on autopilot for the last year as I had been living in Japan studying Japanese full time, so I was really only working on it in my free time.

But slowly and surely Amit and I started talking about selling more and more. It was around this time that we read Tyler Tringas’ article about [selling his own business](https://tylertringas.com/selling-my-bootstrapped-saas-business/). Selling a SaaS business is a lot more reproducible than say, selling Instagram. With Instagram, you are selling a shit ton of millions of users who are highly engaged in your platform, but there’s no clear way to determine how much that is actually worth in real life dollars.

With a SaaS you know how much the company makes every month, you know by how much that increases every month. You know how much it costs to acquire a customer, and how much money you will make over the lifetime of that customer (LTV), so valuing a company is extremely straightforward.

Usually you are looking at getting between 2-5x yearly revenue. The difference between 2x and 5x seems to be primarily based in the yearly growth rate. How much is your total revenue growing every year? So for a seller (like us) the ideal time to sell your business is RIGHT before the inflection point where your growth rate begins to decrease (not that revenue is decreasing, just the rate that revenue is increasing, starts to decrease…hah)

We started doing some math, and the more we thought about it, the more likely it seemed like we were going to try to sell.

The main reason I was ready to sell though had nothing to do with logic or money, it was all burnout. And it was a different kind of burnout than I had felt years previously before we had hired Bryan, it was a slower-burning-burn-out. It came from a few things:

*   The only customer emails I got were the hardest ones
*   Even though it wasn’t much work in terms of the number of hours, it was a huge amount of work in terms of mental bandwidth and background thinking throughout the day
*   With intercom customers tended to ask a lot more repeat questions
*   The way I structured my day, answering emails basically first thing that I didn’t have too much mental energy left over to do stuff for Juicer, let alone work on other projects
*   Got real tired of the codebase, but was too much effort to update it to something more modern.
*   General ennui at what Juicer was doing wasn’t really that meaningful, dislike of social media as a whole.

We tried to find a buyer on our own with limited success. It’s nontrivial to find buyers who are interested in purchasing something that’s too big to be some rich guy’s hobby, and too small for private equity sector to care about. We did manage to find two potential buyers and one of them actually made a reasonable offer but we realized that we had no points for comparison. It would be nice if we could assess the market’s general interest in our product and maybe get a few players to compete for us!

Eventually we decided to get in contact with FE International. We were at the very least curious on what valuation they would give Juicer.

**Selling with a Brokerage**

We contacted FE and had to fill out an enormous application that basically asked us everything about Juicer that ended up being a fair amount of work and then we had to meet with them. They came back with a “what we think we can sell Juicer for” valuation, that was slightly lower than we wanted, but not shockingly lower or anything. We proposed they try to sell it for a higher amount like we wanted because of our low costs of operation and untapped potential growth (since we didn’t do any advertising, outbound marketing, etcâ¦)

The process of selling with FE is really top heavy. You spend hours answering questions that eventually end up being compiled into a prospectus that gets passed around to potential buyers. But the best part is: you only have to do everything once. If you try to sell on your own you basically have to go through this entire long painful process with every single potential buyer. It would have killed me.

Once FE has the prospectus ready to go, they send it out to their huge network of interested buyers. Another great FE selling point: We did not have a huge network of potentially interested buyers, they did.

Then, after a few weeks FE starts lining up meetings with the best people who have expressed the most interest. We did about 10 of these, which also end up being exhausting. They are usually a few hours long, and involve a lot of talking. By the end of the 10 me and Amit got so good at passing the ball back and forth. You always have to tell the “creation myth” of your company (see above) but interestingly enough, all the other questions involved were different for every meeting. This might be because of another great feature of going with a broker like FE: they compile all the other questions you’ve answered in previous meetings and send them to new potential buyers, so you never really have to end up repeating yourself (unlike with customer service, ha ha).

One of our first meetings was with two guys, Tim and Ulrich who were getting a company that buys SaaS companies set up. A few of our other meetings were with experienced investors / groups who had worked in the Tech / SaaS sector before. The rest were with people who seemingly had less experience in the field; finance dudes who had heard good things about Tech and SaaS and knew lots of people with lots of money, but not much about how to run a Software company.

We ended up going with Tim and Ulrich, some of the first people we met with. They had both been founders of [Sedo](https://sedo.com/us/), a domain marketplace back in the mid aughts, and then Tim went on to found AdBlock, which I thought was awesomely punk rock. But most importantly, these guys had experience starting, building and growing companies. I knew Juicer would be safe in their hands.

The third reason that FE is great is that they handle all negotiating for you. When SaaS.Group (Tim and Ulrichs company) made their first offer it was lower than what we asked FE to get for us, and amazingly, to FE’s credit, they didn’t try to convince us to take an offer we were less than happy with.

They ended up coming up with a compromise that worked out pretty well. We ended up doing an 18 month transition period) where we would share profits during this time period. Assuming a normal Juicer growth (basically what it was doing already) we would make as much money as our asking price. This is pretty atypical for this type of deal (most have a transition period of 1-3 months) but it seemed like a good idea for a few reasons:

*   It was good for SaaS.group because it gave us a vested interest in transitioning them over well, and continuing to help them run and grow the business.
*   It was good for us because if Juicer did better than expected (which we thought it might do because, let’s face it, Tim and Ulrich were better than us) we would make _more_ money!
*   As much as Juicer irritated me over the years, it was hard to let go immediately. It’s kind of like seeing an annoying teenager off to college.

After the terms of the deal were negotiated on, Tim and Ulrich sent over a Letter of Intent, or LOI. Basically this says that they get 30 days where we are an open book: They can look at all of our customers, code or financials. During this time we also agreed to an exclusivity period, where we would stop talking to other potential buyers.

As you might expect, those 30 days of due diligence were pretty stressful. I can remember at least two 6-hour meetings, one of which was going through a codebase that I alone had worked on for almost 4 years, I’d imagine it’s a bit like getting your first prostate exam. But I also distinctly remember a sensation of “Hurry up and wait”. The potential buyers would have some new question and I would rush to get them the answer as soon as possible, then go days without hearing anything.

**Sold!**

Then, as soon as it had started, it was over. We had the offer in our hands. It’s hard to describe exactly what it feels like. On one had, it’s amazing. On the other, it’s totally anticlimatic because you’ve been thinking constantly about this happening so the actual moment can be a bit overwhelming. Or maybe you’re like me and you’ve done freelancing long enough that you know a project isn’t officially over until the money has hit your bank account.

Of course the money wasn’t in my hands, it was in escrow for about a week. But the hard part was over. Then it was in my bank account.

Once that happened I got a lot more excited.

**Transitioning**

Part of the deal was that we had to spend a month transitioning them over to running the company. Firstly this involved us creating a “handover document” that got held in escrow with FE until the payment was ready. This was a huge amount of work, you tend to forget how much stuff you just know natively.

One of the surprisingly most annoying parts of this is handing over all the log-in credentials for every single site and app you need to run the business. We especially needed a lot because we had to have a bunch of different accounts on every social media platform to connect to their APIs. Unfortunately a lot of these were tied to our personal accounts, a few of which we just had to give up! Definitely recommend taking the time to create new accounts for everything when starting a new business.

Another part of the deal is that we would fly out to Cologne (Köln) Germany with our whole team (all three of us) to help transition their whole team (also 3? Note: Tim and Ulrich would not actually be working on Juicer day to day, they had 2-3 devs to do that! Genius.)

Meeting the whole new team in Germany was a great experience as well. It’s so much easier to help someone take over ownership of your company when you are face to face. It was also very invigorating. Working on Juicer with fresh eyes of smart people made me more motivated to work on it than I had been since the very beginning. So it was really enjoyable.

Part of the sale was that Bryan went over to the new owners. So he came to Germany as well, as you’d imagine he has a great and unique insight into the product. He seems to get along very well with the Germans still, if not because they are much more responsive and less lazy than me.

**In Conclusion**

Starting and selling a business is a lot of work. But it’s rewarding I’d say. I certainly know a lot more now then I did before I started. It’s hard to sum up a 4 year journey in a few sentences, but the one thing I know I am certainly grateful for: I’ve managed to go 4 years without getting a “real” job. I usually say this a joke to people when they ask me what I do, but really what I mean is I managed to make 4 years without anyone getting exploited. I wasn’t exploited by an employer, the customers weren’t exploited by me (we made a good, useful product available at a fair price). I suppose I was sometimes exploited by customers who had unreasonable demands of my time given the amount of money they paid us, but I could always get rid of them if I so choose, and the business would keep on doing just fine. It felt pretty nice, having everyone get a fair deal and aligning incentives.

So thanks Juicer for a good 4 years. Here’s to hoping you continue to thrive for long after the sale. And thanks to SaaS.group for taking on that responsibility.

**What We’d Do Differently Next Time**

*   Never seeing Juicer as an entity with big potential (always treating it like a lifestyle business):
    *   Could have tried to take it to Y-combinator (we had a number of ideas that could take Juicer in a completely different direction, and may have been more appealing to the masses).
    *   Could have hired more people, or at least a dev or two and focused a lot more on growth
    *   Would have fixed burnout for me and sped up making it a better project.
*   Not hiring a customer service person earlier
*   In the beginning we had no money, so we ran the business very, very cheaply. Eventually we did have a lot of money, but we still ran the business cheaply even though we didn’t have to. We should have spent more money to make our time easier.
*   Create brand new accounts for everything when starting a new business. Makes transitioning so much easier (running it like we were going to sell it)

  
  
from Hacker News https://ift.tt/2YdOrsS