---
title: 'Micro-Cap User Downloads – Now Free'
date: 2020-01-10T02:17:00+01:00
draft: false
---

  
  
from Hacker News https://ift.tt/2GndzFM

![](http://www.spectrum-soft.com/headers/usersection.gif)
---------------------------------------------------------

Micro-Cap 10, 11, and 12 are now free and require no key. You can download the full CD or the executable only.  
  

Full CD: Use this option if you are new to Micro-Cap or want a fresh install.
-----------------------------------------------------------------------------

  
Download the CD and unzip it into a separate folder. Execute the setup.exe program to install the entire program including libraries, sample circuits, and manuals. Make sure you install to a non-write-protected folder. Note that Windows Program Files is a write-protected folder, so install somewhere else.  
  

Executable only: Use this option if you want to retain your old library edits.
------------------------------------------------------------------------------

  
Download the ZIP file and copy all its files into your current Micro-Cap folder, replacing the old .EXE and .DLL files. This option is also available from within Micro-Cap at Help menu / Check for Updates. Older versions of Micro-Cap (MC5 through MC9) downloads are available but still require a key.  
  

![Japanese](http://www.spectrum-soft.com/download/FlagOfJapan.gif)Japanese Version  
The Micro-Cap manuals and Brochures require the [Acrobat Reader](http://www.adobe.com/prodindex/acrobat/readstep.html) in order to read them.

  
  

HASP Security Key Driver for Micro-Cap 8 and Micro-Cap 9
--------------------------------------------------------

Newer Driver:  
[Sentinel\_LDK\_Run-time\_cmd\_line.zip](https://supportportal.gemalto.com/csm?id=kb_article_view&sysparm_article=KB0018319)

The Haspdinst.exe file present in the ZIP file needs to  
be run with the command switch '-i'. Click on the Start menu in Windows and select the Run option  
in the menu. In the Run dialog box, enter the full path (either manually or through the Browse option)  
for the Haspdinst.exe file. At the end of the  
string, hit the spacebar, and then type in -i. For example, if the files  
in the ZIP file were extracted to the path C:\\HASP, the Run dialog box should contain a string such as:  
  
C:\\HASP\\Haspdinst.exe   -i  
  
If Windows has placed double quotes around the path and file name, the -i must be placed outside of the quotes.  
  
This installs the latest security key driver which must be present to run  
the update.  
  
If this does not work, remove the old driver and then reinstall the new one as follows:  
  
%path%\\Haspdinst.exe   -r  
  
This removes the old driver. Then to install the new driver, type:  
  
%path%\\Haspdinst.exe   -i  
  
where %path% is the location that the files were extracted to. A message should appear that states the driver has been successfully installed.