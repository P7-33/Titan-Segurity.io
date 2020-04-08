---
title: 'What’s the most asinine technical requirement you’ve had to work into a design?'
date: 2019-10-08T06:17:00+01:00
draft: false
---

![](https://66.media.tumblr.com/avatar_abbe255953b7_512.pnj "Here’s one for the techies: what’s the most...")  

Here’s one for the techies: what’s the most asinine technical requirement you’ve ever had to work into a design?

I’ll go first:

I was doing development support on a bidirectional inventory reconciliation API, whereby either party’s system could pull a list of changes over the last 24 hours from the other party’s system. As part of the reconciliation process, the API used a global list of makes and models, whereby each manufacturer would be assigned a numeric ID; for example, the Acme Corporation might be manufacturer ID 1, Buy n Large might be manufacturer ID 2, and so forth. Each item in the inventory would be assigned a manufacturer ID, and every partner would use the same list of manufacturers to cross-reference those IDs.

This wasn’t a problem until we ran into a partner who happened to have their own entry in the list of manufacturers. I’m not sure whether the situation arose because of a technician who’d drunk the company Kool-Aid, or a brand manager who had just enough technical knowledge to be dangerous, but halfway through the integration process, they decided to throw a big ugly tantrum about the fact that they weren’t number one – or, more specifically, that their brand wasn’t assigned numeric ID 1 in the global list of manufacturers.

Explaining that **a.** the numeric ID wasn’t a value judgment and didn’t reflect anything other than the order in which the manufacturers had been inserted into the list, and **b.** arbitrarily shuffling the IDs around would cause huge headaches for all the other partners using the system did no good at all – they insisted they _had_ to be number one, or else they’d pull the plug on the whole partnership, and their contract was juuuuust big enough that management wasn’t willing to tell them to go whistle.

We ended up implementing a special hack _just for them_ that would silently rewrite all occurrences of their real manufacturer ID with 1 and all occurrences of manufacturer ID 1 with their own ID whenever data was sent to them, and vice versa whenever data from them was received. Then we just told them that we’d moved them to slot 1, and since they couldn’t see any differently on their end, they believed that’s what we’d actually done!

This may not be the strangest requirement I’ve ever worked on, but in terms of “most asinine” it definitely takes the cake.

How ‘bout you?  

  
  
from Hacker News https://ift.tt/2NlUtUZ