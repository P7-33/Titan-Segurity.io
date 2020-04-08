---
title: 'DirectAccess planning question and answers'
date: 2019-11-09T18:17:00+01:00
draft: false
---

Windows Server 2016 Security, Certificates, and Remote Access Cookbook
======================================================================

[](https://www.blogger.com/u/3/null)One of the most confusing parts about setting up DirectAccess is that there are many different ways to do it. Some are good ideas, while others are not. Before we get rolling with recipes, we are going to cover a series of questions and answers to help guide you towards a successful DA deployment. One of the first questions that always presents itself when setting up DirectAccess is _[](https://www.blogger.com/u/3/null)How do I assign IP addresses to my DA server?_[](https://www.blogger.com/u/3/null). This is quite a loaded question because the answer depends on how you plan to implement DA, which features you plan to utilize, and even upon how secure you believe your DA server to be. Let me ask you some questions, pose potential answers to those questions, and discuss the effects of making each decision.

*   Which client operating systems can connect using DirectAccess?

[](https://www.blogger.com/u/3/null)Windows 7 Ultimate, Windows 7 Enterprise, Windows 8.x Enterprise, and Windows 10 Enterprise or Education. You'll notice that the Professional SKU is missing from this list. That is correct; Windows 7, Windows 8, and Windows 10 Pro do _not_ [](https://www.blogger.com/u/3/null)contain the DirectAccess connectivity components. Yes, this does mean that Surface Pro tablets cannot utilize DirectAccess out-of-the-box. However, I have seen many companies now install Windows 10 Enterprise onto their Surface tablets, effectively turning them into _Surface Enterprises_. This works[](https://www.blogger.com/u/3/null) well and does indeed enable them to be DA clients. In fact, I am currently typing this text on a DirectAccess connected Surface _Pro turned Enterprise_ tablet.

*   Do I need one or two NICs on my DirectAccess server?

[](https://www.blogger.com/u/3/null)Technically, you could set up either way. In practice, however, it really is designed for dual-NIC implementation. Single NIC DirectAccess works[](https://www.blogger.com/u/3/null) okay sometimes to establish a proof-of-concept to test out the technology, but I have seen too many problems with single NIC implementations in the field to ever recommend it for production use. Stick with two network cards, one facing the internal network and one facing the Internet.

*   Do my DirectAccess servers have to be joined to the domain?

Yes.

*   Does DirectAccess have site-to-site failover capabilities?

[](https://www.blogger.com/u/3/null)Yes, though only Windows 8.x and 10 client computers can take advantage of it. This functionality is called Multi-Site DirectAccess. Multiple DA servers that are spread out geographically can be joined together in a multi-site array. Windows 8 and 10 client computers keep track of each individual entry point and are able to swing between them as needed or at user preference. Windows 7 clients do not have this capability and will always connect through their primary site.

*   What are these things called 6to4, Teredo, and IP-HTTPS that I have seen in the Microsoft documentation?

[](https://www.blogger.com/u/3/null)6to4, Teredo, and IP-HTTPS are all IPv6 transition tunneling protocols. All DirectAccess packets that are moving across the Internet between a DA client and DA server are IPv6 packets. If your internal network is IPv4, then when those packets reach the DirectAccess server they get turned down into IPv4 packets by some special components called DNS64 and NAT64. While these functions handle the translation of packets from IPv6 into IPv4 when necessary inside the corporate network, the key point here is that all DirectAccess packets that are traveling over the Internet part of the connection are always IPv6. Since the majority of the Internet is still IPv4, this means that we must tunnel those IPv6 packets inside something to get them across the Internet. That is the job of 6to4, Teredo, and IP-HTTPS. 6to4 encapsulates IPv6 packets into IPv4 headers and shuttles them around the Internet using protocol 41. Teredo similarly encapsulates IPv6 packets inside IPv4 headers, but then uses UDP port 3544 to transport them. IP-HTTPS encapsulates IPv6 inside IPv4 and then inside HTTP encrypted with TLS, essentially creating an HTTPS stream across the Internet. This, like any HTTPS traffic, utilizes TCP port 443. The DirectAccess traffic traveling inside either kind of tunnel is always encrypted since DirectAccess itself is protected by IPsec.

*   Do I want to enable my clients to connect using Teredo?

[](https://www.blogger.com/u/3/null)Most of the time, the answer here is yes. Probably the biggest factor that weighs on this decision is whether or not you are still running Windows 7 clients. When Teredo is enabled in an environment, this gives the client computers an opportunity to connect using Teredo, rather than all clients connecting in over the IP-HTTPS protocol. IP-HTTPS is sort of the catch-all for connections (it is used whenever Teredo and 6to4 are unavailable), but Teredo will be preferred by clients if it is available. For Windows 7 clients, Teredo is quite a bit faster than IP-HTTPS. So enabling Teredo on the server side means your Windows 7 clients (the ones connecting via Teredo) will have quicker response times, and the load on your DirectAccess [](https://www.blogger.com/u/3/null)server will be lessened. This is because Windows 7 clients connecting over IP-HTTPS are encrypting all of the traffic twice. This also means that the DA server is encrypting/decrypting everything that comes and goes twice. In Windows 8 and 10, there is an enhancement that brings IP-HTTPS performance almost on a par with Teredo, and so environments that are fully upgraded to Windows 8 and higher will receive less benefit from the extra work that goes into making sure Teredo works.

*   Can I place my DirectAccess server behind a NAT?

Yes, though there is a downside. Teredo cannot work[](https://www.blogger.com/u/3/null) if the DirectAccess server is sitting behind a NAT. For Teredo to be available, the DA server must have an External NIC with two consecutive _public_ [](https://www.blogger.com/u/3/null)IP addresses. True public addresses. If you place your DA server behind any kind of NAT, Teredo will not be available and all clients will connect using the IP-HTTPS protocol. Again, if you are using Windows 7 clients, this will decrease their speed and increase the load on your DirectAccess server.

*   How many IP addresses do I need on a standalone DirectAccess server?

[](https://www.blogger.com/u/3/null)I am going to leave single NIC implementation out of this answer since I don't recommend it anyway. For scenarios where you are sitting the External NIC behind a NAT or, for any other reason, are limiting your DA to IP-HTTPS only, then we need one external address and one internal address. The external address can be a true public address or a private NATed DMZ address. Same with the internal; it could be a true internal IP or a DMZ IP. Make sure both NICs are not plugged into the same DMZ, however. For a better installation scenario that allows Teredo connections to be possible, you would need two consecutive public IP addresses on the External NIC and a single internal IP on the Internal NIC. This internal IP could be either a true internal or DMZ, but the public IPs really have to be public for Teredo to work.

*   Do I need an internal PKI?

[](https://www.blogger.com/u/3/null)Maybe. If you want to connect Windows 7 clients, then the answer is yes. If you are completely Windows 8 and above, then technically you do not need an internal PKI. But you really should use it anyway. Using an internal PKI, which can be a single, simple Windows CA server, greatly increases the security of your DirectAccess infrastructure. You'll find out during this chapter just how easy it is to implement certificates as part of the tunnel building authentication process, making your connections stronger and more secure.