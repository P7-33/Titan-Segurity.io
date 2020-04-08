---
title: 'New WhatsApp Bug Could Have Let Hackers Spy On Users Just by Sending MP4 Video'
date: 2019-11-16T11:20:00+01:00
draft: false
---

![](https://1.bp.blogspot.com/-8iWiIzfS18g/Xc_Kng-C67I/AAAAAAAA1yg/TSUI3uc6HU86mdGEtjSCVBKQLudC93NQwCLcBGAsYHQ/s728-e100/whatsapp-hacking-vulnerability.png "New WhatsApp Bug Could Have Let Hackers Spy On Users Just by Sending MP4 Video")  

The recent controversies surrounding the

[WhatsApp hacking](https://thehackernews.com/2019/10/whatsapp-nso-group-malware.html)

haven't yet settled, and the world's most popular messaging platform is in choppy waters once again.

The Hacker News has learned that WhatsApp has recently patched yet another critical vulnerability that could have allowed attackers to remotely compromise targeted devices and potentially steal secured chat messages and files stored on them.

The vulnerability — tracked as

**CVE-2019-11931**

— is a stack-based buffer overflow issue that resided in the way vulnerable WhatsApp versions parse the elementary stream metadata of an MP4 file, resulting in denial-of-service or remote code execution attacks.

To remotely exploit the vulnerability, all an attacker needs is the phone number of targeted users and send them a maliciously crafted MP4 file over WhatsApp, which eventually can be used to install a malicious backdoor or spyware on compromised devices silently.

The vulnerability affects both consumers as well as enterprise apps of WhatsApp for all major platforms, including Google Android, Apple iOS, and Microsoft Windows.

According to an

[advisory](https://www.facebook.com/security/advisories/cve-2019-11931)

published by Facebook, which owns the popular messaging app, the list of affected WhatsApp versions are as follows:

*   Android versions before 2.19.274
*   iOS versions before 2.19.100
*   Enterprise Client versions before 2.25.3
*   Windows Phone versions before and including 2.18.368
*   Business for Android versions before 2.19.104
*   Business for iOS versions before 2.19.100

The scope, severity, and impact of the newly patched vulnerability appear similar to a recent

[WhatsApp VoIP call vulnerability](https://thehackernews.com/2019/05/hack-whatsapp-vulnerability.html)

that was exploited by the Israeli company NSO Group to

[install Pegasus spyware](https://thehackernews.com/2019/10/whatsapp-nso-group-malware.html)

on nearly 1400 targeted Android and iOS devices worldwide.

At the time of writing, it's not clear if the MP4 vulnerability was also exploited as a zero-day in the wild before Facebook learned about and patched it.

The Hacker News has reached out to Facebook and WhatsApp for comment and will update the article as soon as we hear back from them.

Meanwhile, if you consider yourself as one of the potential surveillance targets and have received a random, unexpected MP4 video file over WhatsApp from an unknown number in recent months, you should pay more attention to the upcoming developments of this event.

The WhatsApp MP4 vulnerability came just two weeks after

[Facebook sued the NSO Group](https://thehackernews.com/2019/10/whatsapp-nso-group-malware.html)

for misusing WhatsApp service to target its users.

> **Also Read:** [Just a GIF Image Could Have Hacked Your Android Phone Using WhatsApp](https://thehackernews.com/2019/10/whatsapp-rce-vulnerability.html)

However, it didn't go as well as intended, and the social media giant itself came under intense scrutiny from various governments, raising questions about the security of its end-to-end encrypted app — where the revelation of this new bug would not do any good.

For now, it's recommended for all users to make sure they are running the latest version of WhatsApp on their device.

  
  
from The Hacker News https://ift.tt/2CPJ0Gw