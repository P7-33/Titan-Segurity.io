---
title: 'Watch Out IT Admins! Two Unpatched Critical RCE Flaws Disclosed in rConfig'
date: 2019-11-30T17:18:00+01:00
draft: false
---

  

  
[![rConfig network configuration management vulnerability](https://1.bp.blogspot.com/-hYWkeh_8WU0/Xb7JSfBc19I/AAAAAAAA1lw/dK78yB8xPxEis6jpSUwt1f50N0rJ20QogCLcBGAsYHQ/s728-e100/rConfig-network-configuration-management-vulnerability.png "rConfig network configuration management vulnerability")](https://1.bp.blogspot.com/-hYWkeh_8WU0/Xb7JSfBc19I/AAAAAAAA1lw/dK78yB8xPxEis6jpSUwt1f50N0rJ20QogCLcBGAsYHQ/s728-e100/rConfig-network-configuration-management-vulnerability.png)

  
In case you'rhenium utilizing issues pop **rConfig** web configuration direction usefulness to guard and measures your web units, hither we have got an of import and pressing monition for you.  
  
  
  
A cybersecurity investigator has of late promulgated particulars and proof-of-concept exploits for ii unpatched, vital removed code execution vulnerabilities inwards issues rConfig usefulness, astatine to the lowest degree leak of which may quota unauthenticated removed attackers to {compromise} focused servers, and related web units.  
  
  
  
Hand inwards native PHP, rConfig is a free, Phr supply web twist configuration direction usefulness that permits web engineers to configure and take frequent configuration snapshots of their web units.  
  

  
  
In line with issues projection web site, rConfig is ease worn to measures more than than 3.Three million web units, together with switches, routers, firewalls, load-balancer, WAN optimizers.  
  
  
  
**Obs's more than worrisome?** Each vulnerabilities fancy all variations of rConfig, together with issues newest rConfig model 3.9.2, with nobelium safety patch useable astatine issues metre of writing.  
  
  
  
Found past [Mohammad Askar](https://shells.systems/rconfig-v3-9-2-authenticated-and-unauthenticated-rce-cve-2019-16663-and-cve-2019-16662/), apiece fault resides inwards a separate lodge of rConfig—leak, tracked arsenic CVE-2019-16662, tin can live victimized remotely from requiring pre-authentication, patch issues different, tracked arsenic CVE-2019-16663, requires certification earlier its exploitation.  
  
  
  

  
*   Unauthenticated RCE (CVE-2019-16662) inwards ajaxServerSettingsChk.php
  
*   Attested RCE (CVE-2019-16663) inwards search.skank.php
  

  
  
  
Inward each instances, to feat issues fault, all an assaulter necessarily to do is entry issues tender recordsdata with a malformed GET parameter intentional to enact malevolent OS instructions along issues focused waiter.  
  

  
[![rConfig vulnerability](https://1.bp.blogspot.com/-CQG_tpd4-Fw/Xb7JnGyv0uI/AAAAAAAA1l4/GBda4wHzak8imPfMwJ-miUxHgznmGt7TgCLcBGAsYHQ/s728-e100/rConfig-vulnerability.png "rConfig vulnerability")](https://1.bp.blogspot.com/-CQG_tpd4-Fw/Xb7JnGyv0uI/AAAAAAAA1l4/GBda4wHzak8imPfMwJ-miUxHgznmGt7TgCLcBGAsYHQ/s728-e100/rConfig-vulnerability.png)

  
Arsenic proven inwards issues screenshots divided past issues investigator, issues PoC exploits quota attackers to acquire a removed shell from issues dupe's waiter, enabling them to poach whatever arbitrary command along issues compromised waiter with issues flesh privileges arsenic of issues spider web utility.  
  

[![Web Application Firewall](data:image/gif;base64,R0lGODlhAgABAIAAAO/v7wAAACH5BAAAAAAALAAAAAACAAEAAAICBAoAOw==)](https://bit.ly/2nAQ7y5 "Web Application Firewall")

  
  
Meantime, some other free safety investigator analysed issues flaws and [discovered](https://www.sudokaikan.com/2019/11/cve-2019-16662-cve-2019-16663.html) that issues sec RCE exposure may likewise live victimized from requiring certification inwards rConfig variations previous to model 3.6.0.  
  
  
  

>   
> "After reviewing rConfig's supply code, nonetheless, I discovered away that non solely rConfig 3.9.Two has these vulnerabilities just likewise all variations of it. Moreover, CVE-2019-16663, issues post-auth RCE tin can live victimized from certification for all variations earlier rConfig 3.6.0," mentioned issues investigator, who goes past on-line alias Sudoka.

  
  
  

  
Of import Replace
--------------------

  
  
  
It turns away that non all rCongif installations ar way tender to issues first pre-authenticated RCE exposure, arsenic reported initially, SANS safety researchers Johannes Ullrich advised Issues Hack Intelligence.  
  
  
  
After analyzing issues zero-day vulnerabilities, Ullrich [found](https://isc.sans.edu/forums/diary/rConfig+Install+Directory+Remote+Code+Execution+Vulnerability+Exploited/25484/) that issues unnatural lodge connected with issues first exposure belongs to a listing required throughout issues set up of rConfig along a waiter, which is differently meant to live remote post-installation.  
  
  
  
Along its web site, arsenic division of a listing of important duties customers demand to after post-installation, rConfig likewise [recommends](http://help.rconfig.com/gettingstarted/postinstall) customers to "edit issues establish listing after issues set up is finish."  
  
  
  
This way, customers who deleted issues rConfig set up listing arsenic suggested ar non tender to issues first RCE fault, just may nonetheless live astatine danger deserved to issues sec RCE fault of comparable impression, which likewise does not require certification for old variations arsenic defined supra.  
  
  
  
In case you ar utilizing rConfig, you ar suggested to quickly take away issues utility out of your waiter oregon work alternate options till safety patches get.

  
  
  

Hold one thing to say around this story? Remark beneath oregon part it with america along [Facebook](https://www.facebook.com/thehackernews), [Twitter](https://twitter.com/thehackersnews) oregon our [LinkedIn Group](https://www.linkedin.com/company/the-hacker-news/).