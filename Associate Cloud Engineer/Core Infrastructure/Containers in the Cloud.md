# Containers in the Cloud

### Intro to Containers
* Idea of a container is to give the independent scalability of workloads in pass and an abstraction layer of the OS and hardware in it
* A configurable system lets you install your favorite runtime, web server, database or middleware. Configure the underlying system resources such as disk, space, disk IO, or networking and build as you like
* Flexibility comes with a cost - the smallest unit of compute is an app with its VM
* As demand increases, you have to copy an entire VM and boot the guest OS for each instance of your app
* With App Engine, you get access to programming services. You only need to write your code in self contained workloads that use these services and include any dependent libraries - means that as demand increases, the platform scales your app seamlessly and independently by workload and infrastructure
* A container is an invisible box around your code and its dependencies with limited access to its own partition of the file system and hardware
* Only requires a few system calls to create
* All that's needed on each host is an OS kernel that supports containers and a container runtime
* In essence, the OS is being virtualized
* Makes code ultra portable and the OS and hardware can be treated as a black box
* Probably want to build your app using lots of containers, each performing their own function like microservices. If you build them this way and connect them with network connections, you can make them modular and deploy easily and scale independently across a group of hosts

### Kubernetes
* Is an open source platform for managing containerized workloads and services
* Makes it easy to orchestrate many containers on many hosts, scale them as microservices, and easily deploy rollouts and rollbacks
* At the highest level, Kubernetes is a set of APIs that you can use to deploy containers on a set of nodes called a cluster
* The system is divided into a set of primary components that run as the control plane and a set of nodes that run containers
* In Kubernetes, a node represents a computing instance like a machine - this is different to a node on Google Cloud, which is a VM running in Compute Engine
* You can describe a set of apps and how they should interact with each other, and Kubernetes determines how to make that happen
* Deploying containers on nodes by using a wrapper around one or more containers is what defines a pod
* A pod is the smallest unit in Kubernetes that you can create or deploy. It represents a running process on your cluster as either a component of replication or an entire app
* Generally only have one container per pod, but if you have multiple containers with a hard dependency, you can package them into a single pod and share networking and storage resources between them
* Pod provides a unique network IP and set of ports for containers and configurable options to govern how your containers should run
* One way to run a container in a pod in Kubernetes is to use the kubectl run command which starts a deployment with a container running inside a pod
* A deployment represents a group of replicas of the same pod and keeps your pods running even when the nodes they run on fail
* A deployment could represent a component of an app or even an entire app
* To see a list of the running pods in your project, run the command kubectl get pods
* Kubernetes creates a service with a fixed IP address for your pods, and a controller says "I need to attach an external load balancer with a public IP address to that service so that others outside the cluster can access it"
* In GKE, the load balance is created as a network load balancer. Any client that reaches that IP address will be routed to a pod behind the service
* A service is an abstraction which defines a logical set of pods and a policy by which to access them
* As deployments create and destroy pods, pods will be assigned their own IP addresses, but those addresses don't remain stable over time
* A service group is a set of pods and provides a stable endpoint or fixed IP address for them
* For example, if you create two sets of pods called frontend and backend, and put them behind their own service, the backend pods might change, but frontend pods are not aware of this, they simply refer to the backend service
* To scale a deployment, run the kubectl scale command. In this example, three pods are created in your deployment and they're placed behind the service and share one fixed IP address
* Could also use autoscaling with other kinds of parameters.
* For example, can specify that the number of pods should increase when CPU utilization reaches a certain limit
* Real strength of Kubernetes comes when provide a config file that tells it what you want
* Can get deployment config file by running kubectl get pods command
* To update, use kubectl rollout

### Google Kubernetes Engine
* GKE is a Google-hosted managed Kubernetes service in the cloud
* The GKE environment consists of multiple machines, specifically Compute Engine instances grouped together to form a cluster
* You can create a Kubernetes cluster with Kubernetes Engine by using the Google Cloud Console or the gcloud command
* GKE clusters can be customized and they support different machine types, number of nodes, and network settings
* Kubernetes provides the mechanisms through which you interact with your cluster
* Commands and resources are used to deploy and manage apps, perform admin tasks, set policies, and monitor the health of deployed workloads
* Running a GKE cluster comes with the benefit of advanced cluster management features that Google Cloud provides. These include Google Cloud's load balancing for Compute Engine instances, node pool to designate subsets of nodes within the cluster for additional flexibility, automatic scaling of your clusters node instance count, automatic upgrades for your clusters node software, node auto repair to maintain node health and availability, and logging and monitoring with Google Cloud's operation suite
* Running your replication in GKE clusters is also a good foundation to have if you'll need to bridge your on-prem and cloud resources
* To start up Kubernetes on a cluster in GKE, run gcloud container clusters create k1

### Hybrid and Multi-Cloud
* Allows you to keep parts of your system's infrastructure on-prem while moving other parts to the cloud
* Can move only specific workloads to the cloud at your own pace

### Anthos
* Anthos is a hybrid and multi-cloud solution powered by the latest innovations in distributed systems and service management software from Google
* The Anthos framework rests on Kubrnetes and GKE On-Prem
* Provides the foundation for an architecture that's fully integration and has centralized management for a central control plane that supports policy-based app lifecycle delivery across multiple cloud environments
* Provides a rich set of tools for monitoring and maintaining the consistency of your apps across all of your network, whether on-prem, in the cloud, or in multiple clouds
* GKE on cloud side of hybrid network, GKE On-Prem on the on-prem side
* GKE On-Prem is a turnkey production grade version of Kubernetes with best practice config preloaded. Provides an easy upgrade path to the latest Kubernetes releases. Provides access to container services on Google Cloud such as Cloud Build, Container Registry, and Cloud Audit Logs
* Both GKE and GKE On-Prem integrate with marketplace so that all of the clusters in your network, whether on-prem or in the cloud, have access to the same repository of containerized apps
* Service mesh layers communicate across the hybrid network using Cloud Interconnect
* Anthos Configuration Management provides a single source of truth for your cluster's config
* This is kept in the policy repo, which is a git repo. Can be located on-prem or cloud
* Anthos Config Management gives admins and devs the ability to deploy code changes with a single repo commit and the option to implement config inheritance by using namespaces, which is a way to prevent naming and permissions collisions within your app


