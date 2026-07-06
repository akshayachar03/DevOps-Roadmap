# Advanced Networking Services

## Definition

- Azure Advanced Networking Services provide secure, scalable, and high-performance networking for cloud applications.
- These services help manage traffic, secure applications, connect networks, and improve availability.

---

## Why is it used?

- Secure Azure applications.
- Distribute network traffic efficiently.
- Connect Azure with on-premises networks.
- Improve application availability.
- Protect against network attacks.
- Enable hybrid cloud connectivity.

---

## Key Features

- Layer 4 and Layer 7 load balancing.
- Web Application Firewall (WAF).
- Private and secure connectivity.
- Hybrid networking support.
- Intelligent routing.
- Centralized network security.

---

## Advantages

- Highly available.
- Secure communication.
- Better application performance.
- Supports hybrid cloud.
- Easy scalability.

---

## Disadvantages

- Configuration can become complex.
- Additional services increase cost.

---

## Components

- Azure Load Balancer
- Azure Application Gateway
- Web Application Firewall (WAF)
- Azure Firewall
- Azure DNS
- Virtual Network Peering
- VPN Gateway
- ExpressRoute

---

## Real-world Example

A company hosts an e-commerce application using Application Gateway with WAF, Azure Firewall for outbound security, and VPN Gateway to connect its office network to Azure.

---

## Interview Tip

"Azure Advanced Networking Services improve connectivity, security, availability, and traffic management for cloud applications."

---

## Quick Revision

- Supports secure networking.
- Provides traffic distribution.
- Enables hybrid connectivity.
- Includes WAF and Firewall.
- Supports private networking.
- Improves application availability.

---

## Important Interview Questions

1. What are Azure Advanced Networking Services?
2. Which Azure services provide network security?
3. Which Azure services distribute traffic?
4. Which service connects Azure with on-premises?
5. Why are advanced networking services important?

---

# Azure Application Gateway & Web Application Firewall (WAF)

## Definition

- Azure Application Gateway is a Layer 7 (Application Layer) load balancer.
- It routes HTTP/HTTPS traffic based on URL, hostname, or other web request information.
- WAF (Web Application Firewall) protects web applications from common web attacks.

---

## Why is it used?

- Balance web traffic.
- Protect web applications.
- Route requests intelligently.
- Improve application availability.
- Secure internet-facing applications.

---

## Key Features

- Layer 7 load balancing.
- URL-based routing.
- Host-based routing.
- SSL termination.
- Session affinity.
- Web Application Firewall integration.
- Autoscaling support.

---

## Advantages

- Intelligent web traffic routing.
- Built-in WAF protection.
- SSL offloading reduces backend load.
- High availability.
- Easy Azure integration.

---

## Disadvantages

- Works only for HTTP/HTTPS traffic.
- Higher cost than Azure Load Balancer.

---

## Components

### Frontend IP

- Receives client requests.

### Listener

- Listens for HTTP/HTTPS requests.

### Routing Rules

- Decide where requests should go.

### Backend Pool

- Contains web servers.

### Health Probe

- Monitors backend server health.

### WAF

- Blocks malicious web requests.

---

## Workflow

```text
Client
   ↓
Application Gateway
   ↓
WAF Inspection
   ↓
Routing Rules
   ↓
Healthy Backend Server
```

---

## Real-world Example

An online shopping website uses Application Gateway to route "/images" requests to image servers and "/payments" requests to payment servers while WAF blocks SQL Injection attacks.

---

## Interview Tip

"Application Gateway is a Layer 7 load balancer, while WAF protects web applications from common attacks like SQL Injection and Cross-Site Scripting."

---

## Quick Revision

- Layer 7 load balancer.
- Supports HTTP and HTTPS.
- URL-based routing.
- SSL termination.
- WAF protects web applications.
- Backend health monitoring.

---

## Important Interview Questions

1. What is Azure Application Gateway?
2. What is the difference between Application Gateway and Load Balancer?
3. What is WAF?
4. Which attacks can WAF prevent?
5. What is SSL termination?

---

# Azure Load Balancer

## Definition

- Azure Load Balancer is a Layer 4 load balancer.
- It distributes TCP and UDP traffic across multiple virtual machines.

---

## Why is it used?

