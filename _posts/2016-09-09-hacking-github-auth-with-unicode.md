---
title: 'Hacking GitHub''s Auth with Unicode''s Turkish Dotless ''I'''
date: 2019-12-17T02:41:00+01:00
draft: false
---

![](https://eng.getwisdom.io/content/images/2019/12/Hacking-GitHub-with-Unicode.jpg "Hacking GitHub with Unicode's dotless 'i'.")  

From combining emoji marks and astral planes, Unicode is under appreciated and poorly understood. The importance of understanding Unicode extends beyond localization and diversity. Failing to understand Unicode may lead to vulnerabilities in your code.

One lesser known occurrence is Unicode _Case Mapping Collisions_. Loosely speaking, a collision occurs when two _different_ characters are uppercased or lowercased into the same character. This effect is found commonly at the boundary between two different protocols, like email and domain names.

A quick example
---------------

```
'ß'.toLowerCase() // 'ss' 'ß'.toLowerCase() === 'SS'.toLowerCase() // true // Note the Turkish dotless i 'John@Gıthub.com'.toLowerCase() === 'John@Github.com'.toLowerCase() 
```

Transformation Collisions
-------------------------

While there are many Unicode case collisions across all the [Unicode astral planes](https://eng.getwisdom.io/awesome-unicode/), We'll only include the characters that collide into the English alphabet. This Unicode guide includes an [exhaustive list of collisions](https://eng.getwisdom.io/awesome-unicode/#onetomanycasemappings).

#### Uppercase

Char

Code Point

Output Char

ß

0x00DF

`SS`

ı

0x0131

`I`

ſ

0x017F

`S`

ﬀ

0xFB00

`FF`

ﬁ

0xFB01

`FI`

ﬂ

0xFB02

`FL`

ﬃ

0xFB03

`FFI`

ﬄ

0xFB04

`FFL`

ﬅ

0xFB05

`ST`

ﬆ

0xFB06

`ST`

#### Lowercase

Char

Code Point

Output Char

K

0x212A

`k`

Case Study
----------

**Company**: [GitHub](https://github.com/)  
**Vulnerability**: Password reset emails delıvered to the wrong address.  
**Cause**: Forgot password emails validated against lowercase value on file, but sent the provided email.

GitHub's forgot password feature could be compromised because the system lowercased the provided email address and compared it to the email address stored in the user database. If there was a match, GitHub would send the reset password link to the email address provided by the attacker- which was technically speaking, not the same email address. I'll let the GitHub Security team explain further.

**One Quick Note:** Though not strictly required, using punycode conversion from `John@Gıthub.com` to `xn--john@gthub-2ub.com` would have helped prevent this issue. It's doubtful any web apps do this as part of the user registration process.

> John discovered a flaw in the way email addresses were being normalized to standard character sets when used to look up accounts during the password recovery flow. Password reset tokens are associated with email addresses and initiating a password reset with an email address that normalizes to another email address would result in the reset token for one user being delivered to the email address of another account. The attack only works if an email provider allows Unicode in the “local part” of the email address and an attacker can claim an email address containing Unicode that would improperly normalize to the email address of another account (e.g. [mike@example.org](mailto:mike@example.org) vs mıke@example.org). Unicode in the “domain part” is not allowed by GitHub's outgoing mail server and therefore cannot be used as part of a broader attack on common domains (e.g. gmail.com vs gmaıl.com).
> 
> GitHub addressed the vulnerability by making sure the email address in the database matches the email address that initiated the reset flow. This ensures that the email address used to generate the token matches the email address to which the reset token gets delivered.
> 
> [GitHub Security Team](https://bounty.github.com/researchers/jagracey.html)

This particular fix is simple - only send out the original email address that was used to create the account.

* * *

* * *

More Unicode
------------

Have we convinced you that Unicode is Awesome? Checkout our [verbose guide to "Awesome Unicode"](https://eng.getwisdom.io/awesome-unicode/), which made it to the front page of HackerNews.

Follow on Github
----------------

You can follow John Gracey on Github at [github.com/jagracey](https://github.com/jagracey)— or view other articles including:

About Wisdom
------------

[Wisdom](https://getwisdom.io) is a front-end monitoring tool that helps front-end developers catch and fix bugs faster by combining session replay, error tracking, and developer tools— all in one amazing package.

  
  
from Hacker News https://ift.tt/2EpkZXI