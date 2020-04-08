---
title: 'PyTorch elastic training'
date: 2019-12-07T08:10:00+01:00
draft: false
---

[![License](https://camo.githubusercontent.com/6289cd478372b4cc8ce68e6c513b6e24aeb2363f/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d425344253230332d2d436c617573652d626c75652e737667)](https://github.com/pytorch/elastic/blob/master/LICENSE)[![CircleCI](https://camo.githubusercontent.com/4bf145fd216043a29f0a20b96c68f74755975e74/68747470733a2f2f636972636c6563692e636f6d2f67682f7079746f7263682f656c61737469632e7376673f7374796c653d73766726636972636c652d746f6b656e3d39626561343665393461646265326633653066623264343035346231623635356632653230386332)](https://circleci.com/gh/pytorch/elastic)

[](https://github.com/pytorch/elastic#pytorch-elastic)PyTorch Elastic
=====================================================================

PyTorch Elastic (torchelastic) is a framework that enables distributed training jobs to be executed in a fault tolerant and elastic manner. It provides the primitives and interfaces for you to write your distributed PyTorch job in such a way that it can be run on multiple machines with elasticity; that is, your distributed job is able to start as soon as _min_ number of workers are present and allowed to grow up to _max_ number of workers without being stopped or restarted.

[](https://github.com/pytorch/elastic#use-cases)Use cases
---------------------------------------------------------

###### [](https://github.com/pytorch/elastic#fault-tolerant-jobs)Fault Tolerant Jobs

Jobs that run on infrastructure where nodes get replaced frequently, either due to flaky hardware or by design. Or mission critical production grade jobs that need to be run with resilience to failures.

###### [](https://github.com/pytorch/elastic#dynamic-capacity-management)Dynamic Capacity Management

Jobs that run on leased capacity that can be taken away at any time (e.g. AWS spot instances) or shared pools where the pool size can change dynamically based on demand.

[](https://github.com/pytorch/elastic#quickstart)Quickstart
-----------------------------------------------------------

Use one of the included examples and get a job running by following our [Quickstart guide](https://github.com/pytorch/elastic/blob/master/aws/README.md).

[](https://github.com/pytorch/elastic#requirements)Requirements
---------------------------------------------------------------

torchelastic requires

[](https://github.com/pytorch/elastic#installation)Installation
---------------------------------------------------------------

[](https://github.com/pytorch/elastic#how-torchelastic-works)How torchelastic works
-----------------------------------------------------------------------------------

torchelastic induces users to think about their PyTorch jobs as a `train_step` and `state`. It provides the basic control loop that repetitively executes the user provided `train_step` being aware of faults, exceptions, and cluster membership changes.

##### [](https://github.com/pytorch/elastic#train-step)Train Step

The `train_step` is a _unit of work_, typically (although not necessarily) mapping to the processing of a _mini-batch_ of training data. All `k` workers in a distributed torchelastic job run the `train_step()`, each contributing to the final output. What each worker does in a `train_step` and what input data it consumes is a user-defined.

In the simplest use-case, torchelastic drives the execution of `train_step` until either:

1.  the input data is exhausted
2.  an unrecoverable failure condition is encountered
3.  some other user-defined _end of job_ criteria is met

Each `train_step` may not be fully independent since the computations performed in the previous `train_step` can be used and/or updated in the next one. Information is carried across `train_step` calls using the `state` object.

##### [](https://github.com/pytorch/elastic#state)State

The `state`, as the name implies, is an object that carries persistent information throughout the lifetime of the job and is expected to be updated on each `train_step`. For example, in a training job, one of the information that the `state` carries is the model weights. In practice it contains other (meta)data that must be persisted between `train_steps`, for instance, the offset or index of the data stream. The `state` object is the only input parameter to the `train_step`.

##### [](https://github.com/pytorch/elastic#train-loop)Train Loop

The `train_step` is executed in a `train_loop` by torchelastic. The `train_loop` is a fancy `while`\-loop that enables the execution of the job with fault tolerance and elasticity. torchelastic works at `train_step` granularity, hence when a fault occurs **during** a `train_step` the computations performed during the failed `train_step` are considered lost and the state is restored to the previously succeeded `train_step`.

##### [](https://github.com/pytorch/elastic#rendezvous)Rendezvous

Torchelastic jobs define a `[min, max]` range of number of workers that it can run with. For instance, `[2, 10]` means that the job can start when **at least** two workers are present, and can be scaled **up to** ten workers at runtime.

Each time there is a change in membership in the set of workers, torchelastic runs a`rendezvous`, which serves the following purposes:

1.  **barrier** - all nodes will block until `rendezvous` is complete before resuming execution.
2.  **role assignment** - on each `rendezvous` each node is assigned a unique integer valued _rank_ between `[0, n)` where `n` is the world size (total number of workers).
3.  **world size broadcast** - on each `rendezvous` all nodes receive the new `world_size`.

The resource manager is free to add/remove instances from a torchelastic job as long as the total number of workers remain within `[2, 10]`. This is what we refer to as **elasticity**. Additionally, in the event of a worker node failure, as long as the failed node is replaced, torchelastic will detect this event as a membership change and admit the new worker into the group, making the job **fault-tolerant**.

For additional details refer to the [README](https://github.com/pytorch/elastic/blob/master/torchelastic/rendezvous/README.md) in the rendezvous module.

[](https://github.com/pytorch/elastic#usage)Usage
-------------------------------------------------

Please refer to the [usage documentation](https://github.com/pytorch/elastic/blob/master/USAGE.md) for details on how to write and configure a torchelastic job.

See the [CONTRIBUTING](https://github.com/pytorch/elastic/blob/master/CONTRIBUTING.md) file for how to help out.

[](https://github.com/pytorch/elastic#license)License
-----------------------------------------------------

torchelastic is BSD licensed, as found in the [LICENSE](https://github.com/pytorch/elastic/blob/master/LICENSE) file.

  
  
from Hacker News https://ift.tt/2Yr3AHk