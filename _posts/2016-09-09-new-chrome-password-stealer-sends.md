---
title: 'New Chrome Password Stealer, ''CStealer'' Sends Stolen Data to a MongoDB
Database'
date: 2019-11-30T17:23:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-Zo3psMAAdso/XeKXKNhAdKI/AAAAAAAABw4/yt9sCutRVI4ykukB9R9axTgYDE1due1gQCLcBGAsYHQ/s640/browser-773215_960_720.webp)](https://1.bp.blogspot.com/-Zo3psMAAdso/XeKXKNhAdKI/AAAAAAAABw4/yt9sCutRVI4ykukB9R9axTgYDE1due1gQCLcBGAsYHQ/s1600/browser-773215_960_720.webp)

  
The information collected by the Chrome browser including passwords, usernames, and other user credentials is being exposed to heavy risk as a new trojan known as CStealer attempts to steal the confidential data stored onto Google's Chrome browser.  
  
Password stealer trojans include applications that tend to run in the background and silently gather sensitive information about the system such as connected users and network activity. It attempts to steal confidential information stored onto the system and the browsers like usernames, passwords and other credentials which once being stolen are sent to a specified destination by the attacker.  
  
While the idea behind this info-stealing trojan is just like many others- which is to steal user credentials saved onto the browser's password manager, however, the fact that CStealer uses a remote MongoDB database to store the stolen data is what makes this case unprecedented and interesting.  
  
The malware which was discovered by MalwareHunterTeam and was later analyzed by James does not compile and send the stolen data to a C2 under the author's command, rather, it is programmed to directly connect to a remote MongoDB data and utilize it to keep the stolen passwords stored, according to the findings.  
  
As soon as the passwords are successfully stolen, the malware tends to link to the database and store the stolen data as per the network traffic created which was examined by James. In order to carry this out, the malware carries hardcoded MongoDB credentials and to connect to the database, it uses the MongoDB C Driver as the client library.  
  
Notably, the approach is a bit more sophisticated and not as mainstream, however, ultimately it gets the agenda right as it successfully gets the credentials stolen. In doing so, indirectly it also gives a free invitation to other hackers to access the victim's confidential information as it tends to decrypt the privacy layers already. To exemplify, anyone who would examine the malware afterward, from law enforcers to security officers, will be able to retrieve the hardcoded passwords and employ them to get to the stolen data.

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/2OAfN9h