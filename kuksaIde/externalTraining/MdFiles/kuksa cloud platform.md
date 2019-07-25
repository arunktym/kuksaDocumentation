# **9 Kuksa Cloud Platform**

## 9.1 Getting started with the cloud platform

This repo [link](https://github.com/eclipse/kuksa.cloud/tree/master/deployment) contains script directory and it's subdirectories help to setup and deployment of the Kuksa cloud. These scripts assume a running Kubernetes cluster which can be configured using kubectl. More information regarding the parameters of the scripts can be found within the respective script file of the [link](https://github.com/eclipse/kuksa.cloud/tree/master/deployment).

> ### Structure

The deployment scripts are divided into the following parts:

    1. Azure for Azure-specific configuration that provides the basis of Kubernetes.
    2. Eclipse hawkBit enables the deployment of the corresponding software update components, in particular the update server. Note that this step requires the installation of the command line tool kompose. Installation instructions can be found at http://kompose.io/
    3. Eclipse Hono enables the deployment of a messaging infrastructure.
    4. Kubernetes provides functions for the Kubernetes deployment of the Kuksa cloud.
    5. Utils scripts that are included by other parts of the deployment infrastructure (e.g. handling static IP-addresses for the services). It is possible to set static IP-addresses and DNS entries for deployed services. For more details on that configuration see the Readme.md file in the utils directory.



## <span style="color:red"> *9.1.1 Required System Configuration* </span>

To get started, the requied infrastructures are:


    Java 8
    Maven
    Spring-Boot and other dependencies(data-jpa, feign client,pagination)
    Vaadin
    Swagger (for Rest API documentation)

## Prerequisites

Just run AppStoreApplication.java class.Spring boot has an embedded Tomcat instance. Spring boot uses *Tomcat7* by default, if you change Tomcat version, you have to define these configuration in *pom.xml*. But you have a few options to have embedded web server deployment instead of Tomcat like Jetty(HTTP (Web) server and Java Servlet container) or Java EE Application Server. You have to configure these replacements from default to new ones in *pom.xml*. 
For detail information, follow the [link](https://github.com/eclipse/kuksa.cloud/tree/master/kuksa-appstore).

## <span style="color:red"> *9.1.2 Installing and testing the Cloud platform* </span>
## <span style="color:red"> *9.1.3 Installing a Cloud App and its In-Vehicle App* </span>
## <span style="color:red"> *9.1.4 Testing the Cloud App* </span>

 ## 9.2 Configuring the Cloud platform

- The Microsoft Azure Deployment contains the IP adresses and DNS names. This [link](https://github.com/eclipse/kuksa.cloud/tree/master/deployment/azure) explains the deployment of Azure. 
- Similarly, the [Eclipse hawkBit Deployment](https://github.com/eclipse/kuksa.cloud/tree/master/deployment/eclipse-hawkbit) repo link consists of neccessary deployment steps.  
- Deployment of Eclipse hawkBit can be found from the repo link [here](https://github.com/eclipse/kuksa.cloud/tree/master/deployment/eclipse-hawkbit).
- Eclipse Hono Deployment is available from this [link](https://github.com/eclipse/kuksa.cloud/tree/master/deployment/eclipse-hono).
- Kubernetes-specific functionality details can be accessed from the repo link [here](https://github.com/eclipse/kuksa.cloud/tree/master/deployment/kubernetes).

## <span style="color:red"> *9.3 Overview of the Cloud platform and its architecture* </span>

## <span style="color:red"> *9.4 Overview of the Kuksa Cloud API* </span>
 
## 9.5 Marketplace presentation and features


>## Marketplace Backend concept:

ID| Property|
  |------|------|
  |1. |• Stores and manages the software and data artifacts related to the apps that are installed on the in-vehicle platform
||• Initiates and controls the communication with the app provider backends
||• Interacts with potential payment providers, depending on the payment methods applied (Credit/Debit Card, SMS)
||• Stores the data related to registered users (vehicle owners and app developers)
||• Central hub for the interaction with app developers
||• Provides app data to the in-vehicle platforms via the device management back-end
||• Scan app software and data artifacts regarding vulnarabilities and malware
||• Question: Should in-app transactions be possible?|
|2.|**Process**
||• User input via the Marketplace Frontend
||– Vehicle owner core data (Name, Address, Supported payment methods, User vehicle mappings (1 User, N Vehicles))
||– App developer core data (Name, Company, Address, Supported payment methods, Apps provided)
||– Transactional data regarding buying and returning apps (Transaction ID, Transaction status, Payment method applied, Vehicle Identification Number, Version of the app transferred
||**Provide**
||• Software and data artifacts that are provided by the app developers
||– Software (Compiled source code)
||– Data (Licenses, Documentation, Version history, Supported in-vehicle software platforms, Supported in-vehicle hardware platforms)
||– API/Frontend for app developer interaction (Transferring software and data artifacts to the backend, Receiving account and app related information, e.g. number of downloads or total revenue per app)|
|3.|**Input**
||• Marketplace frontend (see informations listed above)
||• Payment provider backends (Handling of payment transactions)
||• App developer backends (Receiving data and software artifacts) Output
||• Marketplace frontend (Deliver data requested by the frontend, e.g., results for search queries)
||• In-vehicle platforms, via Device Management component (Software and dataartifcats regarding specific apps)
||• App developer backends (Transaction and evaluation data)
||• Identity Management (Requests for user authentication and authorisation)|
|4.|• There should be only a single instance within the cloud backend |
|5.|• Deployment configuration regarding micro services
||– External IP addresses
||– Ports
||– Connection to other services, e.g, Identity Management|

>## Marketplace Frontend concept:

ID| Property|
  |------|------|
  |1. |• Provides visual interface that enable the interaction with the Marketplace Backend
||• Vehicle owners can search and order apps as well as initiate their transfer to the in-vehicle platform
||• Allows app developers to access app storage and monitoring data
||• Allows vechicle owners and app developers to edit their core data / profiles|
|2.|**Process**
||• Core data (vehicle owner and app developer) entered via the visual interface
||• Query database regarding apps available for the specific in-vehicle platform
||• Software and data artifacts send by the app developers
||• Data referring to payment transaction, e.g., data exchange with payment providers 
||**Provide**
||• Visual interface depicts information regarding
||– Vehicle owner and app developer core data
||– App transactions
||– App search query results|
|3.|**Input**
||• Vehicle owner
||– Enter and update core data
||– Fill out order forms
||– Search apps via query masks
||• App developer
||– Enter and update core data
||– Upload apps
||– Retrieve monitoring data
||**Output**
||• Vehicle owner
||– Display core data
||– Display app search queries
||• App developer
||– Display core data
||– Display monitoring data|
|4.|• There exists only a single services within the backend
||• There might be several container instances behind this service|
|5.|• Deployment configuration regarding micro services
||– External IP addresses
||– Ports
||– Connection to other services, e.g, Marketplace Backend|

In addition: 

The Eclipse Kuksa Appstore contains: 

> ### Build Eclipse Kuksa Appstore

    Script:
        build_kuksa_appstore.sh
    Purpose:
        Build a Docker image for the Eclipse Kuksa Appstore and push it to a Docker registry
    Options:
        DOCKER_REGISTRY_SERVER: Address of the Docker registry server, e.g. running on Microsoft Azure.
        DOCKER_REGISTRY_USERNAME: Username to sign in to the Docker registry.
        DOCKER_REGISTRY_PASSWORD: Password to sign in to the Docker registry.
        DOCKER_REGISTRY_EMAIL: Email to sign in to the Docker registry.
    Stages:
        Clone the Kuksa Git repository
        Build with Maven
        Build Docker image
        Push Docker image to Docker registry
        Final cleanup
            Remove the clones Git repository

>### Deploy Eclipse Kuksa Appstore

    Script:
        deploy_kuksa_appstore.sh

    Purpose:
        Deploys a Docker image for the Eclipse Kuksa Appstore on a Kubernetes cluster

    Options:
        APPSTORE_USERNAME: The username to set for the admin user of the appstore
        APPSTORE_PASSWORD: The password to set for the admin user of the appstore
        HAWKBIT_HOST: The (cluster-internal) hostname of the hawkbit server to use in the appstore
        HAWKBIT_PORT: The (cluster-internal) port number of the hawkbit server to use in the appstore
        HAWKBIT_USERNAME: The username to be used by the appstore to authenticate with hawkbit.
        HAWKBIT_PASSWORD: The password to be used by the appstore to authenticate with hawkbit.
        DOCKER_REGISTRY_SERVER: Address of the Docker registry server, e.g. running on Microsoft Azure.
        DOCKER_REGISTRY_USERNAME: Username to sign in to the Docker registry.
        DOCKER_REGISTRY_PASSWORD: Password to sign in to the Docker registry.
        DOCKER_REGISTRY_EMAIL: Email to sign in to the Docker registry.
        DOCKER_REGISTRY_SECRET: Name of the secret to access to custom Docker registry. Note that the secret is created during the deploy process within the namespace extension.

    Notes:
        Production mode is enabled for Vaadin.
        H2 console is disabled.
        The H2 database is persisted via a persistent volume claim.
        The service uses a ClusterIP so it is only available behind the Ambassador gateway.

