---
title: 'The Best Ways to Secure Your SSH Server'
date: 2019-10-15T11:44:00+01:00
draft: false
---

![A stylized SSH prompt in a terminal window on a laptop.](https://www.howtogeek.com/wp-content/uploads/2019/07/img_5d28e05a4901f.png)

[Eny Setiyowati/Shutterstock.com](https://www.shutterstock.com/image-vector/secure-shell-ssh-concept-illustration-cryptographic-1353008981)

Secure your Linux system’s SSH connection to protect your system and data. System administrators and home users alike need to harden and secure internet-facing computers, but SSH can be complicated. Here are ten easy quick-wins to help protect your SSH server.

SSH Security Basics
-------------------

SSH stands for [Secure Shell](http://man7.org/linux/man-pages/man1/ssh.1.html). The name “SSH” is used interchangeably to mean either the SSH protocol itself or the software tools that allow system administrators and users to make secure connections to remote computers using that protocol.

The SSH protocol is an encrypted protocol designed to give a secure connection over an insecure network, such as the internet. SSH in Linux is built on a portable version of the [OpenSSH](https://www.openssh.com/) project. It is implemented in a [classic client-server model](https://en.wikipedia.org/wiki/Client%E2%80%93server_model), with an SSH server accepting connections from SSH clients. The client is used to connect to the server and to _display_ the session to the remote user. The server accepts the connection and _executes_ the session.

In its default configuration, an SSH server will listen for incoming connections on Transmission Control Protocol ([TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)) port 22. Because this is a standardized, [well-known port](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers), it is a target for [threat actors](https://en.wikipedia.org/wiki/Threat_actor) and [malicious bots](https://en.wikipedia.org/wiki/Internet_bot#Malicious_bots).

Threat actors launch bots that scan a range of IP addresses looking for open ports. The ports are then probed to see if there are vulnerabilities that can be exploited. Thinking, “I’m safe, there are bigger and better targets than me for the bad guys to aim at,” is false reasoning. The bots aren’t selecting targets based on any merit; they’re methodically looking for systems they can breach.

You nominate yourself as a victim if you haven’t secured your system.

Security Friction
-----------------

Security friction is the irritation—of whatever degree—that users and others will experience when you implement security measures. We’ve got long memories and can remember introducing new users to a computer system, and hearing them ask in a horrified voice whether they _really_ had to enter a password _every time_ they logged in to the mainframe. That—to them—was security friction.

(Incidentally, the invention of the password is credited to [Fernando J. Corbató](https://en.wikipedia.org/wiki/Fernando_J._Corbat%C3%B3), another figure in the pantheon of computer scientists whose combined work contributed to the circumstances that led to the birth of [Unix](https://en.wikipedia.org/wiki/Unix).)

Introducing security measures usually involves some form of friction for someone. Business owners have to pay for it. The computer users may have to change their familiar practices, or remember another set of authentication details, or add extra steps to connect successfully. The system administrators will have additional work to do to implement and maintain the new security measures.

### [Read the remaining 90 paragraphs](https://www.howtogeek.com/443156/the-best-ways-to-secure-your-ssh-server/)