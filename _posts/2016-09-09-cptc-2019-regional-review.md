---
title: 'CPTC 2019 - Regional Review'
date: 2019-10-19T16:30:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-uXYPGp7C_U4/XanqetxaeOI/AAAAAAAAKq0/nJAMiJfTWl4biMwMrHG9iqEjihPWjufMgCLcBGAsYHQ/s640/cptc_west_logo.jpg)](https://1.bp.blogspot.com/-uXYPGp7C_U4/XanqetxaeOI/AAAAAAAAKq0/nJAMiJfTWl4biMwMrHG9iqEjihPWjufMgCLcBGAsYHQ/s1600/cptc_west_logo.jpg)

Welcome back. The first round of this year's Collegiate Penetration Testing Competition ([CPTC](https://nationalcptc.org/)) just concluded last weekend. This post is intentionally going to be scant on information as we still have the National competition a month away (November 22 - 24, at RIT in NY), but I want to provide a few details around the scale of our competition last weekend. For our regional event we supported 45 teams across 6 physical locations (5 in the US, 1 international), concurrently! I helped prepare and run the game remotely this year, leading the OSINT and World teams again. We also ran regional scoring the same way this year as last year, with a small difference of only the top team from each region progressing on to Nationals (instead of the top 2), along with the remaining 4 highest performing teams overall. Before I get too far into this review lets cover those advancing teams:  

*   California State Polytechnic U., Pomona
*   Penn State U.
*   RIT
*   RIT, Dubai
*   Stanford U.
*   U. at Buffalo
*   U. of Central Florida
*   U. of Virginia
*   US Air Force Academy
*   Virginia Commonwealth U.

This year we had a bigger and more prepared regional network than ever before. We continue to use our in-house competition tools like [laforge](https://github.com/gen0cide/laforge), now aided with salt stack, to deploy and administer this massive fleet. Our theme this year is [DinoBank](http://www.dinobank.us/), which we've been vocal about for awhile. We had over 20 target machines, across 5 networks, with multiple working Windows domains and interconnected services for each team. As you may know, we build the entire environment out for each team, so there is no shared infrastructure across different pentest environments. Meaning we had over 900 cloud machines running concurrently for our regional competition, just about triple our size compared to last year. We also had more findings and more attack paths this year. We tried to make each machine both vulnerable and interconnected, meaning there are multiple ways to gain access and pivot. Because of that, grading reports is probably one of my favorite activities; seeing what the different student teams find important and their chosen exploit paths is always very interesting to me. And the competition is not without issue, we had growing pains this year and had to cut two networks off of every team due to hitting limitations in our cloud provider. But we've had internal debriefs, covered lessons learned, and plan on making several improvements in competition operations. Finally, it seemed like people really enjoyed the OSINT findings thus far. We had lots of engagement and I saw OSINT related findings in almost every report. That said we will be taking a break on OSINT between the regional competition and the National competition, to focus on enhancing the in-game charters, stories, and supporting data.  
  

[![](https://1.bp.blogspot.com/-iY7tHhqC78k/Xag0jhdq-FI/AAAAAAAAKqE/mCVqu5DzuVIUy51szEOiQImhh_Hz5jj9ACLcBGAsYHQ/s640/Screen%2BShot%2B2019-10-13%2Bat%2B5.04.26%2BAM.png)](https://1.bp.blogspot.com/-iY7tHhqC78k/Xag0jhdq-FI/AAAAAAAAKqE/mCVqu5DzuVIUy51szEOiQImhh_Hz5jj9ACLcBGAsYHQ/s1600/Screen%2BShot%2B2019-10-13%2Bat%2B5.04.26%2BAM.png)

I hope everyone is getting ready for the National event. We have a ton of surprises ready for Nationals, so I'm really excited for it. Our National competition is open to the public if you want to come and spectate, our monitoring team always puts on a good show. I will also reveal a lot more about our infrastructure and specific OSINT secrets after the National event, when I am more comfortable revealing tangible details. If you still want more details on what goes into making this competition be sure to checkout [Tom and I's DEFCON presentation](https://github.com/ahhh/presentations/blob/master/DEFCON27%20-%20Wall%20of%20Sheep%20-%20CPTCv3.pdf) on CPTC, as well as our [Ethics Panel](https://github.com/ahhh/presentations/blob/master/DEFCON27%20-%20EthicsVillage%20-%20CPTCv3.pdf) (I'll be posting the recordings when they are released). Otherwise, I look forward to seeing everyone at the National Collegiate Penetration Testing Competition, November 22 - 24, at RIT in NY!