---
title: 'Apple Engineers Propose a New Standard for SMS OTPs'
date: 2020-01-31T13:41:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2020/01/Apple-Engineers-Propose-a-New-Standard-for-SMS-OTPs.jpg)

Engineers at Apple have proposed a standardized format for SMS One-Time Passcodes (OTP). To be specific, Apple engineers working on WebKit, the core-component of the Safari web browser have put forth the proposal with two goals.  

Firstly, the engineers want to **eliminate the need for manually copying and pasting codes** from SMSes, which can be annoying at times. In addition, they aim to **establish a standard so that websites could trust the source of SMS** and ensure that the SMS is being entered on the intended source website thereby making the system more secure.  

To achieve these goals, the engineers propose a “lightweight text format” with the URL of the website added right into the SMS. Companies could also add the text they want at the beginning of the SMS. Take a look at the sample OTP SMS below for better understanding.  

```
747723 is your FooBar authentication code.  
  
@foobar.com #747723
```  

In the above example, “747723 is your FooBar authentication code” represents the text added by brands while “@foobar.com” denotes the origin URL (https://foobar.com) and “#747723” is the actual OTP code.  

_“‘@’ and ‘#’ are sigils used to identify the text that follows them. Any origin which is schemelessly same site as https://foobar.com/ is an origin on which this code may be used.”, _note the engineers.  

This approach could make it easier for apps and websites to identify OTPs without compromising on security. If implemented, this could also **eliminate spammy and malicious actors from taking over accounts** with phishing sites.  

As of now, Apple WebKit engineers and Google engineers have welcomed the proposal. There is no word from Firefox engineers so far. We could expect this new SMS feature to be rolled out in future browser updates. If it gets rolled out, third-party apps and services are more likely to adopt the technique which in turn would make it an industry standard for OTPs.  

So, what are your thoughts on this new OTP  format? Let us know in the comments.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/apple-engineers-propose-a-new-standard-for-sms-otps/)  
\[the\_ad id='1307'\]