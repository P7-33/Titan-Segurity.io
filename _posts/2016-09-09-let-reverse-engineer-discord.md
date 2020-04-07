---
title: 'Let''s Reverse Engineer Discord'
date: 2020-01-13T06:47:00+01:00
draft: false
---

![](https://miro.medium.com/max/1000/1*AAHmP58hZKQ4IiRgfJPQ5Q.png "Let’s Reverse Engineer Discord - Tenable TechBlog - Medium")  

Let’s Reverse Engineer Discord
==============================

_Quick note: This research was a joint effort between_ [_Joseph Bingham_](https://medium.com/u/d0e26492c343?source=post_page-----1976773f4626----------------------) _and_ [_David Wells_](https://medium.com/u/5f38fc159ffd?source=post_page-----1976773f4626----------------------)_._

The Discord chat app was the target of our latest research project. While this blog will not be covering any exploits, we will share what we learned about the Discord call protocol, and share our insights into the audio/video privacy of Discord and how we were able to prove Discord audio/video calls are decrypted and inspected by Discord servers.

Reverse Engineering Discord
===========================

The Audio/Video component of the Discord desktop client, which allows calls and screen shares between attendees, was our main area of focus. For this, we reverse engineered the appropriate components to understand the voice call protocol in order to mock audio/video calls ourselves. From our research, we ended up writing a simple python client that does just this: [https://github.com/tenable/DiscordClient](https://github.com/tenable/DiscordClient). Most of the logic we investigated was in “discord\_voice.node“; a native module that’s loaded in Discord to handle audio/video streaming. We found that the Discord client actually interacts with four different servers in order to establish a two-way call with a desired client. As you can see in the illustration below, authentication is started with the discord API over HTTPS and various tokens (or secret\_keys) are extracted from subsequent servers to maintain a chain of trust all the way up to the final server, which is the server that handles encrypted call/video data streaming.

Below shows an RTP packet captured from a Discord client that is sending audio data. In this RTP payload you can see there is encrypted audio data (Salsa20 encrypted), an authentication tag, and a packet sequence number (used for nonce).

If we decrypt the payload section, we can see the audio data, which we found to be [Opus codec](https://opus-codec.org/). In the instance of video streaming, this would be H.264 MPEG codec data.

Once we grasped the server interactions, protocol, and encryption methods, we were able to develop a minimal “mock” discord client, which allowed us to initiate calls and properly fuzz protocol data to find bugs. While we won’t be going over bugs, one interesting side effect we noticed was evidence that Discord servers decrypt and inspect all user’s audio/video data server-side in real-time.

Discord Inspects Users’ Traffic
===============================

As previously illustrated, all audio/video streaming traffic goes through Discord servers. The [Salsa20](https://en.wikipedia.org/wiki/Salsa20) encryption key for encrypting audio/video data was derived from these servers. In our research, we found that the traffic was being decrypted server-side and repackaged for the client. In addition to discord decrypting user data, we also found strong evidence that Discord inspects the compressed codec data.

**Our Testing**

This was tested by crafting a malformed audio packet from our ”mock” Discord client (Client 1), properly encrypting it, and sending it along with our existing mock audio stream. All “valid” audio data passed through the server to Client 2, however, we witnessed the server drop the malformed audio packet (which were encrypted), thus not delivering it to Client 2.

Below, we can see our mock Discord client sending a valid RTP one-byte extension header along with Opus audio data to our remote Discord client.

After encrypting the entire stream and sending with an RTP header, we can see this packet received and decrypted by our remote Discord client which is in a debugger.

Back in our mock Discord client, we now malformed this data by changing the length field byte in the RTP one-byte extension header with a length larger than expected.

Sending this encrypted data over to our remote Discord client, we no longer can see the packet received under debugger.

This effect can also be seen in Wireshark, as an insufficient amount of packets even make it to our remote Discord client, which certainly means there is some MITM decryption, validation, and dropping occurring at Discord servers.

We tested this malformed audio packet dispatch at various points during a voice call and consistently watched all malformed audio packets dropped by the server, which means that Discord servers are actively decrypting and inspecting all audio/video communications in real-time and not just some.

**Final Thoughts**
==================

It is entirely possible that Discord has valid design-driven reasons for inspecting audio/video traffic. The server may be validating call quality or enforcing content guidelines to protect users.

Whatever the reason, it must be very important due to the latency and computational overhead for Discord servers to decrypt and inspect all audio/video communications in real-time ([Two and a half million concurrent voice users a day](https://blog.discordapp.com/how-discord-handles-two-and-half-million-concurrent-voice-users-using-webrtc-ce01c3187429)). Discord provides a policy regarding [user privacy](https://discordapp.com/privacy), which explains it may capture “transient VOIP data”. While it’s a bit unclear what this may entail, our research shows that this “data” includes all voice and video data. Even if Discord’s original intention was to hold user privacy with high regard, they have recently finished their series F funding raising more than $150M from [several diverse corporations](https://pitchbook.com/profiles/company/54805-51) whose intentions with the platform are unknown.

  
  
from Hacker News https://ift.tt/2R9vIeX