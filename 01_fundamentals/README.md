# Guide for the Microsoft Azure Fundamentals Certification (AZ-900)

These notes collect the basics related to using the Azure cloud services.

Some of them were written after following the Udemy tutorial/course by Scott Duffy:

[AZ-900: Microsoft Azure Fundamentals Exam Prep](https://www.udemy.com/course/az900-azure/)

That tutorial prepares students for the [Exam AZ-900: Microsoft Azure Fundamentals](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-900/).

Mikel Sagardia, 2024.  
No guarantees.

Table of contents:
- [Guide for the Microsoft Azure Fundamentals Certification (AZ-900)](#guide-for-the-microsoft-azure-fundamentals-certification-az-900)
  - [1. Introduction](#1-introduction)
  - [2. Cloud Computing and Its Benefits](#2-cloud-computing-and-its-benefits)
    - [Shared Responsibility Model](#shared-responsibility-model)
    - [Types of Clouds](#types-of-clouds)
    - [Cloud Pricing](#cloud-pricing)
    - [Benefits of Cloud Computing](#benefits-of-cloud-computing)
      - [High Availability](#high-availability)
      - [Scalability](#scalability)
      - [Elasticity](#elasticity)
      - [Reliability](#reliability)
      - [Predictability](#predictability)
      - [Security](#security)
      - [Governance](#governance)
      - [Manageability](#manageability)
  - [3. Cloud Service Types](#3-cloud-service-types)
    - [Serverless](#serverless)
  - [4. Core Architectural Components](#4-core-architectural-components)
    - [Regions, Region Pairs, Sovereign Regions](#regions-region-pairs-sovereign-regions)
      - [Sovereign Regions](#sovereign-regions)
    - [Availability Zones (AZ) and Data Centers](#availability-zones-az-and-data-centers)
    - [Resources and Resource Groups](#resources-and-resource-groups)
    - [Subscriptions](#subscriptions)
    - [Management Groups](#management-groups)
  - [5. Compute and Networking](#5-compute-and-networking)
    - [Most Important Compute Services](#most-important-compute-services)
    - [Scaling Virtual Machines Using VM Scale Sets (VMSS)](#scaling-virtual-machines-using-vm-scale-sets-vmss)
    - [App Services, Containers and Azure Virtual Desktop](#app-services-containers-and-azure-virtual-desktop)
    - [Azure Functions](#azure-functions)
    - [Azure Networking Services](#azure-networking-services)
      - [Connectivity Services](#connectivity-services)
      - [Protection Services](#protection-services)
      - [Delivery Services](#delivery-services)
      - [Monitoring Services](#monitoring-services)
    - [IP Adress Spaces and Subnets](#ip-adress-spaces-and-subnets)
    - [Network Peering](#network-peering)
    - [Public and Private Endpoints](#public-and-private-endpoints)
    - [Basic Demos](#basic-demos)
  - [6. Storage](#6-storage)
    - [Overview of Azure Storage](#overview-of-azure-storage)
    - [Azure Blob Storage](#azure-blob-storage)
    - [Azure Storage Demos](#azure-storage-demos)
    - [Azure Files and Azure File Sync](#azure-files-and-azure-file-sync)
    - [Azure Migrate](#azure-migrate)
    - [Azure Data Box](#azure-data-box)
  - [7. Identity, Access and Security](#7-identity-access-and-security)
    - [Microsoft Entra: Benefits](#microsoft-entra-benefits)
    - [Authetication vs Authoraization](#authetication-vs-authoraization)
    - [Azure AD Conditional Access](#azure-ad-conditional-access)
    - [Multi-Factor Authentication (MFA)](#multi-factor-authentication-mfa)
    - [Passwordless](#passwordless)
    - [Role-Based Access Control (RBAC)](#role-based-access-control-rbac)
    - [Zero-Trust Methodology](#zero-trust-methodology)
    - [Defense in Depth](#defense-in-depth)
    - [Microsoft Defender for Cloud](#microsoft-defender-for-cloud)
  - [8. Cost Management](#8-cost-management)
    - [Factors Affecting Cost](#factors-affecting-cost)
    - [Azure Pricing Caltulator](#azure-pricing-caltulator)
    - [Total Cost of Ownership Calculator](#total-cost-of-ownership-calculator)
    - [Azure Cost Management](#azure-cost-management)
    - [Resource Tags](#resource-tags)
  - [9. Governance and Compliance](#9-governance-and-compliance)
    - [Azure Blueprints](#azure-blueprints)
    - [Azure Policy](#azure-policy)
    - [Resource Locks](#resource-locks)
    - [Microsoft Purview](#microsoft-purview)
  - [10. Tools for Managing Deployments](#10-tools-for-managing-deployments)
    - [Azure Portal and Command Line Tools](#azure-portal-and-command-line-tools)
    - [Azure Arc](#azure-arc)
    - [Infrasturcture as Code (IaC)](#infrasturcture-as-code-iac)
    - [ARM Templates, Azure Resource Manager](#arm-templates-azure-resource-manager)
      - [Ex-Course: Deploying the ARM Template with the CLI](#ex-course-deploying-the-arm-template-with-the-cli)
  - [11. Monitoring](#11-monitoring)
    - [Azure Advisor](#azure-advisor)
    - [Azure Service Health](#azure-service-health)
    - [Azure Diagnostics Settings and Azure Monitor](#azure-diagnostics-settings-and-azure-monitor)
  - [12. Basic Demos](#12-basic-demos)
    - [Create a Virtual Machine (VM)](#create-a-virtual-machine-vm)
    - [Connecting to a VM](#connecting-to-a-vm)
    - [Create an Azure App Service - Web App](#create-an-azure-app-service---web-app)
    - [Modifying and Using an Azure App Service - Web App](#modifying-and-using-an-azure-app-service---web-app)
    - [Create Azure Functions](#create-azure-functions)
    - [Create Azure Container Instances](#create-azure-container-instances)
    - [Create Azure Container Apps](#create-azure-container-apps)
    - [Create an Unmanaged Storage Account, Upload and Manage Files](#create-an-unmanaged-storage-account-upload-and-manage-files)
      - [Containers = Buckets for BLOBs](#containers--buckets-for-blobs)
      - [Storage Browser](#storage-browser)
      - [AzCopy: Programmatic Copy of Storage Elements](#azcopy-programmatic-copy-of-storage-elements)
  - [13. Examples](#13-examples)
  - [Extra: Spending Limits](#extra-spending-limits)
  - [Extra: Azure CLI/SDK](#extra-azure-clisdk)
  - [Extra: Azure Cloud Shell](#extra-azure-cloud-shell)
  - [Extra: Azure Blob Storage](#extra-azure-blob-storage)
  - [Extra: Azure Cognitive Search](#extra-azure-cognitive-search)
  - [Extra: Azure Form Recognizer](#extra-azure-form-recognizer)
  - [Extra: Azure Keyvaluts](#extra-azure-keyvaluts)
  - [Extra: Azure OpenAI](#extra-azure-openai)

## 1. Introduction

Updated to October 2023.

The course comprises the foundations and prepares for the exam; it's the first exam that should be taken.

Requirements for the exam (study guide): [Exam AZ-900: Microsoft Azure Fundamentals](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-900/):

- Describe cloud concepts
- Describe Azure architecture and services
- Describe Azure management and governance

**Very IMPORTANT**: Study resource links are contained in the non-comitted file [`scott_duffy_resources.txt`](./scott_duffy_resources.txt):

- Study guide
- Slides
- etc.

Azure Certification Subway map by [David Cervigón Luna](https://www.linkedin.com/in/davidcervigonluna/)

![Azure Certification Subway Map](./assets/azure_subway.png)

## 2. Cloud Computing and Its Benefits

*There is no cloud, it's always some else's computer what we're using.*

Azure has 1000+ services, all accessible from the [Azure portal](https://portal.azure.com) (create account); we can click on **create a resource** to see some of these services:

- Virtual Machine
- Web App: a web application in which the VM is already set up and we care only about the web app
- Function app: we can just write the function in the UI and that's it; for small pieces of code for light tasks run frequently.
- Logic app: connection 2 application together, if an event happens, trigger one or the other, etc.
- ...

![Azure Resources Panel](./assets/azure_resources_panel.png)

If we want to find something, we should type it in the **search space**!

There are **Categories**:

- AI + Machine Learning: Chatbots, NLP, CV, Custom ML service, ...
- Analytics:
  - Azure Machine Learning: custom ML service
  - Azure Synapse Analytics: Data Warehouse
  - ...
- Compute: Containers, Container Registries, Kubernetes, Quantum Computing, ...
- Databases: SQL, MongoDB, Cassandra

Even tools not supported officially by Microsoft are provided by 3rd party vendors, e.g., Oracle (Linux, DB, etc.).

There is a **Marketplace**, where 3rd party vendors offer their cloud products:

- Ubuntu server
- Wordpress app service
- ...

### Shared Responsibility Model

An app requires many hardware and software components, and depending on how everything is set up, the reponsibilities of each of the components vary; that's the [shared responsibility model](https://learn.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility):

- If we have everything on premises, the responsibility is completely of the customer/user.
- IaaS (Infrastructure as a Service): VM Responsibility: everything starting at the OS is the user's responsibility.
- PaaS (Platform): App Service Responsibility (e.g., Web App): the OS becomes resposibility of the coud provider, i.e., Azure. Depending on the app, some component resposibilities might be shared. 
- SaaS (Software): Cloud Respnsibility (e.g., O365): the user is responsible of the components starting at the credentials.

![VM Responsibility](./assets/vm-responsibility.jpg)

![Shared Responsibility Model](./assets/shared-responsibility.svg)

### Types of Clouds

- Public cloud: available to anyone who wants to purchase them.
  - E.g., Azure; Azure owns the HW and offers the services.
- Private cloud: privately owned HW & setup; we need to be invited.
  - Government cloud, etc.
  - Azure also offers private clouds! It looks like the regular Azure cloud, but the customer either owns or leases exclusive access to the HW.
- Hybrid cloud: combination of both.
  - One deprecated example were the SQL DBs that had a local instance but which could scale in the cloud, i.e., Stretch DB.

Obviously, privacy is best in the private cloud.

### Cloud Pricing

Downsides of paying for cloud services:

- Difficult to predict monthly bill
- Difficult to understand what a service will cost
- Possibility of big savings, but no predictability

Factors of a service price, e.g., of a VM:

- Region
- OS
- Do we have a license?
- Instance size
- Disk size
- Bandwidth
- Backup
- Reservation
- Support

Factors of a service price, e.g., of a DB, concretely Cosmos DB:

- API
- Region
- Serverless?
- Ops/sec
- Storage
- Gateway?
- Backup?

Some services are free!

Most commonly we are charged

- by time (second-precission, but price is by hour)
- for storage space (~2 cent/GB/month)
- network traffic
- for operations (read, write, list, delete, query) - usually very cheap per op

Pricing Calculartor: [Azure Pricing Calculator](https://azure.microsoft.com/en-us/pricing/calculator/)

- Basic VM instance prices show, without storage, etc.
- We can also add the services we need for our app to the cart and check their price; however, it's an estimation, because usage factors also affect the price depending on the app's components.

### Benefits of Cloud Computing

In a nutshell:

- High availability
- Scalability
- Elasticity
- Reliability
- Predictability
- Security
- Governance
- Manageability

#### High Availability

High Availability = Uptime; high availability is a conscious effort to avoid downtime.

- Maximum: 100% = 365 days, 24/7; however, all cloud providers have some downtimes (sometimes for seconds).
- Ability of a system to remain operational to users during planned/unplanned outages.
- Planned outages are inevitable:
  - To updated applications
  - OS security patches
  - HW replacement
  - Migrations
- Unplanned outages are also inevitable
  - HW failure
  - NW disruptions
  - Power outages
  - Natural disasters
  - Cyber attacks
  - SW bugs
  - Poor architecture

Methods to mitigate planned outages:

- Gradual deployment: deploy 1 server, then 10, then 100
  - Test and monitor deployments
- Easy rollback plans: Azure has some tools for that, but the app needs to be constructed taking that into account
- Small deployments
- Frequent deplyments; because we become expertrs
- Automation: CICD

Methods to mitigate unplanned outages:

- Components have redundancy
- Use Azure's built-in features
  - Availability sets
  - Availability zones
  - Cross-region load balancing
- Health monitoring
- Automation
- Strong security, to prevent hackers
- Be geographically distributed (due to natural disasters)
- Have a disaster recovery plan and test it!
  - Can I have my systems running again in 20 mins?
- Load testing: in case we have a popular app, test scaling and load

#### Scalability

Scalability = ability of a system to accomodate increasing demand by adding or removing resources as needed.

- We adapt to changing traffic volume without any changes in the code or in the system design.
- Example of punctual traffic fluctuations
  - E-commerce on Black Friday
  - School registrations in September
  - ...

There are different types of scalings:

- Vertical:
  - Adding more resources to a single server: more memory, number of CPUs, etc.
  - Called *scale up* or *scale down*
  - There is an upper limit!
  - Largest server in Azure: 96 vCPUs, 384 GB memory
  - It does not improve the availability
- Horizontal
  - Adding more servers
  - Called *scale out* or *scale in*
  - No limits: number of servers, regions... we can scale in any direction
  - We have additional complexities for load balancing
  - It improves the systems availability

Impact on system cost:

- Cost increases linearly with the amount of resources
- However, we can control our **maximum capacity** on the system easily, so we spend only th emoney we need to spend!

#### Elasticity

Ability of a system to **quickly and easily** scale up/down:

- It needs to be automated: *autoscaling*; metrics are monitored (e.g., CPU usage) and scaling is managed, by modifying the **capacity**.
- *Waste* resources are minimized: systems that are paid for and not used; in non-cloud environments, waste is much larger.

#### Reliability

A high quality service should be:

- Available: accessible to the users when they need it.
- Reliable: system performs as intended without interruption.
  - We want to trust the system, which also requires transparency.
  - Autoscaling is related to the reliability.
  - Multiple-regions are also related to reliability.
  - Backups.
  - Health probes.
- Predictable

#### Predictability

Ability to forecasr and control performance and behaviour of a system:

- We have the confidence the system will work.
- How is the predictability achieved?
  - Autoscaling
  - Load balancing
  - Different instance types
  - Cost management
  - API
  - Pricing calculators

#### Security

Coud providers are massive targets for hackers. Thus, the providers spend a lot of money to be secure. Among others:

- They follow standard compliance certifications.
- They go through audits.
- They provide the users with tools to assure security (for apps and data).
- There is an always-on DDoS (Denial of service attack).
- There is a Microsoft Security Response Center (MSRC).
- They have always up-to-date platform services.
- Encryption by default.
- There are many Azure tools to enhance our security, like Firewalls, etc.


#### Governance

Governance is about how the organization does business and how that is related to the cloud services, i.e., how these services interact with the business processes. It involves the definition, implementation and monitoring of the policies that shape that business-cloud interaction.

Examples:

- The company wants that given policies/measures are followed in the cloud.
- Basic auditing and reporting is required.
- Sometimes some standard compliance is required: GDPR, etc.

How is governance achieved?

- Azure Policy & Blueprint: we can add taging, metadata, etc.
- Management groups: we can have management of different subscriptions.
- Custom roles: we define roles with accesses to certain resources.
- Soft delete: some data is sent to the trash, instead of deleting it (avoid accidental deletes).
- Guides on best practices are provided.

#### Manageability

Management **of** the cloud and **in** the cloud. The *of* part is achieved by:

- Templates
- Automation
- Scaling: autoscaling is possible for many resources.
- Monitoring and alerts: notify resource status, traffic, etc.
- Self-healing

In the case of the managenet *in* the cloud, we achieve it with:

- Web portal
- CLI & scripts
- Cloud Shell: in the we UI
- APIs
- Powershell

## 3. Cloud Service Types

The term **I/P/S as a Service**:

- It refers to something we could buy, but instead, we rent it.
- If we wish, we don't need to commit to a given volume/amount; but we can, so prices are cheaper.
- We pay for what we use.
- The cloud provider is responsible for maintenance & Co.

There are primarily three types of cloud services, as introduced in the shared responsibility model:

- IaaS (Infrastructure as a Service) - VMs
  - Usually, consists of real-world elements we could have on our data center, no abstracted products.
  - Essential services: computing, storage, networking
  - Example: Virtual Machines
    - We pay them by the second
    - We can choose different sizes
  - Example: Azure Storage
    - 5 PB capacity
    - Very cheap
    - Can handle blobs, files, queues, tables, etc.
    - Can be configured as a data lake.
  - Example: Virtual Networks
    - No cost, but we do have bandwidth cost
- PaaS (Platform) - Heroku / Docker container
  - A layer on top of IaaS: middleware, development tools, DB server, etc.
  - Example: Azure App Service
    - We upload code and configuration to Azure, and it runs without needing to configure the VM undereath
    - CI/CD included
  - Example: Managed Storage - Azure SQL Database
    - We don't have to worry about the server, the VM, disk space, etc.
  - Example: Azure Front Door / Load Balancer / Firewall
- SaaS (Software) - Apps / O365 / GDrive
  - App is ready to be used.

### Serverless

It has become a *buzz word*: it is effectively another pricing model in which we pay for service, not for renting the HW. But of course there are servers behind!

We don't pick the HW, concretely, but some size/compute capacity:

- Examples of *non-serverless* payment for SQL DBs:
  - DTU for Azure SQL DB (Data Transaction Unit): we can choose a DTU number withs corresponding price
  - vCORE for Azure SQL DBs: in this case it is related to the number of CPU cores, and the larger the vCORE, the larger the price
- Examples of *serveless* payment model: we don't have a table to choose the size/compute!
  - Azure takes care of the necessary scaling and we pay, for instance, for CPU second.

The advantage of servlerless is that if we don't use the service, we don't pay for it! However, **the price is not predicteble!**

Serverless services:

- Functions
- Container Apps
- Kubernetes
- SQL DB
- Cosmos DB

## 4. Core Architectural Components

### Regions, Region Pairs, Sovereign Regions

Regions:

- Areas of the world where MS has at least 3 data centers
- Currently 60 world-wide, but we not always can use all of them (e.g., sometimes we need to live in the region, etc.)
- Not necessarily countries, but can be; some countries have multiple regions
- Each region has a **region pair**, to which the connection is the fastest
  - We should use that pair for backups, etc.

[2D/3D Azure Infrastructure Map](https://datacenters.microsoft.com/globe/explore)

![Azure Infrastructure Map](./assets/azure_infra_map.jpg)

- Light blue dots: regions
- High speed connections under the see displayed
- US has 9 regions (this can be modified)
- New coming regions are gray dots

Example: Canada:

- It has 2 regions: Central & East
- Data stored in these regions never leaves Canada; **however, that't not always like that**: Brazil has also a region, but the data leaves to the US. In fact, Brazil has a one-way pair to a US region.
- Anyone can use these regions
- These Canadian regions form a pair; as mentioned, each region has usually a pair - the exception is Qatar, which has a region *without* a pair.

Every time we create a resource, we need to choose a region, and that affects the price.

#### Sovereign Regions

They are connected to a country/government. They are not connected to the Azure Public Cloud, and we need an approval to use them. They use different compliance standards. Many details of these sovereign regions are undisclosed.

For instance, in the US:

- We have the Azure Commencial / Public Cloud
- But also other clouds:
  - Azure Government
  - Azure Government Secret: Secret operations (military)
  - Azure Government Top Secret

The Chinese Government has also Azure Sovereign Region(s).

### Availability Zones (AZ) and Data Centers

Availability Zones = physically separate locations within each Azure region. So we have several data centers connected with really high speed cables (5 ms delay):

- They have their own separate building
- Their own connection to the internet
- Their own power supply
- They don't rely on each other

**IMPORTANT**:

- Not all regions have availability zones; that requires having several data centers! If we are interested on deploying on a region with availability zones, we need to see which ones offer that.
- Not all services support availability zones, although most do.

![Availability Zones](./assets/azure_availability_zones.jpg)

We have 3 types of Azure Zone Services:

- Zonal Services
  - You choose to deploy to a specific Availability Zone
  - You should duplicate services in other zones
  - Example: VMs
- Zone-Redundant Services
  - We don't worry about the zone to deploy to
  - Automatic deployment across zones
  - Example: Azure SQL DB
- Always Available Services
  - Global services, not specific to a region
  - Example: Azure Portal, Azure Active Directory, Azure Front Door

In some cases (Gateway, Load Balancer), we can choose the of zone deployment (zone or zone-redundant).

### Resources and Resource Groups

![Azure Management Groups](./assets/azure_management_groups.jpg)

Azure distinguishes hierarchically between:

- Resources: generic Azure service, the actual things that perform the work, e.g., VM, Storage Unit, DB, etc.
  - They are named
  - We can create them in the portal, CLI, etc.
  - Region is generally necessary
  - A resource has a unique subscription, where its cost is managed
- Resource Groups: a logical group of resources, like a folder/container structure
  - Usually they belong to a region, but the resources inside can be from other regions
  - Recommendation: all resources should be linked, e.g., when one is deleted, all should be deleted, when one is deployed, all should, etc.
  - One resource must belong to one resource group.
  - Permissions can be assigned to groups.
  - Any resource can access any other resource in another resource group; so there is no boundary implicitly implemented.
- Subscriptions
- Management Groups

### Subscriptions

Resource groups belong to **Subscriptions**. Subscriptios are **billing units**. User can have access to several subscriptions and have different roles in them.

There are different types of subscriptions:

- Free plan
- Pay as you go
- Enterprise Agreement (EA)
- Free credits

Big organizations have different subscriptions; usually, each subscription is for a different business unit; that makes easier:

- To manage billing between different business units.
- To manage security; e.g., marketing should not be able to access engineering.

### Management Groups

The subscriptions belong to **Management Groups**; the groups can also belong to other groups.

![Azure Subscription Management](./assets/azure_subscription_management.jpg)

We can assing different policies to different groups; that enhances security.

## 5. Compute and Networking

*Compute* means executing in the cloud.

### Most Important Compute Services

- Virtual Machines (VM)
- VM Scale Sets (VMSS)
- App services (Web apps)
- Azure Container Instances (ACI)
- Azure Kubernetes Service (AKS)
- Windows Virtual Desktop

Virtual Machines (VM): The most basic compute

- IaaS
- Full control over it: OS, HW, etc.
- It is virtual, not physical
- AWS equivalent: EC2
- We have over 700 VM tyoes, depending on CPU speed, core, RAM, disk size, etc.

VM Scale Sets (VMSS):

- Two or more VMs running the same code, with a load balancer in front to randomly direct traffic to one of the machines.
- Example: website.
- We can add/remove machines (autoscaling); **elasticity**.
- We can handle up to 100 VMs in a scale set, and can be configuerd to handle 1000.
- To use this functinality, instead of creating a VM, we create a VM scale set, which can scale in/out.

App services (Web apps):

- Cloud-native approach to running code: we upload our code + configuration and Azure runs it.
- No access/configuration of the underlying HW.
- PaaS

Azure Container Instances (ACI) & Azure Kubernetes Service (AKS):

- Another new paradigm for running code.
- Fastest and easiest to deploy.
- Three main containers:
  - Azure Container Instances (ACI): single instance
  - Azure Container Apps: service with several containers beneath; like an App service, but with features of a Kubernetes cluster.
  - Azure Kubernetes Service (AKS): cluster of servers; most complicated.

Azure Windows Virtual Desktop:

- Desktop windows running on the Cloud.
- We access it viw the browser: we log in and everything is installed.

### Scaling Virtual Machines Using VM Scale Sets (VMSS)

These are two or more virtual machines in which the same code is running and they have a load balancer in front. That way, we can scale the service they VM offers if the number of requests/users increases.

Some features:

- In a normal configuration, up to 100 VMs in a single Scale Set.
- Can be configured to increase to 1000; if we need more, we create another Scale Set and put a load balancer in front of all.

### App Services, Containers and Azure Virtual Desktop

These services are more cloud native than VMs or VMSS.

App Service, aka. Web App (PaaS):

- We pass packaged code and configuration to Azure, and everything is set up.
- Performance is promised, but no access to HW.
- Example: [simple_web_app_test](https://github.com/mxagar/simple_web_app_test). In that example, I link a repository to Azure.

Container Services:

- Azure Container Instance: easiest version
- Azure Container Apps: container version of web apps
- Azure Kubernetes Service

Azure Virtual Desktop: Desktop version of Windows that runs in the cloud.

### Azure Functions

Azure Functions = Serverless compute offering:

- Small pieces of code that can be run in the cloud.
- Cheap and we don't care about infrastructure.
- Simple/light utility functions (jobs): does something specific in a finite period of time.
- Can be triggered by:
  - HTTP call
  - Timer
  - Blob creation
  - Message queue
  - etc.

Examples:

- On a regular basis, moves all files from one container to another.
- Every 6h, call an API that clears an external web cache.
- Every tme a new message arrives, it creates 3 new messages in other three queues.
- Every time a blob is updated, a notification email is sent.

### Azure Networking Services

We always need a virtual network, which emulates a physical network between computers; e.g., in AWS it's called a Virtual Private Cloud (VPC). In Azure, it's called **Virtual Network** (VNet). Virtual networks are the most difficult part to understand; in general, we distinguish 4 types of networking services:

- Connectivity Services: Virtual Networks, subnets, etc.
- Protection Services: Firewall, etc.
- Delivery Services: Load Balancer, Gateway, etc.
- Monitoring Services

#### Connectivity Services

The Virtual Network itself is the most important service.

MS has a physical network (MS Global Network), so VNet is a SW-configured part of it.

Other connectivity services:

- Subnet: a subdivision of the VNet, each with specific security rules.
- Virtual Private Network (VPN): we can connect 2 networks together as if they were on the same network; that's achieved witha network gateway. Similarly, we can connect 2 Azure VNets.
- ExpressRoute: high-speed private connection to Azure.
- DNS Services: we buy a domain name and Azure redirects our service to that URL.

#### Protection Services

- DDoS Protection
- **Azure Firewall: it can apply rules to multiple subscriptions and virtual networks.**
- Network Security Groups
- Private Link

#### Delivery Services

- **Load Balancer: distribute traffic evely between multiple backend servers.**
- **Application Gateway: higher level load balancer with optional firewall.**
- Content Delivery Network: stores common static files close to the user for perceived performance.
- Azure Front Door Service: a load balancer, a CDN and a firewall all in one.

#### Monitoring Services

- Network watcher
- ExpressRoute Monitor
- Azure Monitor

### IP Adress Spaces and Subnets

When we create a VNet (Virtual Network), we usually define:

- An **adress space**: the range(s) of possible IPs (left vertical panel when VNet selected).
- **Subnets**: slices/parts in the adress space which will be assigned for given functionalities, being possible to configure each of them with different rules (left vertical panel when VNet selected).

![Azure Portal: Virtual Network](./assets/azure_vnet.jpg)

An IP address is made up of 32 bits, typically represented in four octets (4 groups of 8 bits), and since 8 bits are 2^8 = 255:

`11111111.11111111.11111111.11111111 == 255.255.255.255`

An adress space is a compact way of defining a set of IPs. For instance: `10.0.0.0/16`; that means:

- The first adress in the set/space is `10.0.0.0` (but the first and last are usually reserved).
- Since we have `/16`, the first 16 bits (8 + 8) of the adress are fixed, i.e., the adress space has 2^(32-16) = 65k adresses of the form `10.0.x.x`, being `x in [0,255]`.
- Note that the first and last adresses are usually reserved, so the usable adress space is `10.0.0.1 - 10.0.255.254`.
  - The first adress `10.0.0.0` is the network address.
  - The last `10.0.255.255` is typically reserved as the broadcast address: this address allows networked devices to send communications to all other devices on the same subnet/space simultaneously.
- The notation `/16` is equivalent to saying that *the subnet mask* is `255.255.0.0`: 255 means the octet is fixed and 0 that it is free.

Given the adress space `10.0.0.0/16`, for instance, we could define a **subnet** like `10.0.0.0/24`, which means:

- `/24`: first 3 octets are fixed, i.e., the range is reduced to `10.0.0.0 - 10.0.0.x` with `x in [0,255]`. So we would have 256 possible adresses.
- Note that Azure reserves about 5 adresses for internal tasks. Thus, we end up having 251 usable adresses.

We can create and name as many subnets we want (e.g., `default`, `backend`), as far as their adress ranges are within the adress space of the virtual network.

### Network Peering

A resource group can have several virtual networks! However, note that those networks cannot communicate with each other by default. To achieve that, we need to do **network peering** = notify the different VNets that the other exists.

Note that the different VNets can be in different regions, but then the fees for international/inter-region communications are paid in addition to intra-region fees.

On the left vertical panel, we'll see **Peerings**, which allow 1 or 2-way communications between VNets. For instance, if we have `vnet1` and `vnet2`:

    Choose one network, e.g.: vnet1
    Left panel: Peerings > Add
    We can create 1 or 2 links.
    Each link (1->2 and 2->1) needs a name.
      In *This virtual network*: vnet1_to_vnet2
      In *Remote virtual network*: vnet2_to_vnet1
    We can leave everything default.
    Add.

We can choose the other network and remove the create peering manually under peerings. That way, we'd have a one way connection only (1->2): Select Peering, `...`, Delete.

### Public and Private Endpoints

Resources have a *Networking* configuration (shown during creation) which specifies whether it can be accessed from 

- the outside (i.e., Internet): *Enable access from all networks*. However, authetication is still needed!
- or selected VNets and IP adresses,
- or the access is **disabled**. However, when we disable the access, we can still create **private endpoints**, i.e., private links to access the resource.

For instance, we can create the resource **storage account** and allow access to it from our previous `vnet1`. Note that an endpoint is created in a selected VNet subnet for that communication.

This is not only for storage account, but other resources, too.

### Basic Demos

Basic demos are explained in section [12. Basic Demos](#12-basic-demos).

## 6. Storage

Recall the 3 pillars:

- Compute
- Networking
- **Storage**

### Overview of Azure Storage

We have

- Unmanaged storage: General Purpose Storage = Blob
- Managed storage: Disk storage = Virtual HDs
- File storage
- Storage tiers

Storage is considered IaaS.

**Unmanaged Azure Storage: General Purpose Storage (GPv2)**

- Aka. "Standard storage"
- Four types of data:
  - Container
  - File
  - Queue
  - Table
- Up to 5 PT = 5 million GB
- Pay per use: 2 cents / GB / month: very cheap
- Not recommended for high demand workloads, like a DB
- We get the option to create a **Data lake**:
  - Extremely large storage, up to exabytes (beyond 3 PB)
  - Good for big data analytics
- We also have Premium storage options (for high performance requirements)
  - We can choose between
    - Blob storage: page/block blobs, BLOB = Binary Large OBjects = images, video, audio, etc. Unstructured data.
    - File storage
  - We get
    - premium SSDs
    - triple the operations/second
    - lower latency
    - more cost!
  - The highest premium typpe is Ultra, usually not used.

### Azure Blob Storage

Probably the most famous type os storage.

BLOB = Binary Large OBjects: It means basically any kind of file: PDF, ZIP, JPEG, AVI, ... and also, TXT, CSV, XLSX, ...

Main features:

- Data is stored in so called *containers* (not like Docker containers!); these are like buckets: these are like folders; each container contains blobs
- We have unstructured data
- Can be public/private
- We pay only what we use
- Amazon equivalent: S3
- We can choose the desired region: keep the data close to the compute that uses it; costs vary for each location.
- Redundancy: Azure keeps 3 copies of the data by default (locally or in zone).
  - We can choose the option of Global redundancy: 6 copies = 3 locally, 3 in another region.
  - Failover happens automatically behind the scenes: we don't notice if a disk has a failure, our data is save due to the other copies.
- Access tiers: scale of price depending on how access is easier or not
  - Hot: default, continuous access
  - Cool: cheaper storage, not that frequent access, but more expensive read/write
  - Cold: yet cheaper, less frequent access.
  - Archive: offline (cheapest). It takes several hours to find the files.

### Azure Storage Demos

See Section [12. Basic Demos](#12-basic-demos).

### Azure Files and Azure File Sync

In contrast to blob containers, Azure Files is the true hierarchical structure of a file system; it supports SMB (cross-platform) and NFS (Linux). We can mount it locally on our OS as a volume.

This is like a file server on the cloud, not on premises (prem); and we get additional benefits, like redundancy, recovery, failover, etc.

Azure File Sync is another related service which enables cloud tiering:

- Most used files are local (e.g., 20 GiB)
- Rest of files are on the cloud (20 TB, so hybrid storage)
- We can configura distributed access, backups, etc.

### Azure Migrate

It mighth be ambitious to move to the cloud. Azure Migrate is for that: it guides us.

We can look for Azur Migrate in the search bar and see its features.

![Azure Migrate](./assets/azure_migrate.jpg)

### Azure Data Box

Sometimes it is in-practical to upload huge amounts of data to the cloud. Therefore, Azure hase some HW options to upload data:

- Data box: 100 TB
- Data box disk: 8TB
- Data box heavy: 1 PB

These are basically HW pieces which are used to locally: we upload data to them much faster than using the Internet. Then, the HW is shiped to Azure/MS data centers.

## 7. Identity, Access and Security

Identity = Representation of a **Person, Application or Device**. Examples of identity:

- My name
- My email address
- An application
- A printer

Authntication of the identity can happen in varios ways

- Username + password.
- A secret key received via email or other means.
- A certificate that proves the id.

Some years ago, the mechanism to handle user identity authentication consisted in having a custom, own-managed server which checked the introduced username and password in a database. This is a very bad practice, because:

- Passwords were sometimes stored as plain text, not hashes; thus, if hacked, the passwords were leaked.
- Sometimes old hashing algorithms were used which have been hacked, e.g., MD5.
- In some cases, no password requirements were asked (e.g., 12 symbols, numbers and letters, etc.).

![Authentication: Old, Bad Ways](./assets/authentication_bad.jpg)

**Azure Active Directory (AAD)** and newly **Microsoft Entra ID** are two tools that provide authentication services; that way, we don't have to code our own solution (as said, bad practice). Microsoft Entra is not a replacement of AAD, but it has gained popularity; Entra uses web protocols such as Oauth and SAML.

We can use one of those services as identity provider in our application.

The new model is as follows:

- The user authenticates with the Identity provider (MS Entra), which returns a token, signed by it.
- The user then identifies in the server with the token signed by the trusted Identity provider, which recognizes the signature and the user ID.

This new approach is much more secure and saves a lot of work to the programmers.

![Authentication: Azure Active Directory and Entra](./assets/authentication_aad.jpg)

### Microsoft Entra: Benefits

- Security
  - More secure than hand-crafted solutions
  - MS is world-leader in secure identifications
- Reduced development time (very few lines) and easier support (MS offers support)
- Additional features
  - AI used to look at login patterns
  - Audit features
- Centralized administration
  - We have a central dashboard where we can manage the access of all users
- Single sign-on
  - We can user corporate log in data, or even social media log in data
  - Not need of creating extra credentials
- Integrates with other Azure services: VMs, storage, etc.

### Authetication vs Authoraization

In a nutshell:

- Authentication: user proving who they are, user id & PW.
- Authorization: ensure that user is allowed/permitted to perform an action.
  - Permissions: read, writen, admin, etc.
  - Usually, we should avoid giving admin priviledge.

### Azure AD Conditional Access

A typical way an account is hacked is when the hacker finds out the credentials of an user id; those hackers are usually somewhere else in the world. Therefore, we can start defining different levels of trust, or conditions, to accept the credentials:

- User A attempts to log in from an app **inside the company office**, as everyday, vs. they try to log in with an IP in Afghanistan; in the latter case, we might use an additional MFA step (send text message with a code).
- User B attempts to **log in for the first time in 4 months**: in that case, we should be more careful.
- User C is **administrator**: in those cases, we should be extra careful.
  - If the log in IP is far away from the office, we can be paranoid.

In summary, the *conditional access* tags each login as *routine* or *not normal*, and depending on the tag, more or less verifications need to be passed; after those verifications, Azure AD can enforce the action to:

- Allow access
- Allow limited access
- Deny access
- Block account
- ...

### Multi-Factor Authentication (MFA)

We have 3 additional factors (or pieces of evidence) we can require to authenticate:

- Something you know, i.e., password.
  - Can be hacked, not that secure; thus, companies ask to change PW frequently.
- Something you have, i.e., mobile phone, access to email account.
  - We receive a code via another mean, which is something additional we own.
- Something you are (typially biological), i.e., fingerprint, face.
  - The problem with this type of authentication is that we cannot change it.

Azure has 4 types of MFA:

- Authenticator App
- Email
- SMS
- Phone call

### Passwordless

MS is promoting another type of authentication than MFA: **Passwordless**.

If plotted in a plane of 2 dimensions (security and convenience), it's in the best quadrant.

![Passwordless authentication](./assets/passwordless.jpg)

How is that achieved?

- Gestures in a given device
- Face, fingerprint in a given device
- Sometimes we are logged in or haven been logged in some minutes ago in a device and try to open a new service, and instead of requiring a PW, the Authenticator might require us a code sent to the browser.

### Role-Based Access Control (RBAC)

MS's preferred solution. We create roles that represent the common tasks of the job:

- Developer
- Developer manager
- HR
- Finance
- etc.

We assign quite granular permission for each role; then, the unwanted effects are fewer, even if the user does something unexpected or we get hacked.

Once the roles have been created, we assigne users to roles; we can assign users to more than one role.

That makes easier also to handle many users: we define roles very specifically, and then new users are simply assigned roles.

Typical standard roles:

- Reader: read only.
- Contributor: read & write.
- Owner: ability to give permissions to other people.

### Zero-Trust Methodology

Analogy of the house: usually we lock the front door of the house, once we have the key, inside we don't have any more locks. With the Zero-Trust methodology, we need keys to every room, closet, etc.

The house front-door would be the Firewall; thus, we won't assume that behind the FW everything is secure. Instead, if an app is trying to use another one behind the FW, we'll ensure security measures to do it so: we'll require specific keys for that.

Three Zero-Trust principles:

- Verify explicitly: use every available method to  identify
- Use least privileged access
  - Just-in-time: grant access just then
  - Just-enough-access: grant only the minimum access required
- Assume breach has happened
  - Apply: Encryption, segmentation, threat detection (patterns: e.g., if a user downloads all code)

The MS Security Policy Enforcement diagram:

![Security Policy Enforcement](./assets/security_policy_enforcement.jpg)

- Identity verify and secure each identity
- Devices: check they are valid (compliance), i.e., updated versions, etc.
- Applications: monitor user actions (e.g., is user downloading complete code?)
- Data: protection, encrypt, restrict access
- Network: encryption
- Infrastructure: monitor to detect attacks, flag, report, etc.

### Defense in Depth

This concept consists in applying the security in different layers, not only the user id + PW. Seven security layers:

- Data - i.e. virtual network endpoint
- Application - i.e. API Management
- Compute - i.e. Limit Remote Desktop access, Windows Update
- Network - i.e. NSG, use of subnets, deny by default
  - NSG: Network Security Groups
- Perimeter - i.e. DDoS, firewalls
- Identity & access - i.e. Azure AD
- Physical - i.e. Door locks and key card

For each layer, we have several tools, and we should have at least one good of them active in each layer. We don't need to learn them for the exam.

![Defense in Depth Tools](./assets/defense_in_depth_tools.jpg)

### Microsoft Defender for Cloud

Microsoft Defender for Cloud is a service we can pay to protect different resources.

![Cloud Defender](./assets/cloud_defender.jpg)

The service has a different cost for each resource.

We can do many things:

- Reports and suggestions related to the current protection status
- Apply recommendations automatically
- ...

## 8. Cost Management

### Factors Affecting Cost

- Free services
  - Resource groups
  - Virtual Networks (up to 50)
  - Load balancers (basic)
  - Azure Active Directory (basic)
  - Network Security Groups
  - Free-tier web apps (up to 10)
- Rest of services: we need to pay depending on different factors, such as:
  - Time
  - Number of executions
  - Amount of data consume
  - Backup costs
  - Number of regions
  - ...

Models:

- Pay-per-use
  - Azure Functions
    - 1 million executions free per month
    - Then, 0.2 USD per million execution
    - In contrast, if we used the cheapest VM instead of Functions, the minimum cost would be 20 USD/month
  - Logic Apps
  - Storage (pay per GB)
  - Outbound bandwidth
  - Cognitive Services API
- Pay-per-time (charged by the second)
  - Example: VMs
  - We might want stability in pricing (esp. the Finance department); since cloud costs are unpredictable sometimes, we can in some cases pay/reserve upfront for 1-3 years of a VM usage, for instance.
- Pay-for-bandwidth:
  - Typical: first 5GB free
  - Inbound data is free.
  - Depending on the regions, the pricing is different.
  - Example: if we want to download/transfer 1 PB of data, the cost in data transfer will be 52k USD! When happens that? For instance, when we want to move freom Azure to AWS.

### Azure Pricing Caltulator

Pricing Calculartor: [Azure Pricing Calculator](https://azure.microsoft.com/en-us/pricing/calculator/)

The tool is used for educated guesses: we don't get perfect estimates.

Configurable options: Region, Tier, Subscription Type, Support Options, Dev/Test Pricing, etc.

It has the feeling of a shopping cart, where we configure the products we'd like, we get a price and we can export/share the budget:

- We select several services/resources: VM, storage, etc.
- We configure them: region, tier, usage, reservations, licenses, etc.

### Total Cost of Ownership Calculator

The cost of running a server has other costs that are not explicitly mentions:

- Electricity
- Colling
- Internet connectivity
- Rack space (buildings)
- Setup labor
- Maintenance labor
- Backup
- etc.

MS has a calculator which measures those extra costs as a way to show the trade-off of using cloud computing:

[Total Cost of Ownership Calculator](https://azure.microsoft.com/en-us/pricing/tco/calculator/)

Similarly as before, we define our data center:

- Number of servers
- Storage
- etc.

At the end, we get

- What we would save if used Azure, according to MS
- The cost over time projection: with on-prem model and using Azure

### Azure Cost Management

There is a service called **Cost Management** which helps us check the costs we are having, where, when, make predictions, etc. We can also set **budgets**, which are linked to notifications when these are surpassed.

![Cost Management](./assets/cost_management.jpg)

Here, we'll find also:

- Invoices
- Scheduled reports
- etc.

### Resource Tags

Every time we create a resource (e.g., a VM), we can assign tags to it; these metadata are related to costs and support. We can create cost reports by tag,for instance.

Example tags:

- CreatedBy
- BillingCode
- Department
- (don't put any sensitive data!)

## 9. Governance and Compliance

Governance: composed by the management leaders; those leaders decide to adopt some IT policies; for instance: always have a daily backup. How can we inforce that policy?

- Option 1: Send an email to all employees and hope that they follow the policies
- Option 2: Use Azure tools to enforce rules; we can also audit for compliance.

There are several Azure tools to support **Governance and Compliance**:

- Azure Blueprints
- Azure Policy
- Resource Locks
- Microsoft Purview

### Azure Blueprints

Azure Blueprints = Templates for Azure Subscriptions with pre-defined Roles and Policies.

![Azure Blueprints](./assets/azure_blueprints.jpg)

Blueprints are the only way to assign *deny permissions*; the rest of the methods assign only *allow permissions*.

### Azure Policy

Main policy enforcement tool.

We can create rules that apply to sets of Azure resources (different scopes).

We can evaluate compliance to the rules.

Examples of built-in policies:

- Require SQL server version
- Alloeed storage account SKUs
- Allowed locations
- Allowed VM SKUs
- Apply tags and default values
- Not allowed resource types

Custom policies are created in JSON format.

Look for **Policy** in search bar; in `Definitions` tab (left menu):

- We see +1k standard policy definitions
- We can filter by keywords, e.g. backup
- If we click on one, we see it's defined as a JSON, which can be copied and modified; in any case, we can also use the web UI to define the policy by clicking on `Assign` and going through the condiguration panels.
- If we click on `Assign` after having selected a policy template, a configuration menu/panel with different tabs is opened
  - Basics:
    - Assign to a scope: subscription, resource group, etc.
    - Exclude resources or not
    - Turn on/off
  - Advanced
  - Remediation: by default, only applied to new resource groups, or require also from old?
  - ...
  - Then, we create the policy and it's done!

### Resource Locks

We can enforce locks to resources:

- Read only: make a resource only readable, we cannot change it.
- Cannot delete: we can change the resource, but not delete it.

To use it: we go to a resource (e.g., a VM), select `Locks` (left menu), and `Add` one. Then, we select the lock type: Read-only, Delete (= Cannot-Delete).

![Locks](./assets/locks.jpg)

If we activate the *Delete* lock and try to delete the resource, an error occurs. If we remove the lock, we can delete the resource; the trick is to assign permissions of add/removing locks only to given users/roles.

### Microsoft Purview

It allows **Unified Data Governance**. It has 9 features:

- Auditing data
- Communication compliance
- Data mapping and cataloguing: where is the data, where it comes from
- eDiscovery
- Information protection
- Insider Risk Management
- Data Lifecycle Management: how do you handle data from creation to archiving
- Data Loss Prevention
- Compliance manager: dashboard which evaluates company in terms of data protection

Example: Communication Compliance; every company has communication rules. Let's take as example a finance company.

- The traders department and teh analysts deparment might be incommunicated: we need communications firewall.
- Also, people who work with Visa and Mastercard account within a company might be incommunicated.

We might want to enforce content communication compliance: avoid inappropriate content, etc.

Similarly, sometimes data can be classified as *secret*, *protected*, etc. For given classifications, we can track where those data were distributed.

Another example: someone is fired; if the account is not immediately blocked/restricted, that person might do some bad things because they are angry: delete data, say something offensive/bad to colleagues in company channels, etc.

## 10. Tools for Managing Deployments

### Azure Portal and Command Line Tools

- Azure Portal: Web UI
- Azure CLI SDK: [How to install the Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)
  - We can use it to write scripts, e.g., to create VMs, etc.
  - Then, all those scripts can be source-controlled.
- Azure Cloud Shell: Powershell or Bash CLI
  - Terminal built-in to Azure Portal

See [Extra: Azure CLI/SDK](#extra-azure-clisdk) with example commands.

### Azure Arc

> See and manage all your on-prem infrastructure, anywhere. It's free to get started.

One possible use-case is to have our Kubernetes cluster running on premises or on AWS, for instance, and see and manage it via Azure Arc.

We can register:

- VMs
- Kubernetes clusters
- SQL servers
- ...

### Infrasturcture as Code (IaC)

Infrastructure: servers, storage, database and settings, network and settings, firewalls, load balancers, etc.

Infrastructure is everything that is not data nor programs; it's the glue and foundations that make possible to run the programs which use the data.

How can we back up the insfrastructure? IaC makes possible to do that in a config file. That way, we can even version-control that file. Thus, we can have different versions which can be re-deployed in different places.

Desired State Configuration (DSC): using automation to ensure your configuration doesn't drift from the original setup. Imagine we set up a deployment in 2020; over time, the configuration changes, it drifts from the original. The idea behind DSC is having a configuration file which can be used any time.

IaC options:

- **ARM Templates (JSON)**
- **Bicep: you can compile Bicep scripts into ARM Templates**
- Terraform: 3rd Party solution from HashiCorp
- Chef, Puppet
- PowerShell scripts: not as flexible
- ...

### ARM Templates, Azure Resource Manager

ARM Templates = Azure Resource Manager: Service that runs underneath which allows to interact with all the services.

![Azure ARM](./assets/azure_arm.jpg)

We work with ARM **Templates**, which are **JSON** files that contain resources and their configuration.

To see how to work with those templates/JSON files, we create a new resource in the Azure portal, a *Storage Account*

    Storage account, create
    Basic
      Subscription
      Resource group: rg-storage-arm-test
      Storage account name: storagearmtest42
      Region: West Europe
      Performance: Standard
      Redundancy: Local (LRS)
    Advanced: default
    Networking: default
    Data protection
      Disable all
    Encryption: default
    Review
    NOW: We don't click on Create, but on
    Download a template for automation

When we click on `Download a template for automation`, we get a JSON with all the configurations we clicked. Then, we can:

- Click on `Download`: the JSON files ad downloaded in a ZIP. The ZIP folder is saved uncompressed into [`storage_arm_template/`](./examples/storage_arm_template/); it contains two files:
  - [`template.json`](./examples/storage_arm_template/template.json): This file contains the actual template with the resources and configurations that will be deployed.
  - [`parameters.json`](./examples/storage_arm_template/parameters.json): This file contains parameter values that are passed into the template during deployment, allowing you to customize the deployment without changing the template itself.
- Add to the `Library`: we add it to a cloud repository where we have custom templates; these are like template specs.
  - We save it in a RG.
  - In the RG, we can go to the template and click on `Deploy`.
  - Sometimes parameters need to be re-entered.
- `Deploy` it.

#### Ex-Course: Deploying the ARM Template with the CLI

In this subsection, the downloaded JSON files are used to deploy the Storage account defined above.

```bash
cd .../examples
az logout
az login

# Set the subscription, to be more comfortable
az account set --subscription "<Your-Subscription-ID-or-Name>"
az account set --subscription "Azure subscription 1"

# Use the 'az deployment group create' command to deploy your ARM template to a resource group (which has been previously created)
# The @ symbol is used to indicate that the value is coming from a file.
az deployment group create --name StorageAccountARMDeployment1 --resource-group rg-storage-arm-test --template-file storage_arm_template/template.json --parameters @storage_arm_template/parameters.json

# Now, we should see it in the Azure Portal!
```

## 11. Monitoring

### Azure Advisor

It analyzes the resources we're using and makes recommendations based on patterns; for instance:

- If we have a VM and we're not using it at its maximum capacity; then, Azure would recommend us to downsize it to a smaller one.
- Analyze the performance of apps.
- Security recommendations: RDP port open for a long time.
- Suggestions on availability zones, etc.

We also get expected costs if the suggestions are implemented.

However, it seems that we need to create extra user accounts, since I get this error/notification:

> In order for single sign on to work correctly, users must be created both in Microsoft Entra ID and the target application.
> Open the application's admin console and follow the directions for adding users, if you haven't done so already.

### Azure Service Health

This tool refers to Azure regions in general, not our resources. If we plan to deploy something in a location or have something deployed, but doesn't work as expected, we can check Azure Service Health in the Portal.

In the Health history tab (left menu) we can see past events.

![Azure Service Health](./assets/azure_health.jpg)

### Azure Diagnostics Settings and Azure Monitor

We apply monitoring to the resources; for instance, in Storage account, we have:

- Alerts: emails sent
- Metrics: traffic data
- ...

We can save that information to the Dashboard, and we select the frequency with which the metrics are saved. We can also activate the diagnostic settings and save them to another storage account.

Then, if we look for `Monitor` in the search bar, we see that Azure Monitor dashboard, where all logs that are being monitored are aggregated/shown. We can query the saved logs, etc. A special query language is used.

In particaular, `Monitor | Log` (left menu) is interesting; that's where we can write elaborate queries with desired scopes.

`Monitor | Workbooks`: sets of key metrics to follow.

## 12. Basic Demos

First, create an Azure account; I created one with the Github credentials.

- The first time, we can have a Free Azure account.
- After the Free period finishes, we need to upgrade it; we can do that by selecting
  - Pay-as-you-go, then Basic
  - Add a card

After that, we basically open the [Azure portal](https://portal.azure.com).

The first time, we might need to be requested to create a Subscription.

This section is very interesting, because we see in practice the features of the difference services/resources.

Very important to avoid unwanted costs! Delete the created resources, if not used:

    Open each Resource Group > Delete resource group!

### Create a Virtual Machine (VM)

This very simple demo shows how easy it is to create a VM in Azure.

In [Azure portal](https://portal.azure.com), look for `Virtual Machines` and click on `Create`.
We'll see the typical form composed of several tabs that needs to be filled in to configure/define the resource we want to create.
Each resource has its own features, but the form and the process of creation are similar.

![Azure VM: Create Form](./assets/azure_create_vm.jpg)

We fill in the form:

    Basics
        Subscription: billing account
        Location/Region
          Not all regions offer all services, sometimes we need to check them
        Resource Group: every resource goes to a group
        Name
        Operating System: Windows, Linux (the most chosen)
        Availability options: we can choose to deploy redundant instances -> Zone / VMSS / etc.; we can take None for this example
          Availability zones: if Zone chosen as availability option, we can select the number oz available zones in the Region
        Security Type: Standard; we can upgrade to Trusted if needed
        Image
          There are 9k images! Click on See all images
          In most cases we have an OS + a concrete SW running on top: SQL server, etc. Sometimes licensing options are provided.
          Examples
            Windows Server 2022
            Ubuntu Server 22.04 LTS
        VM architecture
          Arm64: power-efficient new arch (e.g., Apple M1/2), gaining popularity
          x64: typical desktop arch, most extended
        Size: vCPU & RAM
          See all sizes
          Select appropriate; the bigger, the larger the cost
          Standard B1
        Spot instances: free VMs assigned, but can also be evicted (cheaper)
        Authentication type / Administrator account
          Username, Password (if Windows VM, optional in Linux)
            azuser
        Inbound Ports: 
          SSH (Linux), RDP (Windows), HTTP (80), HTTPS (443)
          If we want a web server, we need all those
    Disk
        Hard Disk: SSD, etc.
        Disks independently of VMs, we can choose to keep them 
          https://learn.microsoft.com/en-us/azure/virtual-machines/delete
        We can leave the defaults if we want
    Networking
        Virtual Network (created a new by default)
        Subnet (created a new by default)
        Public IP (created a new by default)
        Load balancers
        ...
        We can leave the defaults
    Management
        Antivirus
        Auto-shutdown
        Backups
        OS Updates
    Monitoring
        OS dignostics
        Boot diagnostics: disable!
    Advanced
        ...
    Tags
        Phone number, etc.

Finally, we `Review + Create`, `Create` and it is deployed.

Then, we can connect to it (RDP, SSH); open the VM resource in the Azure Portal and click on the `Connect` button for more information.

A standard VM costs around 2-17 USD cents/h; however, it's charged by the second.

After the VM is created, we can go to its RG (Resource Group) and check all the resources associated to it:

- The VM itself
- The VNet (virtual network)
- The Network Security Group
- The Public IP
- The Network interface
- ...

![VM Resource Group](./assets/vm_rg.jpg)

We can open the VM resource and check its status or tune its settings:

- We see it's running
- We see its public IP adress
- We can change the size (it stops and starts the VM again)
- ...

### Connecting to a VM

Once the VM has been created as explained in the section above, we can connect to it.

We go to the VM, click on `Connect`.

If the instance is a Windows Server: **RDP connection**:

- A file is donwloaded, we execute it and we can see the Windows desktop in the browser.
  - We need to introduce our username + pw (the ones we created)
- The first time a Windows server is started the configuration is launched (Server manager); we could configure it to be a web server.

If the instance is a Linux, we can connect in 2 ways:

- SSH using Azure CLI: in Azure portal, using the Azure CLI
- **Native SSH**: on the local machine
  - A SSH key is necessary, even if we have chosen user+pw authentication
  - If we don't have an SSH key, we create one and it is donwloaded, e.g.: azure-key-test.pem
  - We place it in `~/.ssh`
  - Then, we open a Terminal an ssh into the VM using the Public IP

```bash
# Download the SSH key to ~/.ssh/azure-key-test.pem
ssh -i ~/.ssh/azure-key-test.pem azuser@<Public-IP>
# If we have specified a username + pw, we are prompted to introduce the PW
```

### Create an Azure App Service - Web App

Web apps are more abstracted components, PaaS: We simply deploy our code and configuration.

We click on `Create > Web App`.

As for the VM, the definition parameters need to be set:

    Basics
      Subscription
      Resource Group
      Name
        The name needs to be unique, since we get a DNS based on it
        E.g., yet-another-web-app.azurewebsite.net
      Publish: we can choose between
        [x] Code
        [ ] Docker Container
        [ ] Static Web App
      Runtime stack: we can choose basically the main language + version
        Python, Java, PHP, .NET, Node
      Region
      Pricing Plan: F1 (Free) / B1 (Basic) / ...
        The prices depend on the capabilities of the plan
        The plans are listed according to ACUs = Azure Compute Units
        We can see how much powerful a plan is compared to another by checking their ACU values
      Zone redundancy
        Obly for the Premium options
        Disabled
    Database
      Not for free plans, but available for basic
    Deployment
      We can connect a Github repo so that we apply CI/CD
      Not for free plans, but available for basic.
    Networking
      We can enable public access or not: usually a web app is accessible from the Internet
      Enable network injection: we can disable internet access and enable access from another Azure VNet
        Not for free plans, but available for basic.
    Monitoring
      Disable
    Review + Create, Create
      The B1 plan costs 13 USD / Month

### Modifying and Using an Azure App Service - Web App

Once the App Service / Web App has been deployed, we can go to its resource group to check all its related resources:

![Web App: Resource Group](./assets/web_app_rg.jpg)

If we click on the web app itself, we interact with it can modify many things of it:

- **Scale up** app service plans (left menu): basic -> standard -> premium
- **Scale out** (left menu): manual/automatic number of instances, etc. We can set some scaling rules, e.g.: scale up/down if x% of CPU is used, etc.
- We can open a web **SSH** to it (left menu)
- **Deployment slots**: if we have a Standard/Premium plan, we can deploy more than one web app simultaneously; use cases:
  - One version could be dev, the other prod.
  - We can control the % of traffic that goes to each other, so we perform A/B testing
  - ...

![Web App: Scale App Service Plan](./assets/web_app_scale.jpg)

### Create Azure Functions

Another even more abstracted method than web apps are Azure Functions.

We click on `Create > Web App`.

    Basics
      Subscription
      Resource Group
      Name
        The name needs to be unique, since we get a DNS based on it
        E.g., yet-another-azure-function.azurewebsite.net
      Publish: we can choose between
        [x] Code
        [ ] Container Image: we can even create our own images and used them!
      Runtime stack: we can choose basically the main language + version
        Python, Java, PHP, .NET, Node, etc.
      Region
      Operating System
      Hosting plan: how we are charged, how it scales
        [x] Consumption: Serverless: we don't need to care about anything; for event-driven workloads
          That's the ideal choice for Functions
        [ ] Functions premium: for workloads running continuously
        [ ] App service plan: functions co-located with app services; similar to an app service
    Networking
      We can enable public access or not: usually a Function is accessible from the Internet
      Enable network injection: we can disable internet access and enable access from another Azure VNet
        Available only starting at Function premium.
    Monitoring
      Disable
    Deployment
      We cann connect our Github account + repo & branch
      to perform Continuous deployment.
      We leave it without connection for this example, since we will write the code another way.
    Review + Create, Create
      The B1 plan costs 13 USD / Month

We haven't written the function code yet, but the Azure Function is deployed. Now, we open the Function resource in the portal and select to write the code with VSCode:

- We sign in to MS Azure using VSCode.
- We need to have the Azure extension on VSCode

Then, we are brought to the site [Develop Azure Functions by using Visual Studio Code](https://learn.microsoft.com/en-us/azure/azure-functions/functions-develop-vs-code?tabs=node-v3%2Cpython-v2%2Cisolated-process&pivots=programming-language-python), which explains to to proceed in VSCode by creating a new Function locally.

Basically:

- We create a local Function in a desired folder
- Select a language: Python
- Select a programming model: V2
- Select a Python interpreter
- Select a typo of trigger: Functions have a trigger which makes them run:
  - [x] HTTP trigger: when we open the URL, they run
  - [ ] Blob
  - [ ] CosmoDB
  - [ ] EventGrid
  - [ ] Timer
  - [ ] ...
- Name: `http_trigger`
- Authorization: Function (usual), Anonymous (anyone can access/use it), Admin
- Then, the Function environment is created with an example Python file.

![Azure VSCode Function](./assets/azure_vscode_function.png)

**However**, I have not managed to upload/deploy the local Function to the Azure instance yet! Maybe the best idea is to link a Github repository or use a container instead of code...?

### Create Azure Container Instances

We can also use containers in Azure, actually in several ways:

- Web apps support containers
- Functions support containers
- VMs can have containers
- Service Fabric
- ...

However, there are 3 specific resources that are designed for containers:

- Azure Kubernetes Service (AKS)
  - Enterprise-level orchestration
  - A cluster is built
  - Orchestration: management of different containers, networking, etc.
- Container Apps:
  - Easier to use than a Kubernetes, but limited to containers, not clusters.
  - Scaling is possible, and load balancing is done, too.
  - It's very similar to web apps.
- Contariner Instances: smallest, quickest way to deploy a container
  - Designed for low-prio jobs, for testing, etc.
  - Not critical part of an application
  - Not great at scaling, etc.

This section shows how to create a **Container Instance**.
Look for it in the search bar and click on `Create`:

    Basics
      Subscription
      RG: we can create one, e.g., rg-udemy-aci
      Container name (unique): aci-test
      Region: West Europe
      Avalability Zones: None
      SKU: Standard
      Image source
        [x] Quistart images: blank template images provided
        [ ] Azure Container Registry: we can have an Azure Registry and push an image there
        [ ] Other registry: We use another registry
      Image
        ms/aci-helloworld:latest
        Hello World template
      Size
        1 vcpu, 1.5 GiB
    Networking
      Public: with puclic IP, accessible from Internet
      Other options: Private, None
      Here, we can also specify a Fully Qualified Domain Name/address = FQDN
    Advanced
      Restart policy
    Review + Create, Create

Now, we can go to the resource and we can see:

- Overview (left menu): the public IP address, along with the FQDN (domain)
- Containers (left menu): events, properties, logs, etc.

If we open the public IP, we see the image of the *Hello World* container:

![ACI Hello World](./assets/aci_helloworld.jpg)

### Create Azure Container Apps

Azure Container Apps are newer than Container Instances.
Apps provide some scaling capabilities compared to the instances; it's very similar to a web app.

Look for **Container Apps** in the search bar and click on `Create`:

    Basics
      Subscription
      RG: we can create one, e.g., rg-udemy-aca
      Container app name (unique): aca-test
      Container Apps Environment
        Region: West Europe
        Container Apps Environment
          This is similar to the web apps' app service plan, it's a hosting plan
          We create one.
            Basics
              Environment type: Workload / Consumption
              Zone Redundancy
            ... Leave the defaults.
    Container
      We can use a quickstart image
      or select an image source: Azure Container Registry / Docker Hub
      We select for the demo purpose the Quickstart Hello World
    Review + Create, Create

Once created, we can open the resource and explore its options (left menu):

- Containers: we see which containers are deployed
- Scale and replicas: we can define scaling rules by clicking on `Edit and deploy`.

### Create an Unmanaged Storage Account, Upload and Manage Files

Look for **Storage account** in the search bar and click on `Create`:

    Basics
      Subscription
      Resource group: we can create a new one, e.g., rg-udemy-storage-demo
      Storage account name: must be unique in Azure, e.g., udemystoragedemo
      Region: West Europe; it has an effect on cost
      Performance: Standard / Premium (a lot faster: SSD)
        If we select Premium, we need to choose an account type
          Block blobs: high transaction rates, low storage latency (more general)
          Page blobs: best for random/read operations
      Redundancy: Local LRS (3 copies locally) / Geo (3+3) / ...
    Advanced
      Security
      Access protocols
        We can choose to enable SFTP access
      Blob storage access tiers: hot / cold (half the price for storage, but more expensive access)
      Azure files: simulated the old SMB protocol, it enables to mount the drive on Windows
    Networking
      Access:
        Public (but still key is required)
        Public from selected VNets
        Disable
      Network routing
        MS has its own networks world-wide; we can choose to use them instead of the regular internet.
    Data protection
      Recovery: options for soft delete (trash can)
      Tracking: option for versioning
      Access control: we can make data immutable, i.e., ensure it does not change (important for legal stuff)
    Encryption
      Encrypted by default, but we can use our own keys, etc.
    Review + Create, Create

We then go to the resource and we see something like this:

![Azure Storage Account](./assets/azure_storage_account.jpg)

As we see in the left panel, we have 4 types of data that can be stored:

- Containers: Blob storage; like a bucket where we can store BLOBs, things.
- File shares: File storage
- Queues: one app comes and leaves a message, the other comes then and reads it; it's a messaging service
- Tables: similar to a DB, but not as reliable as CosmosDB

For all of these 4 types, we need to create their instances to use them.

#### Containers = Buckets for BLOBs

We will focus on **Containers**, not to be confused with docker containers; storage containers are like buckets. Once a Storage account is created, we need to create containers in it:

    Got to Storage account resource
    Containers (left menu)
      + Container
      Name: firstone
      Anonymous level: Private; all other require no key to access the data

Now, we have a container `firstone` in our Storage account. If we go to the container, we can upload files (e.g., files) to it manually and set different properties to them (e.g., blob type, access tier, etc.)

![Storage Container: Upload BLOB](./assets/storage_container_upload_blob.jpg)

Even though storage accounts are created public, we'll need a key to access the files in them.
Storage account keys are located in the `Access keys` (left menu) tab; however, we won't use them &mdash; they should be kept secret.
Instead, we create **Shared Access Signatures (SAS)**, which can be created at container or blob level (do it in the blob/file level to visualize the file/image in the browser):
    
    Select desired element (container, blob, etc.) > Click on `...` > `Generate SAS`
      Important: Check the Permissions we want

In the SAS generation window we can configure the time window of the key, among others, and them create a **SAS token and URL**.

If we take the **URL**, we can access the file via a browser or any other app which operates with the HTTPS protocol.

![Dall-e Cloud](./assets/DALL·E%202024-02-23%2016.24.17%20-%20A%20realistic%20photo%20of%20a%20single%20cloud%20in%20the%20sky%20during%20the%20day.png)

In the left side menu of the storage account we can see several interesting tabs:

- Data management: Redundancy: where the files are, etc.
- Data management: Lifecycle management: we can define rules to manage blobs, e.g., if a file hasn't been modified in a moth, move to cold storage, or vice versa.

#### Storage Browser

Storage services should be used programmatically; if we want to use the browser, we can use the `Storage browser` option (left menu on container).

#### AzCopy: Programmatic Copy of Storage Elements

[AzCopy](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) is a CLI tool that can be used to upload/download files to/from storage accounts; we can use it to move data between storage accounts, too, even between Azure and other cloud provides (e.g., AWS).

- We [download AzCopy](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10#download-azcopy); it is a binary, so I
  - Copied it to `C:\Users\Username\bin\azcopy\10.23.0`
  - And added that path to the Environment variables (Path)
- We create the SAS for
  - the source file/blob: SRC = 'https://xxx'
  - the destination container: DST = 'https://yyy' (we should have write/full permisions here, check them when generating the SAS)
  
Then, we run the command in the Terminal or also in the Azure cloud shell:

```bash
# Check help
azcopy -?

# Copy one file SRC to a container DST
# We can also copy a local SRC file to a DST container!
azcopy copy SRC DST
azcopy copy 'https://xxx' 'https://yyy'
```

This is not the only way of doing it: we can also use authentication instead of SAS, etc.

## 13. Examples

The folder [`examples`](./examples/) is a stand-alone directory which contains independent practical examples, explained in the `README.md` located in there.

## Extra: Spending Limits

Select Subscription > Budgets: Create/Add one; for instance:

- Name, e.g., `HobbyBudget`
- Amount: 10, monthly
- Expiration date: +1 year
- Alerts: add one, e.g., 90% of actual
- Alert emails: xxx

## Extra: Azure CLI/SDK

Not part of the AZ-900 course/exam.

Important links:

- Azure CLI SDK: [How to install the Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli).
- [Azure CLI onboarding cheat sheet](https://learn.microsoft.com/en-us/cli/azure/cheat-sheet-onboarding)
- [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/)

In the following, some handy commands of the Azure CLI/SDK are shown.

Usually, we'd use them in scripts.

```bash
# Set proxy, if required.
# Log out, just in case we're logged in with another account
az logout
 
# Log in via web: Browser is automatically opened
az login
 
# Get Object ID = User ID: Value in field "id"
az ad signed-in-user show

# List all Azure Function Apps
az functionapp list

# List all Azure Web Apps
az webapp list

# Create a ne wresource group
# After the command, we should see it in the Azure portal
az group create --name rg-newrg --location eastus

# Create a VM
# There is a command which lists all images
az vm create  --resource-group rg-newrg --name newvm --image Win2019Datacenter --public-ip-sku Standard --admin-username azmsuser
# Then, a PW is asked; note that we chose Windows, which requires username and password

# Open the port 80 of the VM
az vm open-port --port 80 --resource-group rg-newrg --name newvm

# Delete a resource group and all its contents
az group delete --name rg-newrg

# Get access token (but which token?)
az account get-access-token
```

## Extra: Azure Cloud Shell

Not part of the AZ-900 course/exam.

[Azure Cloud Shell Tutorial - Adam Marczak](https://www.youtube.com/watch?v=If4g2vVaiYk)

The Azure Cloud Shell is a Terminal that can be opened from the Azure Portal; the Azure CLI SDK is installed in there and we can used both PowerShell and Bash CLI.

A storage is created whenever we enable the Azure Cloud Shell. That storage persists across different Cloud Shell sessions, so we can have different scripts stored in it, associated to our account. The Azure Cloud Shell is free, but the storage not; however, the cost should be minimal if we don't save many things in it.

## Extra: Azure Blob Storage

Not part of the AZ-900 course/exam.

:construction:

## Extra: Azure Cognitive Search

Not part of the AZ-900 course/exam.

:construction:

## Extra: Azure Form Recognizer

Not part of the AZ-900 course/exam.

:construction:

## Extra: Azure Keyvaluts

Not part of the AZ-900 course/exam.

:construction:

## Extra: Azure OpenAI

Not part of the AZ-900 course/exam.

:construction:
