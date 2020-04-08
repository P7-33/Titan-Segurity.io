---
title: 'Checkrain fake iOS jailbreak leads to click fraud'
date: 2019-10-15T09:49:00+01:00
draft: false
---

Attackers are capitalizing on the recent discovery of a new vulnerability that exists across legacy iOS hardware. Cisco Talos recently discovered a malicious actor using a fake website that claims to give iPhone users the ability to jailbreak their phones. However, this site just prompts users to download a malicious profile which allows the attacker to conduct click-fraud.

Checkm8 is a vulnerability in the bootrom of some legacy iOS devices that allows users to control the boot process. The vulnerability impacts all legacy models of the iPhone from the 4S through the X. The campaign we’ll cover in this post tries to capitalize off of checkra1n, a project that uses the checkm8 vulnerability to modify the bootrom and load a jailbroken image onto the iPhone. Checkm8 can be exploited with an open-source tool called “ipwndfu” developed by Axi0mX.

The attackers we’re tracking run a malicious website called checkrain\[.\]com that aims to draw in users who are looking for checkra1n.

This discovery made headlines and caught the attention of many security researchers. Jailbreaking a mobile device can be attractive to researchers, average users and malicious actors. A researcher or user may want to jailbreak phones to bypass standard restrictions put in place by the manufacturer to download additional software onto the device or look deeper into the inner workings of the phone. However, an attacker could jailbreak a device for malicious purposes, eventually obtaining full control of the device.

[Read More >>>](https://blog.talosintelligence.com/2019/10/checkrain-click-fraud.html)

  
  
from Cisco Blog » Security https://ift.tt/2OOVEg4