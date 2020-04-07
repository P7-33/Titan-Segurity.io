---
title: 'DeathRansom evolves from joke to actual ransomware'
date: 2020-01-04T02:27:00+01:00
draft: false
---

![DeathRansom encryption](https://zdnet1.cbsistatic.com/hub/i/2020/01/03/13fa9a5f-7d54-4635-b517-317b2204e9ee/deathransom-encryption.png)

The latest encryption scheme used by the DeathRansom ransomware

Image: Fortinet

A ransomware strain known as DeathRansom, once considered a joke, is now capable of encrypting files using a solid encryption scheme, cyber-security firm Fortinet reported today.

Making matters worse, the ransomware has been backed by a solid distribution campaign, and has been making regular victims on a daily basis for the past two months.

### First DeathRansom versions didn't encrypt anything

First DeathRansom infections were reported in November 2019. Initial versions of this ransomware were deemed a joke. At the time, DeathRansom merely mimicked being a ransomware without encrypting any of a user's files.

These first versions would add a file extension to all of a user's files and drop a ransom note on the user's computer asking for money.

All of this was done in an attempt to trick a victim into paying a ransom demand, without the user realizing that their files weren't actually encrypted.

As was reported at the time \[[1](https://id-ransomware.blogspot.com/2019/11/wacatac-ransomware.html), [2](https://www.bleepingcomputer.com/news/security/new-deathransom-ransomware-begins-to-make-a-name-for-itself/)\], all a user had to do to regain acess to their encrypted files was to remove the second extension from any file.

### New version released with a solid encryption scheme

However, work on the DeathRansom code continued, and newer versions are now working as actual ransomware.

According to Fortinet, the new DeathRansom strains use a complex combination of "Curve25519 algorithm for the Elliptic Curve Diffie-Hellman (ECDH) key exchange scheme, Salsa20, RSA-2048, AES-256 ECB, and a simple block XOR algorithm to encrypt files." \[see image above\]

While security researchers are still looking at DeathRansom's encryption scheme for implementation faults, the ransomware appears to be using a solid encryption scheme.

### Fortinet tracks down the DeathRansom author

But Fortinet's investigation into DeathRansom didn't limit itself to analyzing this new malware's source code. Researchers also went looking for clues about the ransomware's author.

By extracting strings from the DeathRansom source code and websites distributing the ransomware payloads, the Fortinet crew was able to successfully link the DeathRansom ransomware to a malware operator responsible for a wide range of cybercrime campaigns going back years.

Fortinet said that prior to creating and distributing DeathRansom, this malware operator had spent his time infecting users with multiple password stealers (Vidar, Azorult, Evrial, 1ms0rryStealer) and cryptocurrency miners (SupremeMiner).

The DeathRansom author appears to have spent years infecting users with malware, extracting usernames and passwords from their browsers, and selling the stolen credentials online, according to various ads Fortinet found on underground hacking forums.

These past malware campaigns left a considerable trail of clues that Fortinet analysts collected. These included the scat01 and SoftEgorka nicknames, the vitasa01\[@\]yandex.ru email address, a Russian phone number, and the gameshack\[.\]ru website (which appears to have been owned and operated by the DeathRansom author rather than being a hacked site).

Using these indicators, researchers found profiles on Iandex.Market, YouTube, Skype, VK, Instragram, and Facebook. All of these linked back to a young Russian named Egor Nedugov, living in Aksay, a small Russian town near Rostov-on-Don.

Past posts on hacking forums reveal that Nedugov, acting under the Scat01 username, had posted reviews for malware strains he was using at the time, and which Fortinet later tracked down and documented in their report -- such as Vidar, Evrial, and SupremeMiner.

![deathransom-forum-posts.png](https://www.zdnet.com/article/deathransom-evolves-from-joke-to-actual-ransomware/#ftag=RSSbaffb68)

<span><img src="https://zdnet4.cbsistatic.com/hub/i/2020/01/04/2ec3fedd-86a7-498d-aecb-f0b390be297e/deathransom-forum-posts.png" alt="deathransom-forum-posts.png" /></span>

Image: Fortinet

In an expansive [two](https://www.fortinet.com/blog/threat-research/death-ransom-new-strain-ransomware.html)\-[series](https://www.fortinet.com/blog/threat-research/death-ransom-attribution.html) report published today, Fortinet lists all of Nedugov's online accounts and the obvious mesh of connections between them.

Fortinet said it's very confident they found the right man behind DeathRansom, and that they found even more online profiles from the same actor which they didn't include in their report.

Furthermore, the DeathRansom author also appears to have broken one of the unwritten rules of the underground cybercrime scene by "phishing and scamming of his forum mates."

"That is why nearly all his accounts on underground forums were eventually banned," Fortinet said.

Currently, DeathRansom is being distributed via phishing email campaigns. The Fortinet report contains indicators of compromise that companies can include in their security products and prevent corporate systems from getting infected. Fortinet also said it's still working on analyzing the ransomware's encryption scheme foor any possible faults, which they hope to use to create a free decrypter to help past victims.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2ZQ96UD