---
title: 'Hackers Infect 50,000 MS-SQL and PHPMyAdmin Servers with Rootkit Malware'
date: 2019-11-30T18:56:00+01:00
draft: false
---

  
[![hacking servers](https://1.bp.blogspot.com/-w8yMV_WvSCw/XO7TRSK8nLI/AAAAAAAA0Es/eTXmXA_XMbEyYWU08TPZhPXsr7F2TOVigCLcBGAs/s728-e100/hacking-servers.jpg "hacking servers")](https://1.bp.blogspot.com/-w8yMV_WvSCw/XO7TRSK8nLI/AAAAAAAA0Es/eTXmXA_XMbEyYWU08TPZhPXsr7F2TOVigCLcBGAs/s728-e100/hacking-servers.jpg)

  
Cyber Safety researchers astatine Guardicore Labs nowadays [published](https://www.guardicore.com/2019/05/nansh0u-campaign-hackers-arsenal-grows-stronger/) a elaborate statement along a widespread cryptojacking warpath attacking Home windows MS-SQL and PHPMyAdmin servers worldwide.  
  
  
  
Dubbed **Nansh0u**, issues malevolent warpath is reportedly ease nem away past an APT-style Formosan hacking grouping who has already contaminated almost 50,000 servers and ar putting in a urbane kernel-mode rootkit along compromised programs to forestall issues malicious software from ease concluded.  
  
  
  
Issues warpath, which dates dorsum to Feb 26 just was first detected inward early-Apr, has been discovered delivering 20 dissimilar payload variations hosted along diverse internet hosting suppliers.  
  

[![Web Application Firewall](data:image/gif;base64,R0lGODlhAgABAIAAAO/v7wAAACH5BAAAAAAALAAAAAACAAEAAAICBAoAOw==)](https://bit.ly/2nAQ7y5 "Web Application Firewall")

  
  
Issues onset depends along issues brute-forcing proficiency after determination doors approachable Home windows MS-SQL and PHPMyAdmin servers utilizing a easy port scanner.  
  
  
  
Upon profitable login hallmark with administrative privileges, attackers head a sequence of MS-SQL instructions along issues compromised scheme to obtain malevolent payload from a outside charge waiter and poach it with SYSTEM privileges.  
  
  
  
Inwards issues background, issues payload leverages a recognized privilege escalation exposure (CVE-2014-4113) to achieve SYSTEM privileges along issues compromised programs.  
  
  
  

>   
> "Utilizing this Home windows privilege, issues attacking stroke injects code into issues Winlogon treat. Issues injected code creates a novel treat which inherits Winlogon SYSTEM privileges, offering correspondent permissions equally issues prior model."

  
  
  
Issues payload so installs a cryptocurrency minelaying malicious software along compromised servers to mine **TurtleCoin** cryptocurrency.  
  

  
  
Too this, issues malicious software likewise protects its treat from terminating utilizing a digitally-signed kernel-mode rootkit for persistence.  
  
  
  

>   
> "We discovered that issues driver had a digital touch issued past issues high Certificates Authority Verisign. Issues certificates – which is expired – bears issues call of a imitation Formosan firm – Hangchow Hootian Web Engineering."

  
  
  
Researchers hold likewise discharged a finish [list of IoCs](https://github.com/guardicore/labs_campaigns/tree/master/Nansh0u) (indicators of {compromise}) and a free [PowerShell-based script](https://github.com/guardicore/labs_campaigns/blob/master/Nansh0u/detect_nansh0u.ps1) that Home windows directors tin can work to bank check whether or not their programs ar contaminated oregon non.  
  
  
  
Since issues onset depends along a weak username and password combos for MS-SQL and PHPMyAdmin servers, admins ar suggested to e'er hold a robust, composite password for his or her accounts.  
  
  

Hold one thing to say around this story? Remark beneath oregon percentage it with america along [Facebook](https://www.facebook.com/thehackernews), [Twitter](https://twitter.com/thehackersnews) oregon our [LinkedIn Group](https://www.linkedin.com/company/the-hacker-news/).