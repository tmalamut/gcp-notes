# Virtual Machines and Networks in the Cloud

### Virtual Private Cloud Networking
* A virtual private cloud (VPC) is a secure, individual, private cloud-computing model hosted within a public cloud
* On a VPC, customers can:
    * Run code, store data, host websites, and anything else that can be done in an ordinary private cloud
    * This private cloud is hosted remotely by a public cloud provider
        * Means that VPC's combine the scalability and convenience of public cloud computing with the data isolation of private cloud computing
* VPC networks connect Google Cloud resources to each other and to the internet
    * Segmenting networks
    * Using firewall rules to restrict access to instances
    * Creating static routes to forward traffic to specific destinations
* Google VPC networks are global and can have subnets in any Google Cloud region worldwide

### Compute Engine
* Can create and run VMs on Google infrastructure
* No upfront investments
* Thousands of virtual CPUs can run on a system that's designed to be fast and to offer consistent performance
* Each VM contains the power and functionality of a full-fledged OS
* Can be configured much like a physical server
* A VM instance can:
    * Be created via the Google Cloud Console or via the gcloud command-line tool
    * Run Linux and Windows Server images provided by Google or any customized versions of these images
    * Build and run images of other OS's and flexibly reconfigure VMs
* Bills by the second with a 1 minute minimum
* Sustained-use discount applies automatically to VMs the longer they run
    * For each VM that runs for more than 25 percent of a month, Compute Engine automatically applies a discount for every additional minute
* Also offers commited-use discounts - means that for stable and predictable workloads, a specific amount of vCPUs and memory can be purchased for up to a 57 percent discount off of normal prices in return for committing to a usage term of one year or three years.
* Preemptible/Spot VMs: Compute Engine has permission to terminate a job if its resources are needed elsewhere. Need to ensure that your job can be stopped and restarted.
* Compute Engine doesn't require a particular option or machine type to get high-throughput between processing and persistent disks - that's the default and it comes to you at no extra cost
* You'll only pay for what you need with custom machine types
* Compute Engine lets you choose the machine properties of your instances, like the number of virtual CPUs and the amounts of memory using a set of predefined machine types, or by creating custom machine types

### Scaling Virtual Machines
* Compute Engine has a feature called Autoscaling where VMs can be added to or subtracted from an app based on load metrics
* The other part of making that work is balancing the incoming traffic among the VMs
* Google's virtual private Cloud VPC supports several different kinds of load balancing
* With Compute Engine, you can configure very large VMs, whcih are great for workloads such as an in memory database and CPU intensive analytics - most customers start off with scaling out, not up
* The max number of CPUs per VM is tied to its machine family and is also constrained by the quota available to the user, which is zone dependent

### Important VPC Compatibilities
* Routing tables:
    * Are built-in
    * No router provisioning or managing
    * Forward traffic from one instance to another
    * No external IP address required
* Firewall:
    * Restrict access to instances
    * Rules can be defined through metadata tags
* VPCs belong to projects, but what if your company has several projects and the VPCs need to talk to each other?
    * VPC peering: A relationship between two VPCs can be established to exchange traffic
    * Shared VPC: To use the full power of IAM to control who and what in one project can interact with the VPC and another

### Cloud Load Balancing
* The job of a load balancer is to distribute user traffic across multiple instances of an app
* By spreading the load, load balancing reduces the risk that app experiences performance issues
* Cloud load balancing is a fully distributed software defined managed service for all your traffic
* Can put cloud loading balancing in front of all your traffic, HTTP or HTTP(S), and other  and SSL traffic and UDP traffic too
* Provides cross region load balancing, including automatic multi-region fail over which gently moves traffic infractions if backends become unhealthy
* Reacts quickly to changes in users, traffic, network, backend health and other conditions
* If you need cross regional load balancing for a web app, use global HTTP load balancing
* For secure sockets layer traffic that's not HTTP, use the global SSL proxy load balancing
* If it's other  traffic that doesn't use SSL, use the global  proxy load balancing
* The last two proxy services only work for specific port numbers and they only work for 
* If you want to load balancing UDP traffic or traffic on any port number, you can still balance across the Google Cloud region with the regional load balancer
* Services are intended for traffic coming into the Google network from the internet
* If you want to load balance traffic inside your project, use the regional internal load balancer - it accepts traffic on a Google Cloud internal IP address and load balances it across Compute Engine VMs

### Cloud DNS and Cloud CDN
* DNS is what translates Internet host names to addresses
* Google Cloud offers Cloud DNS to help the world find the host names and addresses of apps built in Google Cloud
* Cloud DNS is a managed DNS service that runs on the same infrastructure as Google 
    * It has low latency and high availability
    * Cost-effective way to make your apps and services available to users
    * The DNS info you publish is served from redundant locations around the world
    * Is also programmable - can publish and manage millions of DNS zones and records using the Cloud Console, the CLI or the API
* Google has a global system of edge caches
* Edge caching refers to the use of caching servers to store content closer to end users
* Can use this system to accelerate content delivery in your app by using Cloud CDN, content delivery network
* Means that your customers will experience lower network latency
* Origins of your content will experience reduce load and can even save money
* After HTTP load balancing is setup, Cloud CDN can be enabled with a single checkbox
* If already using another CDN provider, chances are it's part of Google Cloud CDN Interconnect Partner Program

### Connecting Networks to Google VPC
* Many customers want to connect their Google VPCs to other networks in their system, such as on-prem networks or other networks in the cloud
* One option is to start with a virtual private network connection over the internet and use the IPsec VPN protocol to create a tunnel connection
* To make the connection dynamic, a Google Cloud feature called Cloud Router can be used - lets other networks and Google VPC exchange route info over the VPN using the border gateway protocol
* Using this method, if you add a new subnet to your VPC, your on-prem network will automatically get roots to it
* But using the internet to connect networks isn't always the best option, either for security concerns or because of bandwidth reliability
* A second option is to consider peering with Google using Direct Peering
* Peering means putting a router in the same public data center as a Google Point of Presence and using it to exchange traffic between networks
* Carrier peering gives you direct access from your on-prem network, through a service provider's network to Google Workspace and to Google Cloud products that can be exposed through one or more public IP addresses. 
* One downside of peering is that it isn't covered by a Google SLA
* If getting the highest uptimes for interconnection is important, using Dedicated Interconnect would be a good solution
* This option allows for one or more direct private connections to Google
* Can be covered by an SLA for up to 99.99 perent
* These connections can be backed up by a VPN for even greater reliability
* Final option is Partner Interconnect, which provides connectivity between an on-prem network and a VPC network or a supported service provider
* A Partner Interconnection connection is useful if a data center is in a physical location that can't reach a Dedicated Interconnect co-location facility, or if the data needs don't warrant an entire 10 GB/s connections
* Also can be covered by an SLA of up to 99.99 percent


   