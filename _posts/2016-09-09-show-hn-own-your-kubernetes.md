---
title: 'Show HN: Own your Kubernetes: installation, addons, best practices – as code'
date: 2019-11-02T06:12:00+01:00
draft: false
---

[](https://github.com/ReSearchITEng/kubeadm-playbook/#update-status-of-the-project-stable)Update Status of the project: Stable
==============================================================================================================================

[kubeadm-playboook ansible project's code is on Github](https://github.com/ReSearchITEng/kubeadm-playbook)

[](https://github.com/ReSearchITEng/kubeadm-playbook/#quick-explanation)Quick explanation
=========================================================================================

[https://medium.com/@re.search.it.eng/batteries-included-kubernetes-for-everyone-bccf9b8558dd](https://medium.com/@re.search.it.eng/batteries-included-kubernetes-for-everyone-bccf9b8558dd)

[](https://github.com/ReSearchITEng/kubeadm-playbook/#what-is-it)What is it:
============================================================================

For 3 years we keep on gathering best guidelines and growing this project for best kubernetes **cluster installation + addons**. It's gluing: kubeadm, offical helm charts for various addons, fine-tunings from docs and best practices.

All based purely on kubeadm and official helm charts.  
It tries to bring together most (if not all) the steps to get from a freshly installed linux to a working k8s cluster.  
Its vision is to find and integrate the best tools out there (while using KISS priciple).

[](https://github.com/ReSearchITEng/kubeadm-playbook/#why)Why
=============================================================

Going beyond minikube, making your own (usually on prem) k8s cluster (with the usuall addons installed) is still too hard or needlesly complex. Kubeadm is so strong now, that complex projects don't make sense.  
The we felt that what is missing is getting things before and after the cluster installation, to get an initial (but reasonable) platform up.

[](https://github.com/ReSearchITEng/kubeadm-playbook/#what-it-makes-it-different)What it makes it different:
============================================================================================================

*   pure kubeadm based (all needless complexity removed); the stronger kubeadm will be, the smaller this project!
*   kubernetes cluster platform: not only k8s, but also the importand addons
*   this project does not hold any "custom" addon, everything that is installed is fetched directly their official repos (mostly helm repos)
*   drives users towards good practices: e.g. segregate nodes in 3 categories (when possible): masters, infra, compute; (infra holds ingress controller, prometheus, grafana, and similar support tools)
*   optionally, when docker\_setup enabled, this project will also setup the docker with known kernel params for os (those from the k8s docs).
*   focused on "on-prem" deployments (but still accepts anything kubeadm can do); (vmware vsphere storage integration is actively used).
*   generates any cluster size, from 1 machine cluster (dev env) to productions sizes: all controlled by the provided inventory.
*   scale UP or DOWN post deployment (e.g. start small with 1 vm, then add nodes, then make multi-master) -> all without downtime thanks to kubeadm.
*   Master HA & ingress setups accepts either: VIPs (using keepalived) or Hardware LB (when available);
*   enterprise-friendly: fully tested with http\_proxy and private docker registry (usually private nexus registry proxy registry of docker.io, quay.io, k8s.gcr.io, etc; private mirror hostname&port fully configurable in this project)
*   actively tested on both Ubuntu/Debian and CentOS/RHEL.
*   any helm chart can be configured/added/removed via addons.yml (more detailed comparison with other solutions towards the end of this readme)

[](https://github.com/ReSearchITEng/kubeadm-playbook/#what-is-in-plan)What is in plan
=====================================================================================

1.  Authentication via LDAP (in plan KeyCloak); integrate it in dashboard, grafana, etc.
2.  Move from heapster to metrics server (once it will be stable)
3.  Logging stack (e.g. EFK - currently helm charts are not fully stable) (PRs are welcome :)

[](https://github.com/ReSearchITEng/kubeadm-playbook/#since-when)Since when
===========================================================================

Started years back. Battle tested on for all Centos/RHEL 7.2+ till 7.6 and Ubuntu 16.04,18.04,19.10 (both with overlay2 and automatic docker\_setup).  
Actively used on a daily basis and tested with k8s starting 1.7 till 1.16.

[](https://github.com/ReSearchITEng/kubeadm-playbook/#targetsproscons)Targets/pros&cons
---------------------------------------------------------------------------------------

Kubeadm simplifies drastically the installation, so for BYO (vms,desktops,baremetal), complex projects like kubespray/kops are not required any longer. Major difference from other projects: it uses kubeadm for all activities, and kubernetes is running in containers.  
The project is for those who want to create&recreate k8s cluster using the official method (kubeadm), with all production features:

*   creates Highly Available (HA cluster - multi master) (using VIPs) - using kubeadm
*   KISS: it's build for kubeadm only (no other complexities arount it)
*   plays nicely for corporate env: allows use of internal registry for images (insted of using internet connection)
*   plays nicely for corporate env: works via proxy
*   prepares your machines (e.g. kernel params like: net.bridge.bridge-nf-call-iptables, etc.)
*   it tries to use modern methods of deploying the "addons". E.g. heapster, ingress, prometheus, etc -> all via helm. Pure and clean:
*   Ingresses (via helm chart)
*   Persistent storage (vsphere/ceph/nfs) (vsphere up to date, rook.io (ceph) needs updates; NFS not actively tested)
*   dashboard (via helm chart)
*   heapster (via helm chart)
*   supports proxy
*   modular, clean code, supporting multiple activies by using ansible tags (e.g. add/reset a subgroup of nodes).
*   optionally help configuring container engine (e.g. docker)

This project targets to get a fully working environment in matter of minutes on any hw: baremetal, vms (vsphere, virtualbox), etc.

### [](https://github.com/ReSearchITEng/kubeadm-playbook/#what-it-does-not-do)What it does not do:

*   k8s version upgrades: while many of its roles can be used for an upgrade, upgrade should be done using kubeadm tool. Kubeadm upgrade is pretty clear and simple, there is no need for much automation around it. If you think otherwise, let us know.

### [](https://github.com/ReSearchITEng/kubeadm-playbook/#pros)PROS:

*   quick (~10 min) full cluster installation
*   all in one shop for a cluster which you can start working right away, without mastering the details
*   applies fixes for quite few issues currently k8s installers have
*   deploys plugins to all creation of dynamical persistent volumes via: vsphere, rook or self deployed NFS
*   kubeadm is the only official tool specialized to install k8s
*   proxy is supported; It can work even no internet access required (when there is internal registry)

### [](https://github.com/ReSearchITEng/kubeadm-playbook/#consfuture-versions)CONS/future versions:

*   old k8s versions (13 and older): for HA Master, Only VIP is supported -> LB support for HA Master was not tested (try to use v1.14 and above).
*   While for installing the cluster there is no need for internet access, the addons which come as helm charts by default look for their images on the internet (but charts have to be either cached or come from an internal helm repo). To take images from on-prem, please update the group\_vars/all/addons.yaml to point to local registry version of the image.

[](https://github.com/ReSearchITEng/kubeadm-playbook/#prerequisites)Prerequisites:
----------------------------------------------------------------------------------

*   ansible min. 2.3 (but higher is recommeneded. Tested on 2.5+)
*   For a perfect experience, one should at least define a wildcard dns subdomain, to easily access the ingresses. The wildcard can pointed to the master (as it's quaranteed to exists).  
    Note: dashboard will by default use the master machine, but also deploy under the provided domain (in parallel, only additional ingress rule)
*   if docker\_setup is True, it will also attempt to define your docker and set it up with overlay2 storage driver (one needs CentOS 7.4+)
*   it will set required kernel modules (if desired)
*   if one needs ceph(rook) persistent storage, disks or folders should be prepared and properly sized (e.g. /storage/rook)

[](https://github.com/ReSearchITEng/kubeadm-playbook/#this-playbook-will)This playbook will:
--------------------------------------------------------------------------------------------

*   pre-sanity: docker sanity
*   kernel modules (load & setup for every restart)
*   Install ntp (to keep time in sync within cluster) (control via `group_vars/all`)
*   Install the kubeadm repo
*   Install kubeadm, kubelet, kubernetes-cni, and kubectl
*   If desired, manipulate SELinux setting (control via `group_vars/all`)
*   Set kubelet `--cgroup-driver=systemd` , swap-off, and many other settings required by kubelet to work (control via `group_vars/all`)
*   Reset activities (like kubeadm reset, unmount of `/var/lib/kubelet/*` mounts, ip link delete cbr0, cni0 , etc.) - important for reinstallations.
*   Initialize the cluster on master with `kubeadm init`
*   Install user specified pod network from `group_vars/all` (flannel, calico, weave, etc)
*   Join the nodes to the cluster with 'kubeadm join' and full set of params.
*   Install helm
*   Install nginx ingress controller via helm (control via `group_vars/all`)
*   Install kubernetes dashboard (via helm)
*   Installs any listed helm charts in the config (via helm)
*   Installs any yaml listed in the config
*   Planned: Install prometheus via Helm (control via `group_vars/all`) -> prometheus operator helm chart is expected soon,
*   Sanity: checks if nodes are ready and if all pods are running, and provides details of the cluster.
*   when enabled, it will create ceph storage cluster using rook operator
*   when enabled, it will create vsphere persistent storage class and all required setup. Please fill in vcenter u/p/url,etc `group_vars/all`, and follow all initial steps there.
*   it will define a set of handy aliases

NOTE: It does support **http\_proxy** configuration cases. Simply update the your proxy in the group\_vars/all.  
This has been tested with **RHEL&CentOS 7.3-7.6 and Ubuntu 16.04** and **Kubernetes v1.6.1 - v1.13.4**  
In general, keep the kube\* tools at the same minor version with the desired k8s cluster. (e.g. For installing k8s v1.7 one must also use kubeadm 1.7 (kubeadm limitation).)  
FYI, higher kube\* are usually supported with 1 minor version older cluster (e.g. kube\[adm/ctl/let\] 1.8.\* accepts kubernetes cluster 1.7.\*).

If for any reason anyone needs to relax RBAC, they can do: `kubectl create -f https://github.com/ReSearchITEng/kubeadm-playbook/blob/master/allow-all-all-rbac.yml`

[](https://github.com/ReSearchITEng/kubeadm-playbook/#how-to-use)How To Use:
============================================================================

[](https://github.com/ReSearchITEng/kubeadm-playbook/#use-the-right-releasebranch)Use the right release/branch
--------------------------------------------------------------------------------------------------------------

Use the release/branch that fits your k8s version needs. While master may have additinal features, it's as tested as the releases.

[](https://github.com/ReSearchITEng/kubeadm-playbook/#full-cluster-installation)Full cluster installation
---------------------------------------------------------------------------------------------------------

```
git clone https://github.com/ReSearchITEng/kubeadm-playbook.git cd kubeadm-playbook/ cp hosts.example hosts vi hosts <add hosts\> # Setul vars in group\_vars vi group\_vars/all/\* <modify vars as needed\> ansible-playbook -i hosts site.yml \[--skip-tags "docker,prepull\_images,kubelet"\]
```

If there are any issues, you may want to run only some of the steps, by choosing the appropriate tags to run. Read the site.yml. Here are also some explanations of important steps:

*   reset any previous cluster, delete etcd, cleanup network, etc. (role/tag: reset)
*   common section which prepares all machines (e.g. docker if required, kernel modules, etc) (role: common)
*   install etcd (role/tag: etcd) (requried only when you have HA only)
*   install master (role/tag: master)
*   install nodes (role/tag: node)
*   install network, helm, ingresses, (role/tag: post\_deploy)

[](https://github.com/ReSearchITEng/kubeadm-playbook/#add-manage-addreinstall-nodes)Add manage (add/reinstall) nodes:
---------------------------------------------------------------------------------------------------------------------

*   modify inventory (**hosts** file), and leave the primary-master intact, but for nodes, keep _ONLY_ the nodes to be managed (added/reset)
*   `ansible-playbook -i hosts site.yml --tags node` ; More in the docs section.

[](https://github.com/ReSearchITEng/kubeadm-playbook/#to-remove-a-specific-node-drains-and-afterwards-kube-resets-etc)To remove a specific node (drains and afterwards kube resets, etc)
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

*   modify inventory (**hosts** file), and leave the master intact, but for nodes, keep _ONLY_ the nodes to be removed
*   `ansible-playbook -i hosts site.yml --tags node_reset`

[](https://github.com/ReSearchITEng/kubeadm-playbook/#other-activities-possible)Other activities possible:
----------------------------------------------------------------------------------------------------------

There are other operations possible against the cluster, look at the file: site.yml and decide. Few more examples of useful tags:

*   "--tags reset" -> which resets the cluster in a safe matter (first removes all helm chars, then cleans all PVs/NFS, drains nodes, etc.)
*   "--tags helm\_reset" -> which removes all helm charts, and resets the helm.
*   "--tags cluster\_sanity" -> which does, of course, cluster\_sanity and prints cluster details (no changes performed)

[](https://github.com/ReSearchITEng/kubeadm-playbook/#check-the-installation-of-dashboard)Check the installation of dashboard
-----------------------------------------------------------------------------------------------------------------------------

The output should have already presented the required info (or run again: `ansible-playbook -i hosts site.yml --tags cluster_sanity`). The Dashboard is set on the master host, and, additionally, if it was set, also at something like: [http://dashboard.cloud.corp.example.com](http://dashboard.cloud.corp.example.com) (depending on the configured selected domain entry), and if the wildcard DNS was properly set up \*.k8s.cloud.corp.example.com pointing to master machine public IP).

e.g. `curl -SLk 'http://k8s-master.example.com/#!/overview?namespace=_all' | grep browsehappy`

Dashboard is also listening on primary hostname, port 443 (or similar if ingress helm params were changed).  
E.g., if your primary-master is vm01.com, browse: [https://vm01.com:443/](https://vm01.com:443/)  
Note: The http version ([http://vm01.com:80/](http://vm01.com:80/)) will ask for token.

For testing the Persistent volume, one may use/tune the files in the demo folder.

```
kubectl exec -it demo-pod -- bash -c "echo Hello TEST >> /usr/share/nginx/html/index.html "
```

and check the [http://pv.cloud.corp.example.com](http://pv.cloud.corp.example.com) page.

[](https://github.com/ReSearchITEng/kubeadm-playbook/#load-ballancing)load-ballancing
=====================================================================================

For LB, one may want to check also:

[](https://github.com/ReSearchITEng/kubeadm-playbook/#demo)DEMO:
================================================================

Installation demo k8s 1.16 on Ubuntu 18.04: [![kubeadm ansible playbook install demo asciinema video - demo single machine Ubuntu k8s 1.16](https://camo.githubusercontent.com/cb769c085c11d78888137d35a054d2af6f8da09e/68747470733a2f2f61736369696e656d612e6f72672f612f3237383031372e737667)](https://asciinema.org/a/278017)

[](https://github.com/ReSearchITEng/kubeadm-playbook/#vagrant)Vagrant
---------------------------------------------------------------------

For using vagrant on one or multiple machines with bridged interface (public\_network and ports accessible) all machines must have 1st interface as the bridged interface (so k8s processes will bind automatically to it). For this, use this script: vagrant\_bridged\_demo.sh.

### [](https://github.com/ReSearchITEng/kubeadm-playbook/#steps-to-start-vagrant-deployment)Steps to start Vagrant deployment:

1.  edit ./Vagrant file and set desired number of machines, sizing, etc.
2.  run:

```
./vagrant\_bridged\_demo.sh --full \[ --bridged\_adapter <desired host interface|auto\> \] # bridged\_adapter defaults to ip route | grep default | head -1 
```

After preparations (edit group\_vars/all, etc.), run the ansible installation normally.

Using vagrant keeping NAT as 1st interface (usually with only one machine) was not tested and the Vagrantfile may requires some changes. There was no focus on this option as it's more complicated to use afterwards: one must export the ports manually to access ingresses like dashboard from the browser, and usually does not support more than one machine.

[](https://github.com/ReSearchITEng/kubeadm-playbook/#kubeadm-ha)kubeadm-ha
===========================================================================

Starting 1.14/1.15, kubeadm supports multimaster (aka HA) setup easy (out of the box), so no special setup. (Our playbook supports master HA also for older v1.11-v1.13, thanks to projects like: [https://github.com/mbert/kubeadm2ha](https://github.com/mbert/kubeadm2ha) ( and [https://github.com/sv01a/ansible-kubeadm-ha-cluster](https://github.com/sv01a/ansible-kubeadm-ha-cluster) and/or github.com/cookeem/kubeadm-ha ).

[](https://github.com/ReSearchITEng/kubeadm-playbook/#how-does-it-compare-to-other-projects)How does it compare to other projects:
==================================================================================================================================

[](https://github.com/ReSearchITEng/kubeadm-playbook/#kubeadm---the-official-k8s-installer)Kubeadm -> the official k8s installer
--------------------------------------------------------------------------------------------------------------------------------

With kubeadm-playbook we are focus only kubeadm. **Pros:**

*   as it's the official k8s installation tool
*   kubeadm is released with every k8s release, and you have a guarantee to be in sync with the official code.
*   self hosted deployment, making upgrades very smooth ; Here is a KubeCon talk presenting even more reasons to go with self-hosted k8s: [https://www.youtube.com/watch?v=jIZ8NaR7msI](https://www.youtube.com/watch?v=jIZ8NaR7msI)

**Cons:**

*   k8s cluster ugprades are not (yet) in plan, (as kubeadm upgrade is too simple (and sensitive) to need automation)
*   when you run the playbook against an existing cluster, by default it will rebuild the entire cluster. Alternativelly, one has to use the ansible "--tags" to specify what exactly is desired (E.g. `ansible-playbook -i hosts -v site.yml --tags post_deploy` )

[](https://github.com/ReSearchITEng/kubeadm-playbook/#other-k8s-installers)Other k8s installers
-----------------------------------------------------------------------------------------------

Similar k8s install on physical/vagrant/vms (byo - on premises) projects you may want to check, but all below are without kubeadm (as opposed to this project)

*   [https://github.com/kubernetes/contrib/tree/master/ansible](https://github.com/kubernetes/contrib/tree/master/ansible) -> the official k8s ansible, but without kubeadm, therefore the processes will run on the nodes, not in docker containers
*   [https://github.com/dcj/ansible-kubeadm-cluster](https://github.com/dcj/ansible-kubeadm-cluster) -> very simple cluster, does not (currently) have: ingresses, helm, addons, proxy support, vagrant support, persistent volumes, etc.
*   [https://github.com/apprenda/kismatic](https://github.com/apprenda/kismatic) -> very big project by apprenda, it supports cluster upgrades
*   [https://github.com/kubernetes-incubator/kargo](https://github.com/kubernetes-incubator/kargo) -> plans to use kubeadm in the future, for the activities kubeadm can do.
*   [https://github.com/gluster/gluster-kubernetes/blob/master/vagrant/](https://github.com/gluster/gluster-kubernetes/blob/master/vagrant/) -> it's much more simple, no ingress, helm, addons, proxy support, and persistent volumes only using glusterfs. Entire project is only focused on CentOS.
*   [https://github.com/kubernetes-incubator/kubespray](https://github.com/kubernetes-incubator/kubespray) & [https://github.com/kubernetes/kops](https://github.com/kubernetes/kops) (amazon) -> Neither of them used the official installtion tool: kubeadm; Updates: as of 2019 kubespray accepts kubeadm (to be checked if kubespray was fully redesigned around kubeadm or adopted as an option). As of May 2019: our projects accepts also master-HA using only kubeadm 1.14, with no other "magic" around.

PRs are accepted and welcome.

PS: work inspired from: @sjenning - and the master ha part from @mbert. PRs & suggestions from: @carlosedp - Thanks. [URL page of kubeadm-playboook ansible project](https://researchiteng.github.io/kubeadm-playbook/) [kubeadm-playboook ansible project's code is on Github](https://github.com/ReSearchITEng/kubeadm-playbook)

Our story: [https://medium.com/@re.search.it.eng/batteries-included-kubernetes-for-everyone-bccf9b8558dd](https://medium.com/@re.search.it.eng/batteries-included-kubernetes-for-everyone-bccf9b8558dd)

License: Public Domain

  
  
from Hacker News https://ift.tt/2GBLOLt