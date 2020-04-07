---
title: 'Academic research finds five US telcos vulnerable to SIM swapping attacks'
date: 2020-01-11T10:29:00+01:00
draft: false
---

![SIM card swapping](https://zdnet4.cbsistatic.com/hub/i/2020/01/11/78f3f544-fb92-4acf-8d35-c14c3660f551/sim-swapping-card.png)

Image: Brett Jordan

A Princeton University academic study published yesterday found that five major US prepaid wireless carriers are vulnerable to SIM swapping attacks.

A SIM swap is when an attacker calls a mobile provider and tricks the telco's staff into changing a victim's phone number to an attacker-controlled SIM card.

This allows the attacker to reset passwords and gain access to sensitive online accounts, like email inboxes, e-banking portals, or cryptocurrency trading systems.

All last year, Princeton academics spent their time testing five major US telco providers to see if they could trick call center employees into changing a user's phone number to another SIM without providing proper credentials.

According to the research team, AT&T, T-Mobile, Tracfone, US Mobile, and Verizon Wireless were found to be using vulnerable procedures with their customer support centers, procedures that attackers could use to conduct SIM swapping attacks.

In addition, the research team also looked at 140 online services and websites and analyzed on which of these attackers could employ a SIM swap to hijack a user's account. According to the research team, 17 of the 140 websites were found to be vulnerable.

### US telco research

For the part of their research that targeted US telcos, the research team said it created 50 prepaid accounts, 10 with each carrier. For each account, the research team used the 50 SIM cards on a unique phone, and for real calls, in order to create a realistic call history.

When the time came, the research team called each telco's customer support center and applied a similar procedure.

![sim-swapping-telcos.png](https://www.zdnet.com/article/academic-research-finds-five-us-telcos-vulnerable-to-sim-swapping-attacks/#ftag=RSSbaffb68)

<span><img src="https://zdnet3.cbsistatic.com/hub/i/2020/01/11/fc2746e7-a312-4873-9635-63ced14a6093/sim-swapping-telcos.png" alt="sim-swapping-telcos.png" /></span>

Image: Lee et al.

The idea was that the attacker calls a telco's support center to request a SIM card change, but intentionally provides a wrong PIN and account owner details.

"When providing incorrect answers to personal questions such as date of birth or billing ZIP code, \[research assistants\] would explain that they had been careless at signup, possibly having provided incorrect information, and could not recall the information they had used," researchers said, explaining the motives they provided to call center staff.

At this point, after failing the first two authentication mechanisms (PIN and account owner details), telco call center operators are required, based on their procedures, to move to a third mechanism during which they ask the account owner to provide details about the last two recently made calls.

The research team says that an attacker could trick a victim into placing calls to specific numbers. For example, a scenario of "you won a prize; call here; sorry, wrong number; call here instead."

After the attacker has tricked the SIM card owner into placing those two calls, they can use these details to call the telco's call center and carry out a SIM swap.

Princeton researchers said they were able to trick all five US prepaid wireless carriers using this scenario.

When they published their research yesterday, four providers were still using the vulnerable procedure, despite the research team notifying all the affected parties. Of the five, T-Mobile told the research team they discontinued the use of call logs for customer authentication after reviewing their research.

### Online service research

But the Princeton researchers also took their study one step further. For the following stage of their research, they wanted to see what they could do once they carried out a SIM swapping attack.

For this, they analyzed the login and multi-factor authentication (MFA) procedures employed by 140 of the most popular online sites and services, ranging from social media networks to email providers, and from cryptocurrency trading sites to enterprise solutions.

They found that on 17 sites, once you managed to hijack a user's phone number via a SIM swap, you could reset the account's password and gain full access to the victim's online profile, with no other security system in place to authenticate the user.

In other words, the account recovery process for these 17 sites relied solely on an SMS-based mechanism. Once an attacker compromised a victim's phone number, the password could be reset without having to control the user's email or provide any other user secret (password reset questions, date of birth, etc.).

The full results for the analysis of the 140 websites is available [here](https://www.issms2fasecure.com/dataset). The research team redacted the names of the 17 vulnerable services from their research in order to prevent SIM swappers from focusing on those sites for future attacks.

Additional details are provided in a white paper named "[An Empirical Study of Wireless Carrier Authentication for SIM Swaps](https://www.issms2fasecure.com/assets/sim_swaps-01-10-2020.pdf)."

  
  
from Latest Topic for ZDNet in... https://ift.tt/2NivUY1