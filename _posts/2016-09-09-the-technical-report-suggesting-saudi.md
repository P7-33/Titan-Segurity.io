---
title: 'The technical report suggesting Saudi Arabia''s prince hacked Bezos'' phone'
date: 2020-01-23T03:35:00+01:00
draft: false
---

A report investigating the potential hack of Jeff Bezos’ iPhone indicates that forensic investigators found a suspicious file but no evidence of any malware on the phone. It also says that investigators had to reset Bezos’s iTunes backup password because investigators didn’t have it to access the backup of his phone. The latter suggests that Bezos may have forgotten his password.  

The report, obtained by Motherboard, indicates that investigators set up a secure lab to examine the phone and its artifacts and spent two days poring over the device but were unable to find any malware on it. Instead, they only found a suspicious video file sent to Bezos on May 1, 2018 that “appears to be an Arabic language promotional film about telecommunications.”

That file shows an image of the Saudi Arabian flag and Swedish flags and arrived with an encrypted downloader. Because the downloader was encrypted this delayed or further prevented “study of the code delivered along with the video.”

Investigators determined the video or downloader were suspicious only because Bezos’ phone subsequently began transmitting large amounts of data. “\[W\]ithin hours of the encrypted downloader being received, a massive and unauthorized exfiltration of data from Bezos’ phone began, continuing and escalating for months thereafter,” the report states.

A screenshot of the report showing the video the MBS account sent to Bezos. Image: Screenshot

“The amount of data being transmitted out of Bezos’ phone changed dramatically after receiving the WhatsApp video file and never returned to baseline. Following execution of the encrypted downloader sent from MBS’ account, egress on the device immediately jumped by approximately 29,000 percent,” it notes. “Forensic artifacts show that in the six (6) months prior to receiving the WhatsApp video, Bezos’ phone had an average of 430KB of egress per day, fairly typical of an iPhone. Within hours of the WhatsApp video, egress jumped to 126MB. The phone maintained an unusually high average of 101MB of egress data per day for months thereafter, including many massive and highly atypical spikes of egress data.

The digital forensic results, combined with a larger investigation, interviews, research, and expert intelligence information, led the investigators “to assess Bezos’ phone was compromised via tools procured by Saud al Qahtani,” the report states.

[Saud al Qahtani](https://www.vice.com/en_us/article/kzjmze/saud-al-qahtani-saudi-arabia-hacking-team) is a friend and close advisor to Saudi Crown Prince Mohammed bin Salman, known as MBS. He was also president and chairman of the Saudi Federation for Cybersecurity, Programming and Drones and was known to procure offensive hacking tools on behalf of the Saudi regime, among them tools made by the Italian company Hacking Team.

Some of the investigation’s findings were first reported by [the Guardian](https://www.theguardian.com/technology/2020/jan/21/amazon-boss-jeff-bezoss-phone-hacked-by-saudi-crown-prince), but has received criticism from information security professionals because the news reports have suggested the tool used might have been developed by the Israeli company NSO Group, a maker of offensive mobile hacking tools. The forensic report does not say an NSO Group tool was used, but simply notes that the company’s tools have the ability to conduct the kind of exfiltration that appears to have occurred on Bezos’ phone.

“Advanced mobile spyware, such as NSO Group’s Pegasus or Hacking Team’s Galileo, can hook into legitimate applications and processes on a compromised device as a way to bypass detection and obfuscate activity in order to ultimately intercept and exfiltrate data,” the report states. “The success of techniques such as these is a very likely explanation for the various spikes in traffic originating from Bezos device.”

In addition to the large amount of data extracted from Bezos’ phone, investigators pointed to the odd nature of two text messages sent to Bezos from the WhatsApp account associated with the crown prince. These included a November 8, 2018 message that included a photo or a woman who resembles Lauren Sanchez, the woman with whom Bezos was having a secret affair at the time. News of the affair had not yet broken when Bezos received the text message and photo.

A screenshot of a section of the FTI Consulting report. Image: Screenshot

The second text sent Feb. 16 arrived after Bezos had been given a phone briefing about an online campaign that was being waged against him by Saudi entities. The WhatsApp message seemed to reference this and told Bezos not to believe everything he hears or is told.

The forensic investigators encountered at least two obstacles in conducting their exam of Bezos's phone. The first related to the encrypted downloader. Farrante’s team first examined the attachment alone before deciding they needed to do a full forensic imaging and analysis of the phone’s contents and traffic. They used a tool from Cellebrite (Cellebrite UFED 4PC Ultimate and Physical Analyzer) to grab forensic images from the phone and set up a secure makeshift lab to do the forensics over two days.

They did not find any malicious code embedded in the video file, but discovered that the video was delivered via an encrypted downloader hosted on WhatsApp’s media server.

“Due to end-to-end encryption employed by WhatsApp, it is impossible to decrypt the contents of the downloader to determine if it contained any malicious code in addition to the delivered video,” the investigators found.

The second obstacle regarded the password for the iTunes backup.

“During the initial attempt to collect a forensic image of the iPhone, FTI determined that the device had iTunes backup encryption enabled, and that full analysis of the contents of the forensic image would require the encryption password,” the report states.

They apparently never obtained the password, however, because the report states that on May 20, 2019, the investigators “tested options for bypassing the iTunes backup encryption password” and ended up resetting “All Settings” on Bezos’ iPhone X to restore the device’s settings to factory defaults, thereby “removing the encryption password while preserving the file system and any relevant data and artifacts. FTI received authorization to perform this resetting step, did so, and then commenced acquisition of an unencrypted Cellebrite forensic image.”

A mobile forensic expert told Motherboard that the investigation as depicted in the report is significantly incomplete and would only have provided the investigators with about 50 percent of what they needed, especially if this is a nation-state attack. She says the iTunes backup and other extractions they did would get them only messages, photo files, contacts and other files that the user is interested in saving from their applications, but not the core files.

“They would need to use a tool like Graykey or Cellebrite Premium or do a jailbreak to get a look at the full file system. That’s where that state-sponsored malware is going to be found. Good state-sponsored malware should never show up in a backup,” said Sarah Edwards, an author and teacher of mobile forensics for the SANS Institute.

“The full file system is getting into the device and getting every single file on there—the whole operating system, the application data, the databases that will not be backed up. So really the in-depth analysis should be done on that full file system, for this level of investigation anyway. I would have insisted on that right from the start.”

The investigators do note on the last page of their report that they need to jailbreak Bezos’s phone to examine the root file system. Edwards said this would indeed get them everything they would need to search for persistent spyware like the kind created and sold by the NSO Group. But the report doesn’t indicate if that did get done.

Motherboard contacted Farrante to ask if his team had completed those final steps to examine the full file system and will update this story if he responds.

“Looks like \[the\] experts were not qualified enough,” Vladimir Katalov, CEO of iOS forensics firm Elcomsoft, told Motherboard.

**_Update: This piece has been updated to include comment from Sarah Edwards and Vladimir Katalov._**

**_Subscribe to our cybersecurity podcast, [CYBER](https://itunes.apple.com/gb/podcast/cyber/id1441708044?mt=2)._**

  
  
from Hacker News https://ift.tt/37gT7li