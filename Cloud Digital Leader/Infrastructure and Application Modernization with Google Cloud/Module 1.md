### Infrastructure Modernization
* First in moving away from an on-prem infrastructure is colocation.
    * A business sets up a large data center, then other organizations rent part of that data center.
    * Organizations no longer have to pay for the cost associated with hosting the infrastructure, but they still need to pay to maintain it. 
* Hardware is often heavily underutilized even in the colocation model, so engineers found a way to package applications and their operating systems into a virtual machine.
    * VMs share the same pool of computer processing, storage, and networking resources. 
    * Optimize the use of available resources and enable businesses to have multiple apps running at the same time on a server in a way that is efficient and manageable.
    * Problem: Still a cap to the physical capacity of existing servers, and companies still have to commit to a substantial amount of capital expenditure upfront.
* Public cloud providers offer infrastructure as a service to help move some or all of an organization's infrastructure away from physical data centers to virtualized data centers in the cloud.

### Compute Options in the Cloud
* Think of the cloud as an on demand self-service for anyone in the business. 
* Broad network access means that access to data and compute resources is no longer tied to a particular geography or location.
* Resources are distributed across a global network of data centers.
    * Resource pooling: If one is down, another data center is available to prevent service disruption.
* Rapid elasticity: Can scale up or down instantly without interruption.
* Compute (cloud context): Refers to a machine's ability to process information to store, retrieve, compare and analyze it, and automate tasks often done by computer programs.
* Virtualization is a form of resource optimization that allows multiple systems to run on the same hardware.
    * Means they share the same pool for computer processing, storage, and networking resources. 
    * Enable businesses to have multiple apps running at the same time on a server in a way that is efficient and manageable. 
    * A hypervisor sits on top of physical hardware and multiple VMs are built on top of it. 
* Containers follow the same priniciple as VMs - they provide isolated environments to run your software services and optimize resources from one piece of hardware
    * More efficient because they only contain exactly what's needed for the particular app that they support.
    * Use a fraction of the memory compared to booting an entire OS.
    * Give developers the ability to create predictable environments that are isolated from other obligations. 
* Kubernetes is an open source cluster management system that provides automated container orchestration. 
    * Simplifies the management of your machines and services for you.
* Serverless computing means that resources such as compute power are automatically provisioned behind the scenes as needed.
    * Businesses do not pay for compute pwoer unless they're actually running a query or app.
    * Businesses provide the code for whatever function they want, and the public cloud provider does everything else.

### Hybrid and Multi-Cloud
* Private cloud is where an organization has virtualized servers in its own data centers to create its own private on-prem environment.
    * Might be done when an org has already made significant investments in its own infrastructure or if, for regulatory reasons, data needs to be kept on-prem.
* Hybrid cloud is where an org is using some combination of on-prem or private cloud infrastructure and public cloud services.
    * Many orgs are currently doing this.
    * Some of their data and apps have been migrated to the cloud, while others remain on-prem and interconnects between private and public clouds allow interoperability.
* Multi-cloud is where an org is using multiple cloud providers as part of its architecture.
    * Org needs flexibility and secure connectivity between the different networks involved.
* Google Cloud has created Anthos, an open app modernization platform that enables you to modernize your existing apps, build new ones, and run them anywhere
    * Allows you to build an app once and run it anywhere - on-prem, Google Cloud, or on a different public cloud.
* Google's network carries as much as 40% of the world's internet traffic everyday.
    * Operating in over 200 countries and territories with 20 regions and over 130 points of access. 

### Google Cloud Compute Solutions
* Compute Engine is a computing and hosting service that lets you create and run VMs on Google's infrastructure.
    * Delivers scalable, high performance virtual machines running in Google's data centers and worldwide fiber network.
    * Comes with persistent disk storage.
    * Ideal if you need complete control over the VM infrastructure.
    * Useful if you need to run a software package that can't easily be containerized or having existing VM images to move to the cloud.
* Google Cloud VMware Engine is a type of software you can run on a VM.
    * Is a fully managed service that lets you run the VMware platform in Google Cloud. 
    * Google manages the infrastructure, networking, and management services, so that you can use the VMware platform efficiently and securely.
* Bare Metal enables you to migrate specialized workloads to the cloud while maintaining your existing investments and architecture. 
    * Allows you access to and integrate with Google Cloud services with minimal latency. 
* Google Kubernetes Engine (GKE) provides a managed environment for deploying, managing, and scaling your containerized apps using Google infrastructure.
    * The GKE environment consists of multiple machines, specifically Compute Engine instances, grouped together to form a cluster.
    * Allows you to securely speed up app dev, streamline operations, and manage infrastructure.
* Google App Engine is a platform as a service and cloud computing platform for developing and hosting web apps.
    * Lets app developers build scalable web and mobile backends in any programming language on a fully managed serverless platform.
* Cloud Run allows developers to build apps in their favorite programming language with their favorite dependencies and tools and deploy them in seconds.
    * Abstracts away all infrastructure management by automatically scaling up and down from zero almost instantly depending on user traffic. 
* Cloud Functions is a serverless execution environment for building and connecting cloud services.
    * Offers scalable, pay-as-you-go functions as a service to run your code with zero server management.
    * Developers are more agile as they can write and run small code snippets that respond to events.
 
