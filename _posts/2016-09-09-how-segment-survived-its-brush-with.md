---
title: 'How Segment survived its brush with death to become a customer data unicorn'
date: 2019-12-05T01:48:00+01:00
draft: false
---

These days, Segment CEO Peter Reinhardt can boast that his customer management company has raised almost $300 million in venture capital for a [$1.5 billion valuation](https://www.bloomberg.com/news/articles/2019-04-02/startup-segment-is-worth-1-5-billion-thanks-to-companies-troves-of-customer-data). But he hasn’t forgotten the moment when the company came within inches of total failure.

It took pivoting from its initial plan and moving in an entirely different direction with a homegrown data management tool to get on track to success.

Founded in 2011, Segment (formerly known as Segment.io) seemed at first to be on the glide path to victory. Reinhardt was studying aerospace engineering at MIT, and his roommates were studying computer science. They had an idea to create a classroom lecture tool. Basically, the tool would allow students to signal to a professor that they were lost or confused during a presentation. The professor could see a graph that would let them know the overall status of the class’ comprehension and thus if the lecture was missing the mark.

The idea got Segment, [now based in San Francisco](https://segment.com/), accepted into Y Combinator. After Demo Day in the spring, the team raised $600,000 over the summer and launched the service into the classrooms that fall.

It was a dud.

“When students opened their laptops, they just went straight to Facebook, went straight to Gmail and Flickr,” Reinhardt said during a recent conversation with VentureBeat at the Slush technology conference in Helsinki, Finland.

[![CEO Peter Reinhardt of Segment](https://venturebeat.com/wp-content/uploads/2019/11/49099806486_1f1403e51c_k.jpg?w=800&resize=800%2C533&strip=all)](https://venturebeat.com/wp-content/uploads/2019/11/49099806486_1f1403e51c_k.jpg?strip=all)

Above: CEO Peter Reinhardt of Segment speaking at Slush 2019 in Helsinki, Finland.

_Image Credit: Slush/Julius Konttinen_

Doing a face plant that fast posed some dilemmas. The founders began calling investors to see if they wanted their money returned. “A couple took the money back, but for the most part, the investors told us to go find something else,” Reinhardt said. “We invested for the team.”

Pivot number one was creating an analytics tool, because the Segment team themselves had been unhappy with existing tools for analyzing data from their website. But they quickly realized that the market, even if imperfect, was saturated. “We spent about a year trying to break into that market and never really found a good differentiator,” he said.

After 18 months of existence, Segment had around $100,000 in the bank and no solid ideas. “It was pretty dark,” Reinhardt said.

The second pivot, and its last desperate play, started with a JavaScript library Segment had developed over those 18 months.

At its most basic, the JavaScript library offered a workaround to deal with the frustration the team had finding a single analytics platforms that could deliver all the insights they wanted. The JavaScript library gathered all the data being collected on the Segment website and then funneled it simultaneously to several analytics services, allowing Segment’s team to glean insights from different services such as Google Analytics or Kissmetrics. Segment could decide which service was best for each criteria it wanted to monitor about customer behavior.

In December 2012, with money running out, cofounder Ian Taylor suggested they open-source the library. “Ian was like, ‘I think this really can be a big idea’,” Reinhardt said. “And I was like, ‘That’s the worst idea I’ve ever heard.'”

Lacking options, they decided to try anyway. They [posted the JavaScript library, dubbed simply “analytics.js”, to GitHub](https://github.com/segmentio/analytics-java), began pitching developers, and shared it to Hacker News. “And it just basically blew up,” Reinhardt said.

Developers could now place one piece of code onto their websites that allowed them to use dozens of analytics services.

With this surge of interest, the company had to scramble to actually build a beta version of a core product that would work on top of this open-source project. The following year, the [company launched a hosted version of the product,](https://venturebeat.com/2013/06/03/segment-io-launches-ios-and-android-sdks-to-enable-every-app-analytics-solution-all-at-once/) called simply “Segment”.

Now, instead of centralizing their customer data using the JavaScript library and then sending it directly to numerous analytics services, companies could send it to Segment and then pick and choose which [third-party services](https://segment.com/catalog/) to integrate, including services that enabled A/B testing, email marketing, SMS push notifications, and various analytics.

Clients of Segment can now better manage the growing amounts of customer information they were gathering that had previously been stuck in different buckets that made it difficult to have a single view of a customer. By having a more complete set of data on each customer, Segment’s clients can personalize their services.

“The number of places where people interact with a company digitally has just been exploding,” Reinhardt said. “Today, you have a mobile app, a website, email, push notifications, the call center, and so on and so forth. These are different siloed communication channels into the company. The result is that the experience used to be very personal, like maybe a bank branch manager who actually knew you as a person. Now, the bank or whoever actually has no idea who you are, because the data that happens on each of those channels and stays in those tools.”

[Since this turnaround](https://venturebeat.com/2014/10/08/dropping-the-io-segment-picks-up-15m-to-become-a-bigger-customer-data-hub/), the company has continued to build new layers to its customer data infrastructure, such as Sources, an API that enhances the data centralization and expands the range of services where the information could be sent for further analysis or personalization.

The company says it now has more than 20,000 customers. That includes IBM, which uses the Segment platform to help standardize data collection across its cloud services so it can be more effectively processed and analyzed by its marketing tools. Startup TravelPerk uses Segment to unify its data collection, after several years of fast growth left different departments using different metrics tools and different data warehouses that left the company unable to answer basic questions such as, “What is the conversion rate from search to purchases?”

Becoming a central hub of customer data has created new possibilities for Segment. That includes Segment’s new data governance feature for GDPR and California’s new privacy rules.

Next up, Reinhardt hinted, are tools that will help customers leverage their information for artificial intelligence and machine learning. Rather than offering AI and ML itself, Segment will introduce tools that improve data quality so it’s more effective when clients run it against algorithms.

“We find that the biggest thing blocking people from doing machine learning is actually having clean data that’s formatted correctly for the input into the machine learning process,” Reinhardt said. “You talk to a data engineer, and they’ll say they spend 80% of their time ‘munging’ data and 20% of their time complaining about it. So what we’re trying to do is take away that 80% of the time munging the data. We’re working on a new beta part of the product that we’ll announce in the coming months that eliminates a lot of that munging.”

Segment has now raised four rounds of venture capital totaling $281 million, [including a $175 million round this past August](https://www.globenewswire.com/news-release/2019/04/02/1795157/0/en/Segment-Raises-175-Million-Series-D-to-Liberate-Customer-Data-from-CRM-and-Usher-in-a-New-Era-of-Customer-Relationships.html). But with this success has come new competition. Among those jumping into this space are [Adobe](https://venturebeat.com/2019/09/10/adobe-reimagines-customer-journey-as-layers-of-data-in-a-photoshop-image/) and [Salesforce](https://venturebeat.com/2019/06/18/salesforce-announces-a-customer-data-platform-to-unify-all-marketing-data/), both of which have announced customer data management platforms this year.

“The biggest players in the space are realizing that \[customer data management\] is a new category,” Reinhardt said.

While the company now faces fiercer battles for customers, Reinhardt recognizes how amazing it is that Segment even exists to be fighting against these big rivals. The company has certainly earned a place alongside such notable Silicon Valley pivots-to-success as Instagram or Slack.

“We sort of tripped over it,” Reinhardt said. “It was a tool that we built for ourselves. And it turned out that this was a big problem lots of people have.”

  
  
from Hacker News https://ift.tt/2OO5YVr