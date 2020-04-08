---
title: 'How to Fix Error 0x80246019 on Windows 10'
date: 2019-10-15T06:38:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

Microsoft unveiled its in-house app marketplace Microsoft Store with the release of Windows 10. However, it has been facing many issues ranging from failed downloads to incomprehensible error messages being thrown while updating apps. Recently, users complained that they are unable to download apps and games from Microsoft Store. It downloads apps but then throws error 0x80246019 while installing them. So, in this article, I will show you how you can fix error 0x80246019 on Windows 10 with just two simple steps.  

Resolve Error 0x80246019 on Windows 10
--------------------------------------

  

We will use the Powershell command shell to restore many Windows settings including Microsoft Store and other apps. Rest assured, the process **will not erase any of your personal data**. Now without any delay, let’s go through the steps.  

1\. First of all, search for “Powershell” from Windows Start Menu. Now, right-click on “Windows Powershell” and **click on “Run as administrator”.**  

![Resolve Error 0x80246019 on Windows 10](https://beebom.com/wp-content/uploads/2019/10/Resolve-Error-0x80246019-on-Windows-10.jpg)

2\. After that, execute the following command on the Powershell window. It will ask for further permission, **type “y” and hit enter**. The permission will allow us to make changes to the execution policy without any restrictions.  

```
Set-ExecutionPolicy Unrestricted
```  

![Resolve Error 0x80246019 on Windows 10 2](https://beebom.com/wp-content/uploads/2019/10/Resolve-Error-0x80246019-on-Windows-10-2.jpg)

3\. Having done that, **perform the following command** on Powershell again. It will start restoring all the apps to their default settings and disable any third-party intervention.  

```
Get-AppXPackage -AllUsers | Foreach Add-AppxPackage -DisableDevelopmentMode -Register "$($\_.InstallLocation)AppXManifest.xml"
```  

![Resolve Error 0x80246019 on Windows 10 3](https://beebom.com/wp-content/uploads/2019/10/Resolve-Error-0x80246019-on-Windows-10-3.jpg)

4\. After the process is over, **restart your PC** and you should have error 0x80246019 resolved by now. Go ahead and download apps and games from the Microsoft Store without any issues.  

**SEE ALSO: [How to Speed up Windows 10 in 2019 \[Effective Methods\]](https://beebom.com/speed-up-windows-10-2/)**  

Fix Microsoft Store with Two Simple Steps
-----------------------------------------

  

So that was our quick guide on how to fix error 0x80246019 on Windows 10. Many users have been complaining about this issue for far too long, but it was compounded recently when they were unable to install games on Windows 10 PC. Anyway, you can just go ahead and restore the default settings with these two commands and everything will fall in place. So that is all from us. If you are still facing issues then comment down below and let us know. We will definitely try to help you out.  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/fix-error-0x80246019-windows-10/)  
\[the\_ad id='1307'\]