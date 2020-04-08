---
title: 'Gluu vs. Keycloak (2018)'
date: 2019-11-05T06:29:00+01:00
draft: false
---

[![](https://www.gluu.org/staging-blog/wp-content/uploads/2018/05/frazier-verus-ali.jpg)](https://www.gluu.org/staging-blog/wp-content/uploads/2018/05/frazier-verus-ali.jpg)

[Keycloak](https://keycloak.org) is a very good open source SSO server, with lots of features, and a strong community. Red Hat is the corporate backer of the project.

How does Gluu compare to Keycloak? We get asked this question a lot! We’re looking very closely at the direction of KeyCloak. Following are some thoughts.

First some level setting. The Gluu Server, our flagship product, is a distribution of several projects: we take open source IAM tools, and make binary distributions that are QA’d and supported for years. “Gluu Server Community Edition” is a free binary (a linux package). And we also sell subscriptions to our Kubernetes binary distribution. So hypothetically, Gluu could use the Apache2 licensed Keycloak as the SSO component. Is this likely to happen? For the near term, the answer is no. But if Keycloak keeps improving, you never know! Following are some considerations.

#### Business

We see a lot of Keycloak business risk. Granted, we’re looking out 5-10 years, and in that time frame a lot can halpen. For now, Red Hat seems committed to the project. But with all the things that could change in the IBM/Red Hat landscape in the next few years, it’s hard for us to understand or predict the possible implications. If Red Hat were to cut back it’s investment, we do not think a volunteer lead project can sustain innovation. From our experience, the most predictable way to lead in innovation is to have a strong business model behind the project.

You might say that Gluu’s has just as much business risk. We could go out of business or be aquired by a large company that hates open source. However, from a Gluu perspective, those are risks we understand! And there are many more play-books for open source companies now then ten years ago when we got started. Although you could say the IAM market has consolidated as a result of successful SaaS IAM offerings (there are fewer players), the size of the market is still healthy and growing–enough so that Ping Identity’s IPO was successful.

#### RDBMS

Everyone loves good old transaction RDBMS platforms. But RDBMS systems have some scale issues–it’s hard to create an active-active replication topology, which is ideal if you have a globally distributed authentication service. Also, it’s hard to the scale RDBMS horizontally. If you want to put more compute and persistence to work, how can you do it without downtime? Gluu prefers either LDAP or Couchbase as the database. LDAP has strong replication capabilities and good performance. Couchbase can support multi-datacenter sharded deploments, and enables you to individually scale the query, index and data services.

#### Infinispan

We are concerned about Keycloak’s reliance on the Infinispan cache, which is a subsytem of the [Wildfly](https://wildfly.org/) J2EE Application Server. Gluu supports the use of Redis or Couchbase as the cache. For small deployments, you can just use the database–caching is not super important. For large deployments, we think moving the memory requirement to Redis or Couchbase makes more sense. In the Gluu Server, we deploy our Java applications in light-weight jetty servlet containers–trying to stay away from relying on complex (i.e. slow to start) J2EE application servers.

#### OAuth

Gluu tries to be the best in OAuth2. While Keycloak is a pretty decent OpenID Connect implementation, we believe that Gluu’s OAuth project (“oxAuth”) covers more features, and is more flexible to configure. We’ve gone out of our way to introduce many interfaces that enable you to customize the behavior of the responses from the Gluu Server. Futhermore, Gluu has the most comprehensive current shipping implementation of the User Managed Access protocol, a profile of OAuth that enables API access control. In particular, Keycloak does not implement the claims gathering endpoint of UMA, which is the front channel used to interact with a user if authorization cannot be otherwise obtained. Use cases for UMA include getting post-authentication consent from a user, progressive risk profiling, and stepped-up authentication workflows.

#### End-to-End Support

To run a mission critical IAM system, many components have to work together. Much of the performance of the system is derived from proper configuration of the database and cache. Without a standard deployment strategy for all the components, much of the work is left to the system administrators to figure out. If every deployment is a one-off, it’s hard to drive down the cost of operations. Gluu looks at the IAM platform wholistically. Reduced figure pointing is achieved by standard devops strategies for all the components.

#### Conclusion

So what does it all mean? Is Keycloak Ali or Frazier? Luckily, the open source world is not a zero sum game. For us at Gluu, cool new open source IAM components are not the enemy–they are the opportunity. We can harness the power of open source innovation. And when there are gaps, we can fill them with our own software. Right now we are on the sidelines with Keycloak. But who knows… maybe for another product or offering, it will make sense. Let’s see how the community continues to evolve.

  
  
from Hacker News https://ift.tt/2qh8gCB