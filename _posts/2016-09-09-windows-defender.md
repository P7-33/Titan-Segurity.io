---
title: 'Windows Defender'
date: 2019-11-05T04:12:00+01:00
draft: false
---

Windows Defender  
Windows Server 2016 includes Windows Defender, the Microsoft anti-malware solution. Windows Defender is enabled by default when you deploy Windows Server 2016. To disable Windows Defender, you must remove it, either by using the Add Roles And Features Wizard, or by using the following Uninstall-WindowsFeature command:  
  
  
Uninstall-WindowsFeature -Name Windows-Server-Antimalware  
  
You can use the following PowerShell cmdlets to manage Windows Defender on computers running the GUI, or the Server Core version of Windows Server 2016:  
  
• Add-MpPreference. Modifies Windows Defender settings.  
  
• Get-MpComputerStatus. View the status of antimalware software on the server.  
  
• Get-MpPreference. View the Windows Defender preferences for scans and updates.  
  
• Get-MpThreat. View the history of malware detected on the computer.  
  
• Get-MpThreatCatalog. Get known threats from the definitions catalog. You can use this list to determine if a specific threat is known to Windows Defender.  
  
• Get-MpThreatDetection. Lists active and past threats that Windows Defender has detected on the computer.  
  
• Remove-MpPreference. Removes an exclusion or default action.  
  
• Remove-MPThreat. Removes an active threat from the computer.  
  
• Set-MpPreference. Allows you to configure scan and update preferences.  
  
• Start-MpScan. Starts an anti-malware scan on a server.  
  
• Start-MpWDOScan. Triggers a Windows Defender offline scan.  
  
• Update-MpSignature. Triggers an update for antimalware definitions.