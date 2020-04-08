---
title: 'WhatsApp Bug That Let Hackers Use MP4 Files to Exploit Devices Fixed'
date: 2019-11-18T16:03:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/01/WhatsApp-Blocked-Contact.jpg)

Many users believe WhatsApp is one of the most secure messaging service on the planet, but recent reports seem to suggest otherwise. After reports of WhatsApp [being used to spy](https://beebom.com/whatsapp-confirms-indian-journalists-activists-were-spied-on-by-israeli-hackers/) on users in India, Facebook ([WhatsApp’s parent company](https://beebom.com/facebook-add-its-name-whatsapp-instagram/)) has now disclosed that an exploit allowing remote code execution has been patched. Previously, hackers could exploit this loophole, using an MP4 video file, to execute the attack and gain access to your personal data.  

Facebook has revealed the vulnerability (which is tagged as [CVE-2019-11931](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-11931)) in a recent security advisory report. It **allowed hackers to use specially-crafted MP4 video files** (which look seemingly standard) **to remotely execute malicious code** on your devices without your knowledge. Not a whole lot of details have been doled out here but the issue was caused by how WhatsApp parses MP4 videos inside your conversations.  

Facebook elaborates on the vulnerability saying, _“A stack-based buffer overflow could be triggered in WhatsApp by sending a specially crafted MP4 file to a WhatsApp user. The issue was present in parsing the elementary stream metadata of an MP4 file and could result in a DoS \[denial of service\] or RCE \[remote code execution\].”_  

This vulnerability exists in WhatsApp Android versions prior to 2.19.274 and iOS versions prior to 2.19.100. Windows Phone versions before and including 2.18.368 and WhatsApp Business versions prior to 2.19.104 on Android and prior to 2.19.100 on iOS are affected.  

_“WhatsApp is constantly working to improve the security of our service. We make public reports on potential issues we have fixed consistent with industry best practices. In this instance, there is no reason to believe that users were impacted,”_ confirms a Facebook spokesperson.  

Facebook suggests updating WhatsApp to the newest software build to avoid the risk of hackers exploiting your personal data. There are no reports of the exploit being actively used at the moment. This is the second exploit that WhatsApp has disclosed in the past month. There’s no way we forget the use of [NSO’s Pegasus spyware](https://beebom.com/whatsapp-responds-committed-user-data-protection/) for keeping tabs on Indian journalists and human rights activists via WhatsApp.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/whatsapp-bug-mp4-file-exploit-fixed/)  
\[the\_ad id='1307'\]