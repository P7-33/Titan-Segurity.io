---
title: 'Visualizing Kubernetes History'
date: 2019-10-02T02:56:00+01:00
draft: false
---

[](https://github.com/salesforce/sloop#sloop---kubernetes-history-visualization)sloop - Kubernetes History Visualization
========================================================================================================================

Sloop monitors Kubernetes, recording histories of events and resource state changes and providing visualizations to aid in debugging past events.

Key features:

1.  Allows you to find and inspect resources that no longer exist (example: discover what host the pod from the previous deployment was using).
2.  Provides timeline displays that show rollouts of related resources in updates to Deployments, ReplicaSets, and StatefulSets.
3.  Helps debug transient and intermittent errors.
4.  Allows you to see changes over time in a Kubernetes application.
5.  Is a self-contained service with no dependencies on distributed storage.

[](https://github.com/salesforce/sloop#screenshots)Screenshots
--------------------------------------------------------------

[![Screenshot1](https://github.com/salesforce/sloop/raw/master/other/screenshot1.png?raw=true "Screenshot 1")](https://github.com/salesforce/sloop/blob/master/other/screenshot1.png?raw=true)

[](https://github.com/salesforce/sloop#architecture-overview)Architecture Overview
----------------------------------------------------------------------------------

[![Architecture](https://github.com/salesforce/sloop/raw/master/other/architecture.png?raw=true "Architecture")](https://github.com/salesforce/sloop/blob/master/other/architecture.png?raw=true)

[](https://github.com/salesforce/sloop#install)Install
------------------------------------------------------

Sloop can be installed using any of these options:

### [](https://github.com/salesforce/sloop#precompiled-binaries)Precompiled Binaries

_DockerHub images coming soon._

### [](https://github.com/salesforce/sloop#helm-chart)Helm Chart

_Helm chart coming soon._

### [](https://github.com/salesforce/sloop#build-from-source)Build from Source

Building Sloop from source needs a working Go environment with [version 1.13 or greater installed](https://golang.org/doc/install).

Clone the sloop repository and build using `make`:

```
$ mkdir -p $GOPATH/src/github.com/salesforce $ cd $GOPATH/src/github.com/salesforce $ git clone https://github.com/salesforce/sloop.git $ cd sloop $ make $ ~/go/bin/sloop
```

When complete, you should have a running Sloop version accessing the current context from your kubeConfig. Just point your browser at [http://localhost:8080/](http://localhost:8080/)

Other makefile targets:

*   _docker_: Builds a Docker image.
*   _cover_: Runs unit tests with code coverage.
*   _generate_: Updates genny templates for typed table classes.
*   _protobuf_: Generates protobuf code-gen.

### [](https://github.com/salesforce/sloop#local-docker-run)Local Docker Run

To run from Docker you need to host mount your kubeconfig:

```
$ make docker $ docker run --rm -it -p 8080:8080 -v ~/.kube/:/kube/ -e KUBECONFIG=/kube/config sloop
```

In this mode, data is written to a memory-backed volume and is discarded after each run. To preserve the data, you can host-mount /data with something like `-v /data/:/some_path_on_host/`

[](https://github.com/salesforce/sloop#contributing)Contributing
----------------------------------------------------------------

Refer to [CONTRIBUTING.md](https://github.com/salesforce/sloop/blob/master/CONTRIBUTING.md)

[](https://github.com/salesforce/sloop#license)License
------------------------------------------------------

BSD 3-Clause

  
  
from Hacker News https://github.com/salesforce/sloop