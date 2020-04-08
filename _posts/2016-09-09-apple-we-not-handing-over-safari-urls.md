---
title: 'Apple: We''re not handing over Safari URLs to Tencent, just IP addresses'
date: 2019-10-15T02:09:00+01:00
draft: false
---

Responding to concern that its Safari browser's defense against malicious websites may [reveal the IP addresses](https://reclaimthenet.org/apple-safari-ip-addresses-tencent/) of some users' devices to China-based Tencent, Apple insists that Safari doesn't reveal a different bit of information, the webpages Safari users visit.

Apple may [deny users in China VPN protection](https://www.theregister.co.uk/2017/07/31/china_russia_clamp_down_on_vpns/), it may [deny Hong Kong democracy protesters an app used to avoid police](https://www.theregister.co.uk/2019/10/10/cook_china_censorship/), and it may [remove references to Taiwan](https://www.theregister.co.uk/2019/10/07/apple_taiwan_flag/) in localized versions of iOS 13 for the Chinese-controlled Hong Kong and Macau.

But it's not giving up website visits – readily available to authorities by monitoring ISPs, DNS, and reportedly by backdooring Android apps \[[PDF](https://cure53.de/analysis_report_sgn.pdf)\] like the Communist Party of China's "Study the Great Nation" – through browser telemetry.

Since [February](https://twitter.com/StijnDV/status/1092515697694003200?s=20) at least and [perhaps longer](https://twitter.com/eromang/status/1183425101074718721?s=20), Safari's Safe Browsing framework has been receiving [hash prefixes](https://developers.google.com/safe-browsing/v4/urls-hashing#suffixprefix-expressions) of known malware sites from Google Safe Browsing database, or for users in mainland China, Tencent's Safe Browsing database.

A 32-bit hash prefix like "ba7816bf" would represent the first eight characters of a 256-bit, 64-character SHA256 digest of a full URL.

Before it loads a requested website, Safari, like other browsers that implement a safe browsing lookup system, will hash the URL of the website to be visited and compare its hash prefix to the received hash segments of malicious sites.

In the event of a match – and there may be several given that hash prefixes aren't necessarily unique, Safari asks the API provider – Google or Tencent – for all the URLs that match the hash prefix.

Using that fetched list, Safari can then determine whether the intended destination matches anything on the list of malicious websites and present a warning if necessary. And it will do so unless the on-by-default "Fraudulent Website Warning" is disabled using the appropriate iOS or macOS settings menu.

### Nothing to see here

And this, Apple contends, is nothing to worry about. In a statement emailed to _The Register_ (!), an Apple spokesperson said:

"Apple protects user privacy and safeguards your data with Safari Fraudulent Website Warning, a security feature that flags websites known to be malicious in nature," it commented.

"When the feature is enabled, Safari checks the website URL against lists of known websites and displays a warning if the URL the user is visiting is suspected of fraudulent conduct like phishing. To accomplish this task, Safari receives a list of websites known to be malicious from Google, and for devices with their region code set to mainland China, it receives a list from Tencent."

![Tim Cook, photo2 by JStone via Shutterstock](https://regmedia.co.uk/2016/08/15/tim_cook_photo2_by_jstone_via_shutterstock.jpg?x=174&y=115&crop=1)

In a touching show of solidarity with the NBA and Blizzard, Apple completely caves to China on HK protest app
-------------------------------------------------------------------------------------------------------------

[READ MORE](https://www.theregister.co.uk/2019/10/10/cook_china_censorship/)

"The actual URL of a website you visit is never shared with a safe browsing provider and the feature can be turned off."

That said, there's still the issue of user IP addresses, which Tencent would see for those using devices with mainland China settings. That's a privacy concern, but its one among many given that other Chinese internet companies – ISPs, app providers, cloud service providers, and the like – can be assumed to collect that information and provide it to the [Chinese surveillance state](https://www.uscirf.gov/news-room/press-releases-statements/uscirf-report-documents-how-china-s-surveillance-state-threatens) on demand.

In a [blog post](https://blog.cryptographyengineering.com/2019/10/13/dear-apple-safe-browsing-might-not-be-that-safe/) on Sunday, Matthew Green, associate professor of computer science at the Johns Hopkins Information Security Institute, pointed out some potential privacy problems in safe browsing APIs like Google's.

The privacy community, he said, has mostly come to terms with the privacy trade-off that comes with Google's Safe Browsing API, figuring the security gains are worth the risk.

"But Tencent isn’t Google," he said. "While they may be just as trustworthy, we deserve to be informed about this kind of change and to make choices about it. At very least, users should learn about these changes before Apple pushes the feature into production, and thus asks millions of their customers to trust them." ®

Sponsored: [How to get more from MicroStrategy by optimising your data stack](https://go.theregister.co.uk/tl/1858/-7813/how-to-get-more-from-microstrategy-by-optimising-your-data-stack?td=wptl1858)

  
  
from Hacker News https://ift.tt/2ONn4Tz