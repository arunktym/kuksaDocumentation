# **7. Kuksa-IDE Building & Deploying**

A documentation repository containing implementation to setup Eclipse Kuksa che instance is available in [here](https://github.com/eclipse/kuksa.ide). Which also contains the Automotive Grade Linux (AGL) stack with Yocto support. AGL represents an automotive specific Linux distribution specifically designed as open software stack for connected car scenarios. An example on how to use the Kuksa-IDE for developing AGL applications and services running on a Rover can be found in [here](https://wiki.eclipse.org/APP4MC/Rover).

## 7.1 Version
### *Table 6.1 Eclipse Che Kuksa instance version*
   |Available|Version number|
   |---------|--------------|
   |Current  |6.10|
   |Plan     |7.0|

The Kuksa-IDE Developers guidance and the neccessary steps for building and running Eclipse Che kuksa instance are explained in this [link](https://kuksa-che-ide.readthedocs.io/en/latest/).

 *For the neccessary <span style="color:lightblue">prerequisites</span> and <span style="color:lightblue">Eclipse Che Kuksa setup</span>, please visit  [here](https://github.com/eclipse/kuksa.ide)*.

## 7.2 IDE

The IDE provided under Eclipse Kuksa not only support the development of applications for the vehicle component, but also the creation of applications for the cloud. Users should be able to choose between two different workspaces and technology stacks that contain the preconfigured and embedded APIs as well as software libraries of the respective applications to be developed. This allows the car to be equipped with new functions and new services to be deployed in the cloud.

Kuksa offers various APIs for implementing vehicle applications, a project template for cloud services, and wizards for easily providing vehicle applications in the App Store via the IDE. The extensive provision of the various APIs and libraries in the IDE enables accessing existing communication interfaces for the secure data transmission, storage, management, and authentication without having to take separate measurements for processing or interpreting the data.

Kuksa also supports the simplified deployment of new applications for both the cloud and vehicle components. This is provided by a pre-configured Eclipse Che stack, to which only the address of a target platform must be specified. Configuration, building and deployment can be done at the push of a button without further configuration or processing. Depending on the application, different development tools (e.g. Logging, Debugging, Tracing,...) can be included. Of course, syntax highlighting, code completion, and other necessary IDE functions are supported. For instance, the in-vehicle Eclipse Kuksa Che stack for AGL development activities features including Yocto based SDKs in order to support target specific programming shown in the screenshot below. After compiling and building software, specifying a target IP allows also the deployment process.

![Kuksa_IDE screenshot](../ImageFile/Kuksa_IDE.png)

In order to make new applications applicable to a greater amount of vehicles, applications need to be centrally checked, managed, and organized with regard to various in-vehicle derivatives and variants in such a way that only vehicle-appropriate applications are accessible. Similar to a Smartphone App Store, it has to be possible to add new functions and applications to their vehicle or perform updates or upgrades. Therefore, standardized interfaces of the in-vehicle and cloud platforms are required and they must offer the most diverse and yet simple infrastructure for vehicle owners. Authentication methods, security concepts, variant management, and suitable data transmission technologies in combination with the publicly accessible ecosystem form mandatory components as well as the difference to existing solutions. [Click](https://www.eclipse.org/community/eclipse_newsletter/2018/july/kuksa.php) here to read more.
> *7.2.1 Here are repository folders for [kuksa.apps](https://github.com/eclipse/kuksa.apps)*
> 
> *7.2.2 Getting started with [Kuksa appstore](https://github.com/eclipse/kuksa.cloud/tree/master/kuksa-appstore)*


> ## 7.3 Getting started with the In-Vehicle platform

[Kuksa IDE - Developers Guide](https://gitlab-pages.idial.institute/pedro.cuadrachamorro/kuksa-ide/) containes the neccessary guides such as:- *Quick start*, *Kuksa IDE Custom Assembly*, *Plugins*, *Stacks* and *Sample Projects*. 

> ## 7.3.1 Kuksa App example

The eclipse Che doesn’t provide a standard mechanism to add custom sample projects during build time. Therefore, Kuksa IDE provides an easy and straight forward mechanism to append them to ones provided by Eclipse Che during build time. [Sample Projects](https://gitlab-pages.idial.institute/pedro.cuadrachamorro/kuksa-ide/samples/index.html) can be found from this link.
