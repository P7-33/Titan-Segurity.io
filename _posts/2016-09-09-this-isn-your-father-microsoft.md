---
title: 'This isn''t your father''s Microsoft'
date: 2019-11-09T05:56:00+01:00
draft: false
---

I have a consulting engagement at a big Windows Enterprise shop. I had to re-familiarize myself with the current Microsoft compute/cloud stack. I’ve been pleasantly surprised. The offerings are compelling.

Case one: PowerShell
--------------------

Once you get past the naming convention (init upper case and hyphenation in function names/args), it’s quite usable. Easy arg processing, obj-orientation - it feels like at least a 10% improvement over bash (which was my first reaction to C# vs Java).

Case two: A new open orientation
--------------------------------

.NET core and PowerShell core are open sourced, and run on Linux. Weird! This is not your father’s Microsoft. Their initial Kubernetes service _only_ runs on top of Linux vms. There are other products as well that are Linux based. Even their beloved SQL Server. The new unfortunately named Azure DevOps, the combined code repo, build and release tool, supports git natively and Linux build and deploys.

Case three: Windows nanoserver
------------------------------

Finally a recognition that servers don’t need a heavy, clunky GUI! CLI is better for automation-oriented sysadmins, thank you very much.

Still, there is some holdover to the grand old desktop orientation. Inexplicably, SSH is _off_ by default in windows server 2016. And WinRM, the remote PS processor, is also non-functional by default. Just RDP is on. What’s up with that? You have to do backflips in Azure with a custom script extension or use set of nasty group policy settings to turn it on. There is no good security or commercial reason that I can see that backs us that product decision. Maybe they’ll fix it in Server 2019?

Case four: Azure
----------------

It's a no-nonsense, right-sized technical offering - it really is competitive with AWS. They hit the large enterprise business concerns - cost allocation, policies, license sharing, hybrid on-prem, and so forth. But it’s rather open on the OS: [half of Azure VMs run Linux](https://www.zdnet.com/article/linux-now-dominates-azure/#ftag=CAD-00-10aag7f).

What's the strategy?
--------------------

Maybe the Microsoft strategy is to intro into the Linux/Java/LAMPish/open-source camp community, burnish their image, and hope they consider their commercial offerings. Will there be significant adoption in the historically non-Microsoft (in many cases anti-Microsoft) community?

I think the strategy is already working on me. Feels like the edge on my bias has softened.

You non-Microsoftees out there: Are you using or would consider using PowerShell? Are you writing or would consider writing .NET core apps?

  
  
from Hacker News https://ift.tt/2C1YK9p