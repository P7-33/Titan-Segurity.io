---
title: 'Docker volumes'
date: 2019-11-03T18:07:00+01:00
draft: false
---

Docker volumes  
In the last section of this chapter, we will cover container storage or Docker volumes as they are referred to. We will take a look at data volumes and data volume containers, the differences between the two, and when to use which one. Lastly, we will also look at the best practices for Docker volumes. This is the data that we want to be persistent or shared between containers. We need to remember that, by default, when you exit a running container, the data isn't saved. When you start the container back up, it will start in its initial state, so Docker volumes become incredibly important in areas like databases or filesystems.  
  
Another switch that we will be covering is the -v or --volume= switch. This switch allows you to provide a volume to the Docker container that you wish contained persistent data. Remember that, when you start a Docker container, the data inside doesn't remain persistent unless you save it (or commit in Docker terms). The volumes switch allows you to have persistent data inside your Docker container such that even if the container is stopped or deleted, the data remains intact. Let's take a look at the two ways we can provide persistent volumes to containers:  
  
Data volumes  
Data volume containers  
Data volumes  
The first volume storage we will look at is data volumes. Data volumes are mounted inside the container when you run the container. However, as stated before, the volume is not tied to the container in events when it stops, is killed, or is deleted. Let's see how we first mount a volume inside a container; then we can dive a little deeper:  
  
$ docker run -it -v /tmp ubuntu /bin/bash  
We are simply running an ubuntu container shelled into /bin/bash, so we can see the /tmp volume mounted. This will create a new volume inside the container at the specified path. Essentially, it overwrites or hides the folder inside the container if it does exist; and in our case, /tmp already exists, so any data the container might have had inside it is no longer there and /tmp will now be an empty folder or volume.  
  
You can also use multiple -v volume switches on a single docker run line:  
  
$ docker run -it -v /tmp -v /data ubuntu /bin/bash  
It is nice to use the -it switch sometimes, so you can actually see how this works. In later times, you will want to be running your containers with the -d switch, so they are not running the foreground.  
  
Now, you can also mount the directory from the local machine the Docker containers are running on into the Docker container. To do so, you can use the -v switch again, but you need to add :/ to the path:  
  
$ docker run -it -v /tmp:/data ubuntu /bin/bash  
This will mount the contents of /tmp (on the Docker host) to the /data directory inside the now running Docker container. If you were to look at the contents of /tmp on the Docker host and the contents of /data on the running Docker container, you will see that they match. Any changes you make inside the Docker containers /data folder will be reflected in the Docker host's /tmp folder.  
  
By default, when you mount a directory from a Docker host to a Docker container, it will mount in the read/write mode. There is a way you can mount it in the read-only mode as well. Again, using the -v switch, we will just append :ro to our volume instruction:  
  
$ docker run -it -v /tmp:/data:ro ubuntu /bin/bash  
You can locate one or several volumes on a Docker container by using the docker inspect container:  
  
$ docker inspect  
The line(s) you will be looking for will resemble the following:  
  
    "Volumes": {  
        "/tmp": "/mnt/sda1/var/lib/docker/volumes/5c4e1bff167ea1479dd9f33f74aeaf5d7f9f4d252d096e95e87befdb9be23ea0/\_data"  
Remember, you can get the container ID by running:  
  
$ docker ps  
The preceding output shows how the docker inspect command actually works. It is mounting /tmp inside the container; but where does the data actually live? The data actually lives in the machine your container runs on in the path specified. If you were to populate data inside the container in the /tmp folder and then navigate from the machine running the Docker container to the /mnt/sda1/var/lib/docker/volumes/5c4e1bff167ea1479dd9f33f74aeaf5d7f9f4d252d096e95e87befdb9be23ea0/\_data directory, the data would be there. Now, we will go into the details of how to manage data and move it around between Docker hosts in the next chapter.  
  
On a side note, you can also use the VOLUME instruction inside the Dockerfile to specify volumes for a container. It would look similar to this:  
  
FROM ubuntu:latest  
MAINTAINER Scott P. Gallagher  
VOLUME \["/datastore"\]  
You can also use the -v flag to mount a single file into a container. So, the discussion isn't just about directories, it's about files as well. Now, we have seen how we can use Volumes to create persistent data that is stored inside containers; but what other options do we have with regards to using Volumes? We can use data volume containers too.  
  
Data volume containers  
Data volume containers come in handy when you have data that you want to share between containers. There is another flag we can utilize on the docker run command. Let's take a look at the --volumes-from switch.  
  
What we will be doing is using the -v switch on one of our Docker containers. Then, our other containers will be using the --volumes-from switch to mount the data to the containers that they run.  
  
First step, let's fire up a container that has a data volume we can add to other containers.  
  
For this example, we will be using the busybox image since it's very small in size. We are also going to use the --name switch to give the container a name that can be used later:  
  
$ docker run -it -v /data --name datavolume busybox /bin/sh  
We are going to create a volume and mount it in /data inside our container. We have also named our container datavolume so that we can leverage in our --volumes-from switch. While we're still inside the shell, let's add some data to the /data directory. So, when we mount it on the other systems, we know it's the right one:  
  
$ touch /data/correctvolume  
This will create the correctvolume file inside the /data directory in the busybox container we are running.  
  
Now, we need to connect some containers to this /data directory in the container. This is where the name we gave it will come in handy:  
  
$ docker run -it --volumes-from datavolume busybox /bin/sh  
If we now perform ls /data, we should see the correctvolume file that we created earlier.  
  
Tip  
Something to note here is that when you use the --volumes-from switch, the directory will be mounted in the same place on both the containers. You can also specify multiple --volumes-from switches on a single command line.  
  
There will come a time when you run into the following error:  
  
$ docker run -it -v /data --name datavolume busybox /bin/bash  
Error response from daemon: Conflict. The name "data" is already in use by container 82af96592008. You have to delete (or rename) that container to be able to reuse that name.  
You can remove the volume if you want, but USE IT CAUTIOUSLY, as once you remove the volume, the data inside that volume will go away with it:  
  
$ docker rm -v data  
You can also use this to clean up the volumes that you no longer want on the system. But again, use extreme caution as stated before that once a volume is gone, the data will go with it.  
  
Docker volume backups  
It is important to remember that while your containers are immutable, the data inside your volumes is mutable. It changes, while the items inside your Docker containers do not. For this reason, you need to make sure that you are backing up your volumes in some manner.  
  
Volumes are stored on the system at /var/lib/docker/volumes/.  
  
The key to remember here is that the volumes are not named the way you named them in this directory. They are given unique hash values, so understanding what content is in them can be confusing if you are just looking at their name. If you are looking at managing volumes at this point, I would highly recommend this image from the Docker Hub: https://hub.docker.com/r/cpuguy83/docker-volumes/.  
  
This container (once built) will allow you to list volumes as well as export them into a tarred up file.