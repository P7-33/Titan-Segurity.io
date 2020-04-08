---
title: 'Avast: No plans to discontinue CCleaner following second hack in two years'
date: 2019-10-22T01:27:00+01:00
draft: false
---

![CCleaner](https://zdnet4.cbsistatic.com/hub/i/2019/10/21/335ade1b-ac93-41be-9201-d7f0702ef0d8/04c1c3c279da30334fe6d40c39d3d5c1/ccleaner.jpg)

Image: Avast

Ever since it bought Piriform in July 2017, the CCleaner software has brought only headaches to Czech cybersecurity firm Avast.

First, Chinese hackers breached Piriform's servers even before the Avast acquisition, inserting malware into official releases; and leaving the Czech antivirus maker to deal with the PR fallout all throughout 2017 and 2018.

Then, [today, Avast discovered that hackers targeted CCleaner once again](https://www.zdnet.com/article/avast-says-hackers-breached-internal-network-through-compromised-vpn-profile/), this time compromising its main internal network in the process, and yet again, seeking to tamper with CCleaner releases.

However, despite being nothing but a source of problems, Avast says it has no plans to discontinue the CCleaner app for the foreseeable future.

"The CCleaner product is a thriving, best in class product and performs an important function for users," Avast told ZDNet today. "We intend for CCleaner to continue to thrive and to be used by current and new customers."

### CCleaner's history and criticism

[CCleaner](https://www.ccleaner.com) is a Windows app that was launched in 2004. For most of its lifetime, the app has been managed by Piriform, a company that [Avast acquired in July 2017](https://press.avast.com/avast-acquires-piriform-maker-of-ccleaner).

The app started as a "registry cleaner," a type of app that removes old Windows Registry entries after users have uninstalled old apps, in an effort to cut down the Registry's size and improve Windows OS speed.

The app evolved across the years, and now supports a trove of other features, such as removing temporary or old files left behind by other apps, performing automatic updates for other apps, and even blocking ad trackers, among many other things.

Avast claims the app has been downloaded more than 2.5 billion times and has 435 million users across 68 countries.

This success came despite the fact that [Microsoft](https://support.microsoft.com/en-us/help/2563254/microsoft-support-policy-for-the-use-of-registry-cleaning-utilities) and [security experts](https://decentsecurity.com/registry-cleaners/) have strongly recommended against using any registry cleaner apps, as most do more harm than good.

### The 2017 hack

But it's exactly this success that brought hackers knocking on Piriform's door. Back in April 2017, even before the Avast acquisition, a group of Chinese state-sponsored hackers breached Piriform's network via a TeamViewer account, searched for CCleaner distribution servers, and then released a CCleaner update tainted with malware.

This malware, known under the name of Floxif, worked as a basic scanner, collecting info on infected hosts, and sending the info back to the Chinese hackers.

Hackers were looking for computers installed on the networks of several major tech companies, such as Cisco, Microsoft, Google, NEC, and others. These computers would receive a second more potent malware strain that worked as a backdoor into the compromised networks.

Avast said that 2.27 million users received the tainted CCleaner update back in 2017; 1,646,536 computers were infected with the first-stage Floxif trojan; but only 40 computers received the more powerful backdoor.

Avast handled the 2017 breach with grace, never using the excuse that "Piriform was hacked, not us," and kept users updated on their investigation at every step \[[1](https://blog.avast.com/update-to-the-ccleaner-5.33.6162-security-incident), [2](https://blog.avast.com/avast-threat-labs-analysis-of-ccleaner-incident), [3](https://blog.avast.com/new-investigations-in-ccleaner-incident-point-to-a-possible-third-stage-that-had-keylogger-capacities), [4](https://blog.avast.com/update-ccleaner-attackers-entered-via-teamviewer)\] -- laying the ground for how many companies should handle security breaches.

### The 2019 hack

But today, Avast disclosed a second hack. This time, the hackers breached Avast's own network, as the company migrated CCleaner to its infrastructure following the 2017 hack. Just like the last time, the hackers were looking to compromise CCleaner again.

Avast said hackers compromised an employee's VPN credentials to access a temporary VPN profile that was left active and without 2FA protection. This was their entry point inside Avast's network.

The company is still investigating this second breach but said that hackers weren't successful at pushing out a malicious CCleaner release today.

While Avast refrained from attributing the attack to any threat actor, the Czech Security Information Service (BIS), the country's intelligence service, said in a [press release](https://www.bis.cz/aktuality/bis-spolupracovala-se-spolecnosti-avast-na-odvraceni-utoku-na-jeji-produkty-6acda7bf.html) today that Chinese hackers were behind this attack, just like in the first.

### More than a registry cleaner

In the light of this second hack, many users have expressed their opinions today, claiming that Avast should just retire CCleaner, as the app is only a magnet for state-sponsored hackers, and that the app has no real purpose (many consider registry cleaner apps as being useless or plain harmful).

However, as previously stated in this article, today, CCleaner is more than just a "useless" registry cleaner. The app now supports remote management features, hard drive defragmentation, email alerts, cloud-based management features, and many more. It's an all-in-one system administration toolkit, and one very good at its job, if we're to look at its download numbers.

The app's gigantic userbase makes CCleaner a perfect target for supply-chain attacks. However, this huge userbase is also the reason why Avast bought it in the first place.

Avast's plan of attack involves bolstering its security. As the company told ZDNet, the threats it's facing are no different than what its competitors are facing.

For example, TeamViewer, which offers an eponymously named product, [also suffered a security breach](https://www.zdnet.com/article/chinese-cyberspies-breached-teamviewer-in-2016/) at the hands of Chinese hackers back in 2016. As long as an app is good at its job, hackers are going to keep coming.

"We believe all global software companies, including both Microsoft and us at Avast, will need to continue to vigilantly protect our networks from attacks by those who seek to damage us and our users," Avast told us.

But Avast and TeamViewer aren't the only companies that have been targeted only to serve as a jumping point into the network of other companies.

Supply-chain attacks are today's top threat, and government agencies in [the US](https://www.us-cert.gov/china) and [France](https://www.zdnet.com/article/france-warns-of-cyberattacks-against-service-providers-and-engineering-offices/) have recently issued alerts about an ongoing campaign perpetrated by Chinese hackers. Such attacks are likely to continue for the coming years, especially as most companies migrate their infrastructure to centrally-managed cloud-based systems.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2JbPQtB