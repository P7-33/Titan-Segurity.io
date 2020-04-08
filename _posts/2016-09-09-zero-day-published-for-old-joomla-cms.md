---
title: 'Zero-day published for old Joomla CMS versions'
date: 2019-10-08T06:09:00+01:00
draft: false
---

![Joomla](https://zdnet1.cbsistatic.com/hub/i/2019/10/08/517d8158-c50f-4642-88e0-e0ab9605b623/c76a4bb966408f58a98e1981ba455136/joomla.jpg)

Image: Joomla team

Details have been published online last week about a vulnerability in older versions of the Joomla content management system (CMS), a popular web-based application for building and managing websites.

The vulnerability was discovered by Italian security researcher Alessandro Groppo of Hacktive Security, and impacts all Joomla versions from 3.0.0 to 3.4.6, released between late September 2012 to mid-December 2015.

The vulnerability is trivial to exploit, and proof-of-concept exploit code has been published online.

It's a PHP object injection that can lead to remote code execution (RCE) under certain scenarios. For example, it can be exploited via the Joomla CMS' login form and can allow attackers to execute code on the site's underlying server.

### Similar to an older 2015 Joomla zero-day

Groppo said the vulnerability is similar to [CVE-2015-8562](https://nvd.nist.gov/vuln/detail/CVE-2015-8562), another PHP object injection that can lead to remote code execution, although they are not related.

CVE-2015-8562 is a well-known Joomla exploit that's [being abused even to this day](https://www.imperva.com/blog/the-worlds-most-popular-coding-language-happens-to-be-most-hackers-weapon-of-choice/). When it was discovered in December 2015, the vulnerability was a zero-day, and hackers were abusing it in the wild to take over sites.

The difference between Groppo's discovery and the 2015 vulnerability is that the newer one impacts a smaller number of Joomla sites, only Joomla 3.x versions, while CVE-2015-8562 impacted all Joomla versions available at the time -- 1.5.x, 2.x, and 3.x branches.

However, despite affecting a smaller number of sites, Groppo's vulnerability has a wider impact, as it's "completely independent from the \[server\] environment," compared to the older release, which only worked against servers running a PHP version before 5.4.45, 5.5.29 or 5.6.13.

The good news is that Joomla developers appear to have fixed the issue at the core of Groppo's zero-day a release after they fixed CVE-2015-8562.

Many website owners run outdated CMS versions due to plugin and theme incompatibilities that can lead to site breakage; however, they don't need to update all the way to the latest release to be protected -- albeit that would be a much better solution.

Updating to any Joomla version of 3.4.7 or later will prevent attacks. The current Joomla version is 3.9.12.

Groppo's zero-day doesn't yet have a CVE identifier. A demo showing the zero-day in action is embedded below. A technical explanation is available [on Groppo's blog](https://blog.hacktivesecurity.com/index.php?controller=post&action=view&id_post=41), while proof-of-concept code was [uploaded on Exploit-DB](https://www.exploit-db.com/exploits/47465) last week.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2Vrpqc7