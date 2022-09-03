# Containers and Kubernetes

### Intro to Containers
* VMs are relatively slow to startup because the entire OS has to boot
* A more efficient way is to implement abstraction at the level of the app and its dependencies 
* Don't have to virtualize the entire machine or the entire OS, but just the user space
    * The user space is all the code that resides above the kernel, includes applications and their dependencies
* Containers are isolated user spaces for running app code
* Are lightweight becuse they don't carry a full OS
* Can be created and shutdown very quickly because you're just starting and stopping the processes that make up the application and not booting up an entire VM and initializing an OS for each app
* You package your code with all the dependencies it needs, and the engine that executes your container, is responsible for making them available at runtime
* Runs the same anywhere

### Containers and Container Images
* An application and its dependencies are called an image
* A container is simply a running instance of an image
* By building software into container images, devs can easily package and ship an app without worrying about the system it will be running on
* Need software to build container images and to run them - Docker is one tool that does both
* Docker is an open source technology that allows you to create and run apps and containers, but it doesn't offer a way to orchestrate those apps at scale like Kubernetes does
* Containers use a varied set of Linux technologies
    * Processes
    * Linux namespaces
    * cgroups
    * Union file systems
* A container image is structured in layers
    * The tool you use to build the image reads instructions from a file called the Container Manifest. For Docker, called a Dockerfile
    * Each instruction in the Dockerfile specifies a layer inside the container image
    * Each layer is read only
    * When a container runs from this image, it will also have a writable ephemeral topmost layer
* Containers promote smaller shared images
    * For example, multiple containers can share the same Ubuntu image
* How can you get containers?
    * Download containerized software from a container registry such as gcr.io
    * Build your own container using the open-source docker command
    * Build your own container using Cloud Build

### Intro to Kubernetes
* Popular container management and orchestration solution
* It's a container-centric management environment
* Automates the deployment, scaling, load balancing, logging, monitoring, and other management features of containerized apps - these are the features that are characteristic of a typical PaaS solution
* Also has features of an IaaS, such as allowing a wide range of user preferences and config flexibility
* Supports declarative and imperative configs, but best practice is declarative
    * Can describe the desired state you want to achieve instead of issuing commands
* Supports different workload types
* Supports stateless apps such as Nginx or Apache web server, and stateful apps, where user and session data can be stored persistently
* Supports batched jobs and daemon tasks
* Can automatically scale in and out containerized apps based on resource utilization
* Can specify resource request levels and resource limits for your workloads
* Kubernetes is open source, so it supports workload portability across on-prem or multiple cloud service providers - allows Kubernetes to be deployed anywhere

### Intro to Google Kubernetes Engine
* Google Cloud's managed service offering for Kubernetes
* Helps you deploy, manage, and scale Kubernetes environments for your containerized apps on GCP
* Is fully managed, means you don't have to provision the underlying resources
* Uses a container-optimized OS and these OS's are maintained by Google
* When you use GKE, you start by directing the service to instantiate a Kubernetes system for you - this system is called a cluster
* GKE's auto-upgrade feature can be enabled to ensure your clusters are automatically upgraded
* The VMs that host your containers inside of a GKE cluster are called nodes
* Enabling GKE's auto repair feature ensures that the services automatically repairs unhealthy nodes for you
* GKE supports scaling the cluster itself, like how Kubernetes supports scaling workloads 

### Computing Options Detail
* Compute Engine
    * Fully customizable VMs
    * Persistent disks and optional local SSDs
    * Global load balancing and autoscaling
    * Use cases:
        * Complete control over the OS and virtual hardware
        * Well suited for lift-and-shift migrations to the cloud
        * Most flexible compute solution, often used when a managed solution is too restrictive
* App Engine
    * Provides a fully managed, code-first platform
    * Streamlines app deployment and scalability
    * Provides support for popular programming languages and app runtimes
    * Supports integrated monitoring, logging, and diagnostics
    * Simplifies version control, canary testing, and rollbacks
    * Use cases:
        * Websites
        * Mobile app and gaming backends
        * RESTful APIs
* Google Kubernetes Engine
    * Fully managed Kubernetes platform
    * Supports cluster scaling, persistent disks, automated upgrades, and auto node repairs
    * Built-in integration with Google Cloud services
    * Portability across multiple environments
        * Hybrid computing
        * Multi-cloud computing
    * Use cases:
        * Containerized apps
        * Cloud-native distributed systems
        * Hybrid apps
* Cloud Run
    * Enables stateless containers
    * Abstracts away infrastructure management
    * Automatically scales up and down
    * Open API and runtime environment
    * Use cases:
        * Deploy stateless containers that listen for requests or events
        * Build apps in any language with any frameworks and tools
* Cloud Functions
    * Event-driven, serverless compute service
    * Automatic scaling with highly available and fault-tolerant design
    * Charges apply only when your code runs
    * Triggered based on events in Google Cloud services, HTTP endpoints, and Firebase
    * Use cases:
        * Supporting microservice architecture
        * Serverless app backends
            * Mobile and IoT backends
            * Integrate with third-party services and APIs
        * Intelligent apps
            * Virtual assistant and chat bots
            * Video and image analysis

