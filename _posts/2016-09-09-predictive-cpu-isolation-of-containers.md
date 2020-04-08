---
title: 'Predictive CPU isolation of containers at Netflix using a MIP solver'
date: 2019-10-02T04:31:00+01:00
draft: false
---

![](https://miro.medium.com/max/1000/1*8zsLvMK0n_Cw2pzauiNf1A.png "Predictive CPU isolation of containers at Netflix - Netflix TechBlog - Medium")  

**Predictive CPU isolation of containers at Netflix**
=====================================================

By Benoit Rostykus, Gabriel Hartmann
------------------------------------

Noisy Neighbors
===============

We’ve all had noisy neighbors at one point in our life. Whether it’s at a cafe or through a wall of an apartment, it is always disruptive. The need for good manners in shared spaces turns out to be important not just for people, but for your Docker containers too.

When you’re running in the cloud your containers are in a shared space; in particular they share the CPU’s memory hierarchy of the host instance.

Because microprocessors are so fast, computer architecture design has evolved towards adding various levels of caching between compute units and the main memory, in order to hide the latency of bringing the bits to the brains. However, the key insight here is that these caches are partially shared among the CPUs, which means that perfect performance isolation of co-hosted containers is not possible. If the container running on the core next to your container suddenly decides to fetch a lot of data from the RAM, it will inevitably result in more cache misses for you (and hence a potential performance degradation).

Linux to the rescue?
====================

Traditionally it has been the responsibility of the operating system’s task scheduler to mitigate this performance isolation problem. In Linux, the current mainstream solution is CFS (Completely Fair Scheduler). Its goal is to assign running processes to time slices of the CPU in a “fair” way.

CFS is widely used and therefore well tested and Linux machines around the world run with reasonable performance. So why mess with it? As it turns out, for the large majority of Netflix use cases, its performance is far from optimal. [Titus](https://netflix.github.io/titus/) is Netflix’s container platform. Every month, we run millions of containers on thousands of machines on Titus, serving hundreds of internal applications and customers. These applications range from critical low-latency services powering our customer-facing video streaming service, to batch jobs for encoding or machine learning. Maintaining performance isolation between these different applications is critical to ensuring a good experience for internal and external customers.

We were able to meaningfully improve both the predictability and performance of these containers by taking some of the CPU isolation responsibility away from the operating system and moving towards a data driven solution involving combinatorial optimization and machine learning.

The idea
========

CFS operates by very frequently (every few microseconds) applying a set of heuristics which encapsulate a general concept of best practices around CPU hardware use.

Instead, what if we reduced the frequency of interventions (to every few seconds) but made better data-driven decisions regarding the allocation of processes to compute resources in order to minimize collocation noise?

One traditional way of mitigating CFS performance issues is for application owners to manually cooperate through the use of core pinning or nice values. However, we can automatically make better global decisions by detecting collocation opportunities based on actual usage information. For example if we predict that container A is going to become very CPU intensive soon, then maybe we should run it on a different [NUMA](https://en.wikipedia.org/wiki/Non-uniform_memory_access) socket than container B which is very latency-sensitive. This avoids thrashing caches too much for B and evens out the pressure on the [L3](https://en.wikipedia.org/wiki/Memory_hierarchy) caches of the machine.

Optimizing placements through combinatorial optimization
========================================================

What the OS task scheduler is doing is essentially solving a resource allocation problem: I have X threads to run but only Y CPUs available, how do I allocate the threads to the CPUs to give the illusion of concurrency?

As an illustrative example, let’s consider a toy instance of 16 [hyperthreads](https://en.wikipedia.org/wiki/Hyper-threading). It has 8 physical hyperthreaded cores, split on 2 NUMA sockets. Each hyperthread shares its L1 and L2 caches with its neighbor, and shares its L3 cache with the 7 other hyperthreads on the socket:

If we want to run container A on 4 threads and container B on 2 threads on this instance, we can look at what “bad” and “good” placement decisions look like:

The first placement is intuitively bad because we potentially create collocation noise between A and B on the first 2 cores through their L1/L2 caches, and on the socket through the L3 cache while leaving a whole socket empty. The second placement looks better as each CPU is given its own L1/L2 caches, and we make better use of the two L3 caches available.

Resource allocation problems can be efficiently solved through a branch of mathematics called combinatorial optimization, used for example for airline scheduling or logistics problems.

We formulate the problem as a Mixed Integer Program (MIP). Given a set of K containers each requesting a specific number of CPUs on an instance possessing d threads, the goal is to find a binary assignment matrix M of size (d, K) such that each container gets the number of CPUs it requested. The loss function and constraints contain various terms expressing a priori good placement decisions such as:

*   avoid spreading a container across multiple NUMA sockets (to avoid potentially slow cross-sockets memory accesses or page migrations)
*   don’t use hyper-threads unless you need to (to reduce L1/L2 thrashing)
*   try to even out pressure on the L3 caches (based on potential measurements of the container’s hardware usage)
*   don’t shuffle things too much between placement decisions

Given the low-latency and low-compute requirements of the system (we certainly don’t want to spend too many CPU cycles figuring out how containers should use CPU cycles!), can we actually make this work in practice?

Implementation
==============

We decided to implement the strategy through Linux [cgroups](http://man7.org/linux/man-pages/man7/cgroups.7.html) since they are fully supported by CFS, by modifying each container’s cpuset cgroup based on the desired mapping of containers to hyper-threads. In this way a user-space process defines a “fence” within which CFS operates for each container. In effect we remove the impact of CFS heuristics on performance isolation while retaining its core scheduling capabilities.

This user-space process is a Titus subsystem called [**titus-isolate**](https://github.com/Netflix-Skunkworks/titus-isolate) which works as follows. On each instance, we define three events that trigger a placement optimization:

*   **_add_**: A new container was allocated by the Titus scheduler to this instance and needs to be run
*   **_remove_**: A running container just finished
*   **_rebalance_**: CPU usage may have changed in the containers so we should reevaluate our placement decisions

We periodically enqueue rebalance events when no other event has recently triggered a placement decision.

Every time a placement event is triggered, **titus-isolate** queries a remote optimization service (running as a Titus service, hence also isolating itself… [turtles all the way down](https://en.wikipedia.org/wiki/Turtles_all_the_way_down)) which solves the container-to-threads placement problem.

This service then queries a local [GBRT](https://en.wikipedia.org/wiki/Gradient_boosting) model (retrained every couple of hours on weeks of data collected from the whole Titus platform) predicting the P95 CPU usage of each container in the coming 10 minutes (conditional quantile regression). The model contains both contextual features (metadata associated with the container: who launched it, image, memory and network configuration, app name…) as well as time-series features extracted from the last hour of historical CPU usage of the container collected regularly by the host from the kernel [CPU accounting controller](https://www.kernel.org/doc/Documentation/cgroup-v1/cpuacct.txt).

The predictions are then fed into a MIP which is solved on the fly. We’re using [cvxpy](https://www.cvxpy.org/) as a nice generic symbolic front-end to represent the problem which can then be fed into various open-source or proprietary MIP solver backends. Since MIPs are NP-hard, some care needs to be taken. We impose a hard time budget to the solver to drive the branch-and-cut strategy into a low-latency regime, with guardrails around the MIP gap to control overall quality of the solution found.

The service then returns the placement decision to the host, which executes it by modifying the cpusets of the containers.

For example, at any moment in time, an r4.16xlarge with 64 logical CPUs might look like this (the color scale represents CPU usage):

Results
=======

The first version of the system led to surprisingly good results. We reduced overall runtime of batch jobs by multiple percent on average while most importantly reducing job runtime variance (a reasonable proxy for isolation), as illustrated below. Here we see a real-world batch job runtime distribution with and without improved isolation:

Notice how we mostly made the problem of long-running outliers disappear. The right-tail of unlucky noisy-neighbors runs is now gone.

For services, the gains were even more impressive. One specific Titus middleware service serving the Netflix streaming service saw a capacity reduction of 13% (a decrease of more than 1000 containers) needed at peak traffic to serve the same load with the required P99 latency SLA! We also noticed a sharp reduction of the CPU usage on the machines, since far less time was spent by the kernel in cache invalidation logic. Our containers are now more predictable, faster and the machine is less used! It’s not often that you can have your cake and eat it too.

Next Steps
==========

We are excited with the strides made so far in this area. We are working on multiple fronts to extend the solution presented here.

We want to extend the system to support CPU oversubscription. Most of our users have challenges knowing how to properly size the numbers of CPUs their app needs. And in fact, this number varies during the lifetime of their containers. Since we already predict future CPU usage of the containers, we want to automatically detect and reclaim unused resources. For example, one could decide to auto-assign a specific container to a shared cgroup of underutilized CPUs, to better improve overall isolation and machine utilization, if we can detect the sensitivity threshold of our users along the various axes of the following graph.

We also want to leverage kernel [PMC events](http://www.brendangregg.com/blog/2017-05-04/the-pmcs-of-ec2.html) to more directly optimize for minimal cache noise. One possible avenue is to use the Intel based bare metal instances [recently introduced](https://aws.amazon.com/about-aws/whats-new/2018/05/announcing-general-availability-of-amazon-ec2-bare-metal-instances/) by Amazon that allow deep access to performance analysis tools. We could then feed this information directly into the optimization engine to move towards a more supervised learning approach. This would require a proper continuous randomization of the placements to collect unbiased counterfactuals, so we could build some sort of interference model (“what would be the performance of container A in the next minute, if I were to colocate one of its threads on the same core as container B, knowing that there’s also C running on the same socket right now?”).

Conclusion
==========

If any of this piques your interest, reach out to us! We’re looking for [ML engineers](https://jobs.netflix.com/jobs/860513) to help us push the boundary of containers performance and “machine learning for systems” and [systems engineers](https://jobs.netflix.com/jobs/869888) for our core infrastructure and compute platform.

  
  
from Hacker News https://ift.tt/2K27KhX