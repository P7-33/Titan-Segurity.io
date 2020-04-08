---
title: 'Stantinko botnet''s strategy now shifts to crypto-mining'
date: 2019-11-29T18:28:00+01:00
draft: false
---

  
Stantinko botnet that's been involved in various criminal ventures has now added a Monero crypto-mining module to its arsenal. Stantiko has since 2012 carried out a range of criminal activities like fraud, ad injections, social network fraud and brute-force password-stealing attacks to Soviet nations targeting Russia, Ukraine, Belarus, and Kazakhstan. But lately, researchers at ESET, discovered that a major source of Stantinko’s monetization since at least August 2018, comes from Monero crypto-mining module.  
  

[![](https://1.bp.blogspot.com/-xJIiAepjrC8/XeFQDU4yNnI/AAAAAAAAL5Y/otJr4yhvlZEvxvnhtPZyaAQYJtOHhI2CQCLcBGAsYHQ/s640/bitcoin-1813503_960_720.jpg)](https://1.bp.blogspot.com/-xJIiAepjrC8/XeFQDU4yNnI/AAAAAAAAL5Y/otJr4yhvlZEvxvnhtPZyaAQYJtOHhI2CQCLcBGAsYHQ/s1600/bitcoin-1813503_960_720.jpg)

  
ESET describes the module as, "highly modified version of the xmr-stark open-source crypto-miner," Stantinko’s mining module, dubbed CoinMiner. Stantinko is so powerful that it can "exhaust most of the resources of the compromised machine." ESET elaborate, that each sample of the model is unique and compile a different module for every victim. "This module’s most notable feature is the way it is obfuscated to thwart analysis and avoid detection," said ESET. CoinMiner. Stantinko is divided into four logical parts with distinct capabilities. The main component does the actual mining, and the other three parts perform the following functions-  
•suspending other (i.e. competing) crypto-mining applications  
•detecting security software  
•suspending the crypto-mining function if the PC is on battery power or when a task manager is detected, to prevent being revealed by the user CoinMiner.  
  
Stantinko doesn't communicate with the mining pool directly, rather it uses a proxy with IP address derived from the description texts, of YouTube videos. This module communicates with the proxies by the hashing algorithm that takes place over TCP and encrypted by RC4. It adapts to adjustments of algorithms to mine the most profitable cryptocurrency. YouTube when alerted of the scam by ESET, removed the offending channels.  
**Preventing Detection**  
CoinMiner.Stantinko is very smart in preventing detection, it removes itself in the presence of a competitor. It temporarily suspends mining if there’s no power supply. "Our discovery shows that the criminals behind Stantinko continue to expand the ways they leverage the botnet they control," Hrcka concludes. "This remotely configured crypto-mining module, distributed since at least August of 2018 and still active at the time of writing, shows this group continues to innovate and extend its money-making capabilities."

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/2ORCBQQ