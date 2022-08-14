# Virtual Private Cloud

### Projects, Networks, and Subnetworks
* A project:
    * Associates objects and services with billing
    * Contains networks (up to 5) that can be shared/peered
* A network:
    * Has no IP address range
    * Is global and spans all available regions
    * Contains subnetworks
    * Is available as default, auto, or custom
* 3 VPC network types:
    * Default:
        * Every project
        * One subnet per region
        * Default firewall rules
    * Auto Mode:
        * Default network
        * One subnet per region
        * Regional IP allocation
        * Fixed /20 subnetwork per region
        * Expandable up to /16
    * Custom Mode:
        * No default subnets created
        * Full control of IP ranges
        * Regional IP allocation
        * Expandable to IP ranges you specify
* Because VM instances within a VPC network can communicate privately on a global scale, a single VPN can securely connect your on-prem network to your Google Cloud network
* VMs can be on the same subnet but in different zones
* A single firewall rule can apply to both VMs
* Expand subnets w/o recreating instances
    * Cannot overlap with other subnets
    * IP range must be a unique CIDR block
    * New subnet IP ranges have to fall within valid IP ranges
    * Can expand but not shrink
    * Auto mode can be expanded from /20 to /16
    * Avoid large subnets

### IP Addresses
* In Google Cloud, each VM can have two IP addressed assigned
* One of them is an internal IP address which is going to be assigned via DHCP internally
* Every VM that starts up and any service that depends on VMs get an internal IP address
* When you create VM, its symbolic name is registered with an internal DNS service that translates the name to an internal IP address
* The DNS is scoped to the network, so it can translate web URLs and VM names of hosts in the same network
* External IP address is optional
* Can assign an external IP address if your device or machine is externally facing
* Can be assigned from a pool making it ephemeral or it can be assigned from a reserved external IP address making it static
* If you reserve a static external IP address and don't assign it to a resource such as a VM instance or a forwarding rule, you are charged at a higher rate than for static and ephemeral external IP addresses that are in use
* Can use your own publicly routable IP address, but must own and bring a /24 block or larger

### Mapping IP Addresses
* Regardless of whether you use an ephemeral or static IP address, the external address is unknown to the OS of the VM
* The external IP address is mapped to the VM's internal address transparently by the VPC
* DNS resolution for internal addresses
    * Each instance has a hostname that can be resolved to an internal IP address:
        * The hostname is the same as the instance name
        * FQDN is [hostname].[zone].c.[project-id].internal
   * Name resolution is handled by internal DNS resolver:
       * Provided as part of Compute Engine (169.254.169.254)
       * Configured for use on instance via DHCP
       * Provides answer for internal and external addresses
* DNS resolution for external addresses
    * Instances with external IP addresses can allow connections from hosts outside the project
        * Users connect directly 
        * Admins can also publish public DNS records pointing to the instance
            * Public DNS records are not published automatically
    * DNS records for external addresses can be published using existing DNS servers (outside of Google Cloud)
    * DNS zones can be hosted using Cloud DNS
* Host DNS zones using Cloud DNS (domain name system)
    * Translate domain names into IP addresses
    * Low latency
    * High availability (100% uptime SLA)
    * Create and update millions of DNS records
    * UI, command line, or API
* Alias IP ranges let you assign a range of internal IP addresses as an alias to a VM's network interface
* This is useful if you have multiple services running on a VM, and you want to assign a different IP address to each service
* Can configure multiple IP addresses representing containers or apps hosted in a VM without having to define a separate network interface

### Routes and Firewall Rules
* Every network has:
    * Routes that let instances in a network send traffic directly to each other
    * A defaultroute that directs packets to destinations that are outside the network
* Firewall rules must also allow the packet
* Routes map traffic to destination networks
    * Apply to traffic egressing a VM
    * Forward traffic to most specific route
    * Are created when a subnet is created
    * Enable VMs on same network to communicate
    * Destination is in CIDR notation
    * Traffic is delivered only if it also matches a firewall rule
* Firewall rules protect your VM instances from unapproved connections
    * VPC network functions as a distributed firewall
    * Firewall rules are applied to the network as a whole
    * Connections are allowed or denied at the instance level
    * Firewall rules are stateful
    * Implied deny all ingress and allow all egress
* Routes map traffic to destination networks
    * direction: Inbound/outbound connections are matched against ingress/egress rules only
    * source or destination: For the ingress direction, sources can be specified as part of the rule with IP addresses, source tags, or a source service account. For the egress direction, destinations can be specified as part of the rule with one or more ranges of IP addresses
    * protocol and port: Any rule can be restricted to apply to specific protocols only or specific combinations of protocols and ports only
    * action: To allow or deny packets that match the direction, protocol, port, and source or destination of the rule
    * priority: Governs the order in which rules are evaluated; the first matching rule is applied 
    * Rule assignment: All rules are assigned to all instances, but you can assign certain rules to certain instances only
* Google Cloud firewall use case: Egress
    * Conditions:
        * Destination CIDR ranges
        * Protocols
        * Ports
    * Action:
        * Allow: Permit the matching egress connection
        * Deny: Block the matching egress connection
* Google Cloud firewall use case: Ingress
    * Conditions:
        * Source CIDR ranges
        * Protocols
        * Ports
    * Action:
        * Allow: Permit the matching ingress connection
        * Deny: Block the matching ingress connection
### Pricing
* Egress or traffic coming into GCP network's is not charged, unless there is a resource, such as a load balancer that is processing egress traffic
* Responses to request account as egress and are charged
* Egress traffic to the same zone is not charged as long as that egress is through the internal IP address of an instance
* Egress traffic to Google products like Youtube, Maps to a different GCP service within the same region is not charged for
* There is a charge for egress between zones in the same region, egress within a zone, if the traffic is through the external IP address of an instance, and egress between regions
* Compute Engine cannot determine the zone of a VM through the external IP address - this traffic is treated like egress between zones in the same region
* Are charged for static and ephemeral external IP addresses
* If you reserve a static external IP address and don't assign it to a resource, such as a VM instance or a forwarding rule, you are charged at a higherrate and for static and ephemeral external IP addresses that are in use
* External IP addresses on preemptible VMs have a lower charge than for standard VM instances
* Recommend using the GCP pricing calculator to estimate the cost of a collection of resources, because each service has its own pricing model
* Pricing calculator is a web-based tool that you use to specify the expected consumption of certain services and resources and then it provides you with an estimated cost





   