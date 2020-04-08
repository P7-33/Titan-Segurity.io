---
title: 'Looking Back at the Snowden Revelations'
date: 2019-09-25T07:52:00+01:00
draft: false
---

Edward Snowden recently [released his memoirs](https://www.engadget.com/2019/09/17/us-edward-snowden-book-permanent-record-lawsuit-memoir/?guccounter=1&guce_referrer=aHR0cHM6Ly93d3cuZ29vZ2xlLmNvbS8&guce_referrer_sig=AQAAAEN9nGGD8_27xhxxu9D07hop95uTL4kNHiDKqIAFI98sz6PjReV6bEUjHmjmyUfWp0C8WdHb91Q7I45x33jODGhmgyFp8XsalfmO-HbDOedCdG6LA7qO8LGpJpC1Fdi7j5FknMe3secd0pfBxyPIfhjE4SgkhYZ2gsjDyTx7OtQA). In some parts of the Internet, this has rekindled an ancient debate: namely, _was it all worth it?_ Did Snowden’s leaks make us better off, or did Snowden just embarass us and set back U.S. security by decades? Most of the arguments are so familiar that they’re boring at this point. But no matter how many times I read them, I still feel that there’s something important missing.

It’s no coincidence that _this is a cryptography blog_, which means that I’m not concerned with the same things as the general public. That is, I’m not terribly interested in debating the value of whistleblower laws (for some of that, see this excellent [Twitter thread](https://threadreaderapp.com/thread/1173278854007394307.html) by Jake Williams). Instead, when it comes to Snowden’s leaks, I think the question we should be asking ourselves is very different. Namely:

_What did the Snowden leaks tell us about modern surveillance capabilities? And what did we learn about our ability to defend against them?_

And while the leaks themselves have receded into the past a bit — and the world has continued to get more complicated — the _technical_ concerns that Snowden alerted us to are only getting more salient.

### Life before June 2013

It’s difficult to believe that the Snowden revelations began over six years ago. It’s also easy to forget how much things have changed in the intervening years.

Six years ago, vast portions of our communication were done in plaintext. It’s hard to believe how bad things were, but back in 2013, Google was one of the only major tech companies who had [deployed HTTPS in its services by default](https://www.wired.com/2011/11/mf_soghoian/), and even there they had some major exceptions. Web clients were even worse. These graphs ([source](https://transparencyreport.google.com/https/overview?hl=en) and [source](https://letsencrypt.org/stats/#percent-pageloads)) don’t cover the whole time period, but they give some of the flavor:

![HTTPSGraph](https://matthewdgreen.files.wordpress.com/2019/09/httpsgraph.png?w=700)

![HTTPSFirefox](https://matthewdgreen.files.wordpress.com/2019/09/httpsfirefox.png?w=700)

Outside of HTTPS, the story was even worse. In 2013 the vast majority of text messages were sent via unencrypted SMS/MMS or poorly-encrypted IM services, which were a privacy nightmare. Future developments like the inclusion of [default end-to-end encryption in WhatsApp](https://www.independent.co.uk/life-style/gadgets-and-tech/news/whatsapp-update-encryption-end-to-end-messages-security-government-privacy-a6970101.html) were years away. Probably the sole (and surprising) exception to was Apple, which had been ahead of the curve in deploying end-to-end encryption. This was largely counterbalanced by the tire fire that was Android back in those days.

But even these raw facts don’t tell the full story.

What’s harder to present in a chart is how different attitudes were towards surveillance back before Snowden. The idea that governments would conduct large-scale interception of our communications traffic was a point of view that relatively few “normal people” spent time thinking about — it was mostly confined to security mailing lists and X-Files scripts. Sure, everyone understood that government surveillance was a thing, _in the abstract._ But actually talking about this was bound to make you look a little silly, even in paranoid circles.

That these concerns have been granted _respectability_ is one of the most important things Snowden did for us.

### So what did Snowden’s leaks really tell us?

The brilliant thing about the Snowden leaks was that he didn’t tell us much of anything. He showed us. Most of the revelations came in the form of a Powerpoint slide deck, the misery of which somehow made it all more real. And despite all the revelation fatigue, the things he showed us were remarkable. I’m going to hit a few of the highlights from my perspective. Many are cryptography-related, just because that’s what this blog is about. Others tell a more basic story about how vulnerable our networks are.

### **“Collect it all”**

Prior to Snowden, even surveillance-skeptics would probably concede that, yes, the NSA collects data on specific targets. But even the most paranoid observers were shocked by the sheer scale of what the NSA was actually doing out there.

The Snowden revelations detailed several programs that were so astonishing in the breadth and scale of the data being collected, the only real limits on them were caused by technical limitations in the NSA’s hardware. Most of us are familiar with the famous examples, like nationwide phone metadata collection. But it’s the bizarre, obscure leaks that really drive this home. For example:

**“Optic Nerve”.** From 2008-2010 the NSA and GCHQ collected [millions of still images from every Yahoo! Messenger webchat stream](https://www.theguardian.com/world/2014/feb/27/gchq-nsa-webcam-images-internet-yahoo), and used them to build a massive database for facial recognition. The collection of data had no particular rhyme or reason — _i.e.,_ it didn’t target specific users who might be a national security threat. It was just… everything. Don’t believe me? Here’s how we know how indiscriminate this was: the program didn’t even necessarily target faces. It got… other things:

![Optic.png](https://matthewdgreen.files.wordpress.com/2019/09/optic.png?w=700)

**MYSTIC/SOMALGET.** In addition to collecting massive quantities of Internet metadata, the NSA [recorded the full audio every cellular call made in the Bahamas](https://theintercept.com/2014/05/19/data-pirates-caribbean-nsa-recording-every-cell-phone-call-bahamas/). (Note: this is not simply calls to the Bahamas, which might be sort of a thing. They abused a law enforcement access feature in order to record all the mobile calls made within the country.) Needless to say, the Bahamian government was not party to this secret.

**MUSCULAR.** In case anyone thought the NSA avoided attacks on American providers, a series of leaks in 2014 [documented that the NSA had tapped the internal leased lines](https://www.washingtonpost.com/world/national-security/nsa-infiltrates-links-to-yahoo-google-data-centers-worldwide-snowden-documents-say/2013/10/30/e51d661e-4166-11e3-8b74-d89d714ca4dd_story.html) used to connect Google and Yahoo datacenters. This gave the agencies access to vast and likely indiscriminate access to torrents of data on U.S. and European users, information was likely above and beyond the data that these companies already shared with the U.S. under existing programs like [PRISM](https://en.wikipedia.org/wiki/PRISM_(surveillance_program)). This leak is probably most famous for this slide:

![addedremoved](https://matthewdgreen.files.wordpress.com/2019/09/addedremoved.png?w=700&h=491)

**Yahoo!, post-Snowden.** And in case you believe that this all ended after Snowden’s leaks, we’ve learned even more disturbing things since. For example, in 2015, Yahoo got caught installing what has been described as a “rootkit” that [scanned every single email in its database for specific selectors](https://www.reuters.com/article/us-yahoo-nsa-exclusive-idUSKCN1241YT), at the request of the U.S. government. This was so egregious that the company didn’t even tell it’s CISO, who left the next week. In fact, we know a lot more about Yahoo’s [collaboration during this time period](https://www.theguardian.com/world/2014/sep/11/yahoo-nsa-lawsuit-documents-fine-user-data-refusal), thanks to Snowden.

These examples are not necessarily the worst things we learned from the Snowden leaks. I chose them only to illustrate how completely indiscriminate the agency’s surveillance really was. _And not because the NSA was especially evil, but just because it was easy to do._ If you had any illusions that this data was being carefully filtered to exclude capturing data belonging to U.S. citizens, or U.S. companies, the Snowden leaks should have set you straight.

### SIGINT Enabling

The Snowden leaks also helped shatter a second illusion: the idea that the NSA was on the side of the angels when it comes to making the Internet more secure. I’ve [written about this plenty](https://blog.cryptographyengineering.com/2013/09/06/on-nsa/) on this blog (with sometimes [exciting results](https://www.theguardian.com/world/2013/sep/10/johns-hopkins-dean-apologises-for-blog)), but maybe this needs to be said again.

One of the most important lessons we learned from the Snowden leaks was that the NSA very much prioritizes its surveillance mission, to the point where it is willing to actively insert vulnerabilities into encryption products and standards used on U.S. networks. And this kind of thing wasn’t just an occasional crime of opportunity — the agency spent $250 million per year on a program called the [SIGINT Enabling Project](https://www.documentcloud.org/documents/784285-sigint-enabling-project). Its goal was, basically, to bypass our commercial encryption at any cost.

![sigint](https://matthewdgreen.files.wordpress.com/2019/09/sigint.png?w=700)

This kind of sabotage is, needless to say, something that not even the most paranoid security researchers would have predicted from our own intelligence agencies. Agencies that, ostensibly have a mission to protect U.S. networks.

![enabling](https://matthewdgreen.files.wordpress.com/2019/09/enabling.png?w=700)

The Snowden reporting not only revealed the existence of these overall programs, but they uncovered a lot of unpleasant specifics, leading to a great deal of follow-up investigation.

For example, the Snowden leaks contained specific [allegations of a vulnerability in a NIST standard called Dual EC](https://blog.cryptographyengineering.com/2013/09/18/the-many-flaws-of-dualecdrbg/). The possibility of such a vulnerability had previously been noted by U.S. security researchers Dan Shumow and Niels Ferguson a few years earlier. But despite making a reasonable case for re-designing this algorithm, those researchers (and others) were basically [brushed off by the “serious” people at NIST](https://csrc.nist.gov/csrc/media/projects/crypto-standards-development-process/documents/dualec_in_x982_and_sp800-90.pdf).

![schneier](https://matthewdgreen.files.wordpress.com/2019/09/schneier.png?w=300&h=240)

The Snowden documents changed all that. The leaks were a devastating embarassment to the U.S. cryptographic establishment, and led to some actual changes. Not only does it appear that the NSA deliberately backdoored Dual EC, it seems that they did so (and used NIST) in order to deploy the backdoor into U.S. security products. Later investigations would show that [Dual EC was present in software by RSA Security](https://blog.cryptographyengineering.com/2017/12/19/the-strange-story-of-extended-random/) (allegedly because of a [secret contract with the NSA](https://www.reuters.com/article/us-usa-security-rsa/exclusive-secret-contract-tied-nsa-and-security-industry-pioneer-idUSBRE9BJ1C220131220)) and in firewalls made by [Juniper Networks.](https://kb.juniper.net/InfoCenter/index?page=content&id=KB28205&actp=METADATA)

(Just to make everything a bit more horrifying, Juniper’s Dual EC backdoor would later [be hijacked and turned against the United States by unknown hackers](https://blog.cryptographyengineering.com/2015/12/22/on-juniper-backdoor/) — illustrating exactly how reckless this all was.)

And finally, there are the _mysteries_. Snowden slides indicate that the NSA has been decrypting SSL/TLS and IPSec connections at vast scale. Even beyond the SIGINT Enabling-type sabotage, this raises huge questions about _what the hell is [actually going on here](https://blog.cryptographyengineering.com/2013/12/03/how-does-nsa-break-ssl/)._ There are [theories](https://blog.cryptographyengineering.com/2015/05/22/attack-of-week-logjam/). These may or may not be correct, but at least now people are thinking about them. At very least, it’s clear that something is very, very wrong.

[![bullrun](https://matthewdgreen.files.wordpress.com/2019/09/bullrun.png?w=300&h=190)](https://www.eff.org/document/20141228-spiegel-gchq-presentation-bullrun-programs-decryption-capabilities)  
[![50522-nsa_combined](https://matthewdgreen.files.wordpress.com/2015/05/50522-nsa_combined.png?w=300&h=157)](https://www.eff.org/document/20141228-spiegel-gchq-presentation-bullrun-programs-decryption-capabilities)

### Have things improved?

This is the $250 million question.

Some of the top-level indicators are surprisingly healthy. HTTPS adoption has taken off like a rocket, driven in part by Google’s willingness to use it as a signal for [search rankings](https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html) — and the rise of free Certificate Authorities like [LetsEncrypt](https://letsencrypt.org/). It’s possible that these things would have happened eventually without Snowden, but it’s less likely.

End-to-end encrypted messaging has also taken off like a rocket, largely due to adoption by WhatsApp and a host of relatively new apps. It’s reached the point where law enforcement agencies have begun to freak out, as the slide below illustrates.

![e2e](https://matthewdgreen.files.wordpress.com/2019/09/e2e.png?w=700)

Slightly dated numbers, source: CSIS (or this [article](https://www.finextra.com/blogposting/16329/secure-messaging-for-financial-institutions))

Does Snowden deserve credit for this? Maybe not directly, but it’s almost certain that concerns over the surveillance he revealed did play a role. (It’s also worth noting that this adoption is _not_ evenly distributed across the globe.)

It’s also worth pointing out that _at least in the open source community_ the quality of our encryption software has [improved](http://events17.linuxfoundation.org/sites/events/files/slides/linuxcon-v2.pdf) [enormously](https://github.com/google/boringssl), largely due to the fact that major companies made well-funded efforts to harden their systems, in part as a result of serious flaws like Heartbleed — and in part as a response to the company’s own concerns about surveillance.

It might very well be that the NSA has lost a significant portion of its capability since Snowden.

### The future isn’t American

I’ve [said this before](https://blog.cryptographyengineering.com/2015/08/16/the-network-is-hostile/), as have many others: even if you support the NSA’s mission, and believe that the U.S. is doing everything right, it doesn’t matter. Unfortunately, the future of surveillance has very little to do with what happens in Ft. Meade, Maryland. In fact, the world that Snowden brought to our attention isn’t necessarily a world that Americans have much say in.

As an example: today the U.S. government is in the midst of forcing a [standoff with China](https://www.apnews.com/e79cdf51aca4468699139c39a1105685) over the global deployment of [Huawei’s 5G wireless networks](https://techcrunch.com/2019/06/25/huawei-wins-5g-contracts/) around the world. This is a complicated issue, and financial interest probably plays a big role. But global security also matters here. This conflict is perhaps the clearest acknowledgement we’re likely to see that our own government knows how much control of communications networks really matters, and our inability to secure communications on these networks could really hurt us. This means that we, here in the West, had better get our stuff together — or else we should be prepared to get a taste of our own medicine.

If nothing else, we owe Snowden for helping us to understand how high the stakes might be.

  
  
from Hacker News https://ift.tt/2lsuOye