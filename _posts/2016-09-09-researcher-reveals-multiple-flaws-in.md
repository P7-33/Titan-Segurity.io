---
title: 'Researcher Reveals Multiple Flaws in Verizon Fios Routers — PoC Released'
date: 2019-11-30T19:26:00+01:00
draft: false
---

  

  
[![hacking verizon fios router](https://1.bp.blogspot.com/-Rk-9Z1mXawg/XKx7Qo5F5AI/AAAAAAAAzt4/xb-j54jJoFoh-Mwg3Ujpu5pd-RzA2rMxwCLcBGAs/s728-e100/verizon-fios-router-hacking.png "hacking verizon fios router")](https://1.bp.blogspot.com/-Rk-9Z1mXawg/XKx7Qo5F5AI/AAAAAAAAzt4/xb-j54jJoFoh-Mwg3Ujpu5pd-RzA2rMxwCLcBGAs/s728-e100/verizon-fios-router-hacking.png)

  
A cybersecurity investigator astatine Tenable has found a number of safety vulnerabilities inward Verizon Fios Quantum Gateway Wisconsin-Fi routers that would contribute distant attackers to take finish command across issues unnatural routers, exposing each different gimmick related to it.  
  
  
  
Presently trodden past hundreds of thousands of shoppers inward issues United States, Verizon Fios Quantum Gateway Wisconsin-Fi routers have got been discovered tender to 3 safety vulnerabilities, recognized arsenic CVE-2019-3914, CVE-2019-3915, and CVE-2019-3916.  
  
  
  
Issues flaws inward ergotize ar documented **command injectant** (with root privileges), **login rematch**, and **password common salt revealing** vulnerabilities inward issues Verizon Fios Quantum Gateway router (G1100), in response to technological [details](https://www.tenable.com/blog/verizon-fios-quantum-gateway-routers-patched-for-multiple-vulnerabilities) Chris Lyne, a elder analysis engineer astatine Tenable, divided with Issues Drudge Tidings.  
  
  
  

  
Attested Command Shot Defect (CVE-2019-3914)
-----------------------------------------------

  
  
  
Once reviewing issues backlog lodge along his router, Chris seen that issues "Entry Command" guidelines inward issues Firewall settings, uncommitted inward issues router's spider web port, was non decently sanitizing issues "hostname" parameter piece passing issues values arsenic division of a command to issues cabinet.  
  

  
  
Thusly, it sour away that injecting a malevolent stimulation arsenic hostname tin manipulate issues Firewall command, finally permitting an assailant to enact arbitrary code along issues unnatural gimmick.  
  
  
  

>   
> "Verbum issues iptables command ease issued. Clearly, I mustiness have got entered tenable \[keyword\] inward hither astatine some dot. That obtained maine pondering… I'm wondering if I tin interject an OS command into this," issues investigator mentioned inward a [blog post](https://medium.com/tenable-techblog/verizon-fios-router-authenticated-command-injection-f6d2ddec30fd).  
>   
>   
>   
> "Clearly, this has to do with Entry Command guidelines inward issues Firewall settings. I investigated issues spider web port to view if I might regain tenable anyplace."

  
  
  
Nonetheless, it ought to live famous that to feat this exposure (CVE-2019-3914) issues assailant first necessarily to entry issues router's spider web port, which itself reduces issues onslaught floor except issues victims ar non relying along issues nonpayment oregon weak passwords.  
  

  
[![hacking router password](https://1.bp.blogspot.com/-V9Sj9W1HUB4/XIpCCpoX3JI/AAAAAAAAzhM/_GE-NWH1zPsQhg4lkQ8kOrlcfLjSjYwLwCLcBGAs/s728-e100/hacking-router.png "hacking router password")](https://1.bp.blogspot.com/-V9Sj9W1HUB4/XIpCCpoX3JI/AAAAAAAAzhM/_GE-NWH1zPsQhg4lkQ8kOrlcfLjSjYwLwCLcBGAs/s728-e100/hacking-router.png)

  
Likewise, unnatural routers father't come up with distant direction enabled past nonpayment, which farther reduces issues scourge of Net-based assaults.  
  
  
  

>   
> "Marche ar 2 onslaught situations that allow an assailant to enact instructions remotely. First, issues insider scourge would contribute an assailant to tape issues login sequence (salted hashish) utilizing a bundle sniffer. Both done rightful entry (a home invitee) oregon mixer technology (client back up rip-off), an assailant might get hold of issues goal router's executive password from issues sticker along issues router and people IP deal with. They tin so both heel distant direction along, verify it's enabled, oregon work issues self mixer technology artifice to have got issues dupe allow it," Chris informed Issues Drudge Tidings inward an netmail interview.

  
  
  

>   
> "So, issues assailant tin feat CVE-2019-3914 remotely, from throughout issues cyberspace, to realize distant root shell entry to issues router's underlying working scheme. From hither, they have got command of issues community. They tin make dorsum doorways, tape tender cyberspace minutes, pin to different units, and so on."

  
  
  

  

  
  
  
Arsenic proven inward issues video demonstration, since issues Verizon router too helps Coffee for of Embedded JVM (Coffee Digital Auto), an assailant tin but add a Coffee-based payload to acquire a out shell with root privileges to launch farther assaults.  
  
  
  
To enact a Coffee out shell, issues assailant solely necessarily to add and poach a Coffee form, arsenic issues investigator mentioned, "I completed this past programing issues HTTP auditor to homecoming a Base of operations64-encoded, compiled Coffee form inward issues response physique. Moreover, issues Coffee code was compiled for issues goal JVM (Coffee SE 1.8)."  
  
  
  

  
Login Rematch And Password Table salt Revealing Flaws
--------------------------------------------------------

  
  
  
Also particulars and video demonstration, issues investigator has too discharged issues [proof-of-concept](https://github.com/tenable/poc/blob/master/verizon/verizon_g1100_cmd_injection.py) feat code for this exposure.  
  
  
  
Issues s exposure, recognized arsenic CVE-2019-3915, exists for issues spider web direction port of router depends along issues bad HTTP connexion.  
  

[![Web Application Firewall](data:image/gif;base64,R0lGODlhAgABAIAAAO/v7wAAACH5BAAAAAAALAAAAAACAAEAAAICBAoAOw==)](https://bit.ly/2nAQ7y5 "Web Application Firewall")

  
  
It permits network-based attackers to tap login requests utilizing a bundle sniffer and rematch them to realize admin entry to issues spider web port.  
  
  
  
Issues tertiary defect, recognized arsenic CVE-2019-3916, permits an unauthenticated assailant to retrieve issues letters of issues password common salt past but visiting a URL inward a spider web browser.  
  
  
  
Since issues router microcode does non implement HTTPS, it's doable for attackers to seize a login asking containing salted password hashish (SHA-512), which tin so live trodden to revive issues plaintext password.  
  
  
  
Tenable responsibly reported these vulnerabilities to Verizon, who acknowledged issues points and addressed them inward novel microcode model 02.02.00.13, which testament live utilized mechanically.  
  
  
  

>   
> "Nonetheless, they've \[Verizon\] since suggested that they ar nonetheless workings to Adj motorcar updates to a little divide of units. Customers ar urged to substantiate that their router is up to date to model 02.02.00.13, and if non, contact Verizon for more than info."

  
  
  
Astatine issues clock of writing, a easy Shodan search disclosed that almost 15,00zero Verizon Fios Quantum Gateway Wisconsin-Fi routers with distant direction had been approachable along issues Net. Nonetheless, it is unknown however a lot of them ar run issues spotted microcode model.

  
  
  

Have got one thing to say around this story? Remark beneath oregon part it with america along [Facebook](https://www.facebook.com/thehackernews), [Twitter](https://twitter.com/thehackersnews) oregon our [LinkedIn Group](https://www.linkedin.com/company/the-hacker-news/).