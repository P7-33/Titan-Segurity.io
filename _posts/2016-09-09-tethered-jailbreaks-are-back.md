---
title: 'Tethered Jailbreaks Are Back'
date: 2019-09-30T02:12:00+01:00
draft: false
---

Earlier today, a new iPhone Boot ROM exploit, checkm8 (or Apollo or Moonshine), was [published on GitHub](https://github.com/axi0mX/ipwndfu/blob/master/checkm8.py) by [axi0mX](https://twitter.com/axi0mx/status/1177542201670168576?s=21), affecting the iPhone 4S through the iPhone X. The vulnerability was patched in devices with A12 and A13 CPUs. As of this writing, the iPhone XS, XS Max, XR, 11, 11 Pro and 11 Pro Max are all safe from this exploit.

We strongly urge all journalists, activists, and politicians to upgrade to an iPhone that was released in the past two years with an A12 or higher CPU. All other devices, including models that are still sold — like the iPhone 8, are vulnerable to this exploit. Regardless of your device, we also recommend an alphanumeric passcode, rather than a 6-digit numeric passcode. A strong alphanumeric passcode will protect the data on your phone from this and similar attacks.

It’s been a long time since the release of a public Boot ROM exploit. The [last one](https://www.theiphonewiki.com/wiki/Limera1n) was discovered in 2010 by George Hotz (geohot), and it affected the iPhone 3GS and iPhone 4.

What was released
-----------------

checkm8 exploits the Boot ROM to allow anyone with physical control of a phone to run arbitrary code. The Boot ROM, also called the Secure ROM, is the first code that executes when an iPhone is powered on and cannot be changed, because it’s “burned in” to the iPhone’s hardware. The Boot ROM initializes the system and eventually passes control to the kernel. It’s the root of trust for the trusted boot chain of iOS and verifies the integrity of the next stage of the boot process before passing execution control.

checkm8 does not include code required to boot a jailbroken kernel, but it does include the first steps. Likely, the community will soon release a full-tethered jailbreak that will slowly evolve to support all devices and versions.

The exploit also includes the ability to enable debugging features like JTAG on the iPhone CPU—a big win for security researchers and jailbreakers. Apple refers to this as “demoting” the phone in their 2016 BlackHat [presentation](https://www.blackhat.com/docs/us-16/materials/us-16-Krstic.pdf). This is probably not what Apple intended when they said they were releasing “[research devices](https://www.theverge.com/2019/8/8/20756629/apple-iphone-security-research-device-program-vulnerabilities).”

Impact and use cases
--------------------

The arbitrary (i.e., not signed by Apple) code that can be executed during the boot process can be used to boot already jailbroken kernels, as was done in ~2011 with [redsn0w](https://www.theiphonewiki.com/wiki/Redsn0w). This early access also provides access to the AES engine, enabling decryption with the GID key of Apple-encrypted firmware like iBoot.

In 2013, [we used the previous Boot ROM exploit](https://github.com/trailofbits/ios-integrity-validator) to get access to user data by brute-forcing passcodes. In the years since, Apple introduced the Secure Enclave (SEP), a separate processor that manages encryption keys for user data. The SEP has been hardened against passcode brute-forcing using replay counters and backoff timers. It’s currently unclear how much access this new exploit provides to the SEP, so we can’t accurately judge the impact to device privacy. In [Apple’s 2016 presentation](https://www.blackhat.com/docs/us-16/materials/us-16-Krstic.pdf), they point out that demoting the device forces the SEP to change the UID key, which is entangled with the passcode. Changing the UID key has the effect of permanently protecting user data on the device by making it impossible to decrypt.

![When designing the SEP, Apple’s threat model included “adversarial” situations such as another Boot ROM exploit.](https://trailofbits.files.wordpress.com/2019/09/screen-shot-2019-09-27-at-1.51.33-pm-1.png?w=690&h=389)

When designing the SEP, Apple’s threat model included “adversarial” situations such as another Boot ROM exploit.

It would not be surprising if the vulnerability exploited by checkm8 has been used by Cellebrite for forensic analysis, but they would need another trick or exploit to undermine the SEP’s protections.

> checkm8 doesn't allow law enforcement to decrypt the phone, but it does allow them to rootkit it with 30 seconds of unattended access. Once it's unlocked by the user they'd get everything they need.
> 
> — Ryan Stortz (@withzombies) [September 27, 2019](https://twitter.com/withzombies/status/1177720876965519360?ref_src=twsrc%5Etfw)

Future
------

The vulnerability has been fixed on new hardware (iPhone XS, iPhone XR, iPhone 11), but Apple still sells hardware vulnerable to this exploit (iPhone 8 and also some iPads and iPods). They would need to create new CPU masks and release updated versions of these devices to secure them. This is unlikely, since Apple did not release a patched iPhone 4 when the previous Boot ROM exploit was released.

It is likely we will see one large community project that will apply common patches and install Cydia and other alternate App Stores. This is a boon to researchers but also to pirates.

Advice for at-risk users
------------------------

Upgrade to an iPhone that was released in the past two years with an A12 or higher CPU. All other devices are vulnerable to this exploit. After upgrading, wipe your previous phone by selecting “Erase All Content and Settings” from Settings > General > Reset. Devices patched for this issue include:

*   iPhone 11, 11 Pro, 11 Pro Max
*   iPhone XS, XS Max
*   iPhone XR

Set an alphanumeric passcode, rather than a 6-digit numeric passcode. Even with this exploit, an attacker must brute-force your password to gain access to your data. A strong alphanumeric passcode will protect your data against these attacks. To configure an alphanumeric passcode:

1.  On iPhone X and later, go to Settings > Face ID & Passcode.  
    On earlier iPhone models, go to Touch ID & Passcode. On devices without Touch ID, go to Settings > Passcode.
2.  Tap Change passcode.
3.  Enter your current passcode.
4.  When prompted to enter a new passcode, tap Passcode Options and select “Custom Alphanumeric Code”

Detecting these jailbreaks
--------------------------

It will still be possible to detect jailbroken phones in the common case, but it is not possible to detect if an iPhone has been exploited with checkm8. Jailbreak detection will have to continue to rely on identifying side-effects of the exploitation. [iVerify Core](https://blog.trailofbits.com/2017/10/12/ios-jailbreak-detection-toolkit-now-available/) continues to offer a comprehensive jailbreak detection suite, and we will continue to update it as new jailbreaks are released. [Contact us](https://www.trailofbits.com/contact/) to learn more about iVerify Core.

  
  
from Hacker News https://ift.tt/2lMwPWg