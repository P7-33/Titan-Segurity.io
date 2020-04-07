---
title: 'First RegRipper 2020 Update'
date: 2020-01-04T14:48:00+01:00
draft: false
---

'cogphn' recently reached to me via the RegRipper GitHub repo to let me know that they'd found an issue with a plugin, and this was followed by a similar issue posted by William Schaefer.  It seems that as soon as the clocks rolled over to 2020, the function within the Parse::Win32Registry module that gets key LastWrite times and translates them from FILETIME to Unix epoch format broke, and started returning 0.  I fixed the function, and recompiled the executable files for _rip.exe_ and the RegRipper GUI (_rr.exe_), and uploaded copies of the files to GitHub.  
  
If you're just using the Windows executables, all you should need to do at this point is simply download the updated EXE files and you'll be on your way.  I've done some local testing and things seem to be back on track.  If you do find that there are continued issues, please let me know.  
  
If you're running RegRipper as its Perl variant, I've also uploaded the 'fixed' Base.pm file, and included instructions in the readme file regarding updating your local copy of the file.  
  
_**Addenum, 10 Jan**_  
This issue also impacted regtime.exe, so I went ahead and recompiled the EXE and uploaded it to the [Github repo](https://github.com/keydet89/Tools/tree/master/exe).  The source code (Perl script) did not require any modifications, but if you are running the Perl script, be sure to get the new Base.pm file and replace the one in your Parse::Win32Registry install, if you haven't already.