---
title: 'Cybercriminals Are Using Coronavirus to Spread Emotet Trojan Virus'
date: 2020-02-08T11:07:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2020/02/Corona-virus-spam-emails.jpg)

Amidst the fear of Coronavirus which originated in the Wuhan district of China, there are reports that bot-net driven emails are using the disease as a clickbait to spread a dangerous trojan virus in computers.  

In a campaign, IBM X-Force saw that **malicious emails are being sent to users that contain infection-prevention measures** for the Coronavirus. The emails are being used to spread the wicked Emotet trojan around regions of Japan.  

Emotet is essentially a trojan virus that is primarily spread via spam emails. The infection may come either through a malicious script, macro-enabled document files or malicious link. These emails may contain familiar branding designs which make it look like a legit email. The trojan once infects the computer can steal financial and banking details of the user and spread to other connected devices.  

Now, most of these emails are written in Japanese which suggest that operators are intentionally targetting regions which might be affected by the outbreak of the disease, Japan being in Asia. The contents of the emails are intriguing and contain the current date with the Japanese word for “notification”. This is making users click and open the contents of the email without giving any second thought.  

![Emotet email sample](https://beebom.com/wp-content/uploads/2020/02/Emotet-email-sample.jpg)

Emotet Trojan Email Sample  
Credit: IBM X-Force

![Emotet email translation](https://beebom.com/wp-content/uploads/2020/02/Emotet-email-translation.jpg)

Emotet Trojan Email Translation  
Credit: IBM X-Force

_“The emails appear to be sent by a disability welfare service provider in Japan,”_ according to a writeup from IBM X-Force, issued this week. _“The text briefly states that there have been reports of coronavirus patients in the Gifu prefecture in Japan and urges the reader to view the attached document.”_  

Other iterations of the emails are in the same language but warn the users about reports of infection in other prefectures of Japan, including Osaka and Tottori. The emails also contain a footer with a legitimate email address, phone and fax number of the public health authority of the respective targetted prefectures.   

When the user opens the email, they can find an attached document. The email urges the user to open and read the attached document. Upon opening the document, it surfaces an Office 365 message which asks the user to “enable the content”, if it is opened in a protected view. Like most Emotet attacks, if the attachment is opened with macros enabled, an overshadowed VBA macro script opens p Powershell and installs an Emotet downloader in the background.  

“_The extracted macros are using the same obfuscation technique as other Emotet emails observed in the past few weeks_,” IBM X-Force analysts said.  

On the other hand, Kaspersky has seen numerous spam email campaigns are emerging in the last weeks which contain a range of coronavirus-themed attachments. The malicious files which are discovered were hidden under the appearance of .PDF, .MP4 and .DOC files about the coronavirus. These files contain several threats that are capable of modifying, blocking, copying, destroying user data and interfering with the operation of computer networks, according to Kaspersky.  

_“As people continue to be worried for their health, we may see more and more malware hidden inside fake documents about the coronavirus being spread,_” wrote Anton Ivanov, Kaspersky malware analyst, in the report.  

As coronavirus continues to spread, it is causing a worldwide panic. People concerned with their health will most likely open up these kinds of emails to gain information. Thus the researchers predict that cybercriminals will capitalise the situation by using the health hazard to spread computer virus worldwide. Oh! The irony.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/cybercriminals-using-coronavirus-spread-emotet-trojan-virus/)  
\[the\_ad id='1307'\]