# Kubernetes Engine

### Definitions
* Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications.
* You create a cluster and configure which containers to run; Kubernetes keeps them running and manages scaling, updates, and connectivity.
* Containers provide a way to virtualize an OS so that multiple workloads can run on a single OS instance. 
    * They are fast and lightweight, and they provide portability. 
* GKE gives you full control over the container down to the nodes with specific OS, CPU, disk, memory, and networking. 
* Also offers Autopilot, when you need flexibility and control but have limited ops and engineering support.

### When To Use
* When you need:
    * Hybrid & multi-cloud deployments
    * Strong CI/CD pipelines
    * GPUs, TPUs, Specific OS
    * Network protocols beyond HTTP/S
* When you use GKE, you are using Kubernetes, which makes it easy to deploy and expand into hybrid and multi-cloud environments.
    * Anthos is a platform specifically designed for hybrid and multi-cloud deployments. It provides a single-pane-of-glass visibility across all clusters from infrastructure through to application performance and topology. 
        * Ex: Microservices-based applications.

### More topics to be added (i.e., other use cases, best practices)