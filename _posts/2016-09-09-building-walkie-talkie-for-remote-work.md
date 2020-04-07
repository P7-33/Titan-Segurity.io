---
title: 'Building a walkie-talkie for remote work'
date: 2020-01-24T03:35:00+01:00
draft: false
---

Pragli is a virtual office for remote teams. One of its key features is quick, synchronous audio/video communication between teammates. This helps teammates communicate faster and build closeness and culture.

Pragli's A/V communication is inspired by a walkie-talkie, rather than a phone call. In this article, I'll explain why we chose walkie-talkie and how we made it work well in Pragli.

Benefits of walkie-talkie vs a phone Call
-----------------------------------------

Walkie-talkie:

*   **Context**: the sender gets a chance to explain why they are calling before the other side chooses whether or not to respond
*   **Speed**: walkie-talkies are fast because there's no waiting for an accept to start speaking; calls take longer to get to the first word out
*   **Success in high pressure scenarios**: walkie-talkies, [first used during WWII](https://en.wikipedia.org/wiki/Walkie-talkie), [continue to be used in emergency scenarios](https://www.sfchronicle.com/california-wildfires/article/In-disaster-prone-California-emergency-sirens-14938016.php), albeit in higher-tech radio or satellite formats

![](https://pragli.com/blog/content/images/2020/01/wt.jpg)

A walkie-talkie demo in 1942 by the US military

Phone Call:

*   **Scale**: click-to-send is annoying for long conversations; people don't want to press a button every time they speak in longer interactions
*   **Less Distracting**: with a walkie-talkie, you have to hear the person out - with a phone call, you can deny before they say anything
*   **Comes naturally**: phones are more common and prevalent than walkie-talkies, so people are more used to phone call analogies

We designed Pragli to facilitate quick, meaningful conversations, so the context and speed of a walkie-talkie felt right to us. But how could we make walkie-talkie interactions scale, reduce distraction, and feel natural?

Version 1: Talk first, accept later
-----------------------------------

Initially, we considered a pseudo-voicemail system. The "caller" would send a voice message to the "receiver," who would then choose whether or not to accept the conversation.

This solved the issue of scalability - once the conversation was accepted, it essentially became a call. However, it didn't reduce distraction and didn't feel natural. Also, it felt slower, since the voicemail wasn't a synchronous call.

Version 2: Mute-by-default
--------------------------

We refined our design by moving to an opt-out design rather than opt-in.

The caller starts a conversation with the receiver. The receiver is muted by default to protect their privacy, while the caller starts talking immediately. The receiver unmutes themselves to start speaking, or they leave the conversation.

![](https://pragli.com/blog/content/images/2020/01/start.gif)

This maximizes the walkie-talkie benefits. The caller **immediately** speaks and provides **context** on the subject matter at hand. It also **scales** well, as it turns into a call once the receiver unmutes themselves.

It **feels natural** for the caller, since they just click on someone to start talking with them. However, it sometimes feels very abrupt for the receiver when they are either a) having another meeting or b) focussing on deep work. In other words, it is still **distracting**.

We knew we were onto something good, since the interactions felt so much more natural and quick than before. But we needed to do more to make it feel less distracting.

Solving Distraction: Presence + Statuses + Calendar
---------------------------------------------------

The key to solving distraction was to add additional context on whether the person was open to receiving a call.

1.  First, we added two forms of presence detection to show whether or not the person was at their desk. That way, the caller knows beforehand that they are unlikely to reach the person.  
      
    
2.  Then, we added manual statuses. Statuses allow users to say that they're "out for a walk," "in another meeting," or simply "focussing - do not disturb."  
      
    Manual statuses work great when users remembered to use them. But it feels heavyweight to constantly set your status. Users frequently forget to actually set them, leading to distracting interactions.  
      
    
3.  Finally, we added Google and Outlook calendar integrations to automatically set status. Calendars record most meetings, personal events like dentist appointments, and increasingly dedicated "focus time." Once the calendar is integrated, Pragli automatically warns away callers during events. This solves most of the issues with manual statuses.

![](https://pragli.com/blog/content/images/2020/01/cal-wt.gif)

Once Pragli supported all of this functionality, our walkie-talkie implementation felt a lot less distracting. People were connecting in a way that wasn't disruptive.

Results
-------

Pragli's walkie-talkie implementation provides:

*   **Speed**: click on someone to start a conversation, and you can immediately speak with them
*   **Context**: no more wondering "What are they calling me about?" - the caller speaks immediately
*   **Privacy**: the receiver is muted by default
*   **Scale**: turns into a call, and therefore scales into longer conversation
*   **Intuitiveness**: it's not quite as intuitive as a phone call for some users, but it's obvious how to start a conversation and users pretty quickly learn the nuances of it. We still have some more work to do here.
*   **Low Distraction**: users can now automatically (via calendar) or manually prevent distraction and presence detection. We will continue to add more social signals to further lower distraction.

Interested in learning about some of our other social signals? Read about [our framework for social signals](https://pragli.com/blog/our-framework-for-adding-social-signals/), learn about [our Spotify integration](https://pragli.com/blog/using-spotify-to-communicate-status/), or dive deeper into [our calendar integration](https://pragli.com/blog/social-signals-3-using-google-calendar-to-signal-availability/).

Give the walkie-talkie for remote work a try - it's free! [Try out Pragli](https://pragli.com/signin).

  
  
from Hacker News https://ift.tt/30Qkwbe