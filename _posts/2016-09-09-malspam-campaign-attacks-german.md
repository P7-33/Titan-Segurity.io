---
title: 'Malspam Campaign attacks German organizations with Buran ransomware'
date: 2019-10-25T13:33:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-ZuTITFJwZ3U/XbLiyDjfV5I/AAAAAAAAAUU/r2nFAcAeGHExXlaT-l8idNqfrFx0r4LsACLcBGAsYHQ/s640/spam.jpg)](https://1.bp.blogspot.com/-ZuTITFJwZ3U/XbLiyDjfV5I/AAAAAAAAAUU/r2nFAcAeGHExXlaT-l8idNqfrFx0r4LsACLcBGAsYHQ/s1600/spam.jpg)

  
As of Oct 2019 researchers have discovered malicious spam (malspam) campaign targeting German organizations that delivered Buran crypto-ransomware family. The emails are crafted so as to appear to be coming from online fax service eFax.  
  
Public reporting indicates that Buran malspam campaigns began on 13 September 2019, corroborated by metadata found in emails and Microsoft Word documents. Then the campaign on 1 October 2019 copied the eFax brand, an online fax service. German organizations were targeted using an email that seemed like it was from eFax and Word document in German.  
  
 **Technical Details **  
  
On opening the mail, the user is given a hyperlink, which if clicked directs the user to a PHP page that contains the malicious word document. The document then contains a Visual Basic for Applications (VBA) macro, when enabled, downloads the malicious executable.  
  
On Activation, the Buran ransomware performs the following tasks- (Sc.Itssecure.com)  
  
•Sends an HTTP GET request to hxxp://geoiptool\[.\]com, in order to determine the location of the victim machine.  
•Copies itself to another directory & renames itself to “Isass.exe”, in order to evade being detected by security solutions in place.  
•It then utilizes a command shell to establish persistence.  
•Further, it modifies the windows registry’s run key, so that “Isass.exe” is executed every time someone logs into the machine.  
•It then disables services like windows event log and windows error recovery & automatic repair.  
•Finally, it deletes any backups made by Volume shadow copy service (VSS).  
•Upon completion of the encryption process, a ransom note is displayed, containing the instructions that need to be followed by the victim, in order to decrypt his files.  
  
These type of malicious spam ransomware campaigns leads to lag in business-critical operations, loss of sensitive and confidential data and financial loss to the organization. Such ransomware keeps surfacing often and can lead to degeneration of an organization and hence organizations should take active measures and protect themselves from such malevolent attacks. The organizations should create strong cybersecurity with updated systems and software and invest in employee training programs, to aware them about malspams, phishing, and other threats.

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/2NaptFD