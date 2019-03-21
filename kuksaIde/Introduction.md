Author: Arun & Kirubel, Date: 20.03.2019,Training Material
# Getting started with the App IDE
## Introduction 
(Write the context of Kuksa - APPSATCLE Project Max 7 sent)
Kuksa IDE is an open source developer workspace and Cloud IDE. The Kuksa IDE is a full custom build based on the Eclipse Che. 
(Write about Kuksa IDE from Che components)
The development of software-intensive automotive systems by the Origional Equipment Manufuctureres (OEM) still has unresolved challanges. Therefore, development of standardized car-to-cloud senario could improve the activities and invites external applications, service providor and use of open-source software. A platform such as: the Eclipse [Kuksa](https://www.eclipse.org/kuksa/), which is based on the APPSTACLE project which itself is part of the Europian ITEA3 program provides mobility as a service as well as after-sales innovations and the means to catch up with the fastly growing of software in changing the business in connected cars. Kuksa is a secure and open automotive platform built as a full custom Eclipse Che Assembly. [Eclipse Che](https://en.wikipedia.org/wiki/Eclipse_Che) is an open-source java based integrated developer inveronment as cloude, and server which provides a mult-user remote development platform. It consists of a Software Development Kit (SDK) to allow application for certain software packages, framework, platform or computer systems by allowing to create plug-ins for those frameworks,languages or tools.
### Getting started with the App IDE
[Kuksa is divided into a series of components](https://wiki.eclipse.org/Kuksa): 

*InVehicle*, *AGL build scripts*, *IDE*, *Cloud*, *Integration*, *Apps*, *[Website](https://projects.eclipse.org/projects/iot.kuksa)*. Each of these components will be discussed in details. 
### Installing Docker for Ubuntu
* Check the Ubuntu version using the command ![*lsb_release -a*](check_ubuntu_version0.png). 
* To Get the Comunity Edition (Docker CE) version for ubuntu, make sure you have 64-bit version of Ubuntu. 
    * Cosmic 18.10
    * Bionic 10.04 (LTS)
    * Xenial 16.04 (LTS)
* Docker CE is supported on *x86_64* (or *amd64*), *armhf*, *arm64*, *s390x* (IBM Z), and *ppc64le* (IBM Power) architectures.
* Uninstall older Docer version using: 
   *   <span style="background-color:grey"> $ sudo apt-get remove docker docker-engine <span>docker.i</span>o containerd runc </span> 
* The supported storage drives for Docker CE on Ubuntu are : *overlay2*, *aufs* and *btrfs*.
* Depending on the needs, Docker CE can be installed in different ways: 
    * For ease installation and upgrade task (Recomended) use [set up Docker's repositories](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-from-a-package).
    * For manual installation and upgrading, use [install it manually](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-from-a-package). Which might be useful in situations as installing Docker on air-gapped systems with no access to the internet.
    * For testing and development purpose, use automated [convenience scripts](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-using-the-convenience-script) to install Docker.
  
  ### Install using the repository
  Set up the Docker repository by following the steps:
  1. Update the <span style="color:lightblue">apt</span> pakage index
    
        <span style="background-color:grey"> $ sudo apt-get update</span>
2. Coppy and paste the following line of command to allow <span style="color:lightblue">apt</span> to use repository over HTTPS:
   
   <span style="background-color:grey">$ sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent    software-properties-common </span>
3. Double-click [Docker](https://docs.docker.com/docker-for-windows/install/) Desktop for Windows Installer.exe to run the installer. The downloaded installer (Docker Desktop Installer.exe), can be found from (download.docker.com). It usually downloads to the Downloads folder, or else, run it from the recent downloads bar at the bottom of the web browser (if Google Chrome is used).

4. Follow the install wizard to accept the license, authorize the installer, and proceed with the install. ![A test image](DockerImage.png)

5. You are asked to authorize Docker.app with your system password during the install process. Privileged access is needed to install networking components, links to the Docker apps, and manage the Hyper-V VMs.![Enabling Hype-V container feature](Enabling Container features.png)

6. Click Finish on the setup complete dialog to launch Docker.


As Eclipse Che is a top-level project in the cloud development Eclipse Cloud Development (ECD), the Che assembly needs to be identified. Therefore, Che assembly is either .war or a Tomcat assembly (https://www.eclipse.org/che/docs/che-6/assemblies.html). However, ***missing*** 