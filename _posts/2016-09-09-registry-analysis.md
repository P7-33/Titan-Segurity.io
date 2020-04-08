---
title: 'Registry Analysis'
date: 2019-10-21T23:16:00+01:00
draft: false
---

Something I've observed over the years is that analysis of the Windows Registry is still a largely misunderstood, misinterpreted, and under-appreciated aspect of analysis of Windows systems.  
  
What is "Registry analysis"?  Registry analysis is the observation and interpretation of data or metadata from the Windows Registry, in the context of other data/metadata, also from the Registry or other sources.  The correct interpretation of this data can add an unprecedented level of granularity to the context surrounding various events observed during, for example, timeline analysis.  
  
"Registry analysis" is _not_ the parsing and display of individual artifacts from within the Registry; that's "parsing and display".  It's also not keyword searching of the Registry; that's "keyword searching".  Keyword searches or searches for indicators do not constitute "analysis". I do understand, however, that not all cases require Registry analysis.  There are more than a few types of cases out there where keyword searching is all that is necessary, and I get it.  Through engaging with other analysts and following up on conversations, I've seen where keyword searches have more than sufficed for a number of types of cases.  But that's not the "analysis" we're talking about here.  
  
That is not to say that keyword or indicator searches cannot be used as pivot points into more fully-fledged analysis.  Very often, these searches can be an excellent entry point into analysis, allowing the investigator to winnow through vast amounts of data to determine what is initially important.   
  
Analysis techniques where I have been able to incorporate data and metadata from the Windows Registry into an overall analysis process, have allowed me to get a better understanding of inherent activity derived or extracted from a system.  This has occurred to the point, in some cases, of changing the direction of my investigation.  Further, I'll be the first to admit that I haven't seen everything there is to see; in fact, within just the past weeks, I've observed activity that I had never seen before, and was able to develop an understanding of what activity led to the observed artifacts.  This is not something for which keyword searching would have sufficed, and was only achieved by bringing together multiple data sources in a manner that allowed me to discern context.  
  
Why is this important?  Well, for one, Windows keeps changing.  Yes, yes, I know, we've heard this before...Windows Vista was a big leap forward (with respect to DFIR artifacts) over XP/2003, and Windows 7 a similar "leap".  There were some pretty interesting changes in the short-lived Windows 8/8.1 world, but we've arguably seen a (dare I say, "significant"?) spike in changes just between versions of Windows 10 since that version has been out.  The point is that you can't often go for a week or two before something new with respect to the Windows operating system (and specifically the Registry) is discovered or observed.  An analysis process accounts for these changes occurring.  For example, one of the approaches I use to winnow down data is to create mini-timelines and overlays; in short, using very specific data sources to create a mini-timeline in order to get a view of the data without all the inherent "noise" of the operating system.  I'll create a timeline from a user's Registry hives, incorporating not just time-based data extracted from the hives (i.e., shellbags, UserAssist data, etc.), but also the overall metadata from those hives.  This way, I can 'see' a user's activities over time, without having to wade through massive amounts of "noise", such as Windows Updates.  And, I'll not only be able to develop context, but I'll also see new things, as well.  
  
Speaking of which, let's take a look at the [great work Jason Hale has done](https://df-stream.com/2019/10/shellbags-windows-10-feature-updates/), as an example. Some of the things we've (I use the universal "we") seen over the years have been Registry key LastWrite times associated with USB devices being universally 'stomped' by updates, as well as Registry hive "backups" no longer being written (by default) to the _RegBack_ folder.  
  
Jason [recently pointed out](https://df-stream.com/2019/10/shellbags-windows-10-feature-updates/) that key LastWrite times associated with MRUs within the shellbags artifacts have been 'stomped' by an update, similar to what was observed with USBStor keys.  What impact would this have had on your analysis had this happened 6 months, or 2 years ago?  How would this have impacted your findings in a case?  
  
Why is understanding the use and function of the Registry important when it comes to analyzing Windows systems?  
  
Two important aspects of the Windows Registry that I've discussed during many of my speaking engagements have been:  
  
_The Windows Registry contains a great deal of configuration information about the system that, if correctly understood and correctly interpreted, can have a significant impact on your analysis._  
  
The Registry contains a lot of configuration settings for the operating system, many set by default, right "out of the box".  There are others that can be changed along the way that have an impact on what users of the systems can see and do, as well as what attackers can do.  For example, there's a setting that tells the Windows operating system to store credentials in memory, in plain text.  Attackers can set this value to "1", wait a week, and come back and dump the credentials from memory, and not have to spend time cracking the passwords.  There are settings that tell the Windows shell to not show all user accounts on the Welcome screen, as well as settings that control the functionality of Terminal Services, etc.  There are even settings within the Registry that control what users can and cannot access, and how their account functions (i.e., deleted files bypass the Recycle Bin, etc.).  Understanding these settings, as well as knowing how to determine when (or if) they changed, can have a significant impact on an investigation.  
  
There are also a number of "autostart" locations within the Registry, keys or values that tell the operating system to start applications with no other interaction from the user beyond booting the system, or logging in. Consider this [Threat Research blog post](https://forums.juniper.net/t5/Threat-Research/New-Gootkit-Banking-Trojan-variant-pushes-the-limits-on-evasive/ba-p/319055) regarding newly-discovered malware, for example.  Not only does it include what is reportedly a new persistence mechanism, but it also includes a figure illustrating how code used by the malware is encoded and placed in the Registry for later use.  Knowing this, encountering an infected system and incorporating this into our analysis will allow us to discover new information about how the malware operated or was used.  
  
As a side-note, does anyone have an NTUSER.DAT file from a user profile infected with the malware identified in the [Juniper Threat Research blog post](https://forums.juniper.net/t5/Threat-Research/New-Gootkit-Banking-Trojan-variant-pushes-the-limits-on-evasive/ba-p/319055)?  I'm curious if the _binaryImage32\_\*_ values are detected by the RegRipper sizes.pl plugin.  Thanks in advance to anyone who can check, or share such a hive file.  
  
_The Windows Registry records and maintains a great deal of user activity that, if correctly understood and interpreted, can illustrate "humanness"; that is, provide strong indications of specific, purposeful human activity, as opposed to the automatic effects of the operating system, or of malware.  _  
  
There are a number of user actions...opening or saving files, launching applications, etc...that are recorded within the Windows Registry, as part of tracking user activity in order to improve the "user experience".  The idea is to make Windows more "user friendly", in part by making the more frequently used functionality more easily accessible to the user.  The key here is that actions specifically taken by the user can be interpreted as "humanness", as the data recorded is the direct result of a person interacting with the Windows shell, applications, etc.  This can provide information to inform an investigation, particularly when knowing when someone was sitting at the keyboard is important, or when discerning whether a user or some automated function accessed data is a critical aspect of an investigation.  
  
_Thankz/Shout-Outz_  
Thankz and shout-outz are due to a number of folks within the #DFIR community who've contributed to the topic through research, creating tools, etc.  In no specific order:  
  
[Mari DeGrazia](https://twitter.com/maridegrazia)  
[Maxim Suhanov](https://twitter.com/errno_fail)  
[Jason Hale](https://df-stream.com/)  
[Eric Zimmerman](https://twitter.com/EricRZimmerman)  
[farmerK](https://twitter.com/elwell)  
  
I apologize profusely for any names I may have missed, as it was not intentional.