- Improve application availability.
- Distribute incoming traffic.
- Prevent server overload.
- Support scalable applications.
- Increase fault tolerance.

---

## Key Features

- Layer 4 load balancing.
- Supports TCP and UDP.
- Public and Internal Load Balancer.
- Health probes.
- High availability.
- Zone-redundant support.

---

## Advantages

- Fast performance.
- Highly available.
- Supports millions of connections.
- Easy to configure.
- Cost-effective.

---

## Disadvantages

- Cannot inspect HTTP requests.
- No URL-based routing.

---

## Types

### Public Load Balancer

- Distributes internet traffic.

### Internal Load Balancer

- Distributes private network traffic.

---

## Workflow

```text
Client
   ↓
Load Balancer
   ↓
Health Probe
   ↓
Healthy VM
```

---

## Real-world Example

A company has four web servers behind an Azure Load Balancer. User requests are automatically distributed among healthy servers.

---

## Interview Tip

"Azure Load Balancer works at Layer 4 and distributes TCP/UDP traffic without inspecting application data."

---

## Quick Revision

- Layer 4 service.
- Supports TCP and UDP.
- Uses health probes.
- Public and Internal versions.
- High availability.

---

## Important Interview Questions

1. What is Azure Load Balancer?
2. What is the difference between Public and Internal Load Balancer?
3. What protocol does Azure Load Balancer support?
4. What are health probes?
5. What is the difference between Load Balancer and Application Gateway?

---

# Azure DNS

## Definition

- Azure DNS is a hosting service for DNS domains.
- It translates domain names into IP addresses using Azure infrastructure.

---

## Why is it used?

- Host DNS zones.
- Improve name resolution.
- Manage DNS records centrally.
- Integrate with Azure services.
- Improve reliability.

---

## Key Features

- Global DNS infrastructure.
- Supports standard DNS record types.
- High availability.
- Azure RBAC integration.
- Fast DNS resolution.

---

## Advantages

- Highly reliable.
- Easy management.
- Secure access using Azure RBAC.
- Global availability.

---

## Disadvantages

- Public DNS only hosts DNS records.
- Does not replace internal DNS servers.

---

## Components

### DNS Zone

- Stores DNS records.

### DNS Records

- A
- AAAA
- CNAME
- MX
- TXT
- NS
- PTR

---

## Workflow

```text
User
  ↓
DNS Query
  ↓
Azure DNS
  ↓
Returns IP Address
```

---

## Real-world Example

A company hosts "www.company.com" in Azure DNS, which points users to the public IP of its web application.

---

## Interview Tip

"Azure DNS hosts DNS records and provides reliable domain name resolution using Azure infrastructure."

---

## Quick Revision

- Hosts DNS zones.
- Supports all common DNS records.
- Highly available.
- Global service.
- Azure-managed.

---

## Important Interview Questions

1. What is Azure DNS?
2. What is a DNS Zone?
3. Which DNS records are commonly used?
4. What is the purpose of an A record?
5. How is Azure DNS different from traditional DNS hosting?

---

# Azure Firewall

## Definition

- Azure Firewall is a managed, stateful network security service.
- It filters inbound, outbound, and east-west network traffic.

---

## Why is it used?

- Protect Azure networks.
- Centralize network security.
- Filter application traffic.
- Control outbound internet access.
- Inspect network traffic.

---

## Key Features

- Stateful firewall.
- Network rules.
- Application rules.
- Threat intelligence.
- High availability.
- Fully managed.
- Logging and monitoring.

---

## Advantages

- Centralized security.
- Easy management.
- Highly available.
- Automatic scaling.
- Azure integration.

---

## Disadvantages

- Additional cost.
- Requires proper rule planning.

---

## Components

### Network Rules

- Filter IP addresses and ports.

### Application Rules

- Filter web traffic using FQDN.

### NAT Rules

- Perform destination NAT.

### Threat Intelligence

- Blocks known malicious traffic.

---

## Workflow

```text
Traffic
   ↓
Azure Firewall
   ↓
Rules Evaluated
   ↓
Allow or Deny
```

---

## Real-world Example

A company forces all outbound internet traffic through Azure Firewall to block access to malicious websites.

---

## Interview Tip

"Azure Firewall is a managed Layer 3–7 firewall that centrally controls network traffic across Azure."

---

## Quick Revision

