---
title: 'Microsoft: MFA bypass attacks are so rare we don''t have good statistics on them'
date: 2019-10-04T06:40:00+01:00
draft: false
---

![two-factor-2.jpg](https://zdnet3.cbsistatic.com/hub/i/2017/05/04/9c4b7d7e-ce34-4c37-ad6d-a6c299e92d91/4979edc14e1d7a457d30d5ee5c4361c8/two-factor-2.jpg)

Attacks on Microsoft user accounts that are capable of bypassing multi-factor authentication (MFA) protections are so rare that the Redmond-based company doesn't even have stats for them.

"Compared to password attacks, attacks which target non-password authenticators are extremely rare," said Alex Weinert, Group Program Manager for Identity Security and Protection at Microsoft.

"When we evaluate all the tokens issued with MFA claims, we see that less than 10% of users use MFA per month in our enterprise accounts (and that includes on premises and third party MFA)," [Weinert added](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/All-your-creds-are-belong-to-us/ba-p/855124).

The Microsoft security expert claims that this slow rate of adoption among Microsoft users is what's kept attackers from evolving and deploying tools that can intercept MFA operations.

"Until MFA is more broadly adopted, there is little reason for attackers to evolve," he said.

But he also warns Microsoft users that tools and methods for bypassing multi-factor authentication exist. One example is [Modlishka](https://www.zdnet.com/article/new-tool-automates-phishing-attacks-that-bypass-2fa/), a tool that ZDNet analyzed earlier this year when it was released.

Other tools and techniques are listed below, along with their ability to be used for real-time phishing (intercept-and-replay of authentication messages using a machine-in-the-middle) or channel-jacking (takeover of the communication channel used for the authenticator).

**Credential                                  **

**RealTime Phishable**

**Channel-jackable**

**Other ways to break credential**

**Passwords** are user-selected secrets which are entered at a login screen and then compared with a representation of the password stored on the server.

Y

Y

[See here](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Your-Pa-word-doesn-t-matter/ba-p/731984).

Personal Identification Numbers (**PIN**s) are simpler user-selected secrets used like passwords, typically four to eight characters. Like biometrics, they are best reserved for local credential access.

Y

Y

As passwords, but easier to guess, with more re-use and (usually) poorer storage hygiene.

Simple **approvals** (only) verify the channel or device is in the user's possession. An app may pop a simple "approve/deny" request, or a phone call may say "Press 1 to approve." Useful in cases where legacy authenticator protocols prevent a more sophisticated interaction.

Y

Y

"Grief" the user by sending multiple requests in hopes the user will approve one.

Steal the device which indicates approval.

Server transmitted one-time **passcodes** (OTP) are codes transmitted to the user for entry in the login screen. They indicate control of the communications channel or target device. The login server sends a code to the user, and the user enters the code to prove they are in control of the channel or device.

Y

Y

Steal the device which receives the OTP.

Time based one-time-passcodes (**[TOTP](https://tools.ietf.org/html/rfc6238)**) on **[OATH](https://openauthentication.org/token-specs/) hardware** tokens use a shared secret between the token and the login server and the current time to generate a code on the token. The secret is built into the hardware token. It must be registered with the server and stored in a recoverable (plaintext or encrypted) form. This can be done out of band by admins, or by the user converting the token ID to a secret via a brokering service. At login, the generated code is entered by the user in the login server UX, which validates it using the stored secret. The code is usually available to anyone in possession of the physical token. There are OATH-derivatives that modify the registration process, but they don't significantly change the security model.

Y

N

Stealing or accessing the device long enough to read the code to achieve login

Intercepting the secret at the time of registration using a person-in-the-middle.

Stealing the database in which the secrets are stored. A high cost attack, but one which yields all OATH tokens for the login server.

**OATH software** TOTP tokens only differ from OATH hardware because the secret can be delivered by the software token to the server. The registration may be more vulnerable than for hardware tokens because the secret is transmitted directly. The actual secret is sometimes brokered in OATH derivative tokens like RSA or Symantec Tokens. Apps that host software OATH tokens such as Microsoft Authenticator and Google Authenticator may protect the codes with a device unlock gesture like a fingerprint, face scan, or PIN.

Y

N\*

\*Unless OS state backup is enabled for secrets.

Stealing the device (may not be as fruitful if an unlock gesture is required)

Attackers may be able to intercept secrets at registration with malware on the device

Authentication **applications** like the **[Microsoft Authenticator](https://www.microsoft.com/en-us/account/authenticator)** use an app which is registered on a device. Like Smartcards and Windows Hello, the registration procedure is secure and registers a public key (no secret stored).

Y

N\*

\*Unless OS state backup is enabled for keys.

Grief the user, unless the app requires the user to know something present on the screen to log-in.

Takeover the OS account, and recover OS backed up app data if backup/restore is available and enabled for the app.

**Smartcards** use a secure registration procedure to exchange keys at registration. The server remembers a public key (no secret stored) which can be used to validate the fact that it is seeing the same token that was registered. In some cards, both registration and use are bound to the hardware that the login is being attempted from, making them unphishable.

N

N

"Shoulder surf" the PIN and steal the card.

**[Windows Hello](https://www.microsoft.com/en-us/windows/windows-hello)** uses a secure registration procedure to exchange keys at registration. The server remembers a public key (no secret stored) which can be used to validate the fact that it is seeing the same token that was registered. Importantly, both registration and use are bound to the hardware that the login is being attempted from.

N

N

"Shoulder surf" the PIN and steal the PC (hard if bio enabled).

**[FIDO](https://fidoalliance.org/fido2/)** tokens use a secure registration procedure to exchange keys at registration. The server remembers a public key (not a secret) which can be used to validate the fact that it is seeing the same token that was registered. Importantly, both registration and use are bound to the hardware that the login is being attempted from. See Pamela Dingle's **[blogs](https://techcommunity.microsoft.com/t5/Identity-Standards-Blog/All-about-FIDO2-CTAP2-and-WebAuthn/ba-p/288910)** to learn more.

N

N

"Shoulder surf" the PIN and steal the token (hard if bio enabled).

But the Microsoft security expert doesn't want users to get discouraged from enabling MFA for their accounts just because these tools and techniques exist.

As he said before, these attacks are so rare that Microsoft barely sees any. Instead, he recommends that users enable MFA for their accounts, with the strongest authentication factor available, as detailed in the table above (factors near the bottom are more secure).

Microsoft, together with the other big tech companies, are big proponents of MFA solutions, constantly urging users to enable the feature for their accounts. Last month, Microsoft said that [MFA blocks 99.9% of all account attacks](https://www.zdnet.com/article/microsoft-using-multi-factor-authentication-blocks-99-9-of-account-hacks/).

  
  
from Latest Topic for ZDNet in... https://ift.tt/2AKcBju