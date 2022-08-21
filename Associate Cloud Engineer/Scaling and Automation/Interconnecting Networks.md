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