- Managed firewall.
- Stateful inspection.
- Network rules.
- Application rules.
- Threat intelligence.
- NAT support.

---

## Important Interview Questions

1. What is Azure Firewall?
2. How is Azure Firewall different from NSG?
3. What are Application Rules?
4. What are Network Rules?
5. Why use Azure Firewall?

---

# Virtual Network Peering and VNet Gateway

## Definition

- Virtual Network Peering connects two Azure VNets using Microsoft's private backbone network.
- VNet Gateway enables communication between VNets and external networks using VPN or ExpressRoute.

---

## Why is it used?

- Connect Azure networks.
- Share Azure resources.
- Reduce network latency.
- Enable hybrid networking.
- Secure communication.

---

## Key Features

### VNet Peering

- Private communication.
- Low latency.
- High bandwidth.
- No public internet.

### VNet Gateway

- Connects VNets.
- Supports VPN and ExpressRoute.
- Encrypted communication.

---

## Advantages

- Secure communication.
- High-speed connectivity.
- Supports hybrid cloud.
- Easy resource sharing.

---

## Disadvantages

- Gateway deployment takes time.
- Additional cost for gateways.

---

## Comparison

| Feature | VNet Peering | VNet Gateway |
|----------|--------------|--------------|
| Uses Gateway | No | Yes |
| Uses Internet | No | VPN uses Internet |
| Speed | Very High | Lower than Peering |
| Encryption | Not required | Encrypted VPN |
| Best For | Azure-to-Azure | Azure-to-On-premises or Cross-region |

---

## Workflow

```text
VNet A
   │
Private Azure Backbone
   │
VNet B
```

---

## Real-world Example

Two Azure applications in different VNets communicate securely using VNet Peering without using the internet.

---

## Interview Tip

"VNet Peering connects Azure VNets directly, while VNet Gateway connects Azure to external networks or other VNets using VPN or ExpressRoute."

---

## Quick Revision

- Peering uses Azure backbone.
- No internet required.
- Gateway supports VPN.
- Gateway enables hybrid cloud.
- Peering is faster than VPN.

---

## Important Interview Questions

1. What is VNet Peering?
2. What is a Virtual Network Gateway?
3. What is the difference between Peering and Gateway?
4. Can peered VNets communicate privately?
5. When would you use VNet Gateway?

---

# Azure VPN Gateway

## Definition

- Azure VPN Gateway is a managed service that provides secure, encrypted communication between Azure VNets and on-premises networks over the public internet.

---

## Why is it used?

- Connect on-premises networks to Azure.
- Enable hybrid cloud.
- Secure branch office connectivity.
- Connect remote users.
- Encrypt network traffic.

---

## Key Features

- IPSec/IKE VPN.
- Site-to-Site VPN.
- Point-to-Site VPN.
- VNet-to-VNet VPN.
- High availability.
- Active-Active configuration.

---

## Advantages

- Secure encrypted connection.
- Easy hybrid connectivity.
- Fully managed.
- Supports multiple VPN connections.

---

## Disadvantages

- Depends on internet connectivity.
- Lower performance than ExpressRoute.

---

## Types

### Site-to-Site (S2S)

- Connects an on-premises network to Azure.

### Point-to-Site (P2S)

- Connects individual users to Azure.

### VNet-to-VNet

- Connects Azure VNets using VPN.

---

## Workflow

```text
On-Premises Network
        │
Encrypted VPN Tunnel
        │
Azure VPN Gateway
        │
Azure Virtual Network
```

---

## Real-world Example

A company securely connects its office network to Azure so employees can access Azure virtual machines as if they were inside the corporate network.

---

## Interview Tip

"Azure VPN Gateway creates encrypted VPN tunnels over the internet to securely connect Azure with on-premises networks or remote users."

---

## Quick Revision

- Managed VPN service.
- Uses IPSec/IKE.
- Site-to-Site VPN.
- Point-to-Site VPN.
- VNet-to-VNet VPN.
- Supports hybrid cloud.

---

## Important Interview Questions

1. What is Azure VPN Gateway?
2. What are the types of VPN connections?
3. What is the difference between Site-to-Site and Point-to-Site VPN?
4. When should VPN Gateway be used instead of ExpressRoute?
5. How does VPN Gateway secure communication?
