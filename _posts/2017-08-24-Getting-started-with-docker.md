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

The *Container* Technology or the concept of Containerization is not something new or recent, but has been in existence since the late seventies. If you will, there are a plethora of resources available on the internet that will give you an insight on the evolution. As a matter of fact, [DZONE](https://dzone.com/articles/evolution-of-linux-containers-future) has elaborately summarized at the following link, including timeline and the players proactively involved behind making this a magical product as we see today.

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

The primary goal of this article is to walk you step-by-step in installing Docker CE 'engine' on a Linux/macOS, run a container and manage it's life Cycle. I will also walk you through some of the basic administrative tasks and get you setup to embark upon one of the stepping stones to the DevOps journey.

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
> Environment
> Platform: AWS
> OS: Ubuntu 18.04/Bionic Beaver
> Kernel: 4.15.0-1023-aws






## Pre-reqs:
The primary distribution method for the AWS CLI on Linux, Windows, and macOS is `pip`, a package manager for Python that provides an easy way to install, upgrade, and remove Python packages and their dependencies.
* Python 2 version 2.6.5+ or Python 3 version 3.3+
* `pip` Python package manager
