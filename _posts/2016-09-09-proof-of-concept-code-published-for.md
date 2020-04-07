---
title: 'Proof-of-concept code published for Citrix bug as attacks intensify'
date: 2020-01-11T08:59:00+01:00
draft: false
---

![Shitrix Citrix bug](https://zdnet2.cbsistatic.com/hub/i/2020/01/11/adaeb9ea-e3b8-4799-8295-2f4d23aa7647/citrix-bug.png)

Image: Project Zero India

Starting with yesterday, there is now public proof-of-concept exploit code for **CVE-2019-19781**, a vulnerability in Citrix enterprise equipment that can allow hackers to take over devices and access a companies' internal networks.

The vulnerability is as bad as it gets and has been deemed one of the most dangerous bugs disclosed in recent years.

Codenamed Shitrix by the larger infosec community, this vulnerability impacts **Citrix Application Delivery Controller (ADC)**, formerly known as NetScaler ADC, and **Citrix Gateway**, formerly known as NetScaler Gateway.

The vulnerability is a path traversal bug that can be exploited over the internet by an attacker. The attacker does not have to provide authentication credentials for the device when launching an attack. All an attacker has to do is send a boobytrapped request to the vulnerable Citrix appliance, along with the exploit code they want to execute on the device.

The bug was discovered and reported to Citrix by Mikhail Klyuchnikov, a researcher at UK security firm Positive Technologies. Klyuchnikov said that at the time he found the bug, there were more than 80,000 organizations running vulnerable Citrix instances.

### Still no patch almost a month later

On December 17, Citrix released a [security advisory](https://support.citrix.com/article/CTX267027) for its customers, but the company did not release a patch. Instead, Citrix published [a support page detailing mitigations](https://support.citrix.com/article/CTX267679) in the form of configuration adjustments.

Almost a month later, Citrix has still not released a patch, despite the bug's severity and its wide impact.

In the meantime, threat actors have been starting to figure out how to exploit the bug -- which many security researchers said was trivial and only required a few lines of code.

Scans have been happening for weeks, but exploitation attemps have also begun for at least three days, according to various security experts and cyber-security firms who run honeypot servers.

> 🚨 In my Citrix ADC honeypot, CVE-2019-19781 is being probed with attackers reading sensitive credential config files remotely using ../ directory traversal (a variant of this issue). So this is in the wild, active exploitation starting up. 🚨 [https://t.co/pDZ2lplSBj](https://t.co/pDZ2lplSBj)
> 
> — Kevin Beaumont (@GossiTheDog) [January 8, 2020](https://twitter.com/GossiTheDog/status/1214892555306971138?ref_src=twsrc%5Etfw)

The bug's severity and the clear danger to enterprise systems did not go unnoticed. Over the past few weeks, security experts, government officials, government cybersecurity agencies, CERT teams, and about anyone under the sun who understands basic enterprise security have been warning companies to apply the Citrix mitigations to prevent attacks from exploiting vulnerable machines until Citrix finally releases a permanent fix in the form of a patch.

> The Citrix RCE is a doozie. Lots of good security architectures appropriately rely on Citrix to reduce the attack surface significantly and now they are at significant risk. Get this patched. [https://t.co/7B9d7e7YK7](https://t.co/7B9d7e7YK7)
> 
> — Rob Joyce (@RGB\_Lights) [January 10, 2020](https://twitter.com/RGB_Lights/status/1215526650605121537?ref_src=twsrc%5Etfw)

> Can’t emphasize enough - please please please do the mitigation steps for the Citrix exploit as soon as possible.  
>   
> This is going to be a really bad one folks.  
>   
> Easy to automate and exploit and is widely used across the Internet.  
>   
> Mitigation here: [https://t.co/jeF0UC6A9V](https://t.co/jeF0UC6A9V)
> 
> — Dave Kennedy (ReL1K) (@HackingDave) [January 11, 2020](https://twitter.com/HackingDave/status/1215800253246513155?ref_src=twsrc%5Etfw)

### Proof-of-concept code broadly available

While attacks have been slowly climbing in intensity over the past few days, the security community believed things wouldn't get out of hand, as attackers would still need to figure out a way to exploit vulnerable Citrix systems, lacking a public exploit.

This changed yesterday, on Friday night, when a group of security researchers calling themselves Project Zero India released [the first proof-of-concept (PoC) exploit code](https://github.com/projectzeroindia/CVE-2019-19781) for the CVE-2019-19781 vulnerability.

A few hours later, the team at TrustedSec followed [with their own PoC](https://github.com/trustedsec/cve-2019-19781). The TrustedSec team had developed their PoC earlier this week but refused to release it because it was aware that publishing the code on the internet would trigger a spike in exploitation attempts, something they did not want to do.

"We are only disclosing this due to others publishing the exploit code first," TrustedSec said in a description of their tool on GitHub. "We would have hoped to have had this hidden for a while longer while defenders had appropriate time to patch their systems."

The security firm hopes that companies use their tool to test their networks for vulnerable Citrix instances and if they configured the Citrix mitigation correctly.

They've also published a blog post on [how to analyze Citrix systems for any possible compromise](https://www.trustedsec.com/blog/netscaler-remote-code-execution-forensics/), just in case some companies have had the unfortunate luck to have already been hacked.

_Additional technical write-ups analyzing the Citrix bug:_ [_Positive Technologies_](https://www.ptsecurity.com/ww-en/about/news/citrix-vulnerability-allows-criminals-to-hack-networks-of-80000-companies/)_,_ [_MDSec_](https://www.mdsec.co.uk/2020/01/deep-dive-to-citrix-adc-remote-code-execution-cve-2019-19781/)_,_ [_TrustedSec_](https://www.trustedsec.com/blog/critical-exposure-in-citrix-adc-netscaler-unauthenticated-remote-code-execution/)_._

  
  
from Latest Topic for ZDNet in... https://ift.tt/2uE1RUi