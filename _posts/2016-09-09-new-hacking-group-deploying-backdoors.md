---
title: 'New Hacking Group Deploying Backdoors and Ransomware in Windows via
Word docs'
date: 2019-11-16T20:51:00+01:00
draft: false
---

  

Researchers from Proofpoint have detected a scheme of malware campaigns from a new hacking group called TA2101, that's targeting various organizations from Germany and Italy, creating backdoor malware into their security systems. These attackers also trick people by impersonating the United States Postal Service and tax entities and distributing 'Maze Ransomware' as well as banking Trojans. The research group noted that these attackers use legal and licensed penetration tools like Cobalt Strike and Metasploit after entering the network. These tools are used by organizations to secure their network by analyzing loopholes and vulnerabilities, meanwhile, adversaries like Cobalt Group, APT32, and APT19 exploit this software by installing backdoors.  

[![](https://1.bp.blogspot.com/-OcgRZRG3rRQ/XdBQ-sAniqI/AAAAAAAALfc/xiYx5kpnGCEoyNCJ9W_FdTbZKZLjw5bAQCLcBGAsYHQ/s640/ransomware-2321665_960_720.png)](https://1.bp.blogspot.com/-OcgRZRG3rRQ/XdBQ-sAniqI/AAAAAAAALfc/xiYx5kpnGCEoyNCJ9W_FdTbZKZLjw5bAQCLcBGAsYHQ/s1600/ransomware-2321665_960_720.png)

  
**Deploying Backdoors in Windows via Word Docs **  
These malicious actors have been tricking victims into clicking through phishing emails that contain ransomware and even banking trojans- by sending email alerts that require immediate action, like emails from the German Federal Ministry of Finance, United States Postal Service, law enforcement and finance firms. But, what's happening behind the curtains is them deploying ransomware in your windows via a word document, that opens when you open the attachment.  
  
Proofpoint researchers have been observing these impersonators from October 16 until November 12, 2019, their collected data gave a clear sight of the attacker's target, how they operate by sending spams to companies, IT units from Germany, Italy, and United States. “Researchers also Observed a consistent set of TTP (Tactics, Techniques, and Procedures) that allows attribution of these campaigns to a single actor with high confidence. These include the use of .icu domains, as well as identical email addresses for the Start of Authority (SOA) resource records stored for the DNS entries for the domains used in these campaigns”, Proof point said.  
  
Among the samples, the emails contained attached weaponized word documents which when opened, made the system perform a series of commands- that is turning on PowerShell script, which eventually downloads and installs the Maze ransomware. In targets related to Healthcare Vertical and companies, the emails and word documents installed IcedID payload trojan into the system.

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/33Sx6Yh