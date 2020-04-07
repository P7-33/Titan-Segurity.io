---
title: 'K3c – Classic Docker for a Kubernetes World'
date: 2020-01-14T03:22:00+01:00
draft: false
---

![](https://avatars2.githubusercontent.com/u/1754002?s=400&v=4 "GitHub - ibuildthecloud/k3c: Lightweight local container engine for container development")  

[](https://github.com/ibuildthecloud/k3c#k3c---classic-docker-for-a-kubernetes-world)k3c - Classic Docker for a Kubernetes world
================================================================================================================================

_**STATUS: EXPERIMENT - Let me know what you think**_

`k3c` is a local container engine designed to fill the same gap Docker does in the Kubernetes ecosystem. Specifically `k3c` focuses on developing and running local containers, basically `docker run/build`. Currently `k3s`, the [lightweight Kubernetes distribution](https://github.com/rancher/k3s), provides a great solution for Kubernetes from dev to production. While `k3s` satisifies the Kubernetes runtime needs, one still needs to run `docker` (or a docker-like tool) to actually develop and build the container images. `k3c` is intended to replace `docker` for just the functionality needed for the Kubernetes ecosystem.

[](https://github.com/ibuildthecloud/k3c#a-familiar-ux)A familiar UX
--------------------------------------------------------------------

There really is nothing better than the classic Docker UX of `run/build/push/pull`. This tool copies the same UX as classic Docker (think Docker v1.12). The intention is to follow the same style but not be a 100% drop in replacement. Behaviour and arguements have been changed to better match the behavior of the Kubernetes ecosystem. One change, for example, is that start/restart will always give you a fresh container because pods in Kubernetes are always ephemeral.

[](https://github.com/ibuildthecloud/k3c#a-single-binary)A single binary
------------------------------------------------------------------------

`k3c`, similar to `k3s` and old school docker, is packaged as a single binary, because nothing is easier than a static binary for distribution.

[](https://github.com/ibuildthecloud/k3c#built-on-kubernetes-tech-and-others)Built on Kubernetes Tech (and others)
------------------------------------------------------------------------------------------------------------------

Fundamentally `k3c` is a built on the [Container Runtime Interface (CRI)](https://github.com/kubernetes/cri-api). In fact it's really like a nicer version of of [cri-tool](https://github.com/kubernetes-sigs/cri-tools). CRI doesn't cover image building and some other small image tasks like tag and push. For image building Moby's [buildkit](https://github.com/moby/buildkit) is used internally, and for other things OCI's [containerd](https://github.com/containerd/containerd) is used.

[](https://github.com/ibuildthecloud/k3c#architecture)Architecture
------------------------------------------------------------------

`k3c` runs as a daemon either as root or one per user for rootless support. **NOTE: root less isn't currently working, that's just the design right now**. The daemon exposes a GRPC API. For building the buildkit API is just exposed directly from the k3c socket. `containerd`, `buildkitd`, and `containerd-cri` are all embedded directly into the k3c binary.

[](https://github.com/ibuildthecloud/k3c#running)Running
--------------------------------------------------------

Start the daemon as root (rootless will be supported in the future if this project takes off)

Run containers like you would with `docker`

```
$ ./k3c --help NAME: k3c - Lightweight local container platform USAGE: k3c [global options] command [command options] [arguments...] VERSION: dev (HEAD) COMMANDS: create Create a new container attach Attach local standard input, output, and error streams to a running container stop Stop one or more running containers start Start one or more stopped containers logs Fetch the logs of a container rm Remove one or more containers exec Run a command in a running container run Run a command in a new container ps List containers build Build an image from a Dockerfile images List images tag Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE pull Pull an image or a repository from a registry rmi Remove one or more images push Push an image or a repository to a registry inspect Return low-level information on k3c objects events Get real time events from the server daemon Run the container daemon volume, volumes, v Manage volumes help, h Shows a list of commands or help for one command 
```

[](https://github.com/ibuildthecloud/k3c#roadmap)Roadmap
--------------------------------------------------------

Right now this is just an experiment. If there is sufficient interest I expect I'll integrate `k3s` + `k3c` + `k3os` + `k3d` to create a full `k3` end to end container solution that will fully encompass all aspects of the container development life cycle.

Windows and macOS can be fully supported to in the future.

[](https://github.com/ibuildthecloud/k3c#license)License
========================================================

Copyright (c) 2014-2020 [Rancher Labs, Inc.](http://rancher.com)

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

  
  
from Hacker News https://ift.tt/2QTDfjb