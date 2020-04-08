---
title: 'Advertise Your Conference Schedule Via SSID'
date: 2019-10-23T03:06:00+01:00
draft: false
---

Whether it’s been a Python script running on a Linux box or an ESP8266, abusing using WiFi SSIDs to convey messages is hardly a new trick. But for DerbyCon 2019, \[vgrsec\] wanted to do put together something a little unique. Dare we say, even useful. Rather than broadcast out SSID obscenities or memes, this [Raspberry Pi created fake WiFi networks that told everyone what talks were coming up](https://www.vgrsec.com/post20191006.html).

[![](https://hackaday.com/wp-content/uploads/2019/10/ssidtalks_detail.png?w=320)](https://hackaday.com/wp-content/uploads/2019/10/ssidtalks_detail.png)The concept here is fairly simple: there’s a text file in `/boot` that contains the truncated names of all the talks and workshops in the schedule, one per line, and each line starts with the time that particular event is scheduled for. The script that \[vgrsec\] wrote opens this text file, searches for the lines beginning with the current time, and generates the appropriate SSIDs. With the number of tracks being run at DerbyCon, that meant there could be as many as five SSIDs generated at once.

Now in theory that would be enough to pull off this particular hack, but there’s a problem. The lack of an RTC on the Raspberry Pi means it can’t keep time very well, and the fact that the WiFi adapter would be busy pumping out SSIDs meant the chances of it being able to connect to the Internet and pull down the current time over NTP weren’t very good.

As the system was worthless without a reliable way of keeping time, \[vgrsec\] added an Adafruit PiRTC module to the mix. Once the time has been synchronized, the system could then run untethered via a USB battery bank. We might have put it into an enclosure so it looks a little less suspect, but then again, there were certainly far more unusual devices than this to be seen at DerbyCon.

Of course, if you’re OK with just dumping the entire schedule out at once and letting the user sift through the mountain of bogus SSIDs themselves, [that’s even easier to accomplish](https://hackaday.com/2018/02/09/esp8266-broadcasts-memorial-wifi-spam/).

  
  
from Hackaday https://ift.tt/2pLlzuE  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)