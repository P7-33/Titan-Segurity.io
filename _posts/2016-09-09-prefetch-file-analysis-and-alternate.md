---
title: '"Hidden" Prefetch File Analysis and Alternate Data Sources'
date: 2020-01-29T00:18:00+01:00
draft: false
---

One of the things I like to do is engage in DFIR analysis of CTF and challenge images, just to see what pops out and what new things I can learn.  I did just that recently with Dr. Ali Hadi's challenge #4, described as "launching attacks from alternate data streams".  Dr. Hadi also has a [corresponding blog post](https://www.binary-zone.com/2019/05/26/creating-a-hidden-prefetch-file-to-bypass-normal-forensic-analysis/) where he digs a bit deeper into how this approach can "bypass normal forensic analysis".  Actually, that last part of the title, about bypassing "normal forensic analysis", is what really got me interested in exploring the topic a bit further.  Let's take a look...  
  
I've been aware of and fascinated by NTFS alternate data streams (or "ADSs") for quite sometime; not just that they exist, but also how they can be and have been used.  ADSs have always been pretty cool, and something of a novelty to me; while I know what they are and look for them during analysis, I don't often find them used for malicious purposes during DFIR engagements.  
  
Dr. Hadi's blog post focuses primarily on the analysis of a single artifact, the application Prefetch files, which won't be available by default on Windows server systems. Also, you're not likely to find these files on workstation versions of Windows running on SSD drives.  In the blog post, he uses several tools for parsing and deriving data from Prefetch files, but again the focus is on those files as the data source, when it comes to finding the use of ADSs.  
  
While I don't want to think that is constitutes "normal forensic analysis", that may be the case.  I like to use multiple data sources, in particular the MFT, Registry, and Windows Event Log when looking at data, and I prefer to correlate the data sources in a timeline format.   
  
One of the first things I noticed when parsing the MFT is that the existence of the ADS jumps right out, as shown below:  
  
Sun May 26 08:36:19 2019 Z  
  MFT\_SI          - ...B \[16\] C:\\Users\\IEUser\\Desktop\\creepy\\LPT1.txt   
  MFT\_FN         - MACB \[16\] C:\\Users\\IEUser\\Desktop\\creepy\\LPT1.txt   
  MFT\_ADS       - ...B \[809984\] C:\\Users\\IEUser\\Desktop\\creepy\\LPT1.txt:putty.exe  
  
Now, an ADS shares the time stamps of its "parent" file, and does not have time stamps of its own.  It does, however, have its own size value, which is good.  So, while the parser I used clearly identifies the ADS, the time listed may not correlate to the actual creation date of the ADS itself.  In fact, the creation time ("...B") of the ADS may more closely correspond to the metadata modification ("..C.") time from the $STANDARD\_INFORMATION attribute, depending upon the actual circumstances.  
  
In this case, we have another data source available, the "bam" key from the System hive, as shown below:  
  
Sun May 26 08:41:41 2019 Z  
  MFT\_SI        - MA.B \[0\] C:\\Windows\\Prefetch\\WELCOME.TXT   
  BAM            - \\Device\\HarddiskVolume1\\Users\\IEUser\\Desktop\\creepy\\  
              welcome.txt:putty.exe (S-1-5-21-321011808-3761883066-353627080-1000)  
  MFT\_ADS    - MA.B \[6462\] C:\\Windows\\Prefetch\\WELCOME.TXT:PUTTY.EXE-A6BB0639.pf  
  MFT\_FN      - MACB \[0\] C:\\Windows\\Prefetch\\WELCOME.TXT   
  
In addition, there were remnants found in other data sources, as well.  For example, parsing the SRUDB.DAT database file, the following entries were located in the Application Resource Usage tab of the resulting XLSX file:  
  
\\Device\\HarddiskVolume1\\Users\\IEUser\\Desktop\\creepy\\LPT1.txt:putty.exe  
\\Device\\HarddiskVolume1\\Users\\IEUser\\Desktop\\creepy\\COM1.txt:revshell.exe  
  
Further, the following entry was found in the Network Usage tab of the same XLSX file:  
  
\\device\\harddiskvolume1\\users\\ieuser\\desktop\\creepy\\com1.txt:revshell.exe  
  
Finally, the following entries were located in the AppCompatCache data within the System Registry hive:  
  
\\\\?\\C:\\Users\\IEUser\\Desktop\\creepy\\welcome2.txt:revshell.exe  Sun May 26 08:33:33 2019 Z  
\\\\?\\C:\\Users\\IEUser\\Desktop\\creepy\\COM1.txt:revshell.exe  Sun May 26 08:37:34 2019 Z  
\\\\?\\C:\\Users\\IEUser\\Desktop\\creepy\\LPT1.txt:putty.exe  Sun May 26 08:37:19 2019 Z  
\\\\?\\C:\\Users\\IEUser\\Desktop\\creepy\\welcome.txt:putty.exe  Sun May 26 08:33:19 2019 Z  
  
As you can see, there is no shortage of artifacts related to ADSs on a Windows system.  The key take-away here for analysis is to not restrict your analysis to just a single artifact; instead, make a holistic approach your new "normal forensic analysis" process.  
  
I want to thank Dr. Hadi for not only providing the image file, but for also putting together the blog post describing his findings with respect to the use of ADSs, and the application Prefetch file artifacts.