---
title: 'Google Removes 500 Malicious Chrome Extensions'
date: 2020-02-14T08:57:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2020/02/Google-removes-500-chrome-extensions.jpg)

A grueling investigation conducted by security researcher Jamila Kaya and Cisco’s Duo Security team has exposed over 500 malicious Chrome browser extensions. Google has now removed the malicious extensions from the Chrome Web Store.  

These extensions **ran malicious ads and uploaded private browsing data** to servers without user consent. The researchers found that the malicious actors had been operating for at least two years and affected about 1.7 million users.  

Kaya made use of Duo’s free automated Chrome extension security assessment tool CRXcavator for the initial findings. The researcher later collaborated with other researchers at Duo for finding more evidence.  

_“The Chrome extension creators had specifically made extensions that obfuscated the underlying advertising functionality from users,”_ wrote the researchers in a [blog post](https://duo.com/labs/research/crxcavator-malvertising-2020). _“This was done in order to connect the browser clients to a command and control architecture, exfiltrate private browsing data without the user’s knowledge, expose the user to risk of exploit through advertising streams, and attempt to evade the Chrome Web Store’s fraud detection mechanisms.”_  

For those wondering how these attackers managed to snoop on your browsing data, they relied primarily on plugins that’d redirected users to malicious websites. The researchers point out that the plugins had the same name as the harmful website.  

For instance, the researchers found similar source code on two plugins namely Mapstrek and Arcadeyum among others. The malicious websites linked to the plugins were [Mapstrekcom](https://www.hybrid-analysis.com/sample/ff6f8c062bb9b4b66de6929ff2921f5fd9eff4b013b32842e9e7e51f609c1f0f?environmentId=100) and [Arcadeyumcom](https://www.hybrid-analysis.com/sample/0c1a8ca8ad72db5c0c3babc8d2488cc4ac7815d8158d170c5fd4c1056cd7dd87/5984bc447ca3e12189510e23). These websites were hosted on AWS.  

To stay safe from similar malicious extensions, the researchers recommend keeping track and regularly checking up on the extensions installed on your browser and removing the suspicious ones, if any.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/google-removes-over-500-malicious-chrome-extensions/)  
\[the\_ad id='1307'\]