---
title: '3 Technical Benefits of Service Mesh, and Security Best Practices'
date: 2019-11-05T01:12:00+01:00
draft: false
---

_By Ran Ilany, co-founder and CEO for [Portshift](https://www.portshift.io/)_

![](https://cloudsecurityalliance.org/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBc2dJIiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--759e9b57d459f67763d98de047f653dd07b16aa9/a-service-mesh.jpg)

Organizations that implement containers often ask about using a service mesh layer. While this isn’t obligatory by any means, there are many benefits to running a service mesh that makes it the sensible choice for organizations seeking security, efficiency, and reliability.

In this article, we will explore the impact of service mesh, discuss the three main ways that a service mesh raises your security profile, and explain how to best implement a service mesh in a way that maximizes benefits while minimizing your DevSecOps time and labor cost.

**What is a service mesh?**

Service mesh is a networking model that forms an infrastructure layer within your architecture. It’s made up of a data plane, which contains the proxies that manage network traffic, and a control plane, which configures the rules that control the data plane. The advent of cloud-native applications and containers created a need for a lightweight and agile service that can deliver vital application services such as load balancing, traffic management, routing, health monitoring, security policies, service and user authentication, and protection against intrusion and DDoS attacks.

The concept of the mesh comes from the numerous proxies in the data plane that connect the many disparate containers, clusters, and layers that make up the complex cloud-native environment. These proxies communicate between services, deliver application services, and monitor the constantly-changing state of service instances, spreading the load across the dynamic service mesh layer, while the control plane tracks and records all of these interactions.

**What are the security benefits of service mesh?**

**1\. Increased transparency into complicated interactions:**

It’s difficult to follow the complex flow of traffic behavior within a dense and murky cloud-native environment. Each message takes such a winding path through the topology, moving between layers of the infrastructure and journeying from pod to pod on a unique track. Service mesh brings transparency to the way in which vital application services are delivered, enabling you to track their behavior.

**2\. Better security in service to service communication:**

An increase in microservices means a parallel increase in network traffic, opening up more opportunities for hackers to break into the flow of communication. Service mesh helps to secure interactions within the network by offering mutual TLS as a full-stack solution to solve the following:

*   Authenticating services
*   Encrypting traffic between services
*   Enforcing security policies

Service mesh providers generate, authorize, and authenticate security certificates in the proxies, enabling the validation of requests and ensuring access controls. Service mesh enables the creation of authorization rules based on the identities in the certificate that are exchanged using mutual TLS protocol.

However, it’s important to remember that service mesh is not a magic wand. There’s a risk that security teams could be lulled into a false sense of security by the existence of a service mesh and end up relaxing other security efforts. A hacker that can compromise the control plane or avoid proxies in the data plane can access immense vulnerabilities in service mesh.

**3\. Encryption:**

With so much communication between microservices, solid encryption becomes a pillar of network security. Service meshes manage keys, certificates, and TLS configuration to ensure continual encryption that doesn’t fail on you. They also provide policy-based authentication that allows two services to establish mutual TLS configuration for secure service-to-service encrypted communication, as well as end-user authentication. With a service mesh, the user no longer needs to implement encryption or manage certificates; these responsibilities are moved from the app developer to the framework layer.

The introduction of microservices, containers, and a cloud-native environment has produced an increasingly disparate environment, which allows for greater flexibility and agility, but also risks leading to fragmentation and dissolution. The service mesh holds these discrete components together, so they can communicate and cooperate. What’s more, the service mesh brings significant security advantages. You can use service mesh to increase network security through encryption, improved service-to-service communication, and enforcement of security policies.

**About the Author**

![](https://cloudsecurityalliance.org/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBc1lJIiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--fcc300968ff84a8641e827883cfd012807f0bc84/Ran%20Ilany%20Portshift.jpg)

Ran Ilany is the founder and CEO of [Portshift](https://www.portshift.io/), a leader in cloud-native application security. Prior to Portshift, he was head of security infrastructure for Check Point Technologies and has held executive positions with Blade Fusion and MainControl (IBM). Ran holds a Bachelor of Science in Computer Science and Robotics from the Technion.

  
  
from Cloud Security Alliance Blog https://ift.tt/33cSibc