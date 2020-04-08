---
title: 'Admodule - Microsoft Signed Activedirectory Powershell Module'
date: 2019-09-25T07:46:00+01:00
draft: false
---

Microsoft signed [DLL](http://www.kitploit.com/search/label/DLL) for the ActiveDirectory [PowerShell](http://www.kitploit.com/search/label/PowerShell) module  
Just a backup for the Microsoft's ActiveDirectory PowerShell module from Server 2016 amongst RSAT as well as module installed. The DLL is commonly institute at this path: C:\\Windows\\Microsoft.NET\\assembly\\GAC\_64\\Microsoft.ActiveDirectory.Management  
as well as the residuum of the module files at this path: C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\Modules\\ActiveDirectory\\  
  
**Usage**  
You tin re-create this DLL to your auto as well as purpose it to enumerate [Active Directory](http://www.kitploit.com/search/label/Active%20Directory) without installing RSAT as well as without having administrative privileges.  
PS C:> Import-Module C:\\ADModule\\Microsoft.ActiveDirectory.Management.dll -Verbose[](https://github.com/samratashok/ADModule/blob/master/img/AD_Module.png?raw=true)  
  

[![](https://1.bp.blogspot.com/-jg1574yZ4ug/W9xsA8pYM1I/AAAAAAAANF4/X6VQrjkcP7cVQklqyL-m-0F6g1xYCSa3QCLcBGAs/s640/ADModule_1_AD_Module.png)](https://1.bp.blogspot.com/-jg1574yZ4ug/W9xsA8pYM1I/AAAAAAAANF4/X6VQrjkcP7cVQklqyL-m-0F6g1xYCSa3QCLcBGAs/s1600/ADModule_1_AD_Module.png)

  
To endure able to listing all the cmdlets inward the module, import the module every bit well. Remember to import the DLL first.  
PS C:> Import-Module C:\\ADModule\\Microsoft.ActiveDirectory.Management.dll -Verbose  
PS C:> Import-Module C:\\AD\\Tools\\ADModule\\ActiveDirectory\\ActiveDirectory.psd1  
PS C:> Get-Command -Module ActiveDirectory  
  
**Benefits**  
There are many benefits similar rattling depression chances of detection yesteryear AV, rattling broad coverage yesteryear cmdlets (I larn out the usage of cmdlets for a afterwards ship service :P), skillful filters for cmdlets, signed yesteryear Microsoft etc. The almost useful one, however, is that this module plant flawlessly from PowerShell's Constrained Language Mode[](https://github.com/samratashok/ADModule/blob/master/img/AD_Module_CLM.png?raw=true)  
  

[![](https://3.bp.blogspot.com/-2bkVDNQY_EA/W9xsFfN13XI/AAAAAAAANF8/Ow38xkPCDvAl8is4jkuRF_3P6eChLpkmACLcBGAs/s640/ADModule_2_AD_Module_CLM.png)](https://3.bp.blogspot.com/-2bkVDNQY_EA/W9xsFfN13XI/AAAAAAAANF8/Ow38xkPCDvAl8is4jkuRF_3P6eChLpkmACLcBGAs/s1600/ADModule_2_AD_Module_CLM.png)

  
**Blog**  
[/search?q=domain-enumeration-from-PowerShell-CLM]( /search?q=domain-enumeration-from-PowerShell-CLM)  
  
  

**[Download ADModule](https://github.com/samratashok/ADModule)**