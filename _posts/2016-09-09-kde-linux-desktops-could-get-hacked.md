---
title: 'KDE Linux Desktops Could Get Hacked Without Even Opening Malicious Files'
date: 2019-11-30T18:14:00+01:00
draft: false
---

  

  
[![kde desktop linux vulnerability](https://1.bp.blogspot.com/-F42V3RvRtIM/XUp9KXvcWRI/AAAAAAAA0pM/FZVXRCu-KvQiYy9ZXfHKcgKtbdke1P9swCLcBGAs/s728-e100/kde-desktop-linux-vulnerability.jpg "kde desktop linux vulnerability")](https://1.bp.blogspot.com/-F42V3RvRtIM/XUp9KXvcWRI/AAAAAAAA0pM/FZVXRCu-KvQiYy9ZXfHKcgKtbdke1P9swCLcBGAs/s728-e100/kde-desktop-linux-vulnerability.jpg)

  
Should you ar run a KDE background setting along your Linux working scheme, you demand to live additional cautious and keep away from downloading whatsoever ".background" oregon ".listing" register for a patch.  
  
  
  
A cybersecurity investigator has discovered an unpatched zero-day exposure inwards issues KDE package fabric that would contribute maliciously crafted .background and .listing recordsdata to taciturnly poach arbitrary code along a exploiter's pc—from fifty-fifty requiring issues dupe to really unfastened it.  
  
  
  
KDE Plasm is leak of issues most pop open-source widget-based background setting for Linux customers and comes equally a nonpayment background setting along many Linux distributions, such equally Manjaro, openSUSE, Kubuntu, and PCLinuxOS.  
  

  
  
Safety investigator **Dominik Penner** who found issues exposure contacted Issues Drudge Word, ratting that marche's a command injectant exposure inwards KDE 4/Five Plasm background owed to issues manner KDE handles .background and .listing recordsdata.  
  
  
  
"Once a .background oregon .listing register is instantiated, it unsafely evaluates setting variables and shell expansions utilizing KConfigPrivate::expandString() by way of issues KConfigGroup::readEntry() part," [Penner said](https://gist.githubusercontent.com/zeropwn/630832df151029cb8f22d5b6b9efaefb/raw/64aa3d30279acb207f787ce9c135eefd5e52643b/kde-kdesktopfile-command-injection.txt).  
  
  
  

  

  
  
  

  

  
  
  
Exploiting this fault, which impacts KDE Frameworks parcel 5.60.zero and infra, is straightforward and includes some sociable technology equally an aggressor would demand to trick KDE exploiter into downloading an archives containing a malevolent .background oregon .listing register.  
  
  
  

>   
> "Utilizing a specifically crafted .background register a removed exploiter may live compromised past just downloading and showing issues register inwards their register coach, oregon past dragging and falling a tie of it into their paperwork oregon background," issues investigator defined.  
>   
>   
>   
> "Theoretically, if we tin command config entries and set off their studying, we tin attain command injectant / RCE."

  
  
  
Arsenic a proof-of-concept, Penner besides promulgated feat code for issues exposure on with 2 movies that efficiently reveal issues onslaught eventualities exploiting issues KDE KDesktopFile Command Shot exposure.  
  

[![Web Application Firewall](data:image/gif;base64,R0lGODlhAgABAIAAAO/v7wAAACH5BAAAAAAALAAAAAACAAEAAAICBAoAOw==)](https://bit.ly/2nAQ7y5 "Web Application Firewall")

  
  
Apparently, issues investigator did non statement issues exposure to issues KDE builders earlier publication issues particulars and PoC exploits, mentioned KDE Profession patch acknowledging issues exposure and assuring customers {that a} set up is along its manner.  
  
  
  

>   
> "Besides, when you find the same exposure, it's best to ship an netmail safety@kde.org earlier fashioning it people. This testament give usa clock to patch it and maintain customers escort earlier issues unhealthy guys seek to feat it," KDE Profession mentioned.

  
  
  
Meantime, issues KDE builders suggested customers to "keep away from downloading .background oregon .listing recordsdata and extracting archive from untrusted sources," for a patch till issues exposure will get spotted.  
  
  
  

  
Replace — KDE v5.61.zero Patches Command Shot Exposure
---------------------------------------------------------

  
  
  
KDE builders have got spotted this exposure past eradicating issues complete characteristic of encouraging shell instructions inwards issues KConfig recordsdata, an intentional characteristic that KDE offers for versatile configuration.  
  
  
  
In response to issues builders, KConfig may live mistreated past miscreants to do KDE customers "instal such recordsdata and acquire code executed fifty-fifty from intentional activity past issues exploiter."  
  
  
  

>   
> "A register coach stressful to regain away issues picture for a register oregon listing may terminal upward execution code, oregon whatsoever utility utilizing KConfig may terminal upward execution malevolent code throughout its inauguration stage for example," KDE mentioned inwards its safety [advisory](https://kde.org/info/security/advisory-20190807-1.txt) discharged Wed.

  
  
  

>   
> "After cautious consideration, issues complete characteristic of encouraging shell instructions inwards KConfig entries has been distant, from we could not regain an precise employ trial for it. Should you do have got an existent employ for issues characteristic, delight contact usa thusly that we tin consider whether or not it could live doable to offer a safe resolution."

  
  
  
Customers ar suggested to replace to model 5.61.zero of KDE Frameworks 5, patch customers along kdelibs ar suggested to use issues patch for kdelibs 4.14 unless inwards issues KDE Projection advisory.

  
  
  

Have got one thing to say around this story? Remark infra oregon percentage it with usa along [Facebook](https://www.facebook.com/thehackernews), [Twitter](https://twitter.com/thehackersnews) oregon our [LinkedIn Group](https://www.linkedin.com/company/the-hacker-news/).