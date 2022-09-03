# Kubernetes Architecture

### Kubernetes Concepts
* Kubernetes object model
* Each thing Kubernetes manages is represented by an object - can view and change attributes and state
* Kubernetes expects you to tell it what you want the state of the objects under its management to be, and it will work to bring that state into being and keep it there by means of its so-called 'watch loop'
* A Kubernetes object is defined as a persistent entity that represent the state of something running in a cluster - its desired state and its current state
* Various kinds of objects represent containerized apps, the resources that are available to them, and the policies that affect their behavior
* Objects have two important elements
    * You give Kubernetes an object spec for each object you want to create
    * With this spec, you define the desired state of object by providing the characteristics that you want
    * The object status is the current state of the object provided by the Kubernetes control plane
        * Control plane refers to the various system processes that collaborate to make a cluster work
* Each object is of a certain type or 'kind'
* Pods are the basic building block of the standard module and are the smallest deployable object
* A pod embodies the environment where containers live and that environment can have one or more containers
* If there is more than one container in a pod, they're tightly coupled and share resources including networking and storage
* Each pod is given a unique IP address
* Containers within the same pod can communicate through localhost 127.0.0.1
* A pod can specify a set of storage volumes to be shared among its containers

### Kubernetes Control Plane
* The fleet of cooperating processes that make a Kubernetes cluster work
* Single component you directly interact with is the kube-APIserver to do things like launching pods
* Use kubectl command to communicate to kube-APIserver
* etcd is the database
* kube-scheduler is responsible for scheduling pods onto nodes
* kube-controller-manager continually monitors the cluster to get to the desired state
    * Many objects are managed by loops of code called controllers
* kube-cloud-manager manages controllers that interact with the underlying cloud providers
* Each node runs a Kubelet, which is like a Kubernetes agent on each node
* When the kube-APIserver wants to start a pod on a node, it connects to that node's kubelet
* Kubelets use the container runtime to start the pod and monitors its lifecycle
* The Linux distribution that GKE uses for its node launches containers using containerd, the runtime component of Docker
* kube-proxy's job is to maintain the network connectivity among the pods in a cluster

### Google Kubernetes Engine Concepts
* GKE takes the responsibility for provisioning and managing all the control plane infrastructure behind it
* Abstracts away having a separate control plane
* In any Kubernetes environment, nodes are created externally by cluster admins - GKE automates this process for you
* It launches Compute Engine VM instances and registers them as nodes
* Can then manage node settings directly from the Cloud Console
* You pay per hour of life of your nodes (not counting the control plane)
* Because nodes run on Compute Engine, you choose your node machine type when you create your cluster
* By default, the node machine type is an e2-medium, which provides 2vCPU and 4 GB of memory
* Can select multiple node machine types by creating multiple node pools
* A node pool is a subset of nodes within a cluster that share a configuration, such as their amount of memory or their CPU generation
* Node pools provide an easy way to ensure that workloads run on the right hardware within your cluster. Node pools are a GKE feature
* Number of nodes can be changed during or after creation of the cluster
* Adding more ndoes and deploying multiple replicas of an app will improve an app availability
* To address the issue of an entire compute zone going down, use a GKE regional cluster
* Regional clusters ensure that the availability of the app is maintained across multiple zones in a single region
* By default, a regional cluster is spread across 3 zones, each containing 1 control plane and 3 nodes
* Once you build a zonal cluster, you cannot convert it into a regional cluster or vice versa
* Regional or zonal cluster can be setup as a private cluster / hidden from the public internet

### Kubernetes Object Management
* All Kubernetes objects are identified by a unique name and a unique identifier
* Objects are defined in a YAML file
* Best practice: Use version control on YAML files
* Cannot have two of the same object types with same names
* If an object is deleted, the name can be reused
* All objects are assigned a unique identifier (UID) by Kubernetes
* Labels are key-value pairs to tag objects
* Labels can be matched by label selectors
* Pods are ephemeral
* Can declare a controller object to manage the state of the pods
* Deployments ensure that sets of pods are running
* Kubernetes allows you to abstract a single physical cluster into multiple clusters known as 'namespaces'
* Namespaces provide scope for naming resources such as pods, deployments, and controllers
* Cannot have duplicate object names in the same namespace
* Namespaces let you implement resource quotas across the cluster and apply specifically to the Kubernetes cluster they're defined on

### Migrate for Anthos Intro
* If you have existing apps that aren't in containers, or not even in the cloud
* Migrate for Anthos is a tool for getting workloads into containerized deployments on Google Cloud
* Moves your existing apps into a Kubernetes environment
* Process is automated
* Workloads can be on-prem or in other cloud providers
* Most migrations are completed in less than 10 mins
* You have the choice of migrating your app's data in one move, or stream it to the cloud until the app is live

### Migrate for Anthos Architecture
* The first step is to allow Migrate for Compute Engine to create a pipeline for streaming or migrating the data from on-prem or another cloud provider into Google Cloud
* Migrate for Compute Engine is a tool that allows you to bring your existing apps into VMs on Google Cloud
* Migrate for Anthos is then installed on a GKE processing cluster and is composed of many Kubernetes resources
* Migrate for Anthos is used to generate deployment artifacts
* Some of these artifacts, like your Kubernetes configs and the dockerfile, are used to create the VM wrapping container
* This container goes into Cloud Storage and the container images are stored in the Container Registry
* After the deployment assets are created, they can be used to deploy your app into a target cluster
* You apply to the generated configuration and it creates all the necessary Kubernetes elements on the target cluster

### Migration Path
* A migration is a multi-step process:
    * Configure processing cluster
        * After that, you install the Migrate for Anthos components onto that cluster
    * Add migration source
        * You can migrate from VMware, AWS, Azure, or Google Cloud
        * Will need to create a migration object with the details of the migration you're performing - this generate a plan template for you in a YAML file
    * Generate and review plan
        * You may need to alter this configuration file to create the level of customization you desire
    * Generate artifacts
        * Generation that container images of your apps on the YAML files required for the deployment
    * Test
        * Both the container images and the deployments will be tested at this state
    * Deploy
        * Can use the generative artifacts to deploy your app into your production clusters

### Summary
* Kubernetes controllers keep the cluster state matching the desired state
* Kubernetes consists of a family of control plane components, running on the control plane and the nodes
* GKE abstracts away the control plane
* Declare the state you want using manifest files



