---
title: 'More Regarding LNK Files'
date: 2019-11-02T16:01:00+01:00
draft: false
---

My [recent post regarding LNK files](http://windowsir.blogspot.com/2019/10/return-of-lnk-files.html) got me thinking about other uses of LNK files.  That previous post really illustrated how some analysts are following Jesse Kornblum's adage of "[using every part of the buffalo](http://jessekornblum.com/publications/di07.pdf)", in that they made use of _everything_ (or as close to it as they could) they had available in order to develop a #threatintel picture.  
  
This got me to thinking...taking a step back, how else can [LNK files](https://attack.mitre.org/techniques/T1023/) be used?  
  
_DFIR Analysis_  
Some DFIR analysts are aware of the fact that when analyzing Windows systems, you're going to find Windows shortcut/LNK files in a number of locations.  For example, there're the user's desktop, the user's Recent folder, etc.  In addition, Automatic JumpList files are OLE structured storage format files, and all but one of the streams follow the LNK file format. So, the file format is widely used on Windows systems, and the location of the file or stream provides some useful context that can also be applied to the content.  
  
LNK files contain a good bit of metadata, as they contain shell items (as do other artifacts, such as shellbags), which are blobs of binary data that describe various objects on Windows systems.  In the case of folder objects, specifically, one of the elements found to be embedded within the metadata is the [MFT reference number](https://jmharkness.wordpress.com/2011/01/27/mft-file-reference-number/) for that folder object.  This reference number is comprised of the record number (i.e., location within the MFT), as well as the sequence number (in short, "...this is the _n_th time this record has been used.")  
  
Okay...so what?  
  
Well, when it comes to artifacts of use, or more specifically, file access, the LNK files created as a result of user activity can remain on the system long after the files and applications with which they're associated have been removed or deleted.  Say that you're investigating access to a particular file (by name or folder path) and your goal is to illustrate that the user had knowledge of that file.  If the user accessed the file by double-clicking on it, an LNK file will have been created, and that file will persist well beyond the deletion of the target file itself.  These artifacts will also persist beyond the removal of the associated application, as well.  
  
This can be useful to us because it gives us something of a historical view of the file system. For example, let's say that the per the MFT, record number 2357, with sequence number 5, points to a folder on the user's desktop called "Personal Stuff".  Now, suppose we find a LNK file that points to the fact that the user opened a file that was located in a folder named "Hacker Tools", and the MFT reference number extracted from the LNK file is 2357/4, or 2357/3.  This provides us with a view of what the file system used to look like, giving us something a historical "smear" of the file system.  
  
Also, these LNK files can provide information regarding external devices, as well.  The basic shell items are created in the user's shellbags when they use Windows Explorer to navigate folders on an external device, such as a USB thumb drive, USB-connected smartphone, etc.  Then if they open files, shell items are created to populate LNK files pointing to those files.   
  
_Adversary Persistence_  
Adversaries have been observed persisting beyond password updates by modifying the iconfile name attribute of an LNK file to point to a resource that they (the adversary) control.  What happens if the LNK file is at the root of a directory is that when a user/admin browsers to the folder, Windows parses the file and attempts to load the icon from the remote resource, using the user's credentials to authenticate, first via SMB, and then via WebDAV.  
  
_Other Ways To Use LNK Files_  
"Using" LNK files can apply to the adversary, as well as to an analyst (DFIR, intel, etc.). There's [this write-up on Kovter](https://www.crowdstrike.com/blog/kovter-killer-how-to-remediate-the-apt-of-clickjacking/), describing how the adversary uses/used LNK files, and there's [this BitOfHex blog post](https://bitofhex.com/2019/07/15/deriving-intelligence-from-lnk-files/) describing how to derive intel from LNK files.  There's also [hexacorn's older blog post](http://www.hexacorn.com/blog/2015/03/13/beyond-good-ol-run-key-part-29/) regarding the use of hotkeys and LNK files, and [this USCERT alert](https://www.us-cert.gov/ncas/alerts/TA17-293A) that describes the use of the adversary persistence technique described above (not 'new' or an 'other' use, but placed here as an illustration).