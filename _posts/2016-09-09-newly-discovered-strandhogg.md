---
title: 'Newly Discovered StrandHogg Vulnerability Puts All Android Users at Risk'
date: 2019-12-03T14:16:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/12/shutterstock_1260320974-e1575367896288.jpg)

A new Android vulnerability has come to light and over 36 malicious apps are said to be exploiting it in the wild. Norwegian in-app security firm Promon has [discovered](https://promon.co/security-news/strandhogg/) this new vulnerability in the Android operating system. And well, it’s a super sneaky one. Dubbed StrandHogg, the vulnerability allows malicious apps to hijack genuine apps and perform malicious operations on their behalf.  

The StrandHogg vulnerability is unique because _“it enables sophisticated attacks without the need for a device to be rooted, uses a weakness in the multitasking system of Android to enact powerful attacks that allows malicious apps to masquerade as any other app on the device,”_ says Promon in its report.  

This vulnerability is “based on an Android control setting called taskAffinity, which allows any app, including the malicious ones, to freely assume any identity in the multitasking system they desire.” This is an OS-level that, sadly, hasn’t been fixed by Google in any version of Android to date and all Android devices are exposed to this security flaw and malicious intent.  

![Permission-Harvesting](https://beebom.com/wp-content/uploads/2019/12/Permission-Harvesting.jpg)

StrangHogg was identified after Promon learned that several banks in the Czech Republic reported money disappearing from customer accounts. A client in the financial sector had provided Promon a data sample to analyze and the security flaw was discovered using the same.  

It then **discovered that a total of 36 apps** were exploiting the flaw to trick users into granting intrusive permissions to malicious apps  – while they thought they were using a legitimate app. Malicious apps were also able to serve fake login pages (phishing attack) inside these apps to further trick people into doling out their personal information.  

Promon hasn’t listed the apps but mentions that none of them are available for download via the Play Store. Instead, the malicious apps were installed on devices as second-stage downloads. Users who had another malicious app on their devices found the StrandHogg-infected apps onboard as well.  

In its report, the security firm further added that there’s no reliable method of detecting StrandHogg exploit being abused on a device. There’s also no way to block the attack at this instant, but you keep a close watch over what permissions an app asks. Also, closing recently opened apps from time-to-time could also help keep you safe, says Promon.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/strandhogg-bug-all-android-users-risk/)  
\[the\_ad id='1307'\]