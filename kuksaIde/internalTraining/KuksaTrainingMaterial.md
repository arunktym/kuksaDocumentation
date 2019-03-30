# Kuksa App IDE
## Overview
> Introduction To Kuksa

The development of software-intensive automotive systems by the Origional Equipment Manufuctureres (OEM) still has unresolved challanges. Therefore, development of standardized car-to-cloud senario could improve the activities and invites external applications, service providor and use of open-source software. A platform such as: the Eclipse [Kuksa](https://www.eclipse.org/kuksa/), which is based on the APPSTACLE project which itself is part of the Europian ITEA3 program provides mobility. In addition, it provides services as well as after-sales innovations and the means to catch up with the fastly growing of software in changing the business in connected cars. Kuksa is a secure and open automotive platform built as a full custom of Eclipse Che Assembly. [Eclipse Che](https://en.wikipedia.org/wiki/Eclipse_Che) is an open-source java based integrated developer inveronment as cloude, and server which provides a mult-user remote development platform. It consists of a Software Development Kit (SDK) to allow application for certain software packages, framework, platform or computer systems by allowing to create plug-ins for those frameworks,languages or tools.
## Docker on Kuksa
> Docker-Configuration
* Get the Comunity Edition (Docker CE) version for ubuntu, make sure you have 64-bit version of Ubuntu.
    * Cosmic 18.10
    * Bionic 10.04 (LTS)
    * Xenial 16.04 (LTS)
* The supported storage drives for Docker CE on Ubuntu are : *overlay2*, *aufs* and *btrfs*.
* Depending on the needs, Docker CE can be installed in different ways: 
    * For ease installation and upgrade task (Recomended) use [set up Docker's repositories](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-from-a-package).
    * For manual installation and upgrading, use [install it manually](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-from-a-package). Which might be useful in situations as installing Docker on air-gapped systems with no access to the internet.
    * For testing and development purpose, use automated [convenience scripts](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-using-the-convenience-script) to install Docker.
> Docker-Single-User

> Docker-Multiple-User

## Getting Started

> Supported Infrastructure in Kuksa
* Docker CE is supported on ```x86_64 (or amd64), armhf, arm64, s390x``` (IBM Z), and ```ppc64le``` (IBM Power) architectures.
> Quick-start

Assembly components specified in Eclipse Che are also included in [Kuksa IDE](https://gitlab-pages.idial.institute/pedro.cuadrachamorro/kuksa-ide/quick/index.html#build-the-assembly) as it is entirely based on customization of [Eclipse Che Assembly](https://www.eclipse.org/che/docs/che-6/assemblies.html). 
> Running single-user

> Running Multi-user

# Kuksa In-Vehicle platform
> Getting started with the In-Vehicle platform

> Required System Configuration (HW/SW)
> Set up the platform
            
> Connect the platform to a Kuksa portal
> Search for an In-Vehicle App

> Install an In-Vehicle App
        
> Configure the In-Vehicle platform

> Overview of the In-Vehicle platform and its architecture

> Overview of the Kuksa In-Vehicle API
# Kuksa Cloud Platform

> Getting started with the Cloud platform

* Required System Configuration
* Installing and testing the Cloud platform
* Installing a Cloud App and its In-Vehicle App
        
> Configuring the Cloud platform

>Overview of the Cloud platform and its architecture

> Overview of the Kuksa Cloud API

> Marketplace presentation and features