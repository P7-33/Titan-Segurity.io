---
title: 'ANU incident report on massive data breach is a must-read'
date: 2019-10-03T02:01:00+01:00
draft: false
---

![anu-campus-web.jpg](https://zdnet4.cbsistatic.com/hub/i/2019/06/04/3e8f4544-211c-4df3-91b9-b629cadb8c75/62f1d8da92edd1e82ba0f63b97fabf1e/anu-campus-web.jpg)

Image: ANU

"This report from ANU is an example to everyone else of how to deal with cyberattacks," [tweeted Vanessa Teague](https://twitter.com/VTeagueAus/status/1179297071943360512), associate professor in cybersecurity at the University of Melbourne, on Wednesday.

"Honest, technical, detailed, and full of good advice for protecting data. Attacks will keep happening. This is the way to understand them and learn to improve our defences."

She's right.

The report in question is a [detailed incident report \[PDF\]](https://imagedepot.anu.edu.au/scapa/Website/SCAPA190209_Public_report_web_2.pdf) of the [massive data breach](https://www.zdnet.com/article/australian-national-university-breached-with-19-years-of-data-accessed/) suffered by Australian National University (ANU) in late 2018, discovered in May 2019, and revealed two weeks later in June.

The hackers had gained access to up to 19 years' worth of data in the university's Enterprise Systems Domain (ESD), which houses its human resources, financial management, student administration, and "enterprise e-forms systems".

ANU's vice-chancellor and president, Professor Brian Schmidt, had committed to making the breach investigation public. This report more than delivers on that promise. It's a must-read.

"The perpetrators of our data breach were extremely sophisticated. This report details the level of sophistication, the likes of which has shocked even the most experienced Australian security experts," Schmidt wrote this week.

The report details how the attackers organised four separate spearphishing campaigns and built their data exfiltration infrastructure on compromised web servers and legacy systems.

![anu-hack-diagram.png](https://www.zdnet.com/article/anu-incident-report-on-massive-data-breach-a-must-read/#ftag=RSSbaffb68)

<span><img src="https://zdnet4.cbsistatic.com/hub/i/2019/10/02/354118fe-1f10-440a-83ad-3b68a82ea60e/c91474d7f6c83c0dfb2bd3021f11fccd/anu-hack-diagram.png" alt="anu-hack-diagram.png" /></span>

Image: ANU

"In addition to their efficiency and precision, the actor evaded detection systems, evolved their techniques during the campaign, used custom malware, and demonstrated an exceptional degree of operational security that left few traces of their activities," the report said.

**The attacker's tradecraft included:**

*   Altering the signatures of more common malware to avoid detection
*   Assembling malware and some tools inside the ANU network after a foothold had been established. Individual components did not trigger endpoint protection
*   Downloading "several types of virtualisation software before selecting one"
*   Downloading disk images for Windows XP and Kali Linux, although "there is little evidence to suggest much use of Kali Linux"
*   Compiling bespoke malware within the ANU network to gain access to ESD. "The purpose of this code remains unknown, and no forensic traces of it or the executable file which was compiled from the code have been found at the time of this report," the report said

"The actor's use of a third-party tool to extract data directly from the underlying databases of our administrative systems effectively bypassed application-level logging. Safeguards against this happening again have been implemented," the report said.

The attackers even tried to maximise the effectiveness of their spearphishing efforts by attempting to disable the university's email spam filters, although "there is no forensic evidence to suggest that they were successful in this attempt".

ANU's analysis shows that the attackers exfiltrated much less data than the 19 years' worth that was originally feared, but does not show exactly what was taken.

"Despite our considerable forensic work, we have not been able to determine, accurately, which records were taken ... We also knew the stolen data has not been further misused," Schmidt wrote.

"Frustratingly this brings us no closer to the motivations of the actor."

Even though the attacker had gained broader access, ANU said it's clear from the pathway taken that their sole aim was to penetrate ESD.

"There is no forensic evidence to suggest the actor accessed or displayed any interest in files containing general administrative documents or research data; nor was the ANU Enterprise Records Management System (ERMS) affected," the report said.

"It is worth noting that ANU was subject to further intrusion attempts within one hour of the public announcement and on the following day, both of which were stopped."

ANU has declined to attribute the attack to any particular adversary.

For years now, chief information security officers (CISOs) and others have been telling organisations to share cybersecurity information to improve their defences. But few do, except perhaps as secret squirrels within their own closed industry groups.

In the past, I've been [highly sceptical](https://www.zdnet.com/article/cyber-cooperation-leads-to-cybersecurity-so-why-wont-australia-cyber-do-it/) about whether all this cyber collaboration talk would ever become cyber action. ANU has now set the example. Who will follow?

### Related Coverage

**[ANU to design artificial intelligence framework with Australian values](https://www.zdnet.com/article/anu-to-design-artificial-intelligence-framework-with-australian-values/)**

The researchers involved hope the design framework can be widely deployed.

**[ANU claims Australians want government to use data for better-targeted benefits](https://www.zdnet.com/article/anu-claims-australians-want-government-to-use-data-for-better-targeted-benefits/)**

Respondents to its survey said they wanted the data to be used to make sure the right people were receiving the right benefits, the Australian National University has reported.

**[ANU applies space tech to predict future droughts and bushfires](https://www.zdnet.com/article/anu-applies-space-tech-to-predict-future-droughts-and-bushfires/)**

The university used space technology to predict droughts and increased bushfire risk up to five months in advance.

**[Cyberwar's strategic value 'unclear': Hugh White](https://www.zdnet.com/article/cyberwars-strategic-value-unclear-hugh-white/)**

Cybers are a cheap and effective deterrent, says one of Australia's leading strategic analysts. But wars will still be fought in the "boring old real world", so let's reconsider nukes.

**[ANU successfully measures light for quantum internet data transfer](https://www.zdnet.com/article/anu-successfully-measures-light-for-quantum-internet-data-transfer/)**

The quantum internet will require fast-moving data and the Australian National University believes it has found a way to measure information stored in light particles which will pave the way for a safe "data superhighway".

**[How to quickly deploy a honeypot with Kali Linux](https://www.techrepublic.com/article/how-to-quickly-deploy-a-honeypot-with-kali-linux/)** (TechRepublic)

Lure possible attackers into a trap with a Kali Linux honeypot.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2n9n98Y