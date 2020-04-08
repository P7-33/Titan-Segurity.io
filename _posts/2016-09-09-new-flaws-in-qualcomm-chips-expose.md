---
title: 'New Flaws in Qualcomm Chips Expose Millions of Android Devices to Hacking'
date: 2019-11-30T18:15:00+01:00
draft: false
---

  

  
[![android qualcomm vulnerability](https://1.bp.blogspot.com/-cp9sA5Bl4VM/XUk2FINo0XI/AAAAAAAA0oo/Sq6eeRL5L64kchRmq7kYaoVe0C8iLPFSQCLcBGAs/s728-e100/android-qualcomm-vulnerability.png "android qualcomm vulnerability")](https://1.bp.blogspot.com/-cp9sA5Bl4VM/XUk2FINo0XI/AAAAAAAA0oo/Sq6eeRL5L64kchRmq7kYaoVe0C8iLPFSQCLcBGAs/s728-e100/android-qualcomm-vulnerability.png)

  
A serial of vital vulnerabilities have got been found inward Qualcomm chipsets that might contribute hackers to {compromise} Humanoid gadgets remotely simply past sending malevolent packets over-the-air with nobelium exploiter interplay.  
  
  
  
Found past safety researchers from Tencent's Vane squad, issues vulnerabilities, collectively recognized arsenic **QualPwn**, reside inward issues WLAN and modem microcode of Qualcomm chipsets that powers tons of of tens of millions of Humanoid smartphones and tablets.  
  
  
  
In accordance with researchers, marche ar chiefly 2 vital vulnerabilities inward Qualcomm chipsets and leak inward issues Qualcomm's Linux kernel driver for Humanoid which if enchained collectively might contribute attackers to take finish command through focused Humanoid gadgets inside their Wisconsin-Fi reach.  
  

  
  
  
  

>   
> "Leak of issues vulnerabilities permits attackers to {compromise} issues WLAN and Modem over-the-air. Issues different permits attackers to {compromise} issues Humanoid Kernel from issues WLAN chip. Issues total stroke chain permits attackers to {compromise} issues Humanoid Kernel over-the-air inward some circumstances," researchers mentioned inward a [blog post](https://blade.tencent.com/en/advisories/qualpwn/).

  
  
  
Issues vulnerabilities inward challenge ar:  
  
  
  

  
*   **CVE-2019-10539** (Flexible WLAN) — Issues first defect is a buffer overflow number that resides inward issues Qualcomm WLAN microcode owed to deficiency of duration bank check once parsing issues prolonged cap IE header duration.
  

  
  
  

  
*   **CVE-2019-10540** (WLAN into Modem number) — Issues sec number is too a buffer-overflow defect that too resides inward issues Qualcomm WLAN microcode and impacts its neighborhood expanse meshing (NAN) part owed to deficiency of bank check of depend letters secondhand inward NAN availability attribute.
  

  
  
  

  
*   **CVE-2019-10538** (Modem into Linux Kernel number) — Issues 3rd number lies inward Qualcomm's Linux kernel driver for Humanoid that tin live victimized past subsequently sending malevolent inputs from issues Wisconsin-Fi chipset to overwrite components of Linux kernel run issues twist's briny Humanoid working scheme.
  

  
  
  
One time compromised, issues kernel offers attackers total scheme entry, together with issues power to instal rootkits, extract tender info, and do different malevolent actions, all spell evading detection.  
  

[![Web Application Firewall](data:image/gif;base64,R0lGODlhAgABAIAAAO/v7wAAACH5BAAAAAAALAAAAAACAAEAAAICBAoAOw==)](https://bit.ly/2nAQ7y5 "Web Application Firewall")

  
  
Although Tencent researchers tried their QualPwn assaults for Google Pel two and Pel three gadgets that ar run along Qualcomm Snapdragon 835 and Snapdragon 845 chips, issues vulnerabilities influence many different chipsets, in response to an [advisory](https://www.qualcomm.com/company/product-security/bulletins) promulgated past Qualcomm.  
  
  
  

>   
> "IPQ8074, MDM9206, MDM9607, MDM9640, MDM9650, MSM8996AU, QCA6174A, QCA6574, QCA6574AU, QCA6584, QCA8081, QCA9379, QCS404, QCS405, QCS605, Qualcomm 215, SD 210/SD 212/SD 205, SD 425, SD 427, SD 430, SD 435, SD 439 / SD 429, SD 450, SD 625, SD 632, SD 636, SD 665, SD 675, SD 712 / SD 710 / SD 670, SD 730, SD 820, SD 820A, SD 835, SD 845 / SD 850, SD 855, SD 8CX, SDA660, SDM439, SDM630, SDM660, SDX20, SDX24, SXR1130"

  
  
  
Researchers found issues QualPwn vulnerabilities inward Feb and March this solar year and responsibly reported them to Qualcomm, who so discharged patches inward June and notified OEMs, together with Google and Samsung.  
  
  
  
Google simply yesterday discharged safety patches for these vulnerabilities arsenic section of its [Android Security Bulletin](https://source.android.com/security/bulletin/2019-08-01) for August 2019. Then, you ar suggested to obtain issues safety patches arsenic presently arsenic they ar uncommitted  
  
  
  
Since Humanoid telephones ar infamously sluggish to acquire patch updates, researchers have got distinct non to reveal finish technological particulars surgery whatever PoC stroke for these vulnerabilities anytime presently, giving end-users plenty meter to have updates from their twist producers.

  
  
  

Have got one thing to say around this story? Remark beneath surgery part it with usa along [Facebook](https://www.facebook.com/thehackernews), [Twitter](https://twitter.com/thehackersnews) surgery our [LinkedIn Group](https://www.linkedin.com/company/the-hacker-news/).