# Interconnecting Networks

### Cloud VPN
* Cloud VPN securely connects your on-premises network to your GCP VPC network
* Useful for low-volume data connections
* 99.9% SLA
* Supports:
    * Site-to-site VPN
    * Static routes
    * Dynamic routes (Cloud Router)
    * IKEv1 and IKEv2 ciphers
* In order to connect to your on-prem network and its resources, you need to configure your Cloud VPN gateway on-prem VPN gateway and to VPN tunnels
* The Cloud VPN gateway is a regional resource that uses a regional external IP address
* Your on-prem VPN gateway can be a physical device in your data center or a physical or software based VPN offering in another cloud provider's network
* In order to create a connection between two VPN gateways, you must establish two VPN tunnels
* Each tunnel defines the connection from the perspective of its gateway and traffic can only pass when the pair of tunnels establish
* To use dynamic routes, need to configure Cloud Router
* Cloud Router can manage routes from Cloud VPN tunnel using border gateway protocol or BGP

### HA VPN
* Google Cloud offers a second type of Cloud VPN gateway
* HA VPN is a high availability Cloud VPN solution that lets you securely connect your on-prem network to your VPC network through an IPsec VPN connection in a single region
* 99.99% SLA

### Cloud Interconnect
* Dedicated Interconnect provides direct physical connections between your on-prem network and Google's network
* This enables you to transfer large amounts of data between networks, which can be more cost effective than purchasing additional bandwidth over the public internet
* In order to use Dedicated Interconnect, you need to provision a cross-connect between the Google network and your own router in a common co-location facility
* To exchange routes between the networks, you can configure a BGP session over the Interconnect between the Cloud Router and the on-prem router
* If not near a supported co-location facility, want to consider Partner Interconnect
* Partner Interconnect provides connectivity between your on-prem network and your VPC network through a supported service provider
* After you establish a BGP session between your cloud router and on-prem router to start passing traffic between your networks
* Best practice is to start with VPN tunnels and when you need enterprise-grade connection to Google Cloud, switch to Dedicated Interconnect or Partner Interconnect, depending on your proximity to a co-location facility and your capacity requirements

### Peering
* Direct Peering provides a direct connection between your business network and Google's
    * Broad-reaching edge network
    * Exchange BGP routes
    * Reach all of Google's services
    * Peering requirements
    * No SLA
* Carrier Peering provides connectivity through a supported partner
    * Carrier Peering partner
    * Reach all of Google's services
    * Partner requirements 
    * No SLA

### Choosing a Connection
* Interconnect services provide direct access to RFC1918 IP addresses in your VPC with an SLA
* Peering services offer access to Google public IP addresses only without an SLA
* If you need to extend your network for Workspace services, Youtube, or Google Cloud s, choose one of the peering services
* If you can meet Google's direct peering requirements, choose direct peering, otherwise, choose carrier peering
* If you don't need to extend your network for Workspace services or Google Cloud s, but want to extend the reach of your network to Google Cloud, you want to pick one of the Interconnect services
* If you cannot meet Google at one of its co-location facilities, choose Cloud VPN or Partner Interconnect
* If you have modest bandwidth needs, Cloud VPN
* If you can meet Google at one of its co-location facilities, you might jump to Dedicated Interconnect
* However, if you cannot provide your own encryption mechanism for sensitive traffic, feel that a 10 Gbps connection is too big, or want access to multiple clouds, you will want to consider Cloud VPN or Partner Interconnect instead

### Shared VPC and VPC Peering
* Shared VPC allows an organization to connect resources from multiple projects to a common VPC network
* This allows the resources to communicate with each other securely and efficiently using internal IPs from that network
* When you use Shared VPC, you designate a project as a host project and attach one or more service projects to it
* VPC network peering, in contrast, allows private RFC1918 connectivity across two VPC networks, regardless of whether they belong to the same project or the same organization
* Each VPC network will have firewall rules that define what traffic is allowed or denied between the networks
* If you want to configure a private communication between VPC networks in different organizations, you have to use VPC network peering - Shared VPC only works within the same org
* Shared VPC only works across projects in the same org
* Shared VPC is a centralized approach to multi-project network
* VPC network peering is a decentralized approach, because each VPC network can remain under the control of separate admin groups and maintain its own global firewall and routing tables


