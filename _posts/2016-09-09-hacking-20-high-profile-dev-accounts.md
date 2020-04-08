---
title: 'Hacking 20 high-profile dev accounts could compromise half of the npm ecosystem'
date: 2019-10-16T02:47:00+01:00
draft: false
---

![npm](https://zdnet1.cbsistatic.com/hub/i/2019/10/15/54d57679-a8a4-483a-930c-dc701f67334a/e16eb971a39720dbfbdae612816f3f7d/npm.png)

Image: npm

The npm ecosystem of JavaScript libraries is more interwoven than most developers think, and the entire thing is a gigantic house of cards, being one bad hack away from compromising hundreds of thousands of projects, according to a recent academic study.

The research, carried out by the Department of Computer Science from the Technical University of Darmstadt, in Germany, analyzed the dependency graph of the entire npm ecosystem.

Researchers downloaded metadata for all the npm packages published until April 2018 and created a giant graph that included 676,539 nodes and 4,543,473 edges (lines connecting the nodes).

In addition, academics also analyzed different versions of the same packages, looking at historical versions (5,386,239 versions for the 676,539 packages), but also at the package maintainers (199,327 npm accounts), and known security flaws impacting the packages (609 public reports).

Their goal was to get an idea of how hacking one or more npm maintainer accounts, or how vulnerabilities in one or more packages, reverberated across the npm ecosystem; along with the critical mass needed to cause security incidents inside tens of thousands of npm projects at a time.

### npm packages have too many dependencies

According to the Darmstadt team, this critical mass is easy to achieve, primarily because the normal npm JavaScript package has an abnormally large number of dependencies -- with a package loading 79 third-party packages from 39 different maintainers, on average.

This number is lower for popular packages, which only rely on code from 20 other maintainers, on average, but the research team found that some popular npm packages (600) relied on code written by more than 100 maintainers.

According to the research team, this high value for the average number of dependencies and third-hand developers contributing code to an upstream package is a side-effect of the "micropackage" trend in JavaScript programming, where basic functionality is separated into npm packages consisting of just a few lines of code.

The negative effect is that npm packages load code from tens of sources, all of which become entry points for attacks carried out by third-party developers, if left unsupervised.

### Just 20 accounts... just 20.

But while some npm packages load code from too many packages and from too many developers, there is another dangerous trend forming on the npm package repository -- namely the consolidation of popular npm packages under a few maintainer accounts.

"391 highly influential maintainers affect more than 10,000 packages, making them prime targets for attacks," the research team said. "If an attacker manages to compromise the account of any of the 391 most influential maintainers, the community will experience a serious security incident."

Furthermore, in a worst-case scenario where multiple maintainers collude, or a hacker gains access to a large number of accounts, the Darmstadt team said that it only takes access to 20 popular npm maintainer accounts to deploy malicious code impacting more than half of the npm ecosystem. \[see image below\]

![npm-fig11.png](https://www.zdnet.com/article/hacking-20-high-profile-dev-accounts-could-compromise-half-of-the-npm-ecosystem/#ftag=RSSbaffb68)

<span><img src="https://zdnet3.cbsistatic.com/hub/i/r/2019/10/16/4fa6c918-1c6b-415a-bd9a-597e9ca0c940/resize/370xauto/74a4cacce9d9c0ffd5e25dfd6812b7f3/npm-fig11.png" alt="npm-fig11.png" /></span>

Image: Zimmerman et al.

But hackers don't necessarily need to hack into accounts. There's also the alternative of finding security flaws in existing npm packages.

Taking into account that the average npm package is loaded into another 230 npm libraries, on average, finding exploitable vulnerabilities even in medium-popular packages can provide attackers with the ability to run code in hundreds of other libraries, some of which might be used in business-critical or financial systems.

Further, attackers don't really need to look for new vulnerabilities. Based on the Darmstadt team's scan, a significant percentage (up to 40%) of all packages depend on code with at least one publicly known vulnerability, showing that many npm packagesmay be vulnerable to attacks right now, along with all the user-facing apps they've been used to help create.

### Things could be better by securing a few accounts, packages

But the research team suggests there could be a way out of this mess. The simplest solution to counteract all these negatives in the npm ecosystem would be to vet developer accounts and audit popular npm packages, to make sure the code is safe and comes from a trusted and voucheable source.

The German academics claim that vetting 140 of the most popular accounts, along with 300 popular npm libraries, should cut the risk of a supply-chain attack inside the npm ecosystem by half.

Much more about this research is available in a white paper named "[Small World with High Risks: A Study of Security Threats in the npm Ecosystem \[PDF\]](https://www.usenix.org/system/files/sec19-zimmermann.pdf)."

VIDEO

The Darmstadt team's research was "inspired" by past supply-chain attacks on the npm ecosystem, such as:

*   [November 2018](https://www.zdnet.com/article/hacker-backdoors-popular-javascript-library-to-steal-bitcoin-funds/) - a hacker backdoored the event-stream npm package to load malicious code inside the BitPay Copay desktop and mobile wallet apps, and steal cryptocurrency.
*   [July 2018](https://eslint.org/blog/2018/07/postmortem-for-malicious-package-publishes) - a hacker compromised the ESLint library with malicious code that was designed to steal the npm credentials of other developers.
*   [May 2018](https://blog.npmjs.org/post/173526807575/reported-malicious-module-getcookies) - a hacker tried to hide a backdoor in a popular npm package named getcookies.
*   [August 2017](https://www.bleepingcomputer.com/news/security/javascript-packages-caught-stealing-environment-variables/) - the npm team removed 38 JavaScript npm packages that were caught stealing environment variables from other projects, in an attempt to collect project-sensitive information, such as passwords or API keys.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2ITNZcB