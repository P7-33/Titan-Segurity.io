---
title: 'Apple Engineers to Standardize the Format of the SMS Messages
Containing OTPs'
date: 2020-01-31T19:39:00+01:00
draft: false
---

[![](https://4.bp.blogspot.com/-CmQlHwlk4Pw/XjRScKQ53NI/AAAAAAAA7zM/lSw3LiFvLzIANPv_QCMGIPZ707cYnePZQCLcBGAsYHQ/s640/photo.webp)](https://4.bp.blogspot.com/-CmQlHwlk4Pw/XjRScKQ53NI/AAAAAAAA7zM/lSw3LiFvLzIANPv_QCMGIPZ707cYnePZQCLcBGAsYHQ/s1600/photo.webp)

  

A proposal comes from Apple engineers working at WebKit, the core component of the Safari web browser, to institutionalize the format of the SMS messages containing one-time passwords (OTP) that users receive during the two-factor authentication (2FA) login process.  
  
 With 2 basic goals, the proposal aims initially is to introduce a way that OTP SMS messages can be associated with a URL, which is essentially done by adding the login URL inside the SMS itself.  
  
And the second being to institutionalize the format of 2FA/OTP SMS messages, so browsers and other mobile applications can undoubtedly distinguish the approaching SMS, perceive web domain inside the message, and afterward consequently extract the OTP code and complete the login operation moving forward without any further user interaction.  
  
According to the new proposal, the new SMS format for OTP codes would look like below:  
  
_747723 is your WEBSITE authentication code. _  
_@website.com #747723 _  
  
The first line, intended for human users, permits them to decide from what site the SMS OTP code originated from and the second line is for both human users as well as for applications and browsers.  
  
 Applications and browsers will consequently extricate the OTP code and complete the 2FA login operation. In the event that there's a 'mismatch' and the auto-complete operation falls flat, human readers will have the option to see the site's original URL, and contrast it with the site they're attempting to login.  
  
On the off chance that the two are not similar, at that point, users will be alerted that they're very a phishing site and forsake their login activity.  
  
When browsers will deliver components for reading SMS OTP codes in the new format, significant providers of SMS OTP codes are required to switch to utilizing it. Starting now, Twilio has already communicated its enthusiasm for actualizing the new arrangement for its SMS OTP administrations.   
  
Presently, while Apple (WebKit) and Google (Chromium) engineers are quite energetic about the proposition, Mozilla (Firefox) has not yet given an official criticism on the standard yet.

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/37WLwsJ