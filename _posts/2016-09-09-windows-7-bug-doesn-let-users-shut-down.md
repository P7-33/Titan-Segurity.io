---
title: 'Windows 7 Bug Doesn''t Let Users Shut down Their Computers, Here''s the
Fix'
date: 2020-02-10T09:21:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2020/02/windows-7-shutdown-bug.jpg)

Microsoft officially discontinued support for Windows 7 last month but it appears like Windows 7 issues won’t let them be done with the operating system quite yet. The tech giant was [forced to roll out an update](https://support.microsoft.com/en-us/help/4539601/windows-7-update-kb4539601) to fix black wallpapers and now, there exists **a bug that reportedly doesn’t let users shut down their Windows 7 PCs**.  

Several users are facing the issue as we see on Microsoft forums and Reddit. **The error states _“You don’t have permission to shut down this computer”_**when users try to shut down their systems as they normally do.  

Microsoft is aware of the issue and the company is striving to fix it. As of now, it remains unclear if the issue has originated from Windows as some users are claiming that a recent Adobe update has caused the issue. _“We are aware of some Windows 7 customers reporting that they are unable to shut down without first logging off and are actively investigating”,_ a Microsoft spokesperson told BleepingComputer.  

Like most other Windows issues, there are unofficial workarounds to fix the issue, so let’s take a look at two possible ways to fix the issue. The workaround below is applicable only to Professional, Ultimate, and Enterprise editions of Windows 7.  

Fix Windows 7 Shutdown Bug
--------------------------

  

1\. Open Run (Windows + R) and access Group Policy Editor by **typing “gpedit.msc”**. In the Group Policy Editor, navigate to Computer Settings -> Windows Settings -> Security Settings -> Local Policies -> Security Options.  

![Fix Windows 7 Shutdown Bug - 1](https://beebom.com/wp-content/uploads/2020/02/Fix-Windows-7-Shutdown-Bug-1.jpg)

2\. Look for “**User Account Control: Run all administrators in Admin approval**” and enable it.  

![Fix Windows 7 Shut down Bug - 2](https://beebom.com/wp-content/uploads/2020/02/Fix-Windows-7-Shut-down-Bug-2.jpg)

3\. Open Command Prompt and run “**gpupdate /force**” and you’re done. Do note that a system restart is mandatory for the changes to take effect. Run the command “shutdown -r ” to restart the machine.

  
  

  

![Fix Windows 7 Shutdown Bug - 3](https://beebom.com/wp-content/uploads/2020/02/Fix-Windows-7-Shutdown-Bug-3.jpg)

   

As I mentioned earlier, some users claim that Adobe is causing the issue. The issue **reportedly gets fixed by disabling its Windows services**. To do so, open Run, type  “services.msc” and **disable “Adobe Genuine Monitor Service”,  “Adobe Genuine Software Integrity Service”,  and “Adobe Update”.**  

![Fix Windows 7 Shut down Bug - 4](https://beebom.com/wp-content/uploads/2020/02/Fix-Windows-7-Shut-down-Bug-4.jpg)

Some users have fixed the issue by creating a new admin account and switching back to the old admin profile, deleting and recreating the Admin profile as well. We will wait for Microsoft’s response to the issue that will hopefully come out once they’re done with the investigation. Until then, follow these workarounds to shut down your system.  

_Featured image courtesy: ZDNet_  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/windows-7-bug-shutdown-issues-fix/)  
\[the\_ad id='1307'\]