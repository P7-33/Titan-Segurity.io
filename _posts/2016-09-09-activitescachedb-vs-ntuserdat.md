---
title: 'ActivitesCache.db vs NTUSER.DAT'
date: 2019-11-28T13:42:00+01:00
draft: false
---

I recently had an opportunity to work with the data available in the Windows 10 Activity Timeline, or ActivitiesCache.db file.  I'd seen a number of descriptions of the file contents, as well as descriptions of tools, but few of these are from the perspective of a DFIR analyst/responder, and none that I could find provided a view of how the data from the database stands up alongside other data sources an analyst might examine.  
  
First, I grabbed a copy of my own ActivitiesCache.db file:  
  
esentutil /y /vss \\ActivitiesCache.db /d ActivitiesCache.db  
  
Then I grabbed a copy of my NTUSER.DAT hive:  
  
reg save HKCU NTUSER.DAT  
  
I used [Eric Zimmerman's WxTCmd tool](https://binaryforay.blogspot.com/2018/05/introducing-wxtcmd.html) to parse the database; from the output, I got two CSV files (as described in Eric's blog post for the tool), one for the Activity table.  I then wrote a Perl script to translate elements of the Activity table into the 5-field TLN timeline format that I use for analysis.  This way, I was able to do something of a side-by-side comparison of data from the NTUSER.DAT hive with the contents of the ActivitiesCache.db database. Specifically, I created a timeline using the TLN variants of the UserAssist, RecentDocs, Applets, MSOffice and RecentApps RegRipper plugins, and then added the Activity table data to the events file before parsing it into a timeline.  
  
What I found was pretty interesting.  
  
For one, the data from the Activities table illustrated some interesting activity.  For example, here's what the data looks like for when I opened a PDF document from my desktop:  
  
Wed Nov 20 23:04:15 2019 Z  
  TIMELINE                   - End Time:Program Files x86\\Adobe\\Reader 11.0\\Reader\\AcroRd32.exe   
  
Wed Nov 20 23:04:14 2019 Z  
  TIMELINE                   - End Time:C:\\Users\\harlan\\Desktop\\WRR.exe   
  
Wed Nov 20 23:00:51 2019 Z  
  TIMELINE                   - Start Time:C:\\Users\\harlan\\Desktop\\WRR.exe   
  
Wed Nov 20 22:58:07 2019 Z  
  TIMELINE                   - Start Time:Program Files x86\\Adobe\\Reader 11.0\\Reader\\AcroRd32.exe C:\\Users\\harlan\\Desktop\\A\_Forensic\_Audit\_of\_the\_Tor\_Browser\_Bundle4.pdf  
  TIMELINE                   - Start Time:Program Files x86\\Adobe\\Reader 11.0\\Reader\\AcroRd32.exe  
  
I was doing some research into a particular Registry value, and a search had revealed a hit within the PDF.  I opened the PDF, and while it was open, also opened the MiTeC Windows Registry Recovery (WRR.exe) tool.  
  
Another interesting finding is illustrated below:  
  
Wed Nov 20 22:50:02 2019 Z  
  REG                        - RegEdit LastKey value -> Computer\\HKEY\_CURRENT\_USER\\Software\\Microsoft\\Windows\\CurrentVersion\\TaskFlow  
  TIMELINE                   - End Time:Windows\\regedit.exe   
  
Wed Nov 20 22:49:11 2019 Z  
  TIMELINE                   - Start Time:Windows\\regedit.exe   
  
Wed Nov 20 22:49:07 2019 Z  
  REG                        - \[Program Execution\] UserAssist - {F38BF404-1D43-42F2-9305-67DE0B28FC23}\\regedit.exe (1)  
  REG                        - \[Program Execution\] UserAssist - {0139D44E-6AFE-49F2-8690-3DAFCAE6FFB8}\\Administrative Tools\\Registry Editor.lnk (1)  
  
I opened RegEdit, navigated to a specific key, and that key was in focus when I closed RegEdit.  With respect to the LastKey value, we're aware that's the context of the data...the key that was in focus with RegEdit was closed.  What this clearly illustrates is "humanness"...human-based actions occurring and being recorded in these data sources.  We can see from the UserAssist data how RegEdit was opened, we can see how long it was open (in this case, ~50 sec or so), and which key was in focus when it was closed.  Looked at together, these artifacts provide a clear illustration of human activity.  
  
Here's another example of what correlating the two data sources can look like:  
  
Wed Nov 20 21:11:29 2019 Z  
  TIMELINE                   - End Time:C:\\Users\\harlan\\Desktop\\WRR.exe   
  
Wed Nov 20 21:10:01 2019 Z  
  REG                        - RecentDocs - Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\RecentDocs - local  
  REG                        - RecentDocs - Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\RecentDocs\\.dat - NTUSER.DAT  
  REG                        - RecentDocs - Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\RecentDocs\\Folder - local  
  
Wed Nov 20 21:09:45 2019 Z  
  TIMELINE                   - Start Time:C:\\Users\\harlan\\Desktop\\WRR.exe   
  REG                        - \[Program Execution\] UserAssist - C:\\Users\\harlan\\Desktop\\WRR.exe (1)  
  
In this particular case, I'd opened WRR and loaded an NTUSER.DAT file from a folder called "local".  
  
Here's an example of how correlating the two data sources can provide additional insight and context into accessing files:  
  
Wed Nov 20 20:20:56 2019 Z  
  REG                        - RecentDocs - Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\RecentDocs\\.doc - Armor of God.doc  
  TIMELINE                   - End Time:Program Files x86\\Microsoft Office\\Office14\\WINWORD.EXE   
  
Wed Nov 20 20:09:29 2019 Z  
  REG                        - Word File MRU - C:\\Users\\harlan\\Desktop\\Armor of God.doc  
  REG                        - Word Place MRU - C:\\Users\\harlan\\Desktop\\  
  
Wed Nov 20 20:09:28 2019 Z  
  TIMELINE                   - Start Time:Program Files x86\\Microsoft Office\\Office14\\WINWORD.EXE   
  REG                        - \[Program Execution\] UserAssist - {7C5A40EF-A0FB-4BFC-874A-C0F2E0B9FA8E}\\Microsoft Office\\Office14\\WINWORD.EXE (5)  
  
In this particular case, I was preparing for Bible study and had a Word document open.  The data from the Activity Timeline database showed that MSWord had been opened, but it took data from the NTUSER.DAT hive (RecentDocs and MSOffice plugins) to provide information about which file had been opened.  In this case, the data illustrates that I'd had the file open approximately 11 minutes.  
  
I could go on with the examples but suffice to say that the ActivitiesCache.db data provides context and validation to data from other sources; in this case, from data from the NTUSER.DAT hive associated with user activity.  Adding additional data from other sources, such as Automatic JumpLists would not only provide additional context, but would be extremely valuable in the face of anti-forensics efforts.  Getting a good view of what constitutes artifact clusters will also help us seen when elements from those clusters are missing, potentially through deletion efforts.  
  
Further, the correlation of multiple data sources gives us a better view not only of artifact clusters, but also of past activities.  As I went through the timeline data, I was references to files and applications that no longer existed on my system. I also saw references to files on external data sources (F:\\, G:\\, etc.), as well.  
  
Something else I found as a result of this exercise was that the first entry in the database table appears to be dated 20 Jun 2019.  Based solely on the data available, it would appear that an update was applied, as I'm also seeing all of the LastWrite times for RecentDocs subkeys set to the same time shortly before the first entry in the database.  A quick query via WMIC reveals that a security update was installed on that day, for KB4498523.  The finding is reminiscent of what [Jason Hale discussed in his blog post](https://df-stream.com/2019/10/shellbags-windows-10-feature-updates/) regarding shellbags and a Win10 feature update.  
  
_Going Deeper_  
A while back, Mari had written a tool to [parse deleted entries from a SQLite database](http://az4n6.blogspot.com/2013/11/python-parser-to-recover-deleted-sqlite.html), so I thought I'd give it a shot.  I downloaded the CLI version of the tool, and after running it, got a TSV file that I opened up in Excel.  There were a total of 630 rows, not all of which seemed to have much data, let alone much data of value.  However, many of the rows contained what looked like extensive JSON-formatted data.  A number of these contained references to files I'd opened in Notepad++, including the full path to the file, as well as the following:  
  
{"gdprType":"ProductAndServiceUsage","clipboardDataId":"  
  
So, much like other data sources, it appears that deleted items from this database file can provide additional insight and context, as well.  
  
_Additional Resources:_  
[GroupIB writeup](https://www.group-ib.com/blog/windows10_timeline_for_forensics)  
[Salt4n6 writeup](https://salt4n6.com/2018/05/03/windows-10-timeline-forensic-artefacts/)  
[CCLGroup LTD writeup](https://cclgroupltd.com/2018/05/03/windows-10-timeline-forensic-artefacts/)  
[Journal of Forensic Science paper](https://onlinelibrary.wiley.com/doi/abs/10.1111/1556-4029.13875)  
[Medium.com article](https://medium.com/@soji256/list-of-windows-10-timeline-analysis-articles-c61595b49e0d) - lists descriptive resources, and tools, including Mark McKinnon's Autopsy plugin  
PureInfoTech article - [disabling the Timeline Activity](https://pureinfotech.com/disable-timeline-windows-10/) feature (be sure to look for this being used for anti-forensics, or check the value if you're not finding the ActivitiesCache.db file)  
  
_Tools_:  
kacos2000 - [WindowsTimeline](https://github.com/kacos2000/WindowsTimeline/releases/)  
forensicMatt - [ActivitiesCacheParser](https://github.com/forensicmatt/ActivitiesCacheParser)  
[Eric Z's Tools site](http://ericzimmerman.github.io/#!index.md)  
[TZWorks](https://tzworks.net/prototype_page.php?proto_id=41) - Timeline ActivitiesCache parser  
Mari's [SQLParser tools](https://github.com/mdegrazia/SQLite-Deleted-Records-Parser/releases)