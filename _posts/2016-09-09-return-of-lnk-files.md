---
title: 'Return of the LNK Files...'
date: 2019-10-28T14:53:00+01:00
draft: false
---

I wanted to put something scary together in time for Halloween; I was gonna go with a mullet wig, a la Joe Dirt, or maybe pass out cards with truly scary cards for those of us who are adulting, full time, such as, "...your septic field just rose and flowed down the yard into your porch...", or "...your teenager just go their license and want to drive home...".  You know, truly scary stuff.  However, from a #DFIR perspective (and maybe even a little bit of #threatintel) this just seemed a bit more fun and appropriate.  
  
A [recent Tweet thread from Nick Carr](https://twitter.com/ItsReallyNick/status/1185276463991406593) regarding the use of LNK files in developing threat intel caught my attention.  In that thread, Nick mentions learning "about LNK analysis as a DFIR and threat intel tool", and that's something I wholeheartedly agree with.  A great deal of value can be derived from LNK files...I've described them as "free money" in the past, due to the fact that an adversary sending an LNK file to a target is essentially giving away information about their infrastructure, particularly when data from LNK files is mapped across multiple campaigns.  
  
Links from Nick's Tweet:  
[2017 - Fin7](https://www.fireeye.com/blog/threat-research/2017/04/fin7-phishing-lnk.html)  
[2018 - Cozy Bear](https://www.fireeye.com/blog/threat-research/2018/11/not-so-cozy-an-uncomfortable-examination-of-a-suspected-apt29-phishing-campaign.html)  
  
Remember what I said about "multiple campaigns"?  If you take a look at the second blog post linked above, you'll see the statement:  
  
_The 2018 and 2016 LNK files are similar in structure and code, and contain significant metadata overlap, including the MAC address of the system on which the LNK was created._  
  
I'd had an opportunity to dig into the Cozy Bear LNK files a bit myself, as illustrated [here](https://windowsir.blogspot.com/2018/12/parsing-cozy-bear-lnk-file.html), and described [here](https://windowsir.blogspot.com/2019/01/lnk-toolmarks-revisted.html) (i.e., in an additional post regarding LNK file [toolmarks](https://windowsir.blogspot.com/2018/07/lnk-toolmarks.html)).  
  
Not long after Nick's tweet, I saw [this one](https://twitter.com/DbgShell/status/1187512157514153985) from ZwSetInformation, and was able to get a copy of the zipped archive, extract the LNK file and run it through my parser.  Not only did I see the individual bits of information exposed by the parser, but looking across the entirety of the information showed me the [toolmarks](https://windowsir.blogspot.com/2018/07/lnk-toolmarks.html) and provided an indication as to how the LNK file had been crafted.