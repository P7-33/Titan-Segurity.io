---
title: 'KubeEdge: Kubernetes Native Edge Computing Framework (Project Under CNCF)'
date: 2020-01-06T05:08:00+01:00
draft: false
---

[](https://github.com/kubeedge/kubeedge#kubeedge)KubeEdge
=========================================================

[![Build Status](https://camo.githubusercontent.com/f99adfd07a2e094eea8a00d2164870ea305848d7/68747470733a2f2f7472617669732d63692e6f72672f6b756265656467652f6b756265656467652e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/kubeedge/kubeedge) [![Go Report Card](https://camo.githubusercontent.com/d4c062780a328643752265cba2f205a9b586a7a3/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f6769746875622e636f6d2f6b756265656467652f6b75626565646765)](https://goreportcard.com/report/github.com/kubeedge/kubeedge) [![LICENSE](https://camo.githubusercontent.com/49a0aa8472c3dffe675281479fa01bb71f4bccd7/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6c6963656e73652f6b756265656467652f6b756265656467652e7376673f7374796c653d666c61742d737175617265)](https://github.com/kubeedge/kubeedge/blob/master/LICENSE) [![Releases](https://camo.githubusercontent.com/032b9d206bb2bf38bfc1823078813d3bd087ccbe/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f6b756265656467652f6b756265656467652f616c6c2e7376673f7374796c653d666c61742d737175617265)](https://github.com/kubeedge/kubeedge/releases) [![Documentation Status](https://camo.githubusercontent.com/caff61a771d069d61fefe854ddc3df65423114b9/68747470733a2f2f72656164746865646f63732e6f72672f70726f6a656374732f6b756265656467652f62616467652f3f76657273696f6e3d6c6174657374)](https://kubeedge.readthedocs.io/en/latest/?badge=latest)

[![](https://github.com/kubeedge/kubeedge/raw/master/docs/images/KubeEdge_logo.png)](https://github.com/kubeedge/kubeedge/blob/master/docs/images/KubeEdge_logo.png)

KubeEdge is an open source system extending native containerized application orchestration and device management to hosts at the Edge. It is built upon Kubernetes and provides core infrastructure support for networking, application deployment and metadata synchronization between cloud and edge. It also supports **MQTT** and allows developers to author custom logic and enable resource constrained device communication at the Edge. KubeEdge consists of a cloud part and an edge part.

[](https://github.com/kubeedge/kubeedge#advantages)Advantages
-------------------------------------------------------------

#### [](https://github.com/kubeedge/kubeedge#edge-computing)Edge Computing

With business logic running at the Edge, much larger volumes of data can be secured & processed locally where the data is produced. Edge nodes can run autonomously which effectively reduces the network bandwidth requirements and consumptions between Edge and Cloud. With data processed at the Edge, the responsiveness is increased dramatically and data privacy is protected.

#### [](https://github.com/kubeedge/kubeedge#simplified-development)Simplified development

Developers can write regular http or mqtt based applications, containerize them, and run them anywhere - either at the Edge or in the Cloud - whichever is more appropriate.

#### [](https://github.com/kubeedge/kubeedge#kubernetes-native-support)Kubernetes-native support

With KubeEdge, users can orchestrate apps, manage devices and monitor app and device status on Edge nodes just like a traditional Kubernetes cluster in the Cloud. Locations of edge nodes are transparent to customers.

#### [](https://github.com/kubeedge/kubeedge#abundant-applications)Abundant applications

It is easy to get and deploy existing complicated machine learning, image recognition, event processing and other high level applications to the Edge.

[](https://github.com/kubeedge/kubeedge#introduction)Introduction
-----------------------------------------------------------------

KubeEdge is composed of the following components:

### [](https://github.com/kubeedge/kubeedge#cloud-part)Cloud Part

*   [CloudHub](https://github.com/kubeedge/kubeedge/blob/master/docs/modules/cloud/cloudhub.md): a web socket server responsible for watching changes at the cloud side, caching and sending messages to EdgeHub.
*   [EdgeController](https://github.com/kubeedge/kubeedge/blob/master/docs/modules/cloud/controller.md): an extended kubernetes controller which manages edge nodes and pods metadata so that the data can be targeted to a specific edge node.
*   [DeviceController](https://github.com/kubeedge/kubeedge/blob/master/docs/modules/cloud/device_controller.md): an extended kubernetes controller which manages devices so that the device metadata/status data can be synced between edge and cloud.

### [](https://github.com/kubeedge/kubeedge#edge-part)Edge Part

*   [EdgeHub](https://github.com/kubeedge/kubeedge/blob/master/docs/modules/edge/edgehub.md): a web socket client responsible for interacting with Cloud Service for the edge computing (like Edge Controller as in the KubeEdge Architecture). This includes syncing cloud-side resource updates to the edge, and reporting edge-side host and device status changes to the cloud.
*   [Edged](https://github.com/kubeedge/kubeedge/blob/master/docs/modules/edge/edged.md): an agent that runs on edge nodes and manages containerized applications.
*   [EventBus](https://github.com/kubeedge/kubeedge/blob/master/docs/modules/edge/eventbus.md): a MQTT client to interact with MQTT servers (mosquitto), offering publish and subscribe capabilities to other components.
*   ServiceBus: a HTTP client to interact with HTTP servers (REST), offering HTTP client capabilities to components of cloud to reach HTTP servers running at edge.
*   [DeviceTwin](https://github.com/kubeedge/kubeedge/blob/master/docs/modules/edge/devicetwin.md): responsible for storing device status and syncing device status to the cloud. It also provides query interfaces for applications.
*   [MetaManager](https://github.com/kubeedge/kubeedge/blob/master/docs/modules/edge/metamanager.md): the message processor between edged and edgehub. It is also responsible for storing/retrieving metadata to/from a lightweight database (SQLite).

### [](https://github.com/kubeedge/kubeedge#architecture)Architecture

[![](https://github.com/kubeedge/kubeedge/raw/master/docs/images/kubeedge_arch.png)](https://github.com/kubeedge/kubeedge/blob/master/docs/images/kubeedge_arch.png)

[](https://github.com/kubeedge/kubeedge#compatibility-matrix)Compatibility matrix
---------------------------------------------------------------------------------

### [](https://github.com/kubeedge/kubeedge#kubernetes-compatibility)Kubernetes compatibility

Kubernetes 1.10

Kubernetes 1.11

Kubernetes 1.12

Kubernetes 1.13

Kubernetes 1.14

Kubernetes 1.15

Kubernetes 1.16

KubeEdge 1.0

✓

✓

✓

✓

✓

✓

\-

KubeEdge 1.1

+

✓

✓

✓

✓

✓

✓

KubeEdge HEAD

+

✓

✓

✓

✓

✓

✓

Key:

*   `✓` KubeEdge and the Kubernetes version are exactly compatible.
*   `+` KubeEdge has features or API objects that may not be present in the Kubernetes version.
*   `-` The Kubernetes version has features or API objects that KubeEdge can't use.

### [](https://github.com/kubeedge/kubeedge#golang-dependency)Golang dependency

Golang 1.10

Golang 1.11

Golang 1.12

Golang 1.13

KubeEdge 1.0

✓

✓

✓

✗

KubeEdge 1.1

✗

✗

✓

✗

KubeEdge HEAD

✗

✗

✓

✗

[](https://github.com/kubeedge/kubeedge#to-start-developing-kubeedge)To start developing KubeEdge
-------------------------------------------------------------------------------------------------

The [set up](https://github.com/kubeedge/kubeedge/blob/master/docs/setup/setup.md) hosts all information about building KubeEdge from source, how to setup. etc.

To build KubeEdge from source there is one option:

```
mkdir -p $GOPATH/src/github.com/kubeedge cd $GOPATH/src/github.com/kubeedge git clone git@github.com:kubeedge/kubeedge.git # If you only want to compile quickly without using go mod, please set GO111MODULE=off (e.g. export GO111MODULE=off) cd kubeedge make 
```

[](https://github.com/kubeedge/kubeedge#usage)Usage
---------------------------------------------------

[](https://github.com/kubeedge/kubeedge#roadmap)Roadmap
-------------------------------------------------------

[](https://github.com/kubeedge/kubeedge#meeting)Meeting
-------------------------------------------------------

Regular Community Meeting: Wednesday at 16:30 Beijing Time (biweekly).

[](https://github.com/kubeedge/kubeedge#documentation)Documentation
-------------------------------------------------------------------

The detailed documentation for KubeEdge and its modules can be found at [https://docs.kubeedge.io](https://docs.kubeedge.io). Some sample applications and demos to illustrate possible use cases of KubeEdge platform can be found at this [examples](https://github.com/kubeedge/examples) repository.

[](https://github.com/kubeedge/kubeedge#contact)Contact
-------------------------------------------------------

If you have questions, feel free to reach out to us in the following ways:

[](https://github.com/kubeedge/kubeedge#contributing)Contributing
-----------------------------------------------------------------

If you're interested in being a contributor and want to get involved in developing the KubeEdge code, please see [CONTRIBUTING](https://github.com/kubeedge/kubeedge/blob/master/CONTRIBUTING.md) for details on submitting patches and the contribution workflow.

[](https://github.com/kubeedge/kubeedge#license)License
-------------------------------------------------------

KubeEdge is under the Apache 2.0 license. See the [LICENSE](https://github.com/kubeedge/kubeedge/blob/master/LICENSE) file for details.

  
  
from Hacker News https://ift.tt/2Fpx16C