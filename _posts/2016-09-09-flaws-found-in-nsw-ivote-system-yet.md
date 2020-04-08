---
title: 'Flaws found in NSW iVote system yet again'
date: 2019-11-14T03:59:00+01:00
draft: false
---

![](https://zdnet4.cbsistatic.com/hub/i/r/2016/12/12/353e2b3c-635e-4b8f-a1c6-adcf414a8d8f/thumbnail/770x578/2ca234e2a7c350005312d3c36933f888/istock-472227510.jpg "Flaws found in NSW iVote system yet again | ZDNet")  

The "Days since last vulnerability found" indicator for the iVote system used in New South Wales' elections was reset to zero on Wednesday thanks to a new research note from University of Melbourne cryptographer Dr Vanessa Teague.

Or rather, the software vendor was notified 45 days earlier to keep with the terms of the source code access agreement while the rest of us found out today.

iVote was purchased from Scytl Australia, a subsidiary of Barcelona-based election technology vendor Scytl Secure Electronic Voting, and is based on the system used by SwissPost.

In March this year, Teague and her colleagues Sarah Jamie Lewis and Olivier Pereira [found a flaw](https://www.zdnet.com/article/nsw-electoral-commission-claims-physical-separation-mitigates-swiss-voting-flaw/) in the proof used by SwissPost system to prevent electoral fraud.

Later that month, they detailed a [second flaw](https://pursuit.unimelb.edu.au/articles/what-a-second-flaw-in-switzerland-s-svote-means-for-nsw-s-ivote) that could be exploited to result in a tampered election outcome.

NSWEC [claimed it was safe](https://www.zdnet.com/article/nsw-electoral-commission-claims-it-is-safe-from-second-swissvote-flaw/) from the second flaw, and had patched the first.

**See also: [Moscow's blockchain voting system cracked a month before election](https://www.zdnet.com/article/moscows-blockchain-voting-system-cracked-a-month-before-election/)**

In July, NSWEC ordered Scytl to [release parts of the source code](https://www.zdnet.com/article/nsw-ivote-source-code-released-for-researchers-to-poke-around-in/) in a bid to prove it contained no further vulnerabilities.

Vulnerabilities have now been found.

"I examined the decryption proof and, surprise, it can easily be faked while passing verification," [Teague tweeted](https://twitter.com/VTeagueAus/status/1194692550268837889) on Wednesday morning.

"This exposes NSW elections to undetectable electoral fraud by trusted insiders & suppliers, people who guessed the passwords of the trusted insiders, people who successfully phished the trusted insiders, etc."

Teague's analysis is detailed in the 8-page _[Faking an iVote decryption proof](https://people.eng.unimelb.edu.au/vjteague/iVoteDecryptionProofCheat.pdf)_ \[PDF\].

"The proof of correct decryption specified in the iVote protocol description is susceptible to the same attack we identified already in the equivalent part of the SwissPost/Scytl system," she wrote.

"This could, for instance, be used by a cheating decryption service to change valid votes into nonsense that would not be counted."

Teague's analysis is based on the protocol description however, rather than on an analysis of the code itself.

"Since the error affects the verification process, it is the specification rather than the current implementation that defines the system's security anyway," she wrote.

"If iVote had independent verification, it would be based on an independent implementation of the verification spec, not on running Scytl's code."

### Scytl thanks Teague for 'responsible disclosure'

In a statement released on Wednesday, Scytl thanked Teague for participating in the [Scytl Online Voting Source Code Review Program](https://www.scytl.com/en/AccessiVote2019/) and for reporting her findings "via the responsible disclosure reporting procedure".

"The publication of the source code is part of Scytl's commitment towards transparency and continuous improvement," said Sam Campbell, Scytl's general manager for Asia-Pacific.

"I'm pleased that Associate Professor Teague has chosen to participate in the program supplying a paper to Scytl and the New South Wales Electoral Commission explaining in detail her finding."

**Say what?: [Australia Post details plan to use blockchain for voting](https://www.zdnet.com/article/australia-post-details-plan-to-use-blockchain-for-voting/)**

This is the first disclosure made under the review program and "has resulted in an update of the documentation related to the iVote system".

So far, more than 60 people have chosen to participate in the program, the company said.

### But do we really need e-voting anyway?

Your writer agrees that Scytl's open source code review significantly increases the transparency of the state's electronic voting process, but remains to be convinced that it's the right way to go.

As I wrote in the wake of Australia's 2016 federal election, e-voting is [the wrong answer to the wrong question](https://www.zdnet.com/article/e-voting-is-still-the-wrong-answer-to-the-wrong-question/).

Transparency is the tricky bit.

"Our paper voting system is easy to understand. Anyone with working eyesight and who can read and count can scrutineer the process. No special skills are required," I wrote.

"With electronic voting, whether online or on stand-alone voting machines, everything happens inside the invisible cave of computer memory. It's impossible to see what's going on at the time the votes are tallied. How can you know that the votes were counted correctly? You just have to trust the system."

Or as [Teague tweeted](https://twitter.com/VTeagueAus/status/1194692567339655168):

> tl;dr
> 
> 1.  Run elections on paper
> 2.  If you can't, use an end-to-end verifiable system
> 3.  If you can't, make the source code openly available before the election
> 4.  If you can't, fix the bugs that you are told about
> 5.  If you can't, be honest about them
> 6.  If you can't, goto 1

Give us the Pencils of Democracy every time.

### Related Coverage

**[NSW iVote source code released for researchers to poke around in](https://www.zdnet.com/article/nsw-ivote-source-code-released-for-researchers-to-poke-around-in/)**

Scytl has published components of the source code used by the NSW Electoral Commission following claims there were two flaws in the same system used in Switzerland.

**[NSW Electoral Commission claims it is safe from second SwissVote flaw](https://www.zdnet.com/article/nsw-electoral-commission-claims-it-is-safe-from-second-swissvote-flaw/)**

Researchers have found another flaw in the SwissVote system, while the NSW Electoral Commission is once again confident the issue is not relevant to the iVote system.

**[NSW Electoral Commission claims physical separation mitigates Swiss voting flaw](https://www.zdnet.com/article/nsw-electoral-commission-claims-physical-separation-mitigates-swiss-voting-flaw/)**

Using an air-gapped machine means the flaws discovered in the Swiss system do not impact NSW, the state electoral commission has claimed.

**[NSW Budget: State continues focus on digital transformation](https://www.zdnet.com/article/nsw-budget-state-continues-focus-on-digital-transformation/)**

Upgrading legacy infrastructure and transforming government delivery were high on the agenda of the New South Wales government in delivering its 2017-18 Budget.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2OdBsT9