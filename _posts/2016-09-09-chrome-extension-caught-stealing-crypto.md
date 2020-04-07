---
title: 'Chrome extension caught stealing crypto-wallet private keys'
date: 2020-01-01T11:06:00+01:00
draft: false
---

A Google Chrome extension was caught injecting JavaScript code on web pages to steal passwords and private keys from cryptocurrency wallets and cryptocurrency portals.

The extension is named [Shitcoin Wallet](https://shitcoinwallet.co) (Chrome extension ID: [ckkgmccefffnbbalkmbbgebbojjogffn](https://chrome.google.com/webstore/detail/shitcoin-wallet/ckkgmccefffnbbalkmbbgebbojjogffn)), and was launched last month, on December 9.

According to an [introductory blog post](https://medium.com/@shitcoinwallet/shitcoin-wallet-introduction-official-launch-9dad94cf368b), Shitcoin Wallet lets users manage Ether (ETH) coins, but also Ethereum ERC20-based tokens -- tokens usually issued for ICOs ([initial coin offerings](https://en.wikipedia.org/wiki/Initial_coin_offering)).

Users can install the Chrome extension and manage ETH coins and ERC20 tokens from within their browser, or they can install a Windows desktop app, if they want to manage their funds from outside a browser's riskier environment.

### Malicious behavior breakdown

However, the wallet app wasn't what it promised to be. Yesterday, [Harry Denley](https://harrydenley.com/), Director of Security at the [MyCrypto platform](https://about.mycrypto.com/), discovered that the extension contained malicious code.

According to Denley, the extension is dangerous to users in two ways. First, any funds (ETH coins and ERC0-based tokens) managed directly inside the extension are at risk.

Denley says that the extension sends the private keys of all wallets created or managed through its interface to a third-party website located at _erc20wallet\[.\]tk_.

![shitcoin-wallet.png](https://zdnet3.cbsistatic.com/hub/i/2020/01/01/1d13ac11-1512-49d0-8c76-c9439464cfee/shitcoin-wallet.png)

Second, the extension also actively injects malicious JavaScript code when users navigate to five well-known and popular cryptocurrency management platforms. This code steals login credentials and private keys, data that it's sent to the same _erc20wallet\[.\]tk_ third-party website.

According to an analysis of the malicious code, the process goes as follows:

\> Users install the Chrome extension  
\> Chrome extension requests permission to inject JavaScript (JS) code on 77 websites \[listed [here](https://gist.github.com/campuscodi/b63ea104e1cf17ef446dfa8e67651e5f#file-manifest-json-L33)\]  
\> When users navigate to any of these 77 sites, the extension loads and injects [an additional JS file](https://gist.github.com/campuscodi/1154becfce7ab1cb6dafa3cabfa28c9f) from: _https://erc20wallet\[.\]tk/js/content\_.js_  
\> This JS file contains obfuscated code \[deobfuscated [here](https://pastebin.com/raw/ZtUpWVvT)\]  
\> The code activates on five websites: _**MyEtherWallet.com**, **Idex.Market**, **Binance.org**, **NeoTracker.io**,_ and _**Switcheo.exchange**_  
\> Once activated, the malicious JS code records the user's login credentials, searches for private keys stored inside the dashboards of the five services, and, finally, sends the data to _erc20wallet\[.\]tk_

At the time of writing, the extension was still available for download through the official Google Chrome Web Store, where it listed 625 installs.

It is unclear if the Shitcoin Wallet team is responsible for the malicious code, or if the Chrome extension was compromised by a third-party. A spokesperson for the Shitcoin Wallet team did not reply to a request for comment before this article's publication.

### Desktop app

On the extension's official website, [32-bit](https://www.virustotal.com/gui/file/0ee02d6aa9c126c3a324685a7b0af581b73837adc34042f34332a4637df53616/detection) and [64-bit](https://www.virustotal.com/gui/file/d58342ddf5c6ca7e757ac2f4c6d519100dab13d271554822c6936d4654be346e/detection) installers were also made available to users.

Scans with VirusTotal, a website that aggregates the virus scanning engines of several antivirus software makers, show both files as clean.

However, numerous comments posted on the wallet's Telegram channel suggest the desktop apps might contain similarly malicious code, if not worse.

![shitcoin-wallet-telegram.png](https://www.zdnet.com/article/chrome-extension-caught-stealing-crypto-wallet-private-keys/#ftag=RSSbaffb68)

<span><img src="https://zdnet2.cbsistatic.com/hub/i/2020/01/01/8fbe2963-638f-4493-a01a-ce070f975946/shitcoin-wallet-telegram.png" alt="shitcoin-wallet-telegram.png" /></span>

Image: ZDNet

  
  
from Latest Topic for ZDNet in... https://ift.tt/36dxYYI