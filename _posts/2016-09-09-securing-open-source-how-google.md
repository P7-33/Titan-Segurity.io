---
title: 'Securing open-source: how Google supports the new Kubernetes bug bounty'
date: 2020-01-14T18:27:00+01:00
draft: false
---

Posted by Maya Kaczorowski, Product Manager, Container Security and Aaron Small, Product Manager, GKE On-Prem Security  

[![](https://1.bp.blogspot.com/-XGzknm5_BDA/Xh0qmu17ppI/AAAAAAAABc4/73fUXZTkUFc96pfkCXX9inChKA3uLWAoQCNcBGAsYHQ/s640/kubernetes-bug-bounty-01.jpg)](https://1.bp.blogspot.com/-XGzknm5_BDA/Xh0qmu17ppI/AAAAAAAABc4/73fUXZTkUFc96pfkCXX9inChKA3uLWAoQCNcBGAsYHQ/s1600/kubernetes-bug-bounty-01.jpg)

  
At Google, we care deeply about the security of open-source projects, as they’re such a critical part of our infrastructure—and indeed everyone’s. Today, the Cloud-Native Computing Foundation (CNCF) announced a [new bug bounty program for Kubernetes](https://hackerone.com/kubernetes) that we helped create and get up and running. Here’s a brief overview of the program, other ways we help secure open-source projects and information on how you can get involved.  

  

**Launching the Kubernetes bug bounty program**  
[Kubernetes](https://kubernetes.io/) is a CNCF project. As part of [its graduation criteria](https://github.com/cncf/toc/pull/145), the CNCF recently funded the project’s first [security audit](https://github.com/kubernetes/community/blob/master/wg-security-audit/findings/Kubernetes%20Final%20Report.pdf), to review its core areas and identify potential issues. The audit identified and addressed several previously unknown security issues. Thankfully, Kubernetes already had a [Product Security Committee](https://github.com/kubernetes/community/tree/master/committee-product-security), including engineers from the Google Kubernetes Engine (GKE) security team, who respond to and patch any newly discovered bugs. But the job of securing an open-source project is never done. To increase awareness of Kubernetes’ security model, attract new security researchers, and reward ongoing efforts in the community, the Kubernetes Product Security Committee began [discussions in 2018](https://docs.google.com/document/d/1dvlQsOGODhY3blKpjTg6UXzRdPzv5y8V55RD_Pbo7ag/edit#heading=h.7t1efwpev42p) about launching an official bug bounty program.  

  

**Find Kubernetes bugs, get paid**  

  

What kind of bugs does the bounty program recognize? Most of the content you’d think of as ‘core’ Kubernetes, included at [https://github.com/kubernetes](https://github.com/kubernetes), is in scope. We’re interested in common kinds of security issues like remote code execution, privilege escalation, and bugs in authentication or authorization. Because Kubernetes is a community project, we’re also interested in the Kubernetes supply chain, including build and release processes that might allow a malicious individual to gain unauthorized access to commits, or otherwise affect build artifacts. This is a bit different from your standard bug bounty as there isn’t a ‘live’ environment for you to test—Kubernetes can be configured in many different ways, and we’re looking for bugs that affect any of those (except when existing configuration options could mitigate the bug). Thanks to the CNCF’s ongoing support and funding of this new program, depending on the bug, you can be rewarded with a bounty anywhere from $100 to $10,000.

  

The bug bounty program has been in a private release for several months, with invited researchers submitting bugs and to help us test the triage process. And today, the new Kubernetes bug bounty program is live! We’re excited to see what kind of bugs you discover, and are ready to respond to new reports. You can learn more about the program and how to get involved [here](https://kubernetes.io/blog/2019/01/14/kubernetes-bug-bounty-announcement).  

  

**Dedicated to Kubernetes security**  
Google has been involved in this new Kubernetes bug bounty from the get-go: proposing the program, completing vendor evaluations, defining the initial scope, testing the process, and onboarding [HackerOne](https://www.hackerone.com/blog/hackerone-launches-bug-bounty-program-kubernetes) to implement the bug bounty solution. Though this is a big effort, it’s part of our ongoing commitment to securing Kubernetes. Google continues to be involved in every part of Kubernetes security, including [responding to vulnerabilities](https://cloud.google.com/blog/products/containers-kubernetes/exploring-container-security-vulnerability-management-in-open-source-kubernetes) as part of the Kubernetes Product Security Committee, [chairing the sig-auth Kubernetes special interest group](https://github.com/kubernetes/community/tree/master/sig-auth), and [leading the aforementioned Kubernetes security audit](https://cloud.google.com/blog/products/containers-kubernetes/kubernetes-security-audit-what-gke-and-anthos-users-need-to-know). We realize that security is a critical part of any user’s decision to use an open-source tool, so we dedicate resources to help ensure we’re providing the best possible security for Kubernetes and GKE.  
  
Although the Kubernetes bug bounty program is new, it isn’t a novel strategy for Google. We have enjoyed a close relationship with the security research community for many years and, in 2010, Google established our own [Vulnerability Rewards Program](https://www.google.com/about/appsecurity/reward-program/) (VRP). The VRP provides rewards for vulnerabilities reported in GKE and virtually all other Google Cloud services. (If you find a bug in GKE that isn’t specific to Kubernetes core, you should still report it to the Google VRP!) Nor is Kubernetes the only open-source project with a bug bounty program. In fact, we recently expanded our [Patch Rewards program](https://www.google.com/about/appsecurity/patch-rewards/) to provide financial rewards [both upfront and after-the-fact](https://security.googleblog.com/2019/12/announcing-updates-to-our-patch-rewards.html) for security improvements to open-source projects.  

  

Help keep the world’s infrastructure safe. [Report a bug to the Kubernetes bug bounty](https://hackerone.com/kubernetes), or a GKE bug to [the Google VRP](https://www.google.com/about/appsecurity/reward-program/).

[![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?d=yIl2AUoC8zA)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=j1UwS1UZTXA:_kJEKpGBX60:yIl2AUoC8zA) [![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?i=j1UwS1UZTXA:_kJEKpGBX60:V_sGLiPBpWU)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=j1UwS1UZTXA:_kJEKpGBX60:V_sGLiPBpWU)

![](http://feeds.feedburner.com/~r/GoogleOnlineSecurityBlog/~4/j1UwS1UZTXA)  
  
from Google Online Security Blog https://ift.tt/2QTa1Ru  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)