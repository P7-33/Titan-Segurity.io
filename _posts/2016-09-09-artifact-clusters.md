---
title: 'Artifact Clusters'
date: 2019-12-04T02:54:00+01:00
draft: false
---

Very often within the DFIR community, we see information shared (usually via blog posts) regarding a "new" artifact that has been recently unearthed, or simply being addressed for the first time.  In some cases, the artifact is new to us, and in others, it may be the result of some new feature added to the Windows operating system or to an application.  Sometimes when we see this new artifact discussed, a tool is shared to parse and make sense of the data afforded by that artifact.  In some cases, we may find that multiple tools are available for parsing the same artifact, which is great, because it shows interest and diversity in the approach to accessing and making use of the data.  
  
However, what we _don't_ often see is how that artifact relates to other artifacts from the same system.  Another way to look at it is, we don't often see how the tool, or more importantly, the data available in the source, can serve us to further an investigation. We may be left thinking, "Great, there's this data source, and a tool that allows me to extract and make some sense of the data within it, but how do I _use_ it as part of an investigation?"  
  
[![](https://1.bp.blogspot.com/-D-LoDVQBe0E/XeEGE2Gz9bI/AAAAAAAACSA/PsfgvCSVUp8SEdw9vQ2S2QnlKqvqbsAcQCLcBGAsYHQ/s200/iws.jpg)](https://1.bp.blogspot.com/-D-LoDVQBe0E/XeEGE2Gz9bI/AAAAAAAACSA/PsfgvCSVUp8SEdw9vQ2S2QnlKqvqbsAcQCLcBGAsYHQ/s1600/iws.jpg)  
I shared an initial example of what this might look like recently in [a recent blog post](http://windowsir.blogspot.com/2019/11/activitescachedb-vs-ntuserdat.html), and this was also the approach I took when I wrote about the investigations in _[Investigating Windows Systems](https://www.amazon.com/Investigating-Windows-Systems-Harlan-Carvey/dp/0128114150)._ I hadn't seen any books available that covered the topic of digital forensic _analysis_ (as opposed to just parsing data) from an investigation-wide perspective, completing an investigation using multiple artifacts to "tell the story".  The idea was (and still is) that a single artifact, or a single entry derived from a data source, does _NOT_ tell the whole story of the investigation.  A single artifact may be a high fidelity indicator that provides a starting point for an investigation, but it does not tell the whole story. Rather than a single artifact, analysts should be looking at artifact clusters to provide the necessary context for an analyst to make a finding as to what happened.  
  
Artifact clusters provide two things to the investigator; validation and context.  Artifact clusters provide validation by reinforcing that an event occurred, or that the user took some action.  That validation may be a duplicate event; in [my previous blog post](http://windowsir.blogspot.com/2019/11/activitescachedb-vs-ntuserdat.html), we see the following events in our timeline:  
  
Wed Nov 20 20:09:28 2019 Z  
  TIMELINE                   - Start Time:Program Files x86\\Microsoft Office\\Office14\\WINWORD.EXE   
  REG                        - \[Program Execution\] UserAssist - {7C5A40EF-A0FB-4BFC-874A-C0F2E0B9FA8E}\\Microsoft Office\\Office14\\WINWORD.EXE (5)  
  
What we see here (above) are duplicate events that provide validation.  We see via the UserAssist data that the user launched WinWord.exe, and we also see validation from the user's Activity Timeline database.  Not only do we have validation, but we can also see what the artifact cluster should look like, and as such, have an understanding of what to look for in the face of anti-forensics efforts, be they intentional or the result of natural evidence decay.  
  
In other instances, validation may come in the form of supporting events.  For example, again from my previous blog post, we see the following two events side-by-side in the timeline:  
  
Wed Nov 20 22:50:02 2019 Z  
  REG                        - RegEdit LastKey value -> Computer\\HKEY\_CURRENT\_USER\\Software\\Microsoft\\Windows\\CurrentVersion\\TaskFlow  
  TIMELINE                   - End Time:Windows\\regedit.exe   
  
In this example, we see that the user closed the Registry Editor, and that the user's LastKey value was set, illustrating the key that was in focus when the Registry Editor was closed.  Rather than being duplicate events, these two events support each other.  
  
Looking at different event sources during the same time period also helps us see the context of the events, as we get a better view of the overall artifact cluster.  For example, consider the above timeline entries that pertain to the Registry Editor.  With just the data from the Registry, we can see when the Registry Editor was closed, and the key that was in focus when it was closed.  But that's about all we know.   
  
However, if we add some more of the events from the overall artifact cluster, we can see not just _when_, but _how_ the Registry Editor was opened, as illustrated below:  
  
Wed Nov 20 22:49:11 2019 Z  
  TIMELINE                   - Start Time:Windows\\regedit.exe   
  
Wed Nov 20 22:49:07 2019 Z  
  REG                        - \[Program Execution\] UserAssist - {F38BF404-1D43-42F2-9305-67DE0B28FC23}\\regedit.exe (1)  
  REG                        - \[Program Execution\] UserAssist - {0139D44E-6AFE-49F2-8690-3DAFCAE6FFB8}\\Administrative Tools\\Registry Editor.lnk (1)  
  
From a more complete artifact cluster, we can see that the user had the Registry Editor open for approximately 51 seconds.  Information such as this can provide a great deal of context to an investigation.  
  
_Evidence Oxidation_  
Artifact clusters give us a view into the data in the face of anti-forensics, either as dedicated, intentional, targeted efforts to remove artifacts, or as natural evidence decay or oxidation.  
  
Wait...what?  "Evidence oxidation"?  What is that?  I [shared some DFIR thoughts on Twitter](https://twitter.com/keydet89/status/1198232826585288705) not long ago on this topic, and in short, what this refers to is the natural disappearance of items from artifact clusters due to the passage of time, as some of those artifacts are removed or overwritten as the system continues to function. This is markedly different from the purposeful removal of artifacts, such as Registry keys being specifically and intentionally modified or deleted.  
  
This idea of "evidence decay" or "evidence oxidation" begins with the _Order of Volatility_, which lists different artifacts based on their "lifetime"; that is to say that different artifacts _age out_ or _expire_ at different rates.  For example, a process executed in memory will complete (often with seconds, or sooner) and the memory used by that process will be freed for use by another process in fairly short order.  That process may result in the operating system or application generating an entry into a log file, which itself may roll over or be overwritten at various rates (i.e., the entry itself is overwritten as newer entries are added), depending upon the logging mechanism.  Or, a file may be created within the file system that exists until someone...a person...purposefully deletes it.  Even then, the contents of the file may exist (NTFS resident file, etc.) for a time after the file is marked as "not in use", something that may be dependent upon the file system in use, the level of activity on the system, whether a backup mechanism (backup, Volume Shadow Copy, etc.) occurred between the file creation and deletion times, etc.  
  
In short, some artifacts may have the life span of a snowflake, or a fruit fly, or a tortoise.  The life span of an artifact can depend upon a great deal; the operating system (and version) employed, the file system structure, the auditing infrastructure, the volume of usage of the system, etc.  Consider this...I was once looking at a USN Change Journal from an image acquired from a Windows 7 system, and the time span of the available data was maybe a day and a half.  Right around that time, a friend of mine contacted me about a Windows 2003 system he was examining, for which the USN Change Journal contained 90 days worth of data.  
  
Windows systems can be very active, even when they appear to be sitting idle with no one actively typing at the keyboard.  The operating system itself may reach out for updates, during which files are downloaded, processes are executed, and files are deleted.  The same is true for a number of applications. Once a user becomes active on the system, the volume of activity and changes may increase dramatically.  I use several applications (Notepad++, UltraEdit, VirtualBox, etc.) that all reach out to the Internet to look for updates when they're launched.  Just surfing the web causes browser history to be generated and cached.