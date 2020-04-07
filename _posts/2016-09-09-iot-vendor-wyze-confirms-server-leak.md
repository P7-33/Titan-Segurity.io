---
title: 'IoT vendor Wyze confirms server leak'
date: 2019-12-29T05:19:00+01:00
draft: false
---

![Wyze](https://zdnet1.cbsistatic.com/hub/i/2019/12/29/797eb17d-df54-4158-9395-bc2756e77fda/wyzeblackcam.jpg)

Image: Wyze, ZDNet

Wyze, a company that sells smart devices like security cameras, smart plugs, smart lightbulbs, and smart door locks, confirmed today a server leak that exposed the details of roughly 2.4 million customers.

The leak occurred after an internal database was accidentally exposed online, Wyze co-founder Dongsheng Song [said in a forum post](https://forums.wyzecam.com/t/updated-12-27-19-data-leak-12-26-2019/79046) published over Christmas.

Song said the exposed database -- an Elasticsearch system -- was not a production system; however, the server was storing valid user data. The Elasticsearch server, a technology for powering super-fast search queries, was set up to help the company sort through the vast amount of user data. The Wyze exec explains:

_"**To help manage the extremely fast growth of Wyze, we recently initiated a new internal project to find better ways to measure basic business metrics like device activations, failed connection rates, etc.**_

_**We copied some data from our main production servers and put it into a more flexible database that is easier to query. This new data table was protected when it was originally created. However, a mistake was made by a Wyze employee on December 4th when they were using this database and the previous security protocols for this data were removed. We are still looking into this event to figure out why and how this happened.**"_

The leaky server was discovered and documented by cyber-security consulting firm [Twelve Security](https://blog.12security.com/wyze/) and independently verified by [reporters from IPVM](https://ipvm.com/reports/wyze-leak), a blog dedicated to video surveillance products.

Song showed his dissatisfaction with how the two parties, Twelve Security and IPVM, handled the data leak disclosure, giving Wyze only 14 minutes to fix the leak before going public with their findings.

_**"We were first contacted through a support ticket at 9:21 a.m. on December 26 by a reporter at IPVM.com. The article was published almost immediately after (Published to Twitter at 9:35 a.m.). It was published in conjunction with a blog post from a private security company also published on December 26th. We were made aware of this article at ~10:00 a.m. from a community member who had read the article."**_

Song confirmed that the leaky server exposed details such as the email addresses customers used to create Wyze accounts, nicknames users assigned to their Wyze security cameras, WiFi network SSID identifiers, and, for 24,000 users, Alexa tokens to connect Wyze devices to Alexa devices.

The Wyze exec denied that Wyze API tokens were exposed via the server. In its blog post, Twelve Security claimed they found API tokens that they say would have allowed hackers to access Wyze accounts from any iOS or Android device.

Second, Song also denied Twelve Security's claims they were sending user data back to an Alibaba Cloud server in China.

Third, Song also clarified Twelve Security claims that Wyze was collecting health information. The Wyze exec said they only collected health data from 140 users who were beta-testing a new smart scale product.

Song didn't deny Wyze collected height, weight, and gender information. He did, however, deny others.

"We have never collected bone density and daily protein intake," the Wyze exec said. "We wish our scale was that cool."

For now, the three parties involved in the disclosure of this leak appear to be at odds in regards to the specifics of this particular leak. Either way, Wyze said it decided to forcibly log out all Wyze users out of their accounts and unliked all third-party app integrations -- two steps that will generate new Wyze API tokens and Alexa tokens once users re-log in and re-link Alexa devices to Wyze accounts.

> As per my records, Wyze had huge Elasticsearch cluster publicly exposed. It included 1,807,201,457 records: log data, API requests and events. [https://t.co/RtxDLiqPtC](https://t.co/RtxDLiqPtC)
> 
> — Bob Diachenko (@MayhemDayOne) [December 28, 2019](https://twitter.com/MayhemDayOne/status/1211064652915978241?ref_src=twsrc%5Etfw)

  
  
from Latest Topic for ZDNet in... https://ift.tt/2MAUjro