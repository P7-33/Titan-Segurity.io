---
title: 'Indian Security Researcher Finds Starbucks API Key Exposed on GitHub'
date: 2020-01-03T12:41:00+01:00
draft: false
---

  

[![](https://1.bp.blogspot.com/-HI2Z5_bYweg/Xg8jjzvh-2I/AAAAAAAAB4E/J7oa3260euIvb4_8GTomJKFS6rMIy9cYwCLcBGAsYHQ/s640/starbucks-2346226_960_720.jpg)](https://1.bp.blogspot.com/-HI2Z5_bYweg/Xg8jjzvh-2I/AAAAAAAAB4E/J7oa3260euIvb4_8GTomJKFS6rMIy9cYwCLcBGAsYHQ/s1600/starbucks-2346226_960_720.jpg)

  
Developers at Starbucks left an API (Application Programming Interface) key exposed to hackers with no password protection that could have been used by them to gain access to internal systems and consequently manipulate the list of authorized users. Hackers could have exploited the vulnerability in several ways which allowed them to execute commands on systems, add or remove the listed users and AWS account takeover.  
  
The key was discovered by Vinoth Kumar who is an India security researcher, he happened to locate the open key in a public GitHub repository and responsibly reported it to Starbucks on 17th October via HackerOne vulnerability coordination and bug bounty platform. While reporting the same, HackerOne told, “Vinoth Kumar discovered a publicly available Github repository containing a Starbucks JumpCloud API Key which provided access to internal system information.”  
  
“While going through Github search I discovered a public repository which contains JumpCloud API Key of Starbucks.” the expert himself told.  
  
The key would have allowed an attacker to access a Starbucks JumpCloud API and hence the severity of the flaw was all the way up to critical. Colorado-based JumpCloud is an Active Directory management platform that offers a directory-as-a-service (DaaS) solution that customers employ to authorize, authenticate and manage users, devices, and applications. Other services it provides include web app single-on (SSO) and Lightweight Directory Access Protocol (LDAP) service.  
  
The issue had been taken into consideration by Starbucks very early on, however, Kumar tends to take note of the same on October 21 and told that the repository had been taken down and the API key had been revoked. As soon as the company examined Kumar's proof-of-concept of the flaw and approved of the same, the expert was rewarded with a bounty worth US$4,000 for responsibly disclosing the vulnerability.  
  
While commenting on the matter, Starbucks said, “Thank you for your patience! We have determined that this report demonstrates “significant information disclosure and is therefore eligible for a bounty,”  
  
“At this time, we are satisfied with the remediation of the issue and are ready to move to closure. Thank you again for the report! We hope to see more submissions from you in the future.”

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/2SNVuaR