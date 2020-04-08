---
title: 'Microsoft launches new open-source projects around Kubernetes and microservices'
date: 2019-10-17T07:32:00+01:00
draft: false
---

[Microsoft](https://crunchbase.com/organization/microsoft) today announced two new open-source projects: [Dapr](https://dapr.io/), a portable, event-driven runtime that takes some of the complexity out of building microservices, and the Open Application Model (OAM), a specification that allows developers to define the resources their applications need to run on Kubernetes clusters and which Microsoft developed in cooperation with Alibaba Cloud.

As Microsoft Azure CTO [Mark Russinovich](https://crunchbase.com/person/mark-russinovich) told me ahead of today’s launch, OAM very much solves a problem that a lot of developers and ops teams are facing every day. “If you take a look just at the Kubernetes ecosystem, [Kubernetes](https://crunchbase.com/organization/kubernetes) has no concept of an application,” he explained. “It’s got the concept of a deployment and services, but nothing that coherently connects these things together into one unit and deployment lifecycle that a developer would understand in the way they look at their applications.” He argues that while Kubernetes has Helm charts, once an application is deployed, Kubernetes doesn’t know about the relationships between the objects that were represented in that chart. “We need a first-class application concept in a Kubernetes cluster.”

OAM is essentially a YAML file. It can be put in a service catalog or marketplace and deployed from there. But what’s maybe most important, says Russinovich, is that the developer can hand off the specification to the ops team and the ops team can then deploy it without having to talk to the developer. He also argues that Kubernetes itself is too complicated for enterprise developers. “At this point, it’s really infrastructure-focused,” he said. “You want a developer to focus on the app. What we saw when we talked to Kubernetes shops, they don’t let developers near Kubernetes.”

As for the cooperation with Alibaba Cloud on this specification, Russinovich noted that the two companies were already working on other projects together and that they both encountered the same problems when they talked to their customers and internal teams. Over time, they plan to bring the specification into an open-source foundation.

Alibaba Cloud will launch a managed service based on OAM, and chances are that Microsoft will do the same over time. “We’re looking to see what adoption looks like to decide,” Russinovich said.

While OAM solves an obvious problem for developers and ops team and fills a gap, Russinovich argues that Dapr may actually be quite revolutionary. “If you take a look at Dapr, it is really going to make microservices, cloud-native development, accessible to the enterprise.”

So what is Dapr? Microsoft describes it as “open source, portable, event-driven runtime that makes it easy for developers to build resilient, microservice stateless and stateful applications that run on the cloud and edge.”

[![](https://techcrunch.com/wp-content/uploads/2019/10/dapr.png)](https://techcrunch.com/wp-content/uploads/2019/10/dapr.png)

That’s a mouthful, but the general idea here is to make it easier for developers to write distributed, microservice-based applications. “If you take a look at the list of problems they run into, they want to be event-driven, so they have to manage things like events and responding to triggers,” he said. “They want communication between these microservices, so they’ve got to do pub/sub. They’ve got to do service discovery — how do I get a service from one microservice to another one. They’ve got to do state management — how does my microservice store state and retrieve it.” And then, depending on whether it’s a stateless or stateful app, developers have to work with different SDKs and programming models. Dapr, on the other hand, doesn’t need an SDK because it delivers its services through a local HTTP or gRPC endpoint, keeping the application code separate from the Dapr code. Because of this, Dapr is also independent of the language you write in.

Dapr abstracts a lot of this away and provides the building blocks (which can be accessed by HTTP or gRPC APIs) that encode best practices for building these distributed services.

[![](https://techcrunch.com/wp-content/uploads/2019/10/2019-10-15_1612.png)](https://techcrunch.com/wp-content/uploads/2019/10/2019-10-15_1612.png)

  
  
from Hacker News https://ift.tt/33twxDQ