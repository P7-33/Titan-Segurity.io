---
title: 'Designing Docker Hub Two-Factor Authentication'
date: 2019-10-22T01:46:00+01:00
draft: false
---

![](https://i1.wp.com/www.docker.com/blog/wp-content/uploads/2019/10/2fa-and-PAT.png?fit=1110%2C524&ssl=1)

We recognize the central role that [Docker Hub](https://hub.docker.com/) plays in modern application development and are working on many enhancements around security and content. In this blog post we will share how we are implementing two-factor authentication (2FA). 

### Using Time-Based One-Time Password (TOTP) Authentication

Two-factor authentication increases the security of your accounts by requiring two different forms of validation that you are the rightful account owner. For Docker Hub, that means providing something you know (your username and a strong password) and something you have in your possession. Since Docker Hub is used by millions of developers and organizations for storing and sharing content – sometimes company intellectual property – we chose to use one of the more secure models for 2FA: software token (TOTP) authentication. 

TOTP authentication is more secure than SMS-based 2FA, which has many attack vectors and vulnerabilities. TOTP requires a little more upfront setup, but once enabled, it is just as simple (if not simpler) than text message-based verification. It requires the use of an authenticator application, of which there are many available. These can be apps downloaded to your mobile device (e.g. Google Authenticator or Microsoft Authenticator) or it can be a hardware key (e.g. [YubiKey](https://www.yubico.com/products/yubikey-hardware/)). To learn about these solutions: 

*   Download Google Authenticator: 
*   Download Microsoft Authenticator:
*   Learn more about [YubiKeys from Yubico](https://support.yubico.com/support/solutions/articles/15000006419-using-your-yubikey-with-authenticator-codes)

### Enabling Two-Factor Authentication in Docker Hub

Two-factor authentication is enabled in your Docker Hub **Account Settings**, under the [**Security**](https://hub.docker.com/settings/security) tab. 

![](https://i1.wp.com/www.docker.com/blog/wp-content/uploads/2019/10/2fa-not-enabled.png?fit=1110%2C777&ssl=1)

The basis of TOTP is that you will need to share a one-time secret between Docker Hub and your authenticator app – either through a unique QR code or 32-character string. After this initial synchronization, your authenticator will run an algorithm to change the passcode at a preset interval (typically under a minute) so it is now a time-sensitive piece of information only you have access to – the second component of 2FA. Subsequent logins into Docker Hub will ask for this passcode in addition to your password.

![](https://i0.wp.com/www.docker.com/blog/wp-content/uploads/2019/10/2FA-Blog-2x.png?fit=1110%2C281&ssl=1)

As the initial synchronization is an important part of the TOTP process, it is also a piece of information that is very sensitive; you do not want someone else gaining access to this initial secret. As a result, we do not share the code after your initial synchronization has been confirmed. If you lose your mobile device or access to your authenticator app, you will not be able to login with 2FA. 

**This is why it is critical to save your recovery code.** You will need the recovery code that is presented when you enable 2FA the first time. Save it somewhere safe so you can [recover your account](https://docs.docker.com/docker-hub/2fa/recover-hub-account/) when needed! 

One additional note: Many Docker users access their Hub account through the CLI. Once you’ve enabled 2FA, you will need to create a [personal access token](https://docs.docker.com/docker-hub/access-tokens/) in order to log into your Hub account from the CLI. Traditional username and password combinations will not work once you have enabled 2FA. Personal access tokens can be created from the same **Security** tab under **Account Settings**.  

For detailed instructions on enabling and using 2FA during the beta, please refer to the following:

### What’s Next for Docker Hub

We’d love for you to try the two-factor authentication beta in Docker Hub today and give us feedback at [https://github.com/docker/hub-feedback/issues](https://github.com/docker/hub-feedback/issues) 

In addition to moving 2FA to general availability in the near future, we are also preparing to add support for further authentication controls:

*   [**WebAuthn**](https://www.w3.org/TR/webauthn/) **support:** This allows you to use a security key or supported browsers with WebAuthn support for 2FA
*   **Mandatory enforcement of 2FA for an organization:** This allows organization administrators to enforce 2FA for all of their members and provide methods for remediating anyone who is not in compliance

To learn more about Docker Hub:

  
  
from Hacker News https://ift.tt/32A9VBj