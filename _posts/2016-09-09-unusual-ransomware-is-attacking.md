---
title: 'Unusual ''PureLocker'' Ransomware is Attacking Enterprise Servers'
date: 2019-11-13T08:27:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2018/03/Top-10-Best-Malware-Removal-Tools-For-Windows.jpg)

Cyber-security researchers at Intezer Labs and IBM X-Force have discovered an unusual ransomware that’s reportedly being used for targeted attacks against enterprise servers. **Named PureLocker because its written in PureBasic**, the malware has apparently been traced back to a well-known Malware-as-a-Service (MaaS) provider utilized by the Cobalt Gang and FIN6 attack groups.  

According to the [official blog post](https://www.intezer.com/blog-purelocker-ransomware-being-used-in-targeted-attacks-against-servers/) from Intezer Labs malware researcher, Michael Kajiloti, code reuse analysis shows that the malware is closely related to the ‘more\_eggs’ backdoor malware, which is sold on the dark web and has been used by multiple threat actors already. As per the report, the attack is targeted at both Windows and Lixus servers, but the malware has evaded detection for weeks by copying some of the code from the aforementioned backdoor.  

>   
> 
> Together with [@IBMSecurity](https://twitter.com/IBMSecurity?ref_src=twsrc%5Etfw) we have identified a new, undetected [#ransomware](https://twitter.com/hashtag/ransomware?src=hash&ref_src=twsrc%5Etfw) being used in targeted attacks against enterprise production servers. Code reuse analysis points its origins to a MaaS provider utilized by [#CobaltGang](https://twitter.com/hashtag/CobaltGang?src=hash&ref_src=twsrc%5Etfw) & [#FIN6](https://twitter.com/hashtag/FIN6?src=hash&ref_src=twsrc%5Etfw) attack groups. [https://t.co/S9U4X2dlQi](https://t.co/S9U4X2dlQi)  
> 
> — Intezer (@IntezerLabs) [November 12, 2019](https://twitter.com/IntezerLabs/status/1194269691667271686?ref_src=twsrc%5Etfw)

  

As mentioned already, the ransomware is written in the PureBasic programming language, which makes it a rather uncommon phenomenon in the malware domain. However, according to Kajiloti, the unusual choice poses advantages for the attacker, because _“AV vendors have trouble generating reliable detection signatures for PureBasic binaries”_. In addition, PureBasic code is portable between Windows, Linux, and OS-X (macOS), making it easier to target different platforms.  

It’s not immediately clear as to how exactly the malware is being delivered to victims, but systems infected with it are receiving ransom notes that contain an email address to negotiate a fee for decrypting the files. The victims are apparently also being told that they have only seven days to pay the ransom, failing which, the private key will be deleted, rendering the locked files unrecoverable.  

Intezer Labs has published a detailed, technical post about the malware and its MO, and you can access all that info via the link above.  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/purelocker-ransomware-attacking-servers/)  
\[the\_ad id='1307'\]