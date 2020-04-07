---
title: 'TrickBot Added New Stealthy Backdoor for High-Value Targets'
date: 2020-01-13T12:17:00+01:00
draft: false
---

  

[![](https://1.bp.blogspot.com/-3i91BFtNvpQ/XhxLFO9z_GI/AAAAAAAAB5k/-FQKDa5ZFRI_1i2kGWSBtVlC8Z0AzFhSQCLcBGAsYHQ/s640/malicious-code-4036349_1280.webp)](https://1.bp.blogspot.com/-3i91BFtNvpQ/XhxLFO9z_GI/AAAAAAAAB5k/-FQKDa5ZFRI_1i2kGWSBtVlC8Z0AzFhSQCLcBGAsYHQ/s1600/malicious-code-4036349_1280.webp)

  
The authors behind the infamous TrickBot malware – a modular banking trojan that targets sensitive financial information and also acts as a dropper for other malware–have developed a stealthy custom backdoor, circulating by the name 'PowerTrick', to monitor high-value targets and infiltrate them accordingly.  
  
Statistics demonstrate that TrickBot is one of the top crimeware codes and cyberattack groups in existence currently. Developers behind TrickBot have made frequent upgradations in order to evade detection even fluently, empower its stealth, make it hard to research and let it bypass security configurations on user devices.  
  
PowerTrick has been primarily created as an attempt to keep up with the fast paced era of constantly evolving defense mechanisms by effectively bypassing some of the most sophisticated security controls and highly secured networks of high value. Referencing from the statements given by SentinelLabs security researchers, Vitali Kremez, Joshua Platt and Jason Reaves on Thursday, "The end-goal of the PowerTrick backdoor and its approach is to bypass restrictions and security controls to adapt to the new age of security controls and exploit the most protected and secure air-gapped high-value networks."  
  
According to the analysis, PowerTrick is configured to carry out commands and send back the results in the Base64 format. It is injected as a follow-up module after the victim's system has been infected by the TrickBot.  
  
**How does it work?**  
  
During the examinations, researchers discovered an initial backdoor script being sent out, at times draped as a Powershell task, it goes on to establish contact with command-and-control (C2) server. Once the contact has been successfully established, the authors send their very first command which leads to the downloading of the main PowerTrick backdoor. After the installation of the same, the malware starts executing common backdoor functions, it carries out check-in and then awaits further commands to act upon. Once received, it acts upon these commands and returns the results/errors.  
  
“Once the system and network have been profiled, the actors either stealthily clean up and move on to a different target of choice, or perform lateral movement inside the environment to high-value systems such as financial gateways,” as per the SentinelLab analysis.  
  
"TrickBot has shifted focus to enterprise environments over the years to incorporate many techniques from network profiling, mass data collection, incorporation of lateral traversal exploits,” researchers concluded.  
  
“This focus shift is also prevalent in their incorporation of malware and techniques in their tertiary deliveries that are targeting enterprise environments, it is similar to a company where the focus will shift depending on what generates the best revenue.”

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/3a1zS0W