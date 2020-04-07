---
title: 'How to Disable Windows Defender Antivirus on Windows 10'
date: 2020-02-12T07:34:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

Contrary to the popular misconception, Microsoft has been shipping a barebone anti-spyware since the Windows XP days. However, after the release of [Windows 7, 8](https://beebom.com/windows-8-vs-windows-7/) and 10, Microsoft brought a full-fledged antivirus, Windows Defender (now called Windows Security) with support for anti-malware execution, real-time detection, and timely definition update. Having said that, some users don’t find the native antivirus effective and some find it too demanding on the computer resources. Recently, we wrote about how Windows Defender [spikes the CPU usage abnormally through the msmpeng.exe process](https://beebom.com/how-disable-msmpeng-exe-reduce-high-cpu-usage/). So, if you are also facing such issues or just want to install an antivirus of your choice then follow our guide and learn how to disable Windows Defender Antivirus on Windows 10.  

Disable Windows Defender Antivirus on Windows 10 Using Registry
---------------------------------------------------------------

  

Here, we will use the Windows Registry tool to disable Windows Defender Antivirus. For this method, **make sure you are using the Administrator account** before proceeding ahead. Now, let’s begin.  

1\. First off, open Windows Defender or Windows Security and go to “Virus and threat protection”. Here, **click on “Manage Settings”**.  

![Disable Windows Defender Antivirus on Windows 10 Using Registry](https://beebom.com/wp-content/uploads/2020/02/4-disable-msmpeng.exe-amd-reduce-high-cpu-usage-1.jpg)

2\. After that, **disable all the toggles** under “Virus and threat protection settings”.  

![Disable Windows Defender Antivirus on Windows 10 Using Registry](https://beebom.com/wp-content/uploads/2020/02/3-disable-msmpeng.exe-amd-reduce-high-cpu-usage-1.jpg)

3\. Now, **search for “registry”** in the [Windows Search](https://beebom.com/search-tips-tricks-windows-10/) box. After that, click on “Run as administrator” in the right pane.  

![Disable Windows Defender Antivirus on Windows 10 Using Registry](https://beebom.com/wp-content/uploads/2020/02/5-disable-msmpeng.exe-amd-reduce-high-cpu-usage-1.jpg)

4\. **Copy the below address and paste it** in the Registry address bar and hit enter. You will be instantly taken to the Windows Defender folder.

  
  

  
```
HKEY\_LOCAL\_MACHINESOFTWAREPoliciesMicrosoftWindows Defender
```  

![Disable Windows Defender Antivirus on Windows 10 Using Registry](https://beebom.com/wp-content/uploads/2020/02/9-disable-msmpeng.exe-amd-reduce-high-cpu-usage-1.jpg)

7\. Right-click on “Windows Defender” and select New -> DWORD (32-bit) value. **Name the file “DisableAntiSpyware”** and click on the “Ok” button.  

![Disable Windows Defender Antivirus on Windows 10 Using Registry](https://beebom.com/wp-content/uploads/2020/02/6-disable-msmpeng.exe-amd-reduce-high-cpu-usage-1.jpg)

8\. Now double-click on the file and **change the value to 1**. After that, click on the “Ok” button and restart your computer.  

![Disable Windows Defender Antivirus on Windows 10 Using Registry](https://beebom.com/wp-content/uploads/2020/02/10-disable-msmpeng.exe-amd-reduce-high-cpu-usage-1.jpg)

9\. Finally, open Windows Defender or Windows Security and you will find the antivirus completely disabled. Now you can go ahead and install a [third-party antivirus on your Windows 10 PC](https://beebom.com/best-antivirus-for-windows-10/).  

_**Note:** If it does not work in the first try then try for the second time and it will surely work._  

![windows defender](https://beebom.com/wp-content/uploads/2020/02/Annotation-2020-02-11-125112.jpg)

10\. In case you want to **enable Windows Defender again**, simply delete the “DisableAntiSpyware” file from Registry and restart your computer. The native Windows antivirus will start working again.

  
  

  

Disable Windows Defender Antivirus on Windows 10 Using Group Policy
-------------------------------------------------------------------

  

If the Registry hack is not working for you then you can take advantage of Group Policy Editor to disable Windows Defender permanently. However, keep in mind, Group Policy Editor is **only available on the Administrator account and PCs running the [Windows 10 Pro version](https://beebom.com/windows-10-home-vs-pro-guide/)**. So with all that said, let’s begin.  

1\. Press the “Windows” and “R” keys at once to open the Run dialog box. Now, **type “gpedit.msc” in the search box** and hit enter to open the Group Policy Editor.  

![gpedit](https://beebom.com/wp-content/uploads/2020/02/Annotation-2020-02-11-124032.jpg)

2\. Here, **expand the “Administrative Templates”** menu under the “Computer Configuration” section.  

![group policy](https://beebom.com/wp-content/uploads/2020/02/Screenshot-2020-02-11-at-12.09.10.jpeg)

3\. Next, expand the “Windows Components” menu and **scroll down to “Windows Defender Antivirus”**.  

![group policy](https://beebom.com/wp-content/uploads/2020/02/Screenshot-2020-02-11-at-12.09.36.jpeg)

4\. Here, double-click on “Turn off Windows Defender Antivirus” and **select “Enabled”** in the top-left corner. Subsequently, click on the “Apply” and “OK” button.  

![group policy](https://beebom.com/wp-content/uploads/2020/02/Screenshot-2020-02-11-at-12.09.57.jpeg)

  
  

  

5\. Finally, **restart your computer** and this time, you will find Windows Defender is disabled on your Windows 10 PC.  

![windows defender](https://beebom.com/wp-content/uploads/2020/02/Annotation-2020-02-11-125112.jpg)

6\. If you wish to **enable it again** then just open the Group Policy Editor again and select “Not Configured”. That’s it.  

Remove Windows Defender Antivirus from Windows 10
-------------------------------------------------

  

So those are the two ways you can remove Windows Defender Antivirus from your Windows 10 PC. While the Registry hack works most of the time, Microsoft sometimes reverses the change after an update. So if you are facing such an issue, go with the more powerful Group Policy Editor which controls the behavior of all system applications on Windows 10 Pro. Apart from that, the older way to disable Windows Defender using Windows Services no longer works so I have not mentioned that method. Anyway, that is all from us. If you found the article helpful, do let us know in the comment section below.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/disable-windows-defender-antivirus/)  
\[the\_ad id='1307'\]