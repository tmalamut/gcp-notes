# Load Balancing and Autoscaling

### Managed Instance Groups
* A managed instance group is a collection of identical VM instances that you control as a single entity using an instance template
* You can easily update all the instances in the group by specifying a new template in a rolling update
* When your apps require additional compute resources, managed instance groups can scale automatically to the number of instances in the group
* Can work with load balancing services to distribute network traffic to all of the instances in the group
* If an instance in the group stops or is deleted by an action other than the instance group's commands, the managed instance group automatically recreates the instance so it can resume its processing tasks
* Can automatically identify and recreate unhealthy instances
* Regional managed instance groups are generally recommended over zonal managed instance groups because they allow you to spread the app load across multiple zones
* To create a managed instance group, you first need to create an instance template, then create managed instance group of N-specificed instances
* When you create an instance group, you define the specific rules for that instance group
* First, you decide what type of managed instance group you want to create
* Can use managed instance groups for stateless serving or batch workloads, or stateful apps
* Second, provide a name
* Third, decide whether the instance group is going to be single or multi-zoned and where those locations will be
* Can optionally provide port name mapping details
* Fourth, select the instance template that you want to use
* Fifth, decide whether you want to auto-scale and under what circumstances
* Finally, consider creating a health check to determine which instances are healthy and should receive traffic

### Autoscaling and Health Checks
* Managed instance groups offer autoscaling capabilities
* Dynamically add/remove instances
    * Increases in load
    * Decreases in load
* Autoscaling policy
    * CPU utilization
    * Load balancing capacity
    * Monitoring metrics
    * Queue-based workload
* In a health check, you define a protocol port and health criteria
* The health criteria defines how often to check whether an instance is healthy

### Overview of HTTP(S) Load Balancing
* Acts at layer seven of the OSI model
* This is the application layer which deals with the actual content of each message allowing for routing decisions based on the URL
* Provides global loading balancing for HTTPS requested destined for your instances
* Means that your apps are available to your customers at a single anycast IP address, which simplifies DNS setup
* Balances HTTP(S) traffic across multiple backend instances and across multiple regions
* HTTP requests are load balance on port 80 or 8080, and HTTPS requests are balanced on port 443
* Supports both IPv4 and IPv6 clients, is scalable, requires no pre-warming, and enables content-based and cross-regional load balancing
* Can configure your own maps that route some URLs to one set of instances and route other URLs to other instances
* Requests are generally routed to the instance group closest to the user
* Backend services
    * Health check
    * Session affinity (optional)
    * Time out setting (30-sec default)
    * One or more backends
        * An instance group (managed or unmanaged)
        * A balancing mode (CPU utilization or RPS)
        * A capacity scaler (ceiling % of CPU/Rate targets)

### HTTP(S) Load Balancing
* Target HTTP(S) proxy
* One signed SSL installed (minimum)
* Client SSL session terminates at the load balancer
* Support the QUIC transport layer protocol
* SSL certificates
    * Required for HTTP(S) load balancing
    * Up to 15 SSL certificates (per target proxy)
    * Create an SSL certificate resource
* Backend buckets
    * Allow you to use Cloud Storage buckets with HTTPS load balancing
    * An external HTTPS load balancer uses a URL map to direct traffic from specified URLs to either a backend service or a backend bucket
    * One common use case is to send requests for genomic content, such as data to a backend service and send requests for static content such as images to backend buckets
* A network endpoint group (NEG) is a configuration object that specifies a group of backend endpoints or services
* 4 types of NEGs:
    * Zonal
    * Internet
    * Serverless
    * Hybrid connectivity

### SSL Proxy Load Balancing
* Global load balancing for encrypted, non-HTTP traffic
* Terminates SSL session at load balancing layer, then balances the connections across your instances using the SSL or TCP protocols
* These instances can be in multiple regions, and the load balancer automatically directs traffic to the closest region that has capacity
* IPv4 or IPv6 clients
* Intelligent routing
* Certificate management
* Security patching
* SSL policies

### TCP Proxy Load Balancing
* Global load balancing for unencrypted, non-HTTP traffic
* Terminates TCP sessions at load balancing layer
* IPv4 or IPv6 clients
* Intelligent routing
* Security patching

### Networking Load Balancing
* Regional, non-proxied load balancer
* All traffic is passed thru the load balancer instead of being proxied
* Traffic can only be balanced between VM instances in the same region
* Forwarding rules (IP protocol data)
* Traffic: UDP, TCP/SSL ports
* Backend service-based architecture
    * Regional backend service
    * Defines the behavior of the load balancer and how it distributes traffic to its backend instance groups
    * Enables new features not supported with legacy target pools
        * Non-legacy health checks
        * Auto-scaling with managed instance groups
        * Connection draining
        * Configurable failover policy
* Target pool-based architecture
    * Forwarding rules (TCP and UDP)
    * Up to 50 per project
    * One health check
    * Instances must be in same region

### Internal Load Balancing
* Regional, private load balancing
    * VM instances in same region
    * RFC 1918 IP addresses
* TCP/UDP traffic
* Reduced latency, simpler configuration
* Software-defined, fully distributed load balancing
* Internal HTTP(S) load balancing
    * HTTP, HTTPS, or HTTP/2 protocols
    * Based on open source Envoy proxy
* Supports 3-tier web services

### Choosing a Load Balancer
* Only the HTTPS, SSL proxy, and TCP proxy load balancing services support IPv6 clients
* If HTTP or HTTPS traffic, use the HTTPS load balancing service as a layer seven load balancer. Otherwise, consider SSL proxy, TCP proxy, or network load balancing services
* If you need an internal load balancing service, you have the internal load balancing service available and it supports both TCP and UDP traffic
* If just regional and IPv4, only for HTTP or HTTPS traffic
* Network load balancing only supports IPv4 clients

        