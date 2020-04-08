---
title: 'ESP32 Flash Encryption and Sec. Boot Keys
Extraction #ESP32 #Encryption #PWN @LimitedResults'
date: 2019-11-18T15:52:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-51.png)

Yikes! [The LimtedResults blog discusses](https://limitedresults.com/2019/11/pwn-the-esp32-forever-flash-encryption-and-sec-boot-keys-extraction/) a persistent exploit, bypassing the Secure Boot and the Flash Encryption on an ESP32 board.

> In this report, I disclose a full readout of protected E-Fuses storing two secret keys, one used for Flash Encryption (**BLK1**) and the other for the Secure Boot (**BLK2**).
> 
> This attack cannot be patched by the vendor on existing devices. It’s a FOREVER pwn.
> 
> Espressif and I decided to go to **Responsible Disclosure** for this vulnerability (**CVE-2019-17391**).

The conclusion:

> The ESP32 platform, set in Full Secure mode (Flash Encryption + Secure Boot), is the target of this investigation. It is the maximum security level recommended by Espressif.
> 
> Using voltage glitching to modify the Read Protection Values of the E-Fuses Controller, a full Readout of Flash Encryption Key (FEK) and Secure Boot Key (SBK) has been achieved.
> 
> This FATAL exploit allows an attacker to decrypt an encrypted firmware because they now possess the AES Flash Encryption Key.
> 
> Worst case scenario, one is able to forge their own valid firmware (using the Secure Boot Key) then encrypt it (using the Flash Encryption Key) to replace the original firmware PERMANENTLY.
> 
> **There is no way to patch this without a hardware revision**.
> 
> Due to the low-complexity, this attack can be reproduced on the field easily. In their opinion, a proficient hacker can reproduce this attack in less than one day and with less than $1000 in equipment.

[See the full post](https://limitedresults.com/2019/11/pwn-the-esp32-forever-flash-encryption-and-sec-boot-keys-extraction/) with a description and exploitation code here.

![](https://limitedresults.com/wp-content/uploads/2019/08/scope_fault-1024x630.png)