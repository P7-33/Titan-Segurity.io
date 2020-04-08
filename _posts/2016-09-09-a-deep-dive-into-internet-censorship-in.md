---
title: 'A Deep Dive into Internet Censorship in Russia'
date: 2019-11-08T08:42:00+01:00
draft: false
---

This post highlights how the Russian government is gradually **building national-level censorship policies on thousands of ISPs using commodity DPIs**, a trend that we fear other countries with similar topological structure will follow. By working with activists on the ground in Russia, Censored Planet **obtained 5 leaked blocklists signed by Roskomnadzor** (Federal Service for Supervision of Communications, Information Technology, and Mass Media) along with **seven years of historical blocklist data**. We used this authoritative blocklist that contains more than 130,000 domains to perform an in-depth investigation into the Russian government’s censorship policy by collecting measurement data from residential, data center and infrastructural vantage points.

### High Level Takeaways:

*   With our measurements from ISPs that cover over 65% of the Russian IP space, and observation of high percentage of blocking in residential networks, we confirm that Russia is succeeding at building a national censorship apparatus out of commodity equipment (i.e., inexpensive DPIs). This raises alarm and confirms that there is neither a need for a government-run technical choke points with several layers of complexity nor major government investment, as seen by the Chinese GFW, to achieve synchronized and homogeneous nationally restrictive internet access.
    
*   Roskomnadzor maintains a real-time authoritative blocklist and passes laws that require ISPs to block content. Currently the blocklist contains 170,000 domains, 1,681,000 IPs, and 39 subnets. It has around 10 times more websites than [Citizen Lab’s curated blocklist](https://github.com/citizenlab/test-lists) from all countries combined. Even with a list of such scale, our measurements show that ISPs are successful at blocking.
    
*   Upon investigation of the content on the websites in the blocklist, we find that 63% of the websites are in Russian and 28% are in English. While the top categories include gambling and pornography, we find some Russian-language news, politics and circumvention websites in the blocklist.
    
*   Looking at 7 years of leaked daily blocklists, the size of the blocklist appears to have grown rapidly since its conception in November 1, 2012, indicating Russia’s growing desire to exercise information control. We observed over the past year that much effort has been put into better maintaining and sanitizing the blocklist.
    
*   Our residential vantage points experience high levels of censorship. Interestingly, what is striking is the transparency of ISPs in injecting explicit notices to users when censorship is enforced, which we later determined is based on guidelines dictated by Roskomnadzor.
    
*   Our findings suggest that data centers block differently from the residential ISPs both in quantity and in method of blocking. In most countries, residential ISPs are subject to different laws and policies for information control.
    

Information control has long been a goal of many countries, and with advancements in technology that enable it, entities like the Great Firewall of China are not the only threats to freedom on the Internet. As filtering technology gets cheaper to buy and easier to deploy, more nation-states are moving towards using them to achieve network and information control. One striking example is what has been happening in Russia over the past decade. A country that once had very little censorship has been thrust into the spotlight due to the blocking of millions IPs to block Telegram and their steadily growing blocklist. In our work, we illuminate on the reality of achieving this control using law and policy to compel ISPs to comply and enforce information control.

**It was long thought that large-scale censorship on decentralized networks like Russia, United States, India and the United Kingdom was prohibitively difficult. Our exhaustive study of Russia’s censorship infrastructure shows that that is not the case.**

Our study has shown that the implementation of such decentralized control breaks the mold of what “censorship” traditionally connotes: the monolithic blocking of large swaths of content from border to border within a country. But in Russia with the advent of SORM and commoditization of censorship and surveillance technology it has become relatively easy and cheap for ISPs to comply. However, the means by which ISPs comply vary widely, as does their degree of compliance.

### Background on Russia

The primary entity in charge of nationwide Russian Internet censorship is called Roskomnadzor. Other government bodies may request that Roskomnadzor block sites that have content directly related to their scope of duty. But Roskomnadzor is responsible for systematizing and maintaining a singular and centralized blocklist.

Figure 1 highlights important events from the past decade illustrating Russia’s tightening censorship that began with a list of “extremist” websites, to which political dissident blogs and content were added, and it slowly evolved to become a list of over 170,000 domains added for a variety of reasons.

![](https://censoredplanet.org/assets/russia-timeline-2.jpg)

_Figure 1._ Timeline of Russian Information Control

### In-depth Analysis

A comprehensive censorship measurement study must overcome three main challenges: 1) What to measure. A measurement study needs an **authoritative blocklist** to understand the censorship regime. Currently, blocklists are often crowdsourced curated domain lists. 2) How to obtain vantage points. The study needs multiple complementary vantage points to obtain insights into different networks. Previous studies often utilized VPSes inside data centers or the collaboration of volunteers. 3) How to infer censorship. Developing methods and establishing sound controls to differentiate natural failures from actual censorship measured in the study.

**What to measure:** Censored Planet obtained **five snapshots of the blocklist digitally signed by Roskomnadzor** from activists within the country. In a snapshot taken on April 24 2019 that was used in our paper, the list contained 132,798 domains, 324,695 IPs and 39 Subnets. **The activists also pointed us to a [GitHub repository](https://github.com/zapret-info/z-i) that contained over 26,000 commits that tracked daily updates to this blocklist.** To validate this repository, we calculated the Jaccard index of the leaked signed blocklists with the repository commit on the same dates and we found that they were over 99% similar.

_Figure 2._ Evolution of the blocklist

![](https://censoredplanet.org/assets/russia-evolution.png)

Using the 7-year historical data from the repository, Figure 2 shows the evolution of the blocklist over the years. As shown, **the size of the blocklist appears to have grown rapidly, indicating Russia’s growing desire to exercise information control.** We see a significant gap between the raw number of IPs and the number of unique IPs added to the blocklist which is due to multiple websites being hosted at the same IPs and added to the list separately. In the past year, the sharp increase in the number of both raw and unique IPs, a moderate increase in the number of unique domains, shows that much effort has been put into **better maintaining and sanitizing the blocklist.** Reports from activists in Russia suggest that there have been deliberate efforts from the government to better maintain the list, mainly due to the [“DIGITALRESISTANCE morse prank”](https://usher2.club/articles/msg-digitalresistance/) and the reason that the number of IPs was growing close to TCAM memory limit of certain router models.

We initially experimented with using off-the-shelf categorization services to classify domains. However, these services do not work well with non-English language webpages. Considering over 63% of the websites are in Russian and 28% are in English, we develop a topic modelling method based on [prior work](https://petsymposium.org/2017/papers/issue1/paper06-2017-1-source.pdf). While the most popular topics by far are gambling and pornography, we also identified **some Russian news websites with political content such as [chechenews.com](https://chechenews.com), [graniru.org](https://graniru.org), [2019.vote](https://2019.vote)** (tactical voting by Alexey Navalny and his team) **and circumvention tools in the blocklist.** We attribute the large number of gambling websites to domains that clone quickly to a mirror domain when added to the blocklist (e.g. 02012019azino777.ru, 02012018azino777.ru).

**How to obtain vantage points:** We used the authoritative blocklist to perform an in-depth investigation into the Russian government’s censorship policy by collecting measurement data from residential, data center and infrastructural vantage points. Considering renting VPSes in Russian data centers requires payment in Rubles, an in-country phone number and address, activists on the ground helped us obtain six VPSes in data centers that observe network filtering. We also recruited participants to help with measurement from their residential networks. Considering the potential risk, we fully followed community norms and obtained their explicit consent.

**How to infer censorship:** Direct measurement methods benefit from direct access to a machine within networks, and they are highly useful for investigating instances of censorship. In our direct measurements, for a given IP address or domain, we determine whether it is being blocked; if yes, we determine how the blocking is performed. We focus on three common types of blocking: TCP/IP blocking, DNS manipulation, and keyword based blocking.

To complement this data, and to determine whether our direct measurements are representative, we use two remote measurement tools from Censored Planet: Satellite and Quack. Satellite and Quack use the behavior of existing Internet protocols and infrastructure to detect DNS and keyword based blocking respectively, i.e. we do not need to obtain access to vantage points but just interact with remote systems to learn information about the remote network.

**With over 1,000 remote measurement vantage points for Quack and Satellite and 20 direct vantage points, our coverage within Russia spans 361 unique ASes that control ≈ 65% of Russian IP address space.**

![](https://censoredplanet.org/assets/russia-blocking.jpg)

_Figure 3._ Results of Direct Measurement—Data center and residential vantage points respectively

From the results of our direct measurement, we see that the blocking percentage (of the blocklist) and the blocking type are different between residential networks and data center networks. This is further confirmed by our knowledge that data center hosting providers are not required to be registered as ISPs and may not have to abide by the same laws.

*   Our residential vantage points experience high levels of censorship. Interestingly, what is striking is the transparency of ISPs in injecting explicit notices to users when censorship is enforced, which we later determined is based on guidelines dictated by Roskomnadzor.
    
*   Our findings suggest that data centers block differently from residential ISPs both in quantity and in method of blocking. An accurate representative view of censorship is achievable only with measurements from a diverse set of vantage points, especially in residential ISPs. In most countries, residential ISPs are subject to different laws and policies for information control.
    
*   We also observe that residential ISPs tend to block the kind of traffic they see more frequently, which is predominantly traffic involving domains, as opposed to IPs.
    

Previously, Russia was known for using naive censorship approaches. For example, while trying to block Telegram, they blocked entire subnets of Amazon Elastic Compute Cloud, Google Cloud, Digital Ocean, OVH (and hence other websites and services) causing collateral damage. They have since moved to more advanced technologies such as deep packet inspection (DPI) and keyword based blocking due to the commoditization of these technologies that make them cheaper and easier to deploy. The “Sovereign RUnet” law that comes into effect on November 1, 2019 requires telecom operators to install “special equipment” on their networks to handle 100% of all traffic in-path as a security measure against “external threats”. The most important part of this enforcement is that Roskomnadzor will be allowed to centrally manage the routing of traffic on this equipment.

This is a trend we have observed in many countries: the United States, the United Kingdom, India, Indonesia, Portugal are all slowly moving towards this model and this should serve as a warning to researchers and policymakers. The United Kingdom’s censorship architecture is similar to Russia’s, with the government providing ISPs a list of websites to block and having governing censorship bodies that correspond to various types of censored material. Indonesia recently implemented content filtering at its network borders. India has been ramping up censorship using Supreme Court orders imposed on ISPs. In the United States, the repeal of net neutrality is allowing ISPs to favor certain content over others, which was the technical starting point of greater censorship in Russia.

**Ethical consideration:** Regardless of whether measurements are collected from participant machines (e.g. volunteers) or from remote vantage points (e.g. organizational DNS servers), censorship measurements can cause risks to owners of these devices. Aiming to set a high ethical standard, we carefully designed our experiments to follow the best practices described in the [Menlo reports](https://www.caida.org/publications/papers/2012/menlo_report_actual_formatted/menlo_report_actual_formatted.pdf) as well as community norms. We also shaped our data collection methods through a year of continuous communication with prominent activists within Russia, with colleagues experienced in censorship and measurement research, and with our university's General Counsel.

### Conclusion

From November 1, 2012, seven years ago, when Roskomnadzor rolled out its first official blocklist to ISPs until now, we have seen how gradually Russia is building national-level censorship policies on top of its decentralized network. Russia is not stopping here; rather, it has sought perfect harmony in blocking by rolling out another law this week, Russia’s “Sovereign RUnet” law, that requires telecom operators to install “special equipment” on their networks in the name of security measures against “external threats”.

Russia’s effort over the past decade to control content on its decentralized networks and the lessons and experiences it has gathered in tightening control are applicable to networks in countries all over the world—notably, countries that historically have not favored censorship. **Russia’s censorship architecture is a blueprint, and perhaps a forewarning of what national censorship regimes could look like in many other countries that have similarly diverse ISP ecosystems to Russia’s.**

_Russia's rise to prominence as a censor is wake-up call for censorship researchers, journalists, activists, and citizens of the global Internet. Understanding decentralized control will be key to continuing to preserve Internet freedom for years to come._

  
  
from Hacker News https://ift.tt/2CqYhxu