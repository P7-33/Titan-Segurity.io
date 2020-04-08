---
title: 'We Stood Up to a Patent Troll and Won'
date: 2019-11-05T01:49:00+01:00
draft: false
---

![](https://blog-cloudflare-com-assets.storage.googleapis.com/2019/10/unnamed.png)

Remember 2016? [Pokemon Go](https://www.youtube.com/watch?v=p-XnTDcQZjY) was all the rage, we [lost Prince](https://www.billboard.com/articles/news/7341522/prince-dead), and there were surprising election results in both the [UK](https://www.cnbc.com/2016/06/24/brexit-how-did-this-just-happen.html) and [US](https://www.politico.com/story/2016/11/election-results-2016-clinton-trump-231070). Back in 2016, Blackbird Technologies was notorious in the world of patent litigation. It was a boutique law firm that was one of the [top ten](https://www.rpxcorp.com/wp-content/uploads/sites/2/2017/05/the-most-active-patent-trolls-of-2016.pdf) most active patent trolls, filing lawsuits against more than 50 different defendants in a single year.

In October 2016, Blackbird was looking to [acquire](https://assignment.uspto.gov/patent/index.html#/patent/search/resultAssignment?id=39923-226) additional patents for their portfolio when they found an incredibly broad software patent with the ambiguous title, “PROVIDING AN INTERNET THIRD PARTY DATA CHANNEL.” They acquired this patent from its owner for $1 plus “other good and valuable consideration.” A little later, in March 2017, Blackbird decided to assert that patent against Cloudflare.

As we have [explained previously](https://blog.cloudflare.com/standing-up-to-a-dangerous-new-breed-of-patent-troll/), patent trolls benefit from a problematic incentive structure that allows them to take vague or abstract patents that they have no intention of developing and assert them as broadly as possible. Instead, these trolls collect licensing fees or settlements from companies who are otherwise trying to start a business, produce useful products, and create good jobs. Companies facing such claims usually convince themselves that settlements in the tens or hundreds of thousands of dollars are quicker and cheaper outcomes than facing years of litigation and millions of dollars in attorneys fees.  

The following is how we worked to upend this asymmetric incentive structure.  

### The Game Plan

After we were sued by Blackbird, we decided that we wouldn’t roll over. We decided we would do our best to turn the incentive structure on its head and make patent trolls think twice before attempting to take advantage of the system. We created Project Jengo in an effort to remove this economic asymmetry from the litigation. In our initial [blog post](https://blog.cloudflare.com/standing-up-to-a-dangerous-new-breed-of-patent-troll/) we suggested we could level the playing field by: (i) defending ourselves vigorously against the patent lawsuit instead of rolling over and paying a licensing fee or settling, (ii) funding awards for crowdsourced prior art that could be used to invalidate any of Blackbird’s patents, not just the one asserted against Cloudflare, and (iii) asking the relevant bar associations to investigate what we considered to be Blackbird’s violations of the rules of professional conduct for attorneys.

How’d we do?

### The Lawsuit

As promised, we fought the lawsuit vigorously. And as explained in a [blog post earlier this year](https://blog.cloudflare.com/winning-the-blackbird-battle/), we won as convincing a victory as one could in federal litigation at both the trial and appellate levels. In early 2018, the District Court for the Northern District of California dismissed the case Blackbird brought against us on subject matter eligibility grounds in response to an _Alice_ motion. In a mere [two-page order](https://blog.cloudflare.com/bye-bye-blackbird/), Judge Vince Chhabria held that “\[a\]bstract ideas are not patentable” and Blackbird’s assertion of the patent “attempts to monopolize the abstract idea of monitoring a preexisting data stream between a server and a client.” Essentially, the case was rejected before it ever really started because the court found Blackbird’s patent to be invalid.

Blackbird appealed that decision to the Court of Appeals for the Federal Circuit, which unceremoniously affirmed the lower court decision dismissing the appeal just three days after the appellate argument was heard. Following this ruling, we celebrated.  

> Killed another Blackbird. [pic.twitter.com/xSNQbHbl6Y](https://t.co/xSNQbHbl6Y)
> 
> — Matthew Prince 🌥 (@eastdakota) [February 15, 2019](https://twitter.com/eastdakota/status/1096230176109735936?ref_src=twsrc%5Etfw)

As noted in our earlier [blog post](https://blog.cloudflare.com/winning-the-blackbird-battle/), although we won the litigation as quickly and easily as possible, the federal litigation process still lasted nearly two years, involved combined legal filings of more than 1,500 pages, and ran up considerable legal expenses. Blackbird’s right to seek review of the decision by the US Supreme Court expired this summer, so the case is now officially over. As we’ve said from the start, we only intended to pursue Project Jengo as long as the case remained active.  

Even though we won decisively in court, that alone is not enough to change the incentive structure around patent troll suits. Patent trolls are repeat players who don’t have significant operations, so the costs of litigation and discovery are much less for them.

### Funding Crowdsourced Prior Art to Invalidate Blackbird Patents

#### Prior Art

An integral part of our strategy against Blackbird was to engage our community to help us locate prior art that we could use to invalidate all of Blackbird’s patents. One of the most powerful legal arguments against the validity of a patent is that the invention claimed in the patent was already known or made public somewhere else (“prior art”). A collection of prior art on all the Blackbird patents could be used by anyone facing a lawsuit from Blackbird to defend themselves. The existence of an organized and accessible library of prior art would diminish the overall value of the Blackbird patent portfolio. That sort of risk to the patent portfolio was the kind of thing that would nudge the incentive structure in the other direction. Although the financial incentives made possible by the US legal system may support patent trolls, we knew our secret weapon was a very smart, very motivated community that loathed the extortionary activities of patent trolls and wanted to fight back.

And boy, were we right! We established a prior art bounty to pay cash rewards for prior art submissions that read on the patent Blackbird asserted against Cloudflare, as well as any of Blackbird’s other patents.  

We received hundreds of submissions across Blackbird’s portfolio of patents. We were very impressed with the quality of those submissions and think they call the validity of a number of those patents into question. All the relevant submissions we collected can be found [here](https://www.cloudflare.com/blackbirdpatents/jengo/) sorted by patent number, and we hope they are put to good use by other parties sued by Blackbird. Additionally, we’ve already forwarded prior art from the collection to a handful of companies and organizations that reached out to us because they were facing cases from Blackbird.

A high-level breakdown of the submissions:

*   We received 275 total unique submissions from 155 individuals on 49 separate patents, and we received multiple submissions on 26 patents.
*   40.1% of the total submissions related to the [’335](https://patents.google.com/patent/US6453335) patent asserted against Cloudflare.
*   The second highest concentration of prior art submissions (14.9% of total) relate to [PUB20140200078](https://patents.google.com/patent/US20140200078) titled “Video Game Including User Determined Location Information.” The vast majority of these submissions note the similarity between the patent’s claims and the Niantic game [Ingress](https://en.wikipedia.org/wiki/Ingress_(video_game)).

A few interesting examples of prior art that were submitted that we think are particularly damaging to some of the Blackbird patents:  

*   **[Internet based resource retrieval system](https://patents.google.com/patent/US8996546B2/en) (No. 8996546)**  
    The first two sentences of this 2004 patent’s abstract summarize the patent as a “resource retrieval system compris\[ing\] a server having a searchable database wherein users can readily access region-based publications similar to, but not necessarily limited to, printed telephone directories. The resource retrieval system communicates with at least one user system, preferably via the Internet.”  
      
    The Project Jengo community reviewed the incredibly broad language in the patent claims and submitted a reference to an [online phone book](https://web.archive.org/web/20001109034000/http://anywho.com/) that allowed for the searching of local results from an online AT&T database. The submission is a link to an archive of a webpage from the year 2000, potentially calling into question the Blackbird patent on eligibility grounds.

*   **[Illuminated product packaging](https://patents.google.com/patent/US7086751B2/en) (No. 7086751)**  
    This patent seeks protection for packaging “intended to hold a product for sale. The product package includes one or more light sources disposed therein and configured to direct light through one or more openings in the exterior of the product package, in order to entice customers to purchase the product.”  
      
    In one of the more interesting Project Jengo submissions we received, the following information was provided: The [CD packaging](https://en.wikipedia.org/wiki/Pulse_(Pink_Floyd_album)#/media/File:Pink_Floyd_Pulse_Light_Case.jpg) for Pink Floyd’s ‘Pulse’ included a blinking LED within the cardboard box that was active and visible on store shelves. We felt that this also spoke to the heart of this broad and seemingly obvious patented product.

*   **[Sports Bra](https://patents.google.com/patent/US7867058) (No. 7867058)**  
    This Blackbird patent involves a “sports bra having an integral storage pouch.”  
      
    The Project Jengo community found that a submission on a [public discussion forum](https://www.fodors.com/community/europe/a-different-spin-on-hiding-money-in-bra-639147/) that pre-dates the ’058 patent and disclosed an idea of modifying a bra by creating an incision in the inner lining and applying a velcro strip so as to form a resealable pocket within the bra… Or essentially the same invention.  

### As a Bonus – an Ex Parte Victory

Almost immediately after we announced Jengo, we received an [anonymous donation](https://blog.cloudflare.com/patent-troll-battle-update-doubling-down-on-project-jengo/) from someone who shared our frustration with patent trolls. As we announced, this gift allowed us to expand Jengo by using some of the prior art to directly challenge other Blackbird patents in administrative proceedings.

We initiated an administrative challenge against Blackbird Patent [7,797,448](http://patft.uspto.gov/netacgi/nph-Parser?Sect2=PTO1&Sect2=HITOFF&p=1&u=/netahtml/PTO/search-bool.html&r=1&f=G&l=50&d=PALL&RefSrch=yes&Query=PN/7797448) (“GPS-internet Linkage”). The patent describes in broad and generic terms “\[a\]n integrated system comprising the Global Positioning System and the Internet wherein the integrated system can identify the precise geographic location of both sender and receiver communicating computer terminals.” You don’t have to be particularly technical to realize how largely obvious and widely applicable such a concept would be, as many modern Internet applications attempt to integrate some sort of location services using GPS. This was a dangerous patent in the hands of a patent troll.

Based on the strength of the [prior art we received](https://blog.cloudflare.com/project-jengo-strikes-its-first-targets-and-looks-for-more/) from the Project Jengo community and the number of times Blackbird had asserted the ’448 Patent to elicit a settlement from startups, we filed for an ex parte reexamination (EPR) of the ’448 Patent by the US Patent & Trademark Office (USPTO). The EPR is an administrative proceeding that can be used to challenge obviously deficient patents in a less complex, lengthy, or costly exercise than federal litigation.

We submitted our EPR challenge in November 2017. Blackbird responded to the ex parte by attempting to amend their patent’s claims to make them more narrow in an effort to make their patent more defensible and avoid the challenge. In March 2018, the USPTO issued a Non-Final Office Action that proposed rejecting the ’448 Patent’s claims altogether because the claims were found to be preempted by prior art submitted by Project Jengo. Blackbird did not respond to the Office Action. And a few months later, in August 2018, the USPTO issued a [final order](https://storage.googleapis.com/blog-cloudflare-com-assets/2019/10/jengo.pdf) in line with the office action, which cancelled the ’448 Patent’s claims. The USPTO’s decision means the ‘448 patent is invalid and no one can assert the incredibly broad terms of the ‘448 patent again.

### Rewarding the Crowd

As promised, Cloudflare distributed more than $50,000 in cash awards to eighteen people who submitted prior art as part of the crowdsourced effort. We gave out more than $25,000 to people in support of their submissions related to the ’335 patent asserted against Cloudflare. Additionally we awarded more than $30,000 to submitters in support of our efforts to invalidate the other patents in Blackbird’s portfolio.

In general, we awarded bounties based on whether we incorporated the art found by the community into our legal filings, the analysis of the art as provided in the submission, whether someone else had previously submitted the art, and the strength and number of claims the art challenged in the specified Blackbird patent.

We asked many of the recent bounty winners why they decided to submit prior art to Project Jengo and received some of the following responses:  

* * *

_"Over the years I've been disappointed and angered by a number of patent cases where I feel that the patent system has been abused by so-called ‘patent trolls’ in order to stifle innovation and profit from litigation. With Jengo in particular, I was a fan of what Cloudflare had done previously with Universal SSL. When the opportunity arose to potentially make a difference with a real patent troll case, I was happy to try and help."_

— **Adam**, Security Engineer

* * *

_"I read the ’335 patent and thought it basically described a fundamental design principle of the world wide web (proxy servers). I was pretty sure such software was in widespread use by the priority date of the patent (1998). At that point I was curious if that was true so I did some Googling."_

– **David**, Software Developer

* * *

_"Personally, I believe the vast majority of software patents are obvious and trivial. They should have never been granted. At the same time, fighting a patent claim is costly and time consuming regardless of the patent’s merit, while filing the claim is relatively cheap. Patent trolls exploit this imbalance and, in turn, they stifle innovation. Project Jengo was a great opportunity to use my knowledge of prior academic work for a good cause."_

– **Kevin**, Postdoctoral Research Scientist

* * *

_"I'm pretty excited, I've never won a single thing in my life before. And to do it in service of taking down evil patent trolls? This is one of the best days of my life, no joke. I submitted because software patents are garbage and clearly designed to extort money from productive innovators for vague and obvious claims. Also, I was homeless at the time I submitted and was spending all day at the library anyway."_

— **Garrett**, San Francisco

* * *

### What was the Impact?

The whole point of Project Jengo was to flip the incentive structure around patent trolls, who assume they can buy broad patents, spend a little money to initiate litigation, and then sit back and expect that a great percentage of defendants will send them a check. Under a proper incentive structure, they should have to expend some effort to prove their claims have merit, and we wanted to make available information that would support other potential defendants who may want to push back against claims under Blackbird patents.

One very simple measure of the impact is to review the number of new lawsuits Blackbird is bringing with its patent portfolio, which is a public record. So what does Blackbird’s activity look like on that point?

![](https://blog-cloudflare-com-assets.storage.googleapis.com/2019/10/Project_Jengo-01.png)

In the one-year period immediately preceding Project Jengo, (Q2’16-Q2’17) Blackbird filed more than 65 cases. Since Project Jengo launched more than 2.5 years ago, the number of cases Blackbird has filed has fallen to an average rate of 10 per year.  

Not only are they filing fewer cases, but Blackbird as an organization seems to be operating with fewer resources than they did at their peak. When we launched Project Jengo in May 2017, the [Blackbird website](http://web.archive.org/web/20170511234303/http://www.blackbird-tech.com/the-team/) identified a total team of 12: six lawyers, including two co-founders, four litigation counsel, as well as a patent analysis group of 6. Today, based on a review of the [website](http://www.blackbird-tech.com/leadership/) and LinkedIn, it appears only three staff remain: one co-founder, one litigation counsel, and one member of the patent analysis group.  

**Ethics Complaints** (_section_ _submitted by Cloudflare’s General Counsel, Doug Kramer)_

We filed ethics complaints against both of Blackbird’s co-founders before the bar associations in Massachusetts, Illinois, and the USPTO based on their self-described “new model” of pursuing intellectual property claims. Our complaints were based on rules of professional conduct prohibiting lawyers from acquiring a cause of action to assert on their own behalf, or in the alternative, rules prohibiting attorneys to split contingency fees with a non-attorney.

We did not file such complaints lightly, as we take ethical standards seriously and don’t think such proceedings should be used merely to harass. In this case, we think the public perception of patent trolls, who are seen as lawyers chasing an easy buck by taking advantage of distortions in the litigation process, has damaged the public perception of attorneys and respect for the legal profession--the exact sort of values the ethical rules and bar associations are meant to protect.

We based our complaints on the [assignment agreement](https://assignment.uspto.gov/patent/index.html#/patent/search/resultAssignment?id=39923-226) we found filed with the USPTO, where Blackbird purchased the ’335 patent from an inventor in October 2016 for $1. It seemed apparent that the actual but undisclosed compensation between the parties was considerably more than $1, so Blackbird may have simply acquired the cause of action or the agreement involved an arrangement where Blackbird would split a portion of any recovered fees with the inventor. Such agreements are generally prohibited by the ethical rules.

In public statements, Blackbird’s [defense](http://fortune.com/2017/05/11/blackbird-patent-troll/) to these allegations was that it (i) was not a law firm (despite the fact it is led exclusively by lawyers who are actively engaged in the litigation it pursues) and (ii) does not use contingency fee arrangements for the patents it acquires, but does use something “[similar](http://fortune.com/2017/05/11/blackbird-patent-troll/).” Both defenses were rather surprising to us. Isn’t an organization led and staffed exclusively by lawyers who are drafting complaints, filing papers with courts, and arguing before judges amount to a “law firm”? In fact, we found pleadings in other Blackbird cases where the Blackbird leadership asked to be treated as lawyers so they could have access to sensitive technical evidence in those cases that is usually off-limits to anyone but the lawyers. And what does it mean for an agreement to be merely “similar” to a contingency agreement?

The disciplinary proceedings in front of bar associations are generally confidential, so we are limited in our ability to report out developments in those cases. But regardless of the outcome, we’ve only approached bar associations in two states. Getting this back on the right track will require more than successful adjudications in front of such committees. Instead, it will take a broader change in orientation by these professional associations across the country to view such matters as more than mere political disputes or arguments between active litigants.  

Our questions go to the very heart of ensuring an ethical legal profession, they are meant to determine what safeguards should be put in place to make sure that attorneys who take the oath are held to a standard beyond mere greed or base opportunism. They go to the question of whether being an attorney is merely a job or if there are higher standards they should be held to, making sure their monopoly over the ability to bring lawsuits as officers of the court (and all the implications, costs, and power that represents) is only wielded by people who can be trusted to do so responsibly. Otherwise, what’s the point of ethical standards?

### That’s all ... for now

We’ve said from the beginning that Project Jengo was a response to the patent troll litigation and we would end it as soon as the case was over. And now it is. Although we are proud of our work on this issue, we need to turn our focus back to the company’s mission -- to help build a better Internet. But we may be back at some point. Patent trolls remain a risk to growing companies like Cloudflare and nothing in this experience has persuaded us that settling a patent lawsuit is ever the right answer. We don’t plan to settle, and if brought into such litigation again at some point in the future, we think we have a pretty good blueprint for how to respond.

The Blackbird prior art will remain available [here](https://www.cloudflare.com/blackbirdpatents/jengo/), and we remain available to consult with our colleagues at other companies who face these issues, as we have done many times over the past few years.

Finally, we would like to express our sincere gratitude to the community who researched the Blackbird patent portfolio and helped us fight this troll. It was our confidence in all of you that inspired the idea of Project Jengo in the first place, so its success belongs to you.

Thank you.  

  
  
from Hacker News https://ift.tt/32eq5zx