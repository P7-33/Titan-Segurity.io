---
title: 'Europe’s Galileo satellites going dark'
date: 2019-11-11T02:16:00+01:00
draft: false
---

Key details about the failure of Europe’s Galileo satellite system over the summer have started to emerge - and it’s not pretty.

While one key official has sought to blame a single individual for the system going dark, insiders warn that organizational chaos, excessive secrecy and some unusual self-regulation is as much to blame.

Combined with those problems, a battle between European organizations over the satellite system, and a delayed independent report into the July cock-up, means things aren’t looking good for Europe’s answer to America’s GPS system. A much needed shake-up may be on its way.

In mid-July, the agency in charge of the network of 26 satellites, the European Global Navigation Satellite Systems Agency (EGSA), warned of a “service degradation” but [assured everyone](https://www.theregister.co.uk/2019/07/15/galileo_outage/) that it would quickly be resolved.

It wasn’t resolved however, and six days later the system was not only still down but getting [increasingly inaccurate](https://www.theregister.co.uk/2019/07/17/europe_galileo_satellites_down/), with satellites reporting that they were in completely different positions in orbit than they were supposed to be - a big problem for a system whose entire purpose is to provide state-of-the-art positional accuracy to within 20 centimeters.

Billions of organizations, individuals, phones, apps and so on from across the globe simply stopped listening to Galileo. It’s hard to imagine a bigger mess, aside from the satellites crashing down to Earth.

But despite the outage and widespread criticism over the failure of those behind Galileo to explain what was going on and why, there has been almost no information from the various space agencies and organizations involved in the project.

### Inquiry

In September, it was [announced](https://ec.europa.eu/growth/content/kick-independent-inquiry-board-galileo_en) that there would be an independent inquiry into what happened - largely as a result of the lack of information. That inquiry’s “preliminary recommendations” were due in October - last month. So far, nothing.

Then, earlier this week, the man in overall charge of the system, the EC’s deputy director general in charge of space and defense industries Pierre Delsaux, [broke the silence](https://www.gpsworld.com/unacceptable-never-again-ec-deputy-on-galileo-outage/) at a breakfast meeting on the EU’s space policy in Washington DC no less.

In a Q&A session after the presentations, Delsaux was asked about press criticism - including from _El Reg_ - about the lack of communication and transparency and no apparent backup for the system. He blew up, insisting that the problem had been caused by a single individual who made an error and then failed to take the right action to fix it. The error was “unacceptable,” he told the audience before declaring “never again!”

Delsaux failed to address the backup question or the lack of communication or transparency. But other EC officials pushed back on that too, pointing out that a presentation had been given at a recent conference - something which led space observers scrambling to the [website](https://www.ion.org/publications/abstract.cfm?articleID=16900) of the Institute of Navigation Conference and its Miami conference in September.

One of those digging into what is going on has been Bert Hubert, a DNS expert who became intrigued by the Galileo mess this summer and decided to set up an independent resource that would monitor how the system is doing. This week Hubert [posted a report](https://berthub.eu/articles/posts/state-of-galileo-and-accident/) into what he’s discovered since undertaking that project, including some of the organizational and political problems at the heart of the Galileo.

### Ain't got the numbers

Among the most notable details surrounding Galileo are that of its 26 satellites in space, only 21 of them are functional - and there needs to be a minimum of 24 to achieve the accuracy that the system is designed to provide.

More satellites are due to go up next year but those launches look increasingly uncertain, especially with a bun fight going on between the European Space Agency (ESA) and the European Union (EU).

ESA built the Galileo system and is working on the updated version of the system, including new satellite additions. But thanks to European politics, [made worse](https://www.theregister.co.uk/2018/12/03/brexit_satellite/) by the UK’s Brexit process, the EU now wants to assert more control over the project.

The EU is planning to create a new European Space Agency, called EUSA, which will largely be a renaming of the existing Global Navigation Satellite System agency. Yet another space entity, GSA, will become the EU Agency for the Space Program, and the EC will soon have a new director general position in charge of the “defense industry and space.” In short, there are a lot of political maneuverings and that is causing all kinds of other problems.

### Rundown

In the middle of all that comes the complete failure of Europe’s flagship GPS system, Galileo, with no one clearly explaining how or why it happened. Here’s what we do know based on the report given at the Miami conference in September and additional details dug out by Hubert and others.

*   The vague reports from the Galileo team that everything was fine and no one should worry was built on the fact that the actual satellites themselves were all still working (well, apart the ones that aren’t) and were in their expected positions. In other words, the actual hardware in orbit was fine; it hadn’t been hit by anything, or gone flying off at tangents.
*   The actual problem almost certainly came from the software that undertakes the complex job of keeping the whole system in sync. It is no mean feat to keep the atomic clocks on the satellites accurate to within nanoseconds when everything in flying around in multiple orbits. There was some kind of anomaly in the reference time system while it was being upgraded - which is where the operator error came in - and that sent the whole system spinning.
*   For reasons that remain unclear, the backup system was not available, meaning that it wasn’t possible to simply rollback to the previous version. As a result, things got more and more inaccurate.
*   Additionally, it appears that at the time everything went awry, the system was not configured in the normal way so engineers had a hard time figuring out how to get it all back working together.
*   Eventually the decision was made that it has taken so long to figure out what had gone wrong that the best solution was to effectively reboot the entire system. Which is what they did. But because it is a fiendishly complex setup, that reboot took several days to complete.

So those are the best details we have about what actually happened. But there remains precious little information about how and why it all went so wrong in the first place and why adequate recovery systems weren’t in place.

### Complexity

It looks increasingly likely that the complex set of organizations that are responsible for operating and developing different parts of the system are a significant part of the problem. It became immediately apparent when things went wrong that clear communication within Galileo does not exist and no doubt there was a significant amount of finger-pointing among the various agencies that only made things worse.

![galileo](https://regmedia.co.uk/2019/11/08/galileo-org-chart.jpg "galileo")

A chart showing just some of Galileo operations & control. Pic: Bert Hubert

On top of that, there is a question over whether one organization - GMV - has an additional degree of responsibility for the whole mess. GMV runs no less than three different parts of the Galileo structure.

But most notably in this case, it runs the part responsible for generating the data that went awry in this case - called ephemerides, the Galileo Orbit Synchronization Processing Facility (OSPF). In addition to generating ephemerides, GMV was also selected as the organization responsible for independently reviewing and monitoring that same data - the Galileo Integrity Processing Facility (IPF).

![gps](https://regmedia.co.uk/2016/04/29/galileo_satellite_teaser.jpg?x=174&y=115&crop=1)

Galileo, Galileo, Galileo, where to go? Navigation satellite signals flip from degraded to full TITSUP\* over span of four days
-------------------------------------------------------------------------------------------------------------------------------

[READ MORE](https://www.theregister.co.uk/2019/07/15/galileo_outage/)

Did the fact that the same company was monitoring itself in part responsible for the collapse of the Galileo system?

As for public communication, no one in the satellite of organizations around Galileo felt they were authorized to talk about what was going on, leaving it up to EC officials - none of whom knew what was going on either. In other words, a classic clusterfuck of communication.

We still don’t know exactly what happened but hopefully the independent inquiry will make its report available soon. It is supposed to be finished by the end of the year.

In the meantime, a dangerous amount of political maneuvering means all the engineers are keeping their heads down. Which is a shame because by all accounts, there is a lot of good work going on, not helped by organizational silos.

In short, Galileo is a classic European venture: a great idea with talented people that has turned into a bureaucratic mess in which no one wants to take the blame for problems caused by unnecessary organizational complexity. ®

Sponsored: [Technical Overview: Exasol Peek Under the Hood](https://go.theregister.co.uk/tl/1858/-7802/technical-overview-exasol-peek-under-the-hood?td=wptl1858)

  
  
from Hacker News https://ift.tt/2Q0UZJm