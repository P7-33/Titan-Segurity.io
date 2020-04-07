---
title: '7 Ways to Fix Windows File Explorer Search'
date: 2020-01-20T15:07:00+01:00
draft: false
---

![windows-explorer-search](https://static.makeuseof.com/wp-content/uploads/2020/01/windows-explorer-search.jpg)

Windows 10 File Explorer search is a handy option to find files. If you have a folder full of documents, you can enter a keyword. Or, if you don’t know the name of the file but you do know the file extension, you can search that way with a wildcard.

**Unlock the FREE "Ultimate Windows Keyboard Shortcuts" cheat sheet now!**

This will sign you up to our newsletter

Enter your Email

Unlock

[Read our privacy policy](//www.makeuseof.com/legal/)

Unless, of course, File Explorer search is not working. File Explorer search can break for several reasons. Thankfully, most of these errors are easy to resolve.

Here are seven ways you can fix File Explorer search.

1\. Make Sure Windows Search Service Is Running
-----------------------------------------------

The first thing to do is to make sure the Windows Search service is up and running. Windows Services control a lot of what Windows can do. If a service switches off or bugs out, it can have unexpected consequences. Accordingly, if the Windows Search service is off or broken, you cannot search for your file using the File Explorer search.

Press **Windows Key + R** to open the Run dialog, then input **services.msc**.

Scroll down the list of services until you find **Windows Search**, then check its status.

If Windows Search is running, this is not the cause of the issue. If it’s not running, double-click Windows Search to open the options, then **Start** the service. Hit **Apply** and close the options.

If you want to restart the Windows Search service in the hope that it jolts it to life, select **Stop**, then **Apply**, then **Start**, then **Apply**.

2\. Rebuild the Search Index
----------------------------

If stopping and starting the Windows Search service doesn’t coax File Explorer search back into life, you can rebuild the search index. The search index is a long list of every file on your computer. If Windows doesn’t have an index of where files are, it cannot search your computer to tell you where to look for them (or guide you right to them!).

Rebuilding the search index can take a little while. However, it is one of the best ways to resolve a Windows File Explorer search issue.

Press **Windows Key + R** to open the Run dialog, then input the following:

```
rundll32.exe shell32.dll,Control\_RunDLL srchadmin.dll
```

The Windows Indexing Options panel will appear. Select **Advanced**, then under **Troubleshooting**, select **Rebuild.**

Select **OK** when Windows tells you the rebuild will take “a long time,” then wait for the process to complete. You can use your computer during this time, but the File Explorer search won’t work until the re-indexing is complete.

3\. Make Sure the Search Index Includes Your Drive Locations
------------------------------------------------------------

If rebuilding the search index doesn’t fix your File Explorer and Windows search issues, make sure the folders you’re searching are included in the index.

Reopen the Windows Indexing Options panel (as shown in the previous section). Select **Modify**. Now, check your Indexed Locations.

At the very least, you want to index your C:/ drive. For most people, C:/ contains your operating system, Windows user profile, photos, videos, music, and documents. If you do not include those folders in the index, File Explorer search will miss many of your files.

After selecting your drive locations, press **OK**. Windows will index the new locations automatically. Depending on the size of the drives you add, indexing could take some time.

4\. Run the Windows Index Troubleshooter
----------------------------------------

The Windows Index Options panel is home to a troubleshooter, too. Head back to the Windows Index Options panel.

Under **Troubleshooting**, select **Troubleshoot search and indexing**. You then have four options:

Select your search indexing issue, then continue. The Search and Indexing Troubleshooter will apply fixes automatically, then tell you about any changes.

The fourth option is a little different. You can attempt to describe your File Explorer search issues, and Windows 10 will keyword match the errors and attempt to provide a fix. It is hit and miss, as you might imagine.

5\. Switch Cortana Off
----------------------

Switching Cortana off can sometimes jolt File Explorer back into life, such is the integration of the tool with Windows search options. Cortana was [the specific cause of a broken Windows Search issue](//www.makeuseof.com/tag/windows-10-broken-search/), too.

Right-click your taskbar and select **Task Manager**. Open the **Processes** tab, then scroll down to **Cortana.** Right-click the Cortana process and select **End task**.

Cortana will shut down, then reopen.

6\. Run CHKDSK
--------------

If at this point File Explorer search still isn’t working, you need to consider some more serious fixes. The Windows Check Disk (CHKDSK) is a Windows system tool you can use to verify the file system. You can set CHKDSK to fix any issues it runs into as it runs.

Type **command prompt** in your Start menu search bar, then right-click the best match and select **Run as administrator**. (Alternatively, press **Windows key + X**, then select **Command Prompt (Admin)** from the menu.)

Next, type **chkdsk /r** and press Enter. The command will scan your system for errors and fix any issues along the way.

7\. Run SFC
-----------

The System File Check (SFC) is another Windows file check tool. Instead of checking your entire drive for errors, like CHKDSK, the System File Check analyzes and fixes your Windows installation specifically.

Before running the SFC command, it is best to double-check that it is completely functional.

**DISM** stands for Deployment Image Servicing and Management. DISM is an integrated Windows utility with a vast range of functions. In this case, [**the DISM Restorehealth command ensures that our next fix will work properly**](//www.makeuseof.com/tag/fix-corrupted-windows-10-installation/). Work through the following steps.

1.  Type **Command Prompt (Admin)** in the Start menu search bar, then right-click and select **Run as administrator** to open an elevated Command Prompt.
2.  Type the following command and press Enter: **DISM /online /cleanup-image /restorehealth**
3.  Wait for the command to complete. The process can take up to 20 minutes, depending on your system’s health. The process seems stuck at certain times, but wait for it to complete.
4.  When the process completes, type **sfc /scannow** and press Enter.

Fixing File Explorer and Windows Search
---------------------------------------

When File Explorer search isn’t working, finding a specific file is time-consuming. Fixing File Explorer search doesn’t take long and will help you keep tabs on your most important (or completely lost!) files.

Windows isn’t the only place where the loss of a search function is irritating and time-consuming. Here’s [how you fix Outlook search](//www.makeuseof.com/tag/outlook-search-not-working/) when it is not working. Or, if your issues don’t involve search, here are some of the [best free Windows 10 repair tools](//www.makeuseof.com/tag/5-free-tools-fix-problem-windows-10/) to fix any problem.

Read the full article: [7 Ways to Fix Windows File Explorer Search](https://www.makeuseof.com/tag/fix-windows-file-explorer-search/)

  
  
from MakeUseOf https://ift.tt/2G9GOeB  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)