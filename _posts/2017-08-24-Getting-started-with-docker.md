---
layout: post
comments: true
title:  "Getting started with Docker Container"
date:   2017-08-24 13:12:08 +0530
categories: docker
tags: docker container microservice
---

<img src="/assets/img/docker-banner.png">

For those of you wondering what [Docker](https://www.docker.com/why-docker) is, you might want to go through the basics of Container, what they do, how they fit in and how they play an important role in today's CI/CD pipeline and Blue/Green automated application deployment in the DevOps world?

### The _Not So_ Brief history of 'Containers'

The *Container* Technology or the concept of Containerization is not something new or recent, but has been in existence since the late seventies. If you will, there are a plethora of resources available on the internet that will give you an insight on the evolution. As a matter of fact, [DZONE](https://dzone.com/articles/evolution-of-linux-containers-future) has elaborately summarized at the following link, including timeline and the players proactively involved behind making this magical product a huge success and is being widely adopted as we see today.

Containerization is increasingly becoming popular for the following reasons:

* Flexible: Even the most complex applications can be containerized.
* Lightweight: Containers leverage and share the host kernel.
* Interchangeable: You can deploy updates and upgrades on-the-fly.
* Portable: You can build locally, deploy to the cloud, and run anywhere.
* Scalable: You can increase and automatically distribute container replicas.
* Stackable: You can stack services vertically and on-the-fly

Source: [Docker Docs](https://docs.docker.com/get-started/#docker-concepts)

Some of the other widely adopted Container platforms are:
* Red Hat's [CoreOs](https://coreos.com/os/docs/latest/) and it's [Roadmap](https://www.redhat.com/en/about/press-releases/red-hat-unveils-roadmap-coreos-integration-red-hat-openshift)
* Linux [LXC Containers](https://linuxcontainers.org/lxc/introduction/)

The primary goal of this series of articles is to walk you step-by-step in installing Docker CE 'engine' on a Linux/macOS, run a container and manage it's life Cycle. I will also walk you through some of the basic administrative tasks and get you setup to embark upon one of the stepping stones to the DevOps journey.

For *macOS* Installation, please refer to the Docker's official step-by-step [Documentation](https://docs.docker.com/docker-for-mac/install/) along with the minimum system requirements for optimum and seamless performance. Once you have the installation successfully completed, you should be able to open your terminal land run few commands to validate.

```shell
$ docker --version
Docker version 18.06.1-ce, build 6a1727d
#=> you should have this output above
```

```shell
$ docker info
#=> output should give you the same version of both Server and Client
```

Please Note! I shall running most of the commands on a Linux Ubuntu

#### Linux Install and Operation
* Environment
* Platform: AWS
* OS: Ubuntu 18.04/Bionic Beaver - Clean Install
* Kernel: 4.15.0-1023-aws

1. Login to Ubuntu 18.04 on AWS

2. Install Docker following the official [documentation](https://docs.docker.com/install/linux/docker-ce/ubuntu/#upgrade-docker-ce). This is pretty self explanatory.

* SET UP THE REPOSITORY

- Update the apt package index:

```shell
$ sudo apt update
```

- Install packages to allow apt to use a repository over HTTPS:
```shell
$ sudo apt install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

- Add Docker's official GPG key:
```shell
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

- Install docker by adding the repository as below
```shell
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
```

- Finally run the Installation
```shell
$ sudo apt install docker-ce
```

3. Validate Installation
```shell
ubuntu@ip-172-31-88-136:~$ docker --version
Docker version 18.06.1-ce, build e68fc7a #=>output
```

Running `$ docker info` OR any `docker run ..` cmd immediately post installation will error out with the following error
`docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.26/containers/create: dial unix /var/run/docker.sock: connect: permission denied.
`
##### Why?
The Docker daemon binds to a Unix socket instead of a TCP port. By default that Unix socket is owned by the user `root` and other users can only access it using `sudo`. The Docker daemon always runs as the root user. Now that would be an inconvenience (at least for me) running an additional command, so we create a 'docker' group and add the `$user` to the group.

From what I can tell, 'docker' group is automatically created with the installation since v18.x so all we need to do is add the `$user` to the group like so -
```shell
$ sudo usermod -a -G docker $USER
$ sudo systemctl restart docker
```
```shell
$ docker info
Containers: 10
 Running: 3
 Paused: 0
 Stopped: 7
Images: 2
Server Version: 18.06.1-ce
Storage Driver: overlay2
 Backing Filesystem: extfs
 Supports d_type: true
 Native Overlay Diff: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
 Volume: local
 Network: bridge host macvlan null overlay
 Log: awslogs fluentd gcplogs gelf journald json-file logentries splunk syslog
Swarm: active
 NodeID: ixk83ma2zamtt3e36xhl80lul
 Is Manager: true
 ClusterID: klcfjsxkvfd5osgymoydiimw7
 Managers: 1
 Nodes: 3
 Orchestration:
  Task History Retention Limit: 5
 Raft:
  Snapshot Interval: 10000
  Number of Old Snapshots to Retain: 0
  Heartbeat Tick: 1
  Election Tick: 10
 Dispatcher:
  Heartbeat Period: 5 seconds
 CA Configuration:
  Expiry Duration: 3 months
  Force Rotate: 0
 Autolock Managers: false
 Root Rotation In Progress: false
 Node Address: 172.31.88.136
 Manager Addresses:
  172.31.88.136:2377
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 468a545b9edcd5932818eb9de8e72413e616e86e
runc version: 69663f0bd4b60df09991c08812a60108003fa340
init version: fec3683
Security Options:
 apparmor
 seccomp
  Profile: default
Kernel Version: 4.15.0-1023-aws
Operating System: Ubuntu 18.04.1 LTS
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 983.9MiB
Name: ip-172-31-88-136
ID: 6N3L:5D24:6TV7:QA6O:UZK7:WAIC:4NHI:AWY2:MHYH:R6YT:GKOH:ZNAT
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Registry: https://index.docker.io/v1/
Labels:
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
```
Please make sure to go through the description of [Docker Architecture]() for the details in the output.

We are now set to pull an image from dockerhub and run our first container.

```shell
$ docker run docker/whalesay cowsay 'Welcome to the world of Docker YOURNAME'
#=> checkout this output ;)
```

Checking a list of Images
```shell
$ docker images ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
docker/whalesay     latest              6b362a9f73eb        3 years ago         247MB
```

Checking a list of containers
```shell
docker ps -a
CONTAINER ID     IMAGE               COMMAND                  CREATED          STATUS                     PORTS     NAMES            
0dabfec7d17f     docker/whalesay     "cowsay 'Hello Jassy'"   3 minutes ago    Exited (0) 4 minutes ago             elastic_einstein
```

Basic commands you may start with
`
## List Docker CLI commands
docker
docker container --help

## Display Docker version and info
docker --version
docker version
docker info

## Execute Docker image
docker run hello-world

## List Docker images
docker image ls

## List Docker containers (running, all, all in quiet mode)
docker container ls
docker container ls --all
docker container ls -aq
`

We should be good to proceed to the next step of managing Docker containers and it's lifecycle.

Stay tune for the [second](#) part of this walkthrough.
