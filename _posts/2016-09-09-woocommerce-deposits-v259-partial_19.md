---
title: 'WooCommerce Deposits v2.5.9 – Partial Payments Plugin'
date: 2019-10-19T17:49:00+01:00
draft: false
---

Docker services are extensively used in IT operations, so it is very important that you start learning from docker basics. In this article, we will cover the installation and setup of the docker, along with its specific uses.

Learn web application in

### **Table of Content**

*   Introduction to docker
*   Docker and its terminology
*   Advantages of docker
*   Installation and usage

### **Introduction to Docker**

Docker is a third-party tool developed to create an isolated environment to execute any application. These applications are run using containers. These containers are unique because they bring together all the dependencies of an application into a single package and deploy it. 

Now, to work with docker you will need to install docker-engine in your host. It is a foundation to the docker system, which basically runs as a client-server application. Its daemon process is referred to as server and the command-line interface is referred to as a client and REST API is used to create a communication link between client and server.

In Linux, docker client interacts with docker server through the CLI. Here, the terminal is docker client and docker host will run the docker daemon.

![](https://i1.wp.com/1.bp.blogspot.com/-NmgwWy9QXCs/Xas_mhrG8gI/AAAAAAAAhBQ/dQ_dxYrMctQ5wqmEelR8m7f6gcbGgQZDgCLcBGAsYHQ/s1600/0.png?w=687&ssl=1)

Whereas in windows, to work with docker, we need to install docker toolbox component in docker host in order to set up an environment on your Windows or iOS.

![](https://i0.wp.com/1.bp.blogspot.com/-diNaQA97EwE/Xas_mciCKWI/AAAAAAAAhBI/61yYi3qjuyIyXzA6q5qHwIGNPnDKnt80ACLcBGAsYHQ/s1600/1.1.png?w=687&ssl=1)

### **Docker and its terminology**

When working with docker, one should be familiar with the following terms :

*   **Docker Hub:** It is a repository which available to all who uses docker through cloud. Through docker hub, one can create, store, test, pull and share container images.
*   **Docker Images :** Docker image acts as a template in order to create container. Build command is used to create docker images. Docker images makes it easy.
*   **Docker containers :** Containers are said to be isolated environment provided to the docker image and its dependencies so that it can run independently. The focus of deploying a container is to update or repair an application or just simply modify it and share it. When working on an image, container lets you create a layer of a single command used which make it easy to modify it, or upgrade or degrade is version.
*   **Docker Registry :** All the docker images are stored in docker registry. User can either can have local registry on their system or they can have a public one like docker hub.

### **Advantages of docker**

*   Easy to use
*   Faster scaling systems
*   Better software delivery
*   Flexibility
*   Provides isolated environment
*   Supports software-defined networking
*   Rapid deployment
*   Security

### **Installation and usage**

To install docker, simply open the terminal of Linux and type the following command :

```
apt install docker.io
```

![](https://i2.wp.com/1.bp.blogspot.com/-2moCSgc7k60/Xas_mdjHmqI/AAAAAAAAhBM/H_E04JLty8Qv4MT0smgOidLjKBkZTGDKgCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

To check the version one can use the following command :

```
docker --version
```

Further, you can run help command in docker, which is as follows, to know all the options that docker provides at your service.

```
docker --help
```

![](https://i1.wp.com/1.bp.blogspot.com/-5D1m9NZkgyY/Xas_pmva3nI/AAAAAAAAhBw/tJb3yQe4NxMmt0NdcF_a4GGfDdvuB_WHACLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

Once the docker is up and running, you can run or pull any image in your docker container. For instance, here we have run hello-world. When you run the following command, it will first check your local repository; if the image is not available there then it will pull it from docker hub.

```
docker run hello-world
```

![](https://i2.wp.com/1.bp.blogspot.com/-fmN6NmbUywQ/Xas_qdJvQTI/AAAAAAAAhB0/EiEOuxeKzmAeMin1IxYiN9aKX98TegzBgCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

As we have explained before, CLI works as a client, so directly from the terminal, you can search for any image you like. Like, here we have searched for ubuntu. One thing to remember here is that image with more stars will be the most authentic one.

```
docker search ubuntu
```

Once you find your image, you can pull it into your container with the following command :

```
docker pull ubuntu
```

![](https://i0.wp.com/1.bp.blogspot.com/-kqFibjO9ugE/Xas_qZnjahI/AAAAAAAAhB4/WTymfkHGEh8jJGIjq4Df7OuFhh8DIuRQQCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

Now to check how many images you have in your docker, simply type the following command :

```
docker images
```

![](https://i2.wp.com/1.bp.blogspot.com/-0DrDiZzW4qk/Xas_q_a6pGI/AAAAAAAAhB8/3AKNrSMH1EIyjCGRV2-GQL4kHsWowl_UQCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

To remove any image, use the following command :

```
docker rmi hello-world
```

Here, rmi refers to remove image.

![](https://i0.wp.com/1.bp.blogspot.com/-deSczaHhwlA/Xas_rM691cI/AAAAAAAAhCE/a7R7akm7Xs0cqTXHsnQyVb-J4m3CtmoUgCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

Now, in the details given by ps command, you can see that the name of our ubuntu image is **adoring curie**, which is a random name generated by docker for every image. To, rename this name we can use the following command :

```
docker run -it -d –name "ignite" ubuntu
```

**![](https://i0.wp.com/1.bp.blogspot.com/-2wIPEk0-Re4/Xas_rMSG7QI/AAAAAAAAhCA/PBTnhn6m3L058cD2KrnFygHCRSAtIQz3wCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)**

And you can confirm with the ps command again that the name has been changed as shown in the image below :

The docker attaches command permits you to attach to a running container using the container ID or name, you can use one instance of shell only though attach command. But if you crave to open new terminal with new instance of container’s shell, we just need run docker exec.

```
docker attach ignite  
docker exec -i -ignite /bin/bash
```

![](https://i2.wp.com/1.bp.blogspot.com/-wkn9VHa3l8g/Xas_rtuc8aI/AAAAAAAAhCI/bmisJNTRNqAlxOwObZqNUtOg_-yVv7cKgCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

Using the ps command we can see all the processes that are running in docker. There, for this, type :

```
docker ps  
docker ps -a
```

![](https://i0.wp.com/1.bp.blogspot.com/-c063YvirntU/Xas_nf51SMI/AAAAAAAAhBU/XoCA_lRSti0COKoBKXttNayNJP11VhjMQCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

To stop the running container, you can use stop command as shown in the below image, we have stopped the container and its process which can be confirm with the help of process command. As result there should be no running process for ignite.

```
docker stop 
```

![](https://i2.wp.com/1.bp.blogspot.com/-mMHEl5UmqcM/Xas_ndI2wkI/AAAAAAAAhBY/5chQJmLUQ4Mv6mzSUex60La3dubu8pfjACLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

If you can export the docker filesystem as a tar archive, use export command to compress the filesystem of a docker container into tar. The export commands fetch the whole container like a snapshot of a regular VM.

```
docker export  | gzip > {path for tar} filename.tar
```

![](https://i0.wp.com/1.bp.blogspot.com/-amLweSPVJ4E/Xas_ntQbXCI/AAAAAAAAhBc/TJWPDwROxwM_BjyIbKaHIemQ7WpAg9VMwCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

```
docker export  | gzip > {path for tar} filename.tar
```

It will give you a flat .tar archive containing the filesystem of your container.

![](https://i0.wp.com/1.bp.blogspot.com/-B56byuJLPvo/Xas_oVWb8PI/AAAAAAAAhBg/mdlEvJ9QKy8jpIceAX8K1Ra2K2DzAwU8wCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

When you will export container as tar file, the file has hash value which can read as:

```
cat {path of exported tar file} |docker import – newignitelab
```

In order to save the image of container which you can upload on other docker use save command.  You can subsequently load this “saved” images into a new docker instance and create containers from these images.

```
docker save  | gzip > {path for tar} filename.tar  
docker load -i /home/raj/docker/igniteimage.tar
```

![](https://i0.wp.com/1.bp.blogspot.com/-GdjtqnNZ44Y/Xas_ozRBozI/AAAAAAAAhBk/hahXDF6C6k44hE5OLqUHcOAoi9XeILQUACLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

In order to clear all image and or stop all process of the container. It will pack the layers and metadata of all the chain required to build the image.

```
docker rm -f $(docker ps -aq)
```

![](https://i0.wp.com/1.bp.blogspot.com/-otr4Alc21sY/Xas_pGi1McI/AAAAAAAAhBs/9czDZJIL1hkJ5JI7mSpAxQtezjNDCd38wCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

To learn how to set up vulnerable web application setup using docker from **[here](https://www.hackingarticles.in/web-application-pentest-lab-setup-using-docker/)**.

**Author**: **Yashika Dhir** is a passionate Researcher and Technical Writer at Hacking Articles. She is a hacking enthusiast. contact **[here](https://www.linkedin.com/in/yashika-dhir-b94722a3?trk=pulse-det-athr_prof-art_hdr)**

The post [Docker Installation & Configuration](https://www.hackingarticles.in/docker-installation-configuration/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2Mty6Ma