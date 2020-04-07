---
title: 'Modified TrickBot Trojan can now Steal Windows Active Directory
Credentials'
date: 2020-01-25T15:33:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-hXYgjtG1WVE/XixL818VsYI/AAAAAAAAB8A/kUIEsHXBOhgnmKnC0ZypxMAKkdyE9tLwgCLcBGAsYHQ/s640/windows-on-android-2690101_960_720.jpg)](https://1.bp.blogspot.com/-hXYgjtG1WVE/XixL818VsYI/AAAAAAAAB8A/kUIEsHXBOhgnmKnC0ZypxMAKkdyE9tLwgCLcBGAsYHQ/s1600/windows-on-android-2690101_960_720.jpg)

  
TrickBot trojan, a strain of malware that has been around affecting users since 2016 - is now evolved to steal Windows Active Directory credentials. Today, in the cybersecurity ecosystem it is considered as one of the top threats abusing businesses, experts estimate that TrickBot is responsible for compromising more than 250 million email accounts till date. Earlier, TrickBot went a step further while targeting Windows 10 users by disabling Windows defender onto their systems rather than just bypassing the protection. Fundamentally, TrickBot is a banking Trojan and is generally deployed through spearphishing emails like invoices mailed to the accounts department. Typically, it is attached as infected Microsoft Excel or Word documents. The malware can be spread across an organization in a number of ways, one of them is via exploiting vulnerabilities in a protocol called SMB which makes the process of sharing and accessing files on other systems easy for Windows computers.  
  
First identified by Sandor Nemes, a security researcher from Virus Total, this new module of TrickBot dubbed as "ADII" further amplifies the threat it possesses for security, it steals Windows Active Directory information by executing a set of commands.  
  
An Active Directory database is being created and stored into the default C:\\Windows\\NTDS folder on the domain controller, a server here is acting as the domain controller. Now, all the information including passwords, computers, users, and groups of Windows Active Directory are saved in a file by the name "ntds.dit" in the database. As all the aforementioned information is sensitive in nature, Windows resort to a BootKey that is located in the system component of the Registry and encrypts the information with the help of it. Admins who are responsible for database maintenance use a special tool known as "ntdsutil" to work with that database. Reportedly, standard file operations cannot access the BootKey.  
  

#### **How TrickBot Goes About Stealing Active Directory Credentials?**

  
Administrators use the command "install from media", also known as "ifm", to create a dump of Active Directory. The command leads to the creation of an installation media for setting up new Domain Controllers. The new module "ADII" exploits the ifm command to produce a copy of the Windows Active Directory database; after the database is dumped into the %Temp% folder, the bot collects the information and transfers it to the admin. The collected data can be effective in infecting more systems in the same network and could also be employed by various other malware in search of similar vulnerabilities.

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/38CmBdz