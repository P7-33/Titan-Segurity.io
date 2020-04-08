---
title: 'Windows Terminal Preview 1910 Released With Updated UI, Dynamic
Profiles and More'
date: 2019-10-24T15:04:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/10/Windows-Terminal-website.jpg)

Microsoft has [released](https://devblogs.microsoft.com/commandline/windows-terminal-preview-1910-release/) a new update to the Preview channel of Windows Terminal, bringing an updated UI, dynamic profiles and new launch settings, alongside a bunch of bug fixes. Users wanting to try out the new-look **Windows Terminal Preview 1910** can do so from the [Microsoft Store](https://www.microsoft.com/en-us/p/windows-terminal-preview/9n0dx20hk701). It will appear as build v0.6 in the ‘About’ popup.  

Updated UI
----------

  

First off, the **WinUI TabView has been updated to version 2.2**, bringing better color contrast, rounded corners on the dropdown and tab separators. Also, when too many tabs fill the screen, you can now scroll through them with buttons, just like browser tabs on Chrome or Firefox.  

![](https://beebom.com/wp-content/uploads/2019/10/Windows-Terminal-Preview-1910-body1.jpg)

Dynamic Profiles
----------------

  

With the latest update, **Windows Terminal will be able to automatically detect any Windows Subsystem for Linux** (WSL) distribution on the machine along with PowerShell Core. Any such installation following the update will make them automatically appear in the profiles.json file. In case you don’t want a profile to appear in the dropdown menu, you can just set `"hidden": true`.  

![](https://beebom.com/wp-content/uploads/2019/10/Windows-Terminal-Preview-1910-body2.jpg)

Cascading Settings
------------------

  

The latest build of the Windows Terminal also ships with a **defaults.json file with all of the default settings**. It can be accessed by holding down the ‘Alt’ key and clicking on the settings button in the dropdown menu. While users won’t be able to make any changes to this file, they’ll still be able to add your own custom settings to the profiles file as usual.  

New Launch Settings
-------------------

  

Users can now also **set the Terminal to launch as maximized or set its initial position**. Setting the Terminal to launch as maximized can be done by adding the global setting `launchMode`, which accepts either `default` or `maximized`.  

```
"launchMode": "maximized"
```  

The Terminal’s initial position can be set by adding `"initialPosition"` as a global setting with the desired pixels as X and Y coordinates, separated by a comma. Multiple monitors may require users to set negative coordinates.  

```
"initialPosition": "0,0"
```  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/windows-terminal-update-ui-profiles/)  
\[the\_ad id='1307'\]