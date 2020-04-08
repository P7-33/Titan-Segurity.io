---
title: '10 Common Problems in Windows 10 (With Solutions)'
date: 2019-11-15T09:21:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

Windows 10 is unquestionably awesome with its experimental yet innovative features. Along **with its exciting features also come bunch of bugs** that have troubled lots of people including us. Hence today, in this post, we’re going to talk about the 10 most common problems in Windows 10 along with their solutions. Come on folks, let’s solve problems.  

1\. Windows 10 Can’t Install Windows Updates
--------------------------------------------

  

**Problem:** I can’t install updates anymore in Windows 10 after Windows Update got crashed one day due to some issue (like Internet or power failure or system crash).  

**Solution:** The problem occurs because Windows Update files get corrupted due to the issue. Hence, removing the corrupted files solves the issue, which can be done easily by following these steps:  

1.  Press **Win+R** keys to open the Run dialog
  
3.  Type “_C:WindowsSoftwareDistributionDownload_” and press OK
  
5.  File Explorer gets open – **delete all the files/folders** in this directory (in case you can’t delete the files, boot Windows into ‘safe mode’ and then try deleting the files)
  
7.  Restart your PC and try running the Windows Update again – it will work
  

![Windows 10 Can’t Install Windows Updates](https://beebom.com/wp-content/uploads/2016/05/1-windows-10-can%E2%80%99t-install-windows-updates.jpg)

2\. Windows Store Can’t Install or Update Apps
----------------------------------------------

  

**Problem:** I am unable to install or update metro apps through Windows Store after upgrading my system to Windows 10. The new OS is more or less useless for me this way.  

**Solution:** The problem arises due to the excessive cache files that clutter-up your system, causing various issues including this one. This problem could be solved by cleaning those cached files, which can be done using these steps:  

1.  Press **Win+R** keys to open the Run dialog
  
3.  Type “_WSReset.exe_” and click OK
  
5.  A blank, **black window will appear** that will auto-close after sometime
  
7.  Windows Store will also open thereafter, and even if not, open Windows Store yourself and try installing or updating apps now – it will work
  

![Windows Store Can’t Install or Update Apps](https://beebom.com/wp-content/uploads/2016/05/2-windows-store-can%E2%80%99t-install-or-update-apps.jpg)

3\. Can’t Find ‘Open with’ in Windows 10
----------------------------------------

  

**Problem:** I can’t find the ‘Open with’ option in the context menu after right-clicking any file in Windows 10. I’m not sure it disappeared recently or wasn’t there from right after the upgradation to Windows 10, but I’d like to get ‘Open with’ back.  

**So****lution:** This problem is an infrequent case but it very probably happens due to some missing or corrupted system files or configuration settings after upgrading to Windows 10. The issue can be fixed by following these steps:

  
  

  

1.  Open **Notepad**
  
3.  Type in following:
  

Windows Registry Editor Version 5.00  
\[HKEY\_CLASSES\_ROOT\*shellexContextMenuHandlersOpenwith\]@=”09799AFB-AD67-11d1-ABCD-00C04FC30936”  

3.  Save the file by going to File -> **Save as** (and not Save), and type “Openwith.reg” as filename and choose ‘All files’ and click OK
  
5.  Close Notepad and **double-click** on this file to open
  
7.  Press **Yes** in the confirmation dialog and try using ‘Open with’ now – it will work
  

![Can’t Find ‘Open with’ in Windows 10](https://beebom.com/wp-content/uploads/2016/05/3-can%E2%80%99t-find-%E2%80%98open-with%E2%80%99-in-windows-10.jpg)

4\. Can’t Login Automatically using Microsoft Account
-----------------------------------------------------

  

**Problem:** I am unable to use ‘automatic login’ facility using the (new) Microsoft account. I really wish I don’t have to type the password every time to login into Windows 10.  

**Solution:** Logging in automatically using the Microsoft account comes disabled in Windows 10, and to enable this feature, follow these steps:  

1.  Press **Win+R** keys to open the Run dialog
  
3.  Type in “_netplwiz_” and press OK
  
5.  In the opened window, click on the account for which you want to enable ‘automatic login’
  
7.  Uncheck (or untick) the option ‘**Users must enter a username and password to use this computer**’ and click OK
  
9.  Enter that account’s password twice in the new dialog, and click OK to enable automatic login and try logging in automatically now – it will work
  

![Can’t Login Automatically using Microsoft Account](https://beebom.com/wp-content/uploads/2016/05/4-can%E2%80%99t-login-automatically-using-microsoft-account.jpg)

5\. Windows 10 Overuses Mobile Data
-----------------------------------

  

**Problem:** I have noticed that tethering mobile data to Windows 10 via WiFi Hotspot depletes the mobile data quickly than ever. I found that Windows 10’s automatic updates was one of the main source, and even various metro apps uses lots of data. How can I disable them?  

**Solution:** The problem happens in Windows 10 because of its automatic updates and other apps eating up data, even if you’re connected to a hotspot. To fix this issue, you can set the tethered hotspot as a ‘metered connection’ by following the given steps:  

1.  Connect to the tethered connection (WiFi Hotspot)
  
3.  Open the new **Settings** and then ‘_Network & Internet_’
  
5.  Choose **Wi-Fi** on the left and click ‘_Advanced Options_’
  
7.  Toggle the ‘**Set as metered connection**’ to on state
  

![Windows 10 Overuses Mobile Data](https://beebom.com/wp-content/uploads/2016/05/5-windows-10-overuses-mobile-data.jpg)

6\. WiFi Sense Risks Privacy
----------------------------

  

**Problem:** I don’t find WiFi Sense as useful as advertised and thinks it concerns privacy. I want to disable ‘WiFi Sense’ on my Windows 10 PC and prevent anyone (even my friends and relatives) to automatically connect to WiFi networks.

  
  

  

**Solution:** WiFi Sense encrypts and shares your WiFi networks’ passwords with your specific contact lists so that they can automatically connect to your wireless networks. Though helpful, it risks privacy and to disable WiFi Sense, please follow the steps below:  

1.  Connect to the tethered connection (WiFi Hotspot)
  
3.  Open the new **Settings** and then ‘_Network & Internet_’
  
5.  Choose **Wi-Fi** on the left and click ‘_Manage Wi-Fi settings_’
  
7.  Uncheck the option ‘_Connect to suggested open hotspots_’ and ‘_Connect to networks shared by my contacts_’ to disable WiFi Sense – it’s switched off
  

![WiFi Sense Risks Privacy](https://beebom.com/wp-content/uploads/2016/05/6-wifi-sense-risks-privacy.jpg)

7\. Can’t Open Start Menu in Windows 10
---------------------------------------

  

**Problem:** After upgrading to Windows 10, I can’t open Start menu or Start screen. Everything else is working superfine, but the Start menu or screen simply doesn’t work even if pressing the Windows button on keyboard or Start button on the Windows taskbar.  

**Solution:** This probably happens due to the improper installation of system files. In order to resolve this problem, please follow with the steps given below:  

1.  Open the Run dialog by pressing **Win+R**
  
3.  Type “_sfc /scannow_” and hit Enter
  
5.  A **blank command prompt** will open and close (in a flash, may be)
  
7.  Restart the PC to check if it helped
  

In case it did not work, then follow the following process:  

1.  Search for “**cmd**”, and right-click & choose ‘_Run as administrator_’
  
3.  Type in “_Dism /Online /Cleanup-Image /RestoreHealth_” and press OK
  
5.  Restart the PC after the scan completes – it will work
  

![Can’t Open Start Menu in Windows 10](https://beebom.com/wp-content/uploads/2016/05/7-can%E2%80%99t-open-start-menu-in-windows-10.jpg)

8\. Windows 10 Doesn’t Switch On
--------------------------------

  

**Problem:** When I try to boot (or switch on) my Windows 10 PC, I get a bluescreen error stating ‘Your PC needs to be repaired’. This mostly happens after plugging in any USB stick (like flash drive or Internet dongle) or Android device.  

**Solution:** This problem mostly happens because of an USB stick plugged in your PC because that may change the hard disk’s partition numbers, hence Windows fails to find the required files and the error. Please follow these steps to rectify this issue:  

1.  **Remove the USB drive/stick** from the PC and restart it
  
3.  If required, plug in the USB drive after Windows is loaded (after the lock screen or desktop is shown) – it will work
  

9\. Prevent Automatic Driver Installations
------------------------------------------

  

**Problem:** After upgrading my PC to Windows 10, the OS seems to install several drivers automatically without notifying about the driver packages. I want to disable this feature and prevent Windows from downloading drivers automatically.

  
  

  

**Solution:** To solve this issue, you need to disable this feature by following the steps below:  

1.  Press **Win+E** to open the File Explorer
  
3.  Right-click on ‘_This PC_’ and go to Properties
  
5.  Click on **Advanced System Settings** and select the Hardware tab
  
7.  Click on Device Installation Settings
  
9.  Select ‘_No, let me choose what to do_’
  
11.  Check the option ‘_Never install driver software from Windows Update_’ and press ‘_Save Changes_‘ and then OK
  

![Prevent Automatic Driver Installations](https://beebom.com/wp-content/uploads/2016/05/8-prevent-automatic-driver-installations.jpg)

10\. Windows Search Can’t Find any Applications
-----------------------------------------------

  

**Problem:** After I upgraded to Windows 10, from sometime after some update got installed recently on my PC, the Cortana’s search function fails to find any application in the system – even the Notepad or Calculator.  

**Solution:** This problem basically arises in the Windows 10 update, but the current update (Threshold 2) will supposedly remove it. Till the update rolls out for everyone, you can follow the process below to solve the issue:  

1.  Click **Ctrl+Alt+Del** and choose ‘_Task Manager_’
  
3.  Kill the process ‘_Explorer.exe_’
  
5.  Press **Win+R** to open the Run dialog
  
7.  Type “_regedit_” and press Enter
  
9.  In registry editor, delete the following registry key:
  

HKEY\_LOCAL\_MACHINESOFTWAREMicrosoftWindowsCurrentVersionExplorerFolderTypesef87b4cb-f2ce-4785-8658-4ca6c63e38c6TopViews00000000-0000-0000-0000-000000000000  

6.  In the Task Manager, go to **File -> Run new task**
  
8.  Type in “_explorer.exe_” and press OK
  

If the problem still occurs in Cortana, then please do these:  

1.  Press **Win+X** and choose ‘_Command Prompt (Admin)_’
  
3.  Type “_start powershell_” and hit Enter
  
5.  Run the following command there:
  

Get-AppXPackage -Name Microsoft.Windows.Cortana | Foreach Add-AppxPackage -DisableDevelopmentMode -Register “$($\_.InstallLocation)AppXManifest.xml”  

4.  The problem will be fixed within sometime – try searching now
  

![Windows Search Can’t Find any Applications](https://beebom.com/wp-content/uploads/2016/05/9-windows-search-can%E2%80%99t-find-any-applications.jpg)

### Bonus: [FixWin for Windows 10](http://www.thewindowsclub.com/fixwin-for-windows-10)

  

FixWin is a free portable tool for Windows 10 that **resolves various problems** including the system update issues in mere minutes without manual efforts. It’s a **swiss army knife** for fixing Windows 10 problems without doing any long, boring process. FixWin helps you solve a number of Windows 10 issues like enabling task manager (if not working), resetting start menu or Cortana search and a lot more, so don’t forget to download it.  

**SEE ALSO: [How to Make Windows 10 More Accessible For People With Low Vision](https://beebom.com/how-make-windows-10-more-accessible-people-low-vision/)**  

That’s all about Windows 10 problems and their solutions. If you get stuck or have any other problem, don’t forget to share with us using the comments section below.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/common-problems-windows-10-solutions/)  
\[the\_ad id='1307'\]