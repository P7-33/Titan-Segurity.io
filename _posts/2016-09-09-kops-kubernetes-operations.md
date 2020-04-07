---
title: 'Kops – Kubernetes Operations'
date: 2020-01-22T04:53:00+01:00
draft: false
---

[![kops logo](https://github.com/kubernetes/kops/raw/master/docs/img/logo.jpg)](https://github.com/kubernetes/kops/blob/master/docs/img/logo.jpg)

[](https://github.com/kubernetes/kops#kops---kubernetes-operations)kops - Kubernetes Operations
===============================================================================================

[![Build Status](https://camo.githubusercontent.com/ca4e5145e81842e1e4aeb4cc93a324ba34b2be5f/68747470733a2f2f7472617669732d63692e6f72672f6b756265726e657465732f6b6f70732e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/kubernetes/kops) [![Go Report Card](https://camo.githubusercontent.com/e261ce862ac98cd33be3d1a9aaf43d7b60e9bfda/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f6b38732e696f2f6b6f7073)](https://goreportcard.com/report/k8s.io/kops) [![GoDoc Widget](https://camo.githubusercontent.com/c95b5a3ef78ab849474dba23f1a240b36f0c9a3e/68747470733a2f2f676f646f632e6f72672f6b38732e696f2f6b6f70733f7374617475732e737667)](https://godoc.org/k8s.io/kops)

The easiest way to get a production grade Kubernetes cluster up and running.

[](https://github.com/kubernetes/kops#what-is-kops)What is kops?
----------------------------------------------------------------

We like to think of it as `kubectl` for clusters.

`kops` helps you create, destroy, upgrade and maintain production-grade, highly available, Kubernetes clusters from the command line. AWS (Amazon Web Services) is currently officially supported, with GCE and OpenStack in beta support, and VMware vSphere in alpha, and other platforms planned.

[](https://github.com/kubernetes/kops#can-i-see-it-in-action)Can I see it in action?
------------------------------------------------------------------------------------

[![](https://camo.githubusercontent.com/4d96844924e8447fe6f19ddd4e6328ce8264c2ec/68747470733a2f2f61736369696e656d612e6f72672f612f39373239382e706e67)](https://asciinema.org/a/97298)

[](https://github.com/kubernetes/kops#launching-a-kubernetes-cluster-hosted-on-aws-gce-digitalocean-or-openstack)Launching a Kubernetes cluster hosted on AWS, GCE, DigitalOcean or OpenStack
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

To replicate the above demo, check out our [tutorial](https://github.com/kubernetes/kops/blob/master/docs/getting_started/aws.md) for launching a Kubernetes cluster hosted on AWS.

To install a Kubernetes cluster on GCE please follow this [guide](https://github.com/kubernetes/kops/blob/master/docs/getting_started/gce.md).

To install a Kubernetes cluster on DigitalOcean, follow this [guide](https://github.com/kubernetes/kops/blob/master/docs/getting_started/digitalocean.md).

To install a Kubernetes cluster on OpenStack, follow this [guide](https://github.com/kubernetes/kops/blob/master/docs/getting_started/openstack.md).

**For anything beyond experimental clusters it is highly encouraged to [version control the cluster manifest files](https://github.com/kubernetes/kops/blob/master/docs/manifests_and_customizing_via_api.md) and [run kops in a CI environment](https://github.com/kubernetes/kops/blob/master/docs/continuous_integration.md).**

[](https://github.com/kubernetes/kops#features)Features
-------------------------------------------------------

*   Automates the provisioning of Kubernetes clusters in [AWS](https://github.com/kubernetes/kops/blob/master/docs/getting_started/aws.md), [OpenStack](https://github.com/kubernetes/kops/blob/master/docs/getting_started/openstack.md) and [GCE](https://github.com/kubernetes/kops/blob/master/docs/getting_started/gce.md)
*   Deploys Highly Available (HA) Kubernetes Masters
*   Built on a state-sync model for **dry-runs** and automatic **idempotency**
*   Ability to generate [Terraform](https://github.com/kubernetes/kops/blob/master/docs/terraform.md)
*   Supports custom Kubernetes [add-ons](https://github.com/kubernetes/kops/blob/master/docs/operations/addons.md)
*   Command line [autocompletion](https://github.com/kubernetes/kops/blob/master/docs/cli/kops_completion.md)
*   YAML Manifest Based API [Configuration](https://github.com/kubernetes/kops/blob/master/docs/manifests_and_customizing_via_api.md)
*   [Templating](https://github.com/kubernetes/kops/blob/master/docs/cluster_template.md) and dry-run modes for creating Manifests
*   Choose from eight different CNI [Networking](https://github.com/kubernetes/kops/blob/master/docs/networking.md) providers out-of-the-box
*   Supports upgrading from [kube-up](https://github.com/kubernetes/kops/blob/master/docs/upgrade_from_kubeup.md)
*   Capability to add containers, as hooks, and files to nodes via a [cluster manifest](https://github.com/kubernetes/kops/blob/master/docs/cluster_spec.md)

[](https://github.com/kubernetes/kops#documentation)Documentation
-----------------------------------------------------------------

Documentation is in the `/docs` directory, and can be seen at [kops.sigs.k8s.io](https://kops.sigs.k8s.io/).

[](https://github.com/kubernetes/kops#kubernetes-release-compatibility)Kubernetes Release Compatibility
-------------------------------------------------------------------------------------------------------

### [](https://github.com/kubernetes/kops#kubernetes-version-support)Kubernetes Version Support

kops is intended to be backward compatible. It is always recommended to use the latest version of kops with whatever version of Kubernetes you are using. We suggest kops users run one of the [3 minor versions](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew) Kubernetes is supporting however we do our best to support previous releases for a period of time.

One exception, in regard to compatibility, kops supports the equivalent Kubernetes minor release number. A minor version is the second digit in the release number. kops version 1.13.0 has a minor version of 13. The numbering follows the semantic versioning specification, MAJOR.MINOR.PATCH.

For example, kops 1.12.0 does not support Kubernetes 1.13.0, but kops 1.13.0 supports Kubernetes 1.12.2 and previous Kubernetes versions. Only when the kops minor version matches the Kubernetes minor version does kops officially support the Kubernetes release. kops does not stop a user from installing mismatching versions of K8s, but Kubernetes releases always require kops to install specific versions of components like docker, that tested against the particular Kubernetes version.

#### [](https://github.com/kubernetes/kops#compatibility-matrix)Compatibility Matrix

kops version

k8s 1.11.x

k8s 1.12.x

k8s 1.13.x

k8s 1.14.x

k8s 1.15.x

1.15.0

✔

✔

✔

✔

✔

1.14.x

✔

✔

✔

✔

⚫

1.13.x

✔

✔

✔

⚫

⚫

1.12.x

✔

✔

⚫

⚫

⚫

1.11.x

✔

⚫

⚫

⚫

⚫

Use the latest version of kops for all releases of Kubernetes, with the caveat that higher versions of Kubernetes are not _officially_ supported by kops. Releases who are crossed out _should_ work but we suggest should be upgraded soon.

### [](https://github.com/kubernetes/kops#kops-release-schedule)kops Release Schedule

This project does not follow the Kubernetes release schedule. `kops` aims to provide a reliable installation experience for kubernetes, and typically releases about a month after the corresponding Kubernetes release. This time allows for the Kubernetes project to resolve any issues introduced by the new version and ensures that we can support the latest features. kops will release alpha and beta pre-releases for people that are eager to try the latest Kubernetes release. Please only use pre-GA kops releases in environments that can tolerate the quirks of new releases, and please do report any issues encountered.

[](https://github.com/kubernetes/kops#installing)Installing
-----------------------------------------------------------

### [](https://github.com/kubernetes/kops#prerequisite)Prerequisite

`kubectl` is required, see [here](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

### [](https://github.com/kubernetes/kops#osx-from-homebrew)OSX From Homebrew

```
brew update && brew install kops
```

The `kops` binary is also available via our [releases](https://github.com/kubernetes/kops/releases/latest).

### [](https://github.com/kubernetes/kops#linux)Linux

```
curl -LO https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag\_name | cut -d '"' -f 4)/kops-linux-amd64 chmod +x kops-linux-amd64 sudo mv kops-linux-amd64 /usr/local/bin/kops
```

### [](https://github.com/kubernetes/kops#windows)Windows

1.  Get `kops-windows-amd64` from our [releases](https://github.com/kubernetes/kops/releases/latest).
2.  Rename `kops-windows-amd64` to `kops.exe` and store it in a preferred path.
3.  Make sure the path you chose is added to your `Path` environment variable.

[](https://github.com/kubernetes/kops#release-history)Release History
---------------------------------------------------------------------

See the [releases](https://github.com/kubernetes/kops/releases) for more information on changes between releases.

[](https://github.com/kubernetes/kops#getting-involved-and-contributing)Getting Involved and Contributing
---------------------------------------------------------------------------------------------------------

Are you interested in contributing to kops? We, the maintainers and community, would love your suggestions, contributions, and help! We have a quick-start guide on [adding a feature](https://github.com/kubernetes/kops/blob/master/docs/development/adding_a_feature.md). Also, the maintainers can be contacted at any time to learn more about how to get involved.

In the interest of getting more newer folks involved with kops, we are starting to tag issues with `good-starter-issue`. These are typically issues that have smaller scope but are good ways to start to get acquainted with the codebase.

We also encourage ALL active community participants to act as if they are maintainers, even if you don't have "official" write permissions. This is a community effort, we are here to serve the Kubernetes community. If you have an active interest and you want to get involved, you have real power! Don't assume that the only people who can get things done around here are the "maintainers".

We also would love to add more "official" maintainers, so show us what you can do!

What this means:

**Issues**

*   Help read and triage issues, assist when possible.
*   Point out issues that are duplicates, out of date, etc.
    *   Even if you don't have tagging permissions, make a note and tag maintainers (`/close`,`/dupe #127`).

**Pull Requests**

*   Read and review the code. Leave comments, questions, and critiques (`/lgtm` ).
*   Download, compile, and run the code and make sure the tests pass (make test).
    *   Also verify that the new feature seems sane, follows best architectural patterns, and includes tests.

This repository uses the Kubernetes bots. See a full list of the commands [here](https://go.k8s.io/bot-commands).

[](https://github.com/kubernetes/kops#office-hours)Office Hours
---------------------------------------------------------------

Kops maintainers set aside one hour every other week for **public** office hours. This time is used to gather with community members interested in kops. This session is open to both developers and users.

Office hours are hosted on a [zoom video chat](https://zoom.us/my/k8ssigaws) on Fridays at [12 noon (Eastern Time)/9 am (Pacific Time)](https://www.worldtimebuddy.com/?pl=1&lid=100,5,8,12) during weeks with odd "numbers". To check this weeks' number, run: `date +%V`. If the response is odd, join us on Friday for office hours!

### [](https://github.com/kubernetes/kops#office-hours-topics)Office Hours Topics

We do maintain an [agenda](https://docs.google.com/document/d/12QkyL0FkNbWPcLFxxRGSPt_tNPBHbmni3YLY-lHny7E/edit) and stick to it as much as possible. If you want to hold the floor, put your item in this doc. Bullet/note form is fine. Even if your topic gets in late, we do our best to cover it.

Our office hours call is recorded, but the tone tends to be casual. First-timers are always welcome. Typical areas of discussion can include:

*   Contributors with a feature proposal seeking feedback, assistance, etc
*   Members planning for what we want to get done for the next release
*   Strategizing for larger initiatives, such as those that involve more than one sig or potentially more moving pieces
*   Help wanted requests
*   Demonstrations of cool stuff. PoCs. Fresh ideas. Show us how you use kops to go beyond the norm- help us define the future!

Office hours are designed for ALL of those contributing to kops or the community. Contributions are not limited to those who commit source code. There are so many important ways to be involved-

*   helping in the slack channels
*   triaging/writing issues
*   thinking about the topics raised at office hours and forming and advocating for your good ideas forming opinions
*   testing pre-(and official) releases

Although not exhaustive, the above activities are extremely important to our continued success and are all worth contributions. If you want to talk about kops and you have doubt, just come.

### [](https://github.com/kubernetes/kops#other-ways-to-communicate-with-the-contributors)Other Ways to Communicate with the Contributors

Please check in with us in the [#kops-users](https://kubernetes.slack.com/messages/kops-users/) or [#kops-dev](https://kubernetes.slack.com/messages/kops-dev/) channel. Often-times, a well crafted question or potential bug report in slack will catch the attention of the right folks and help quickly get the ship righted.

[](https://github.com/kubernetes/kops#github-issues)GitHub Issues
-----------------------------------------------------------------

### [](https://github.com/kubernetes/kops#bugs)Bugs

If you think you have found a bug please follow the instructions below.

*   Please spend a small amount of time giving due diligence to the issue tracker. Your issue might be a duplicate.
*   Set `-v 10` command line option and save the log output. Please paste this into your issue.
*   Note the version of kops you are running (from `kops version`), and the command line options you are using.
*   Open a [new issue](https://github.com/kubernetes/kops/issues/new).
*   Remember users might be searching for your issue in the future, so please give it a meaningful title to help others.
*   Feel free to reach out to the kops community on [kubernetes slack](https://github.com/kubernetes/community/blob/master/communication.md#social-media).

### [](https://github.com/kubernetes/kops#features-1)Features

We also use the issue tracker to track features. If you have an idea for a feature, or think you can help kops become even more awesome follow the steps below.

*   Open a [new issue](https://github.com/kubernetes/kops/issues/new).
*   Remember users might be searching for your issue in the future, so please give it a meaningful title to help others.
*   Clearly define the use case, using concrete examples. EG: I type `this` and kops does `that`.
*   Some of our larger features will require some design. If you would like to include a technical design for your feature please include it in the issue.
*   After the new feature is well understood, and the design agreed upon we can start coding the feature. We would love for you to code it. So please open up a **WIP** _(work in progress)_ pull request, and happy coding.

  
  
from Hacker News https://ift.tt/298XsID