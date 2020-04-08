---
title: 'Anti-Virus Maker Discovers A Bug within Ryuk Ransomware'
date: 2019-12-12T19:25:00+01:00
draft: false
---

[![](https://4.bp.blogspot.com/-D0dFlS_3XgQ/XfET0pREknI/AAAAAAAA6qA/oUyay1rdaQk6SqGCXwDpIJG-s64hPBb9ACLcBGAsYHQ/s640/Ryuk.png)](https://4.bp.blogspot.com/-D0dFlS_3XgQ/XfET0pREknI/AAAAAAAA6qA/oUyay1rdaQk6SqGCXwDpIJG-s64hPBb9ACLcBGAsYHQ/s1600/Ryuk.png)

  

An antivirus maker discovered a bug in the decrypter application of the Ryuk Ransomware, the application "the Ryuk gang" basically provides to victims to recoup their files, after they paid the ransom.  
  
While the bug causes a deficient recuperation of certain types of documents, prompting data loss, regardless of whether the victim paid the ransom demand, the primary issue, as elaborated by the antivirus maker Emsisoft in a blog post, is that the decrypter shortens one byte from the end of each file it decodes.  
  
The secondary issue is that the Ryuk gang's decryptor additionally erases the original encoded files, which means that the victims can't re-run the 'decryption operation' again with a "fixed" decryptor.   
  
While the last byte in many records is there for cushioning and is generally unused, for some file extensions those bytes contain essential data that when expelled will permanently degenerate that information and thusly prevent the document from being opened.  
  
"A lot of virtual disk type files like VHD/VHDX as well as a lot of database files like Oracle database files will store important information in that last byte and files damaged this way will fail to load properly after they are decrypted," Emsisoft says.  
  
"We're hoping to get the word out about this as quickly and widely as possible so that affected organizations can avoid data loss,"  

 - Emsisoft representative Brett Immature told ZDNet. 

  
Emsisoft advised the victims to connect by means of ryukhelp@emsisoft.com to have its analysts fix the decrypter they got from the Ryuk gang.  
  
 In any case, while Emsisoft is the organization who discharged the most "free ransomware decrypters" in the past, this is a 'paid service', as it infers its experts attempting to address each decrypter partially, a very tedious undertaking.  
  
Infections attributed to Ryuk include - manage service provider T-Systems, financial service provider ASD Audit, insulating technology manufacturer TECNOL, automation tool manufacturer Pliz, city of New Bedford (US), Tribune Publishing, managed service provider PerCSoft, healthcare provider CorVel, IT service provider CloudJumper, the city of Lake City (US), and many other more.

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/36xngMG