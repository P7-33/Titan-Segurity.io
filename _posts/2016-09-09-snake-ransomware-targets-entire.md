---
title: 'SNAKE Ransomware Targets Entire Corporate Systems?'
date: 2020-01-11T08:47:00+01:00
draft: false
---

[![](https://2.bp.blogspot.com/-ktCDDLhRWS0/Xhh7gJuWLMI/AAAAAAAA7TM/wOsJ5KukMoQ_795RV-Pj9lfGE2i9R4t_wCLcBGAsYHQ/s640/snake-ransomware-header.jpg)](https://2.bp.blogspot.com/-ktCDDLhRWS0/Xhh7gJuWLMI/AAAAAAAA7TM/wOsJ5KukMoQ_795RV-Pj9lfGE2i9R4t_wCLcBGAsYHQ/s1600/snake-ransomware-header.jpg)

  

The new Snake Ransomware family sets out to target the organizations’' corporate networks in all their entirety, written in Golang and containing a significant level of obfuscation, the observations and disclosure for the attacks were made by a group of security specialists from the MalwareHunterTeam.  
  
The Ransomware upon successful infection subsequently erases the machine's Shadow Volume Copies before ending different processes related to SCADA frameworks, network management solutions, virtual machines, and various other tools.  
  
After that, it continues to encrypt the machine's files while skirting significant Windows folders and system files. As a feature of this procedure, it affixes "EKANS" as a file marker alongside a five-character string to the file extension of each file it encrypts. The threat wraps up its encryption routine by dropping a ransom note entitled "Fix-Your-Files.txt" in the C:\\Users\\Public\\Desktop folder, which instructs victims to contact "bapcocrypt@ctemplar.com" so as to purchase a decryption tool.  
  

[![](https://4.bp.blogspot.com/-EUCkTIlm9Uc/XhiDgBPhC6I/AAAAAAAA7TY/nSQgcrmxuOkuuyZLCmRgsb6ocKGp-w3AQCLcBGAsYHQ/s640/Screen-Shot-2020-01-08-at-06.49.28.png)](https://4.bp.blogspot.com/-EUCkTIlm9Uc/XhiDgBPhC6I/AAAAAAAA7TY/nSQgcrmxuOkuuyZLCmRgsb6ocKGp-w3AQCLcBGAsYHQ/s1600/Screen-Shot-2020-01-08-at-06.49.28.png)

The ransom note of SNAKE ransomware (Source: Bleeping Computer)

  
“It is clearly evident from the language in the ransom note, that this Ransomware specifically targets the entire network rather than individual workstations. Further indicating that any decryptor that is purchased will be for the network and not individual machines, but it is too soon to tell if they would make an exception.”  

 - This is what Bleeping Computer said in a blog post on SNAKE. 

  
Nonetheless, the rise of SNAKE Ransomware highlights the critical requirement for organizations to defend themselves against a Ransomware infection.  
  
While making effective use of the suggestions to forestall a Ransomware infection in the first place, they ought to likewise consider 'investing' into a solution like Tripwire File Analyzer for the purpose of distinguishing suspicious documents and conduct on the network.  
  

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/36ICgI1