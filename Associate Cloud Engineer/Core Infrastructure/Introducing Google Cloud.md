# Introducing Google Cloud

### Cloud Computing Overview
* Cloud computing is a way of using information technology that has these five equally important traits
    * Customers get computing resources that are on-demand and self-service
    * Customers get access to these resources over the internet, from anywherre
    * The provider of these resources allocates them to users out of that pool
    * Resources are elastic - which means they're flexible, so customers can be
    * Customers pay only for what they use, or reserve as they go
* History of the cloud model:
    * First wave: **Colocation** gave users the financial efficiency of renting physical space
    * Second wave: The components of **virtualized data centers** match the physical building blocks of hosted computing but now they're virtual devices
    * Third wave: Container-based architecture, which Google Cloud provides to customers

### IaaS and PaaS
* The move to virtualized data centers introduced customers to two new types of offerings: Infrastructure as a Service (IaaS) and Platform as a Service (PaaS)
* IaaS offerings provide raw compute, storage and network capabilities that are organized into resources that are similar to physical data centers
* PaaS offerings, in contrast, bind code to libraries that provide access to the infrastructure that the application needs - this allows more resources to be focused on the app logic
* In the IaaS model, customers pay for the resources they allocate ahead of time
* In the PaaS model, customers pay for the resources they actually use
* As cloud computing has evolved, the momentum has shifted towards managed infrastructure and managed services
* Serverless allows developers to concentrate on their code, rather than on server configuration, by eliminating the need for any infrastructure management.
    * Cloud Functions, which manages event-driven code as a pay as you go service
    * Cloud Run, which allows customers to deploy their containerized microservices-based apps in a fully managed environment
* Software as a Service (SaaS) apps aren't installed on your local computer - they run in the cloud as a service and are consumed directly over the internet by end users
    * Gmail, Docs, and Drive

### The Google Cloud Network
* Designed to give customers:
    * Highest possible throughput
    * Lowest possible latencies
* Leverages 100+ content caching nodes worldwide
    * High demand content is cached for quicker access
* Google Cloud's infrastructure is based in five major geographic regions:
    * North America
    * South America
    * Europe
    * Asia
    * Australia
*  App location affects:
    *  Availability
    *  Durability
    *  Latency
* Latency measures the time a packet of information takes to travel from its source to its destination
* Each location is divided into several different regions and zones
    * Regions represent independent geographic areas and are composed of zones.
    *  For example, London is known as region europe-west2 and is composed of 3 zones
    *  A zone is an area where Google Cloud resources are deployed
    *  For example, if you launch a virtual machine using Compute Engine, it will run in the zone that you specify to ensure resource redundancy
    *  Can also run resources in different regions - useful for bringing apps closer to users around the world and also for protection in case there are issues within an entire region such as a natural disaster.
    *  For example, Cloud Storage lets you place data within the Europe multi-region - means that it's stored redundantly in at least two geographic locations separated by at least 160km within Europe, like London and Belgium
    
### Environmental Impact
* Altogether, existing data centers use roughly 2% of the world's electricity
* Google's data centers were the first to achieve ISO 14001 certification, which is a standard that maps out a framework for an organization to enhance its environmental performance through improving resource efficiency and reducing waste

### Security
* Hardware infrastructure layer
    * Hardware design and provenance
    * Secure boot stack
    * Premises security
* Service deployment layer
    * Encryption of inter-service communication
* User identity layer
    * User identity
* Storage services layer
    * Encryption at rest
* Internet communication layer
    * Google Front End (GFE)
    * Denial of Service (DoS) protection
* Operational security layer
    * Intrusion detection
    * Reducing insider risk
    * Employee Universal Second Factor (U2F) use
    * Software development practices

### Open Source Ecosystems
* Google publishes key elements of technology using **open source licenses** to create ecosystems that provide customers with options other than Google
* For example, TensorFlow is an open source library for machine learning at the heart of a strong open source ecosystem
* Kubernetes and Google Kubernetes Engine give the ability to mix and match microservices running across different clouds
* Operations Suite let customer monitor workloads across multiple cloud providers

### Pricing and Billing
* Google was the first major cloud provider to delivery per-second billing for its IaaS service compute offering Compute Engine.
* Per-second billing is now also offered for users of Google Kubernetes Engine (container IaaS), Dataproc (equivalent of the big data system Hadoop but operating as a service), and App Engine flexible enviornment VMs (PaaS)
* Compute Engine offers automatically applied sustained-use discounts, which are automatic discounts that you get for running a VM instance for a significant portion of the billing month
* When you run an instance for more than 25% of a month, Compute Engine automatically gives you a discount for every incremental minute you use for that instance
* Custom VM types allow Compute Engine VMs to be fine tuned with optimal amounts of vCPU and memory for the app so that you can tailor your pricing for your workloads
* You can define budgets at the billing account level or at the project level
* A budget can be a fixed limit or it can be tied to another metric, for example, a percentage of the previous month spent
* To be notified when costs approach your budget limit, you can create an alert - alerts are generally set at 50%, 90%, and 100%, but can also be customized
* Reports is a visual tool in the Google Cloud Console that allows you to monitor expenditure based on a project or services
* Google Cloud implements quotas which are designed to prevent the over consumption of resources because of an error or a malicious attack protecting accounts' owners and the Google Cloud community as a whole
* Two types of quotas: Rate quotas and Allocation quotes - both are applied at the project level
    * Rate quotas reset after a specific time. 
        * For example, by default, the GKE service implements a quota of 1000 calls to its API from each Google Cloud project every 100 seconds. After that 100 seconds, the limit is reset
    * Allocation quotas govern the number of resources you can have in your projects
        * For example, by default, each Google Cloud project has a quota allowing it no more than five virtual private cloud networks
* Although projects all start with the same quotas, you can change some of them by requesting an increase from Google Cloud support

