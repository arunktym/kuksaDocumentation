# Architecture
The overall platform of the security-relevant aspects of the Appstacle environment architecture is divided in to three building blocks:
   > 1. In-vehicle platform,
   > 2. 5G Infrastructure, and
   > 3. Cloud back-end. 
   
The above mentioned building blocks comprises a set of components which communicates between components of the same building block and/or components of different blocks.

## 1. In-Vehicle Platform

The APPSTACLE environment is created to provide addon services to the connected vehicles. This provides a complite functionality of the vehicles through deploying the *Apps* on the in-vehicle platform. Therefore, three layers of components are required to enable this purpose:

**Core Layer**: Contains the in-vehicle platform components, such as operating system and application runtime. It, furthermore, allows the vehicle owner to interact with the vehicle, e.g., via smartphone access. In addition, it provides an intrface to the 5G infrastructure similar to the core layer of the cloud back-end. 

**API / Binding Layer**: consists of relevant APIs and components for internal and external communication.

**Application Layer**: It represents the arrangement of all Apps that are running within the in-vehicle platform. Some of the Eclipse base Open source solutions to inreach kuksa components are: 
*  Automotive Grade Linux (AGL)  
*  Eclipse hawkBit
*  Eclipse Hono
*  Eclipse Ditto
*  Eclipse Che
*  Keycloak
*  ...

<img src="kuksaComponents.png" width="750" height="300" />

*(source:https://www.researchgate.net/profile/Marco_Wagner2/publication/330281127_Innovation_through_Openness_-_The_Open_Source_Connected_Vehicle_Framework_Eclipse_Kuksa/links/5c371b5892851c22a3691df8/Innovation-through-Openness-The-Open-Source-Connected-Vehicle-Framework-Eclipse-Kuksa.pdf?origin=publication_detail)*

 

The in-vehicle platform addtionally provides means for rertrieving telemetry data collected by the vehicle itself as well as a human machine interface (HMI ) for user interaction.

## **In-vehicle connectivity** concept:

|ID| Property|
  |------|------|
  |1. | It enables communication with the infotainment unit or the ECUs internal to the vehicle |
|2.|• Telemetry data or data specified in the Cloud platform related to internal vehicle functionalities.|• Vehicle diagnostics (e.g. health monitoring).
| |• System metadata (which components are present, heartbeats etc)|
|3.|• Interacts with the in-vehicle HW for data gathering and with the ex-vehicle connectivity for data forwarding|
|4.|• One component per vehicle with different interfaces according to the employed protocols.|
|5.|• Information about the protocols used in the internal vehicle architecture
||• Depending on the chosen protocols: what components are communicating what information|
||• Development of software modules for handling data for each protocol|

## **Ex-vehicle connectivity** concept:

|ID| Property|
  |------|------|
  |1. | It enables outward and inward communication between the vehicle and the external entity |
|2.|• No data processing as such.
||• Re-Packs the data received from bus to appropriate format for the external entity and vice versa.|
|3.|• It has the direct connection to the BUS and no direct user interaction.|
|4.|• There will be multiple instances in the minimum two cases.|
|5.|• Driver for hardware component
||• (Since Development Stage) Need manual configuration at the moment for 5G mm Radio.|


## **App Runtime** concept:

|ID| Property|
  |------|------|
  |1. | The APP Runtime provides the environment for executing APPs and starts / stops APPs. It has to provide and control resources for the APP, enforce access control (permissions), and isolate APPs from each other. |
|2.|APPs, configuration data (permissions, options, ...), APP data|
|3.|The APP Runtime permits or denies communication between APPs, or APP and backend (depending on "the policy"). The APP Runtime obtains APPs from the marketplace. It can be configured by the OEM and/or the vehicle owner (via backend and/or an in-vehicle user interface; probably also by devices [with authorization]).|
|4.|There is one APP Runtime per in-vehicle platform. It could be part of the operating system.|
|5.|Initialisation / start up: The APP Runtime is started during the (secure) boot process. It can be configured by the OEM and the vehicle owner (details are left open in this document), e.g., to configure permissions ("the policy").|

## **Automotive API** concept:

|ID| Property|
  |------|------|
  |1. | The Automotive API provides an interface to in-vehicle data for APPs (and cloud ser-vices? other entities??). An (operating system) service ("Automotive API server") implements the Automotive API, for instance similar to the "Vehicle Information Service" specified by the W3C. |
|2.|Vehicle data (sensor data, diagnosis information, configuration of vehicle compo-nents, vehicle status information, ...)|
|3.|It can be used by APPs (and cloud services, etc.) to retrieve information from the vehicle, to send data to in-vehicle components, and to write (vehicle) configuration data.|
|4.|There is one Automotive API per in-vehicle platform.|
|5.|Initialisation / start up: The "Automotive API" service is started during the (secure) boot process.|


## **Apps** concept:

|ID| Property|
  |------|------|
  |1. |(In-vehicle) APPs are programs that provide new features to the vehicle. |
|2.|App data (depends on APP / use case)|
|3.|APPs are executed and controlled by the APP Runtime and can access in-vehicle data via the Automotive API. They can communicate with other entities via con-nectivity APIs (cf. architecture picture). If permitted (by "the policy"), they might communicate with cloud services (backend providers) and other APPs, and they could interact with the driver via a GUI (if available). APPs can access resources via the APP Runtime (subject to "the policy"). A user can install APPs from the Marketplace in the vehicle.|
|4.|There can be multiple APPs per in-vehicle platform.|
|5.|Initialisation / start up: APPs are started by the APP Runtime. Configuration data depends on the APP / use case.|

## **Device Management Client** concept:

|ID| Property|
  |------|------|
  |1. |The DM is responsible for keeping the devices compliant to the whole system land-scape. This starts with building up a base in communication and process protocols. It is also providing features for securely enrolling new devices, governing and con-figuring them while being out in the field, monitoring and debugging their behavior remotely and maintaining the devices with software updates. Four subjects can be distinguished:
||• Enrollment includes provisioning and authentication for bringing new devices into an IoT landscape. The authentication assures that only trust-worthy devices are added to the network and connected to cloud services. Also only authorized users should be able to bring in new devices and gain access according to their roles granted.
||• Governing contains features for controlling and configuring devices. As IT systems are often under a constant development, some parts change and so do some of their constants, for example network addresses or ports.
||• Monitoring keeps an eye on all components of the system and their status. Reports and alerts for incidents are raised and logged. An on-time awareness of system issues is enabled. For diagnosis and solving software bugs it is also imperative to load log dumps remotely from devices.
||• Maintenance with the ability to distribute and apply software updates is the fourth subject. The device management assures that the update is delivered and applied to the device according to the present constraints. Feedback mechanisms answer back to the cloud for a detailed status of the update. |
|2.|**Process**
||• System states
||• Application states
||• Update states
||• Management Calls
||• Push Calls
||• Alarms
||• Enrollment policies
||• Updates, Update scheduling
||• Inventory Hardware/Software listings
||• Communication requests
||**Provide**
||• Access to resources through OMA-DM Management Objects (http://www.openmobilealliance.org/wp/OMNA/LwM2M/LwM2MRegistry.html)
|| – Management access through LwM2M)
||• Push Service (for notifying in-vehicle Applications form the cloud)
||• Monitoring Service
||• Update Service (Maintanance)
||• Keep-Alive Signal Service
||• Inventory Hardware/Software
||• Enrollment Service
||• Control Service (e.g. shutdown certain components)|
|3.|• Apps, OS: (Re-)Configure, Update
||• ECU: Flashing/Updating ECUs
||• Apps: Notify/Wake Up through push
||• HW/SW: Read Inventory
||• HW/SW: access on resource (if Management Object is defined)
||• User: Update scheduling|
|4.|The DM can only exist once per vehicle. But it is split into its functional groups (subjects). A hierarchical design of distributed DMs in a vehicle might be the subject of another design.|
|5.|• Authentication Set (MAC, UUID, Public Key)
||• Cloud contact
||– Address of DM at the desired cloud
||– Certificate|

## **Operating System (OS)** concept:

|ID| Property|
  |------|------|
  |1. |The Operating System is the backbone any platform where it operates including In-vehicle platform. We also consider drivers as being part of the Operating system.
||*Operating System*
||• consists of kernel and user space components
||• provides security
||• I/O and networking services to applications running in user space
||• runs on bare metal or hypervisor
||• OS kernel provides:
||– processes/thread management including scheduling
||– inter process communication
||– memory management
||– access to underlying HW
||– networking stacks
||– I/O stacks
||– security subsystem include:
||∗ access control (e.g. MAC)
||∗ crypto and key management
||∗ integrity measurement
||∗ entropy pools and gatherig entropy from variouos sources It is also important to highlight that the security hardening of an OS scrucial to the platform and application security |
|2.|**Process**
||• data to/from underlying HW
||• data to/from networking
||• data to/from file system
||• user input
||• data exchanged between kernel and user space
||• data exchanged between processes
||• configuration data such as security policies, system settings,..
||**Provide**
||• System state information (running processes, CPU utilization, etc.)
||• log data
||• debug or diagnostics data if certain debug features are enabled|
|3.|• *Access to underlying HW*
||– peripherals
||– networking interfaces
||– any physical interface
||– HW based crypto and key management functionality
||– HW based TRNG (True Random Number Generator)
||• *App-Runtime (transport layer)*
||– Provide transport layer interface for Apps (inter-app communication, app to cloud backend communication)
||– Provide system level services (file access, etc.)
||• *Device Management Client (transport layer)*
||– Provide transport layer interface for communication with device management (cloud backend)
||• *5g Infrastructure (data link layer)*
||– Connection Management
||• *Smartphone (data link layer)*
||– Pairing
||– Connection Management
||– Data Transfer
||• *Net-IDS*
||– Provides Interface to allow the Net-IDS to monitor network traffic.|
|4.|Different subsystems on a vehicle may be running their own OSes
||• whether on bare metal or virtualized
||• whether micro kernel based, unikernel based or rich OS such as Linux|
|5.|• build and runtime OS configuration
||– for process, resource management, memory management, functionality, security,..
||– policies (e.g. security)
||– configuration of different processes
||– networking configuration
||• User credentials|


## 2. 5G-Infrastructure
The 5G infrastructure enables the communication between the connected vehicles and the cloud back-end. Based on the 5G standard discription, two component layers are structured as *control plane* and *user plane* which represents communication with cloud back-end and communication with the connected vehicle respectively.


## **Evolved Packet Core (EPC)** concept:

|ID| Property|
  |------|------|
  |1. |EPC includes a number of components such as MME (Mobility Management Entity), SGW (Serving Gateway), PGW (Packet Data Network Gateway), HSS (HomeSubscriber Server). Each of these components have their own purpose
||• MME (Mobility Management Entity): located in the control plane and handles authentication, roaming and other management functions
||• SGW (Serving Gateway): handles routing user data packets
||• PGW (Packet Data Network Gateway): handles data connectivity with external networks. This is also where packet processing and lawful interception can take place
||• HSS (Home Subscriber Server): handles user subscription information |
|2.|• MME (Mobility Management Entity): authentication data, roaming data
||• SGW (Serving Gateway): processes user data packets
||• PGW (Packet Data Network Gateway): policy enforcement, packet processing and filtering.
||• HSS (Home Subscriber Server): processes and stores user ubscription data|
|3.|• MME interacts with eNodeB, SGW and HSS
||• SGW interacts with MME and PGW
||• PGW interacts with SGW and external network
||• HSS interacts with MME|
|4.|There can be multiple instances|
|5.|Depends on the vendors and the products|


## **eNodeB (BBU)** concept:

ID| Property|
  |------|------|
  |1. |BBU (Baseband Unit) is responsible for processing baseband signals received from RRUs and further communicating data with EPC.|
|2.|Processes baseband signals received from RRUs (Remote Radio Units) and other data from EPC|
|3.|Interacts with RRUs and EPC|
|4.|There can be multiple instances|
|5.|Depends on the vendors and the products|

## **eNodeB (RRU)** concept:

ID| Property|
  |------|------|
  |1. |Interacts with user equipment by using a signaling protocol and relays baseband signals to BBUs for further processing|
|2.|Signaling data|
|3.|Interacts with user equipment and BBUs|
|4.|Multiple instances|
|5.|Depends on the vendors and the products|


## 3. Cloud back-end

The cloud back-end provides service components to the connected vehicle by making sure a reliable and safe functionality according to the pre-defiened operation. Just like the In-vehicle platform, the cloud back-end is composed of multiple layers: 
**Core Layer**: the core layer fuctions as
* central back-end applciations
* messaging infrastructure
* control the message flow from and to the connected vehicles, and
* device update management and data management. 
**Data Analytic & Visualization Layer**: this layer analyzis and visualizes the data transmitted by the vehicle based on the functionalities of the core layer.
**Application Layer**: In general, applications that are deployed on in-vehicle platforms require a cloud back-end counterpart. Often, applications in the back-end are provided by third parties allowing vehicle owners to aquire certain functionalities. The market place is also accessible for developers and serivce providers to register and upload applications. The original equipment manufacturers (OEM s) has the access and controls on contents of the market place.

## **Message Gateway** concept:

ID| Property|
  |------|------|
  |1. |• Serves as central messaging hub
||• Provides a set of micro services that transport messages from the car to the other components within the APPSTACLE backend and vice versa
||• Implements routing and brokering mechanisms|
|2.|**Input and Output**
||• Telemetry data
||• Event messages
||• Command & control messages
||• Software updates
||• Each message type may have a different quality of service level, depending on the configuration of the system
||**Messaging Protocols**
||• *MQTT*
||– Publish/subscribe model
||– Implements own security model
||• *HTTP (REST-based)*
||– GET, SET, PUT, DELETE
||• *Other protocols*|
|3.|• Receiving and routing messages to the correct recipient
||• Providing or leveraging identity management for connected devices|
|4.|• There exists only a single instance within the cloud backend|
|5.|• Deployment configuration regarding micro services:
||– External IP addresses
||– Ports
||– Connection to other services, e.g, identity management, service bus, etc.|


## **Device Management Backend** concept:

ID| Property|
  |------|------|
  |1. |• Managing the software stack on the individual devices
||• Responsible for distributing the sotware artifacts to the devices
||• Steering software rollout campaigns for large sets of devices|
|2.|• It provides arbitrary software and data artifacts that are stored in one or multiple repositories|
|3.|**Input**
||• It interacts either with an app store or a backend service that is provided by the OEM
||• It receives commands that initiate the change of software stack of one or multiple devices 
||**Output**
||• It sends software and data artifacts to one or multiple devices
||• The outbound communication is ideally conducted via the messaging gateway, managing the packaging according to the according protocol
||– HTTP
||– LWM2M
||– OMA-DM
||– Other
||• The outbound communication may also be realised using direct communication to the devices|
|4.|• There exists only a single service within the cloud backend
||• The may exist multiple instances behind the service interface|
|5.|• The configuration for initialization is provided within deployment scripts
||• The device management resources are expected to be deployed into an existing cluster|


## **Report Generation** concept:

ID| Property|
  |------|------|
  |1. |Report Generation is a component to generate business reports from the data collected by the cloud platform.|
|2.|data collected by the cloud platform and, in particular, results from data analytics; output is a "report" (document)|
|3.|The Report Generation component takes data from the Data Management (e.g.,results of the data analytics component) and creates reports, including visualizations,lists, documents, charts, etc.
||It is implemented based on Eclipse BIRT.
||Q: How is report generation triggered - periodically? by Apps? what interfaces exist?
||Q: Who can request request reports? End-users (e.g., vehicle owner)? Service providers? OEMs?
||Remark: It must be ensured that report generation cannot be misused by malicious users to violate data protection rules or to obtain confidential information without authorization.|
|4.|Usually there is one logical report generation component per cloud instance, but potentially, there could be different report generation components for different kinds of reports.|
|5.|• The configuration for initialization is provided within deployment scripts
||• The device management resources are expected to be deployed into an existing cluster|

## **Marketplace Backend** concept:

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


## **Visualization** concept:

ID| Property|
  |------|------|
  |1. |The Visualization component creates graphical representations of time series data retrieved via the Data Management component. For example, the Visualization component can generate graph like representations of the evolution of telemetry data over time.|
|2.|**Process**
||• Time series data (e.g., telemetry data, performance/monitoring data) 
||**Provide**
||• Graphical representations that can be utilized for report generation|
|3.|• Data mangement component
||– retrieving time series data
||– sending representation for storage and use in report generation|
|4.|There should be at least one Visualization instance per Data Management instance because of scalability aspects. Multiple instances per data management instance are possible. **Not sure here**|
|5.|• Data source
||• Dashboard information
||– Metrics
||– Representation style
||– Layout information|


## **Marketplace Frontend** concept:

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


## **Data Management** concept:

ID| Property|
  |------|------|
  |1. |• Manages the data that is transferred from the in-vehicle platforms to the cloud backend
||**Historical Data**
||• Provides storage mechanisms to persist historical sensor data
||• Is indepedent of the storage technoligies applied
||– Time series vs. transactional vs. analytical data bases
||– Relational vs. object data bases 
||**Streaming Data**
||• It assumed that only portions of the data transferred can actually be stored, due to the large volume
||• Instead of storing the full set of data, it may be analysed on-the-fly
||• Therefore data must be rerouted to corresponding systems|
|2.|• Sensor data that is collected by the in-vehicle platform and transmitted by the message gateway|
|3.|**Input**
||• Message Gateway
||– Sends sensor data to the Data Management component
||– Data Management component acts as a consumer
||**Output**
||• Data bases
||– Receive subset of data that is transferred via the Message Gateway
||• Stream processing engines
||– Receive full set of data that is transferred via the Message Gateway|
|4.|• There exists of a single vertically scaled instance within the cloud backend
||• It may be connected to multiple data bases and stream processing engines|
|5.|• Deployment configuration regarding micro services
||– External IP addresses
||– Ports
||– Connection to other services, e.g, Message Gateway and Big Data Analysis|


## **Identity Management** concept:

ID| Property|
  |------|------|
  |1. |• Managing the identities of the entities within the connected car environment, such as:
||– Vehicles
||– Backend services within the following layers:
||∗ Core Layer
||∗ Data Analytic & Visualization Layer
||∗ Application Layer
||– Marketplace users
||• Authorization of vehicle access by marketplace users|
|2.|• Login data of the marketplace users
||• Authentication data of backend services as well as vehices
||• Authorization data of vehicles, backend services and marketplace users|
|3.|• Exchange of login data, authorization data and authentication data|
|4.|• There exists only a single instance within the cloud environment.|
|5.|• The setup of the identity management component requires the awareness regarding the individual backend services.
||• Regarding the authentication and authorization of vehicles and marketplace users, specific mechanisms have to be selected and configured.|


## **Device Representation** concept:

ID| Property|
  |------|------|
|1. |• Providing an abstraction between the physical devices, the vehicles, and their digital representations (digital twin)
||• Managing the state of the vehicles attached to the backend infrastructure   (reported vs. desired vs. current)
||• Providing a unified interface for accessing the information provided by the vehicles
||• Organizing the digital twins for all vehicles attached to the backend infrastructure|
|2.|• Information provided by the physical devices, in particular sensor data|
|3.|• Synchronizing data between the physical devices and their digital representations
||• Processing data provided by the physical devices|
|4.|• There exists only a single instance managing all digital twins referring to all cars within the connected car environment|
|5.|• The Device Representation component has to be connected to the message gateway
||• A digital twin is created for each connected vehicle added to the environment|


## **Big Data Analysis** concept:

ID| Property|
  |------|------|
|1. |• Vehicles provide large amounts of data that are is by the Data Management component.
||• Big data analysis provides insights, e.g., the properties and usage of individual vehicles as well as their interaction.|
|2.|• It consumes data collected by the vehicles that is persisted by the Data Management component.
||• This data serves as input for the analytical tasks, depending on the individual objectives.
||• The analytical results are provided to Domain-specific services.|
|3.|• Data is retrieved from the Data Management component.
||• Analytical tasks are initiated by Domain-specific Services.|
|4.|• There may be multiple Big Data Analysis components within the environment.|
|5.|• The Big Data Analysis component(s) have to be connected to the Data Management component as well as the Domain-specific Services.
||• This includes deployment configuration data, such as:
||– External IP addresses
||– Ports|


## **Core Services** concept:

ID| Property|
  |------|------|
|1. |• Provide an abstraction layer regarding the access of the connected vehicles within in the environment.
||• The focus is especially on the sending messages to and receiving messages from the connected vehicles.
||• Therefore, it relies on the functionality provided by the Message Gateway component.
||• Potentially restrict the access of Domain-specific Services.|
|2.|• It provides access to the information provided by the connected vehicles to the Domain-specific Services.
||• It allows to send messages from Domain-specific Services to the connected vehicles.|
|3.|• Consume data from the Message Gateway component and route it to the Domain-specific Services.
||• Consume messages from the Domain-specific Services and route them to the Message Gateway component.|
|4.|• There exist different services but for each service a single instance.|
|5.|• The Core Services have to be connected to the Message Gateway component as well as the Domain-specific services.
||• This includes deployment configuration data, such as:
||– External IP addresses
||– Ports|


## **Domain-specific Services** concept:

ID| Property|
  |------|------|
|1. |• The Domain-specific Services provide added value to the users of the APPSTACLE connected car environment.
||• The provide selected functionalities that leverage the data as well as the communication provided by the connected vehicles.|
|2.|• It consumes data that is provided the Core Services component.
||• It accesses and synchronizes the state of the connected vehicles via the Device Representation component.
||• It consumes aggregated data that is provided by the Big Data Analysis component.|
|3.|• Accessing and consuming data that is provided by the components attached.
||• Sending messages to the connected vehicles.|
|4.|• Domain-specific Services may be provided by third-party developers.
||• Therefore, there may exist a set of individual services which do not necessarily depend on each other.|
|5.|• Depending on the use case, the individual services have to be connected to the Device Representation component, the Big Data Analysis component as well as the Core Services component.
||• This configuration data includes:
||– External IP addresses
||– Ports|




![The general system architecture](CloudeArchitecture.png)
           
**The picture below summurizes the concepts discussed above.**