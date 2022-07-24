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
* Testing




   