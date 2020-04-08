---
title: 'Protecting programmatic access to user data with Binary Authorization for Borg'
date: 2019-12-17T18:26:00+01:00
draft: false
---

Posted by Daniel Rebolledo Samper and Mark Lodato, Software Engineers, Security & Privacy  
  
At Google, the safety of user data is our paramount concern and we strive to protect it comprehensively. That includes protection from insider risk, which is the possible risk that employees could use their organizational knowledge or access to perform malicious acts. Insider risk also covers the scenario where an attacker has compromised the credentials of someone at Google to facilitate their attack. There are times when it’s necessary for our services and personnel to access user data as part of fulfilling our contractual obligations to you: as part of their role, such as user support; and programmatically, as part of a service. Today, we’re releasing a whitepaper, “Binary Authorization for Borg: how Google verifies code provenance and implements code identity,” that explains one of the mechanisms we use to protect user data from insider risks on Google's cluster management system [Borg](https://research.google.com/pubs/pub43438.html?hl=es).  

**Binary Authorization for Borg is a deploy-time enforcement check**

  

Binary Authorization for Borg, or BAB, is an internal deploy-time enforcement check that reduces insider risk by ensuring that production software and configuration deployed at Google is properly reviewed and authorized, especially when that code has the ability to access user data. BAB ensures that code and configuration deployments meet certain standards prior to being deployed. BAB includes both a deploy-time enforcement service to prevent unauthorized jobs from starting, and an audit trail of the code and configuration used in BAB-enabled jobs.  
BAB ensures that Google's official software supply chain process is followed. First, a code change is reviewed and approved before being checked into Google's central source code repository. Next, the code is verifiably built and packaged using Google's central build system. This is done by creating the build in a secure sandbox and recording the package's origin in metadata for verification purposes. Finally, the job is deployed to Borg, with a job-specific identity. BAB rejects any package that lacks proper metadata, that did not follow the proper supply chain process, or that otherwise does not match the identity’s predefined policy.  

**Binary Authorization for Borg allows for several kinds of security checks**

  

BAB can be used for many kinds of deploy-time security checks. Some examples include:  

*   Is the binary built from checked in code?
*   Is the binary built verifiably?
*   Is the binary built from tested code?
*   Is the binary built from code intended to be used in the deployment?

After deployment, a job is continuously verified for its lifetime, to check that jobs that were started (and any that may still be running) conform to updates to their policies.  

  

**Binary Authorization for Borg provides other security benefits**  
Though the primary purpose of BAB is to limit the ability of a potentially malicious insider to run an unauthorized job that could access user data, BAB has other security benefits. BAB provides robust code identity for jobs in Google’s infrastructure, tying a job’s identity to specific code, and ensuring that only the specified code can be used to exercise the job identity’s privileges. This allows for a transition from a job identity—trusting an identity and any of its privileged human users transitively—to a code identity—trusting a specific piece of reviewed code to have specific semantics and which cannot be modified without an approval process.  
  
BAB also dictates a common language for data protection, so that multiple teams can understand and meet the same requirements. Certain processes, such as those for financial reporting, need to meet certain change management requirements for compliance purposes. Using BAB, these checks can be automated, saving time and increasing the scope of coverage.  

  

**Binary Authorization for Borg is part of the BeyondProd model**  
BAB is one of several technologies used at Google to mitigate insider risk, and one piece of how we secure containers and microservices in production. By using containerized systems and verifying their BAB requirements prior to deployment, our systems are easier to debug, more reliable, and have a clearer change management process. More details on how Google has adopted a cloud-native security model are available in another whitepaper we are releasing today, [“BeyondProd: A new approach to cloud-native security.”](https://cloud.google.com/security/beyondprod/)

  

In summary, implementing BAB, a deploy-time enforcement check, as part of Google’s containerized infrastructure and continuous integration and deployment (CI/CD) process has enabled us to verify that the code and configuration we deploy meet certain standards for security. Adopting BAB has allowed Google to reduce insider risk, prevent possible attacks, and also support the uniformity of our production systems. For more information about BAB, read our whitepaper, [“Binary Authorization for Borg: how Google verifies code provenance and implements code identity.”](https://cloud.google.com/security/binary-authorization-for-borg/)

  

_Additional contributors to this whitepaper include Kevin Chen, Software Engineer; Tim Dierks, Engineering Director; Maya Kaczorowski, Product Manager; Gary O’Connor, Technical Writing; Umesh Shankar, Principal Engineer; Adam Stubblefield, Distinguished Engineer; and Wilfried Teiken, Software Engineer; with special recognition to the entire Binary Authorization for Borg team for their ideation, engineering, and leadership_

[![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?d=yIl2AUoC8zA)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=An25UyKkHMY:Mpwvkej3Mug:yIl2AUoC8zA) [![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?i=An25UyKkHMY:Mpwvkej3Mug:V_sGLiPBpWU)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=An25UyKkHMY:Mpwvkej3Mug:V_sGLiPBpWU)

![](http://feeds.feedburner.com/~r/GoogleOnlineSecurityBlog/~4/An25UyKkHMY)  
  
from Google Online Security Blog https://ift.tt/2rKeyMh  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)