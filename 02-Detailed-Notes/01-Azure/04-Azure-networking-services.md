# Azure Networking Services

## Definition

- Azure Networking Services provide secure and reliable communication between Azure resources, on-premises networks, and the internet.
- They help manage connectivity, routing, security, load balancing, and private access.

---

## Why is it used?

- Connect Azure resources securely.
- Enable communication between virtual machines and services.
- Control network traffic.
- Connect on-premises networks to Azure.
- Improve application availability and security.

---

## Key Features

- Virtual Networks (VNets) for private networking.
- Network Security Groups (NSGs) for traffic filtering.
- Load Balancer for distributing traffic.
- VPN Gateway for secure site-to-site connections.
- ExpressRoute for private dedicated connectivity.
- Azure Firewall for centralized network protection.
- Private Link for private access to Azure services.

---

## Advantages

- Secure communication.
- Highly scalable.
- Supports hybrid cloud.
- Easy integration with Azure services.
- Fine-grained network security.

---

## Disadvantages

- Can become complex in large environments.
- Incorrect network configuration may cause connectivity issues.

---

## Components

- Virtual Network (VNet)
- Subnets
- Network Security Groups (NSGs)
- Application Security Groups (ASGs)
- Route Tables
- VPN Gateway
- ExpressRoute
- Azure Load Balancer
- Azure Firewall
- Private Endpoint

---

## Real-world Example

A company hosts web servers, application servers, and databases in separate subnets inside a VNet. NSGs restrict traffic between layers while a Load Balancer distributes incoming user requests.

---

## Interview Tip

"Azure Networking Services provide secure connectivity, traffic management, and network security for Azure resources."

---

## Quick Revision

- Azure VNet is the foundation of Azure networking.
- NSGs filter network traffic.
- Route Tables control packet routing.
- VPN Gateway connects Azure with on-premises.
- ExpressRoute provides private connectivity.
- Azure Firewall offers centralized protection.
- Load Balancer distributes incoming traffic.

---

## Important Interview Questions

1. What are Azure Networking Services?
2. What networking components are commonly used in Azure?
3. What is the difference between VPN Gateway and ExpressRoute?
4. How do Azure resources communicate securely?
5. Why is Azure networking important?

---

# Azure Virtual Network (VNet)

## Definition

- Azure Virtual Network (VNet) is a logically isolated private network in Azure.
- It allows Azure resources to communicate securely with each other, the internet, and on-premises networks.

---

## Why is it used?

- Connect Azure resources.
- Isolate applications.
- Secure communication.
- Enable hybrid connectivity.
- Support network segmentation.

---

## Key Features

- Private IP addressing.
- Supports IPv4 and IPv6.
- Contains multiple subnets.
- Supports VNet Peering.
- Connects to VPN Gateway and ExpressRoute.
- Integrates with NSGs and Route Tables.

---

## Advantages

- Secure private networking.
- Easy network segmentation.
- Highly scalable.
- Supports hybrid cloud.
- Integrates with Azure services.

---

## Disadvantages

- Requires proper IP planning.
- Misconfiguration may lead to connectivity issues.

---

## Components

### Address Space

- Defines the IP range of the VNet.

### Subnets

- Divide the VNet into smaller networks.

### Network Interface (NIC)

- Connects Azure resources to the VNet.

### Route Tables

- Control packet routing.

### NSGs

- Filter network traffic.

---

## Workflow

```text
Create Resource Group
        ↓
Create Virtual Network
        ↓
Define Address Space
        ↓
Create Subnets
        ↓
Deploy Virtual Machines
        ↓
Apply NSGs and Route Tables
```

---

## Real-world Example

A company creates one VNet with separate subnets for web servers, application servers, and databases to isolate traffic and improve security.

---

## Interview Tip

"A Virtual Network is the foundation of Azure networking and provides secure communication between Azure resources."

---

## Quick Revision

- VNet is a private Azure network.
- Uses private IP addresses.
- Contains multiple subnets.
- Supports hybrid connectivity.
- Works with NSGs and Route Tables.
- Supports VNet Peering.

---

## Important Interview Questions

1. What is Azure Virtual Network?
2. Why do we use VNets?
3. What components exist inside a VNet?
4. What is VNet Peering?
5. Can multiple VNets communicate?

---

# Subnets and CIDR

## Definition

- A subnet divides a Virtual Network into smaller logical networks.
- CIDR (Classless Inter-Domain Routing) defines the IP address range using prefix notation.

---

## Why is it used?

- Organize resources.
- Improve network security.
- Reduce broadcast traffic.
- Simplify network management.
- Separate application layers.

---

## Key Features

- Multiple subnets inside one VNet.
- Each subnet has its own IP range.
- CIDR defines subnet size.
- NSGs can be applied per subnet.
- Route Tables can be associated with subnets.

---

## Advantages

- Better security.
- Easier management.
- Improved scalability.
- Efficient IP allocation.

---

## Disadvantages

- Poor planning can waste IP addresses.
- Changing subnet ranges later is difficult.

---

## CIDR Examples

| CIDR | Total IPs | Usable IPs |
|------|-----------|------------|
| /24 | 256 | 251 (Azure reserves 5 IPs) |
| /25 | 128 | 123 |
| /26 | 64 | 59 |
| /27 | 32 | 27 |

---

## Workflow

```text
VNet (10.0.0.0/16)
      ↓
Web Subnet (10.0.1.0/24)
      ↓
App Subnet (10.0.2.0/24)
      ↓
DB Subnet (10.0.3.0/24)
```

---

## Real-world Example

A banking application uses separate subnets for web servers, application servers, and databases to improve security.

---

## Interview Tip

"CIDR determines the IP range, while subnets divide a VNet into smaller logical networks."

---

## Quick Revision

- Subnets divide VNets.
- CIDR defines IP ranges.
- One VNet can have multiple subnets.
- Azure reserves first 4 and last IP.
- NSGs and Route Tables work with subnets.

---

## Important Interview Questions

1. What is a subnet?
2. What is CIDR notation?
3. Why do we create subnets?
4. How many usable IPs are available in a /24 subnet in Azure?
5. Can NSGs be applied to subnets?

---

# Azure Routes and Route Tables

## Definition

- Routes determine how network traffic travels between Azure resources.
- Route Tables contain one or more custom routes.

---

## Why is it used?

- Control traffic flow.
- Redirect traffic to firewalls or appliances.
- Customize default Azure routing.
- Improve network security.

---

## Key Features

- Azure provides system routes by default.
- Custom routes can override default routes.
- Route Tables are associated with subnets.
- Supports User Defined Routes (UDRs).

---

## Advantages

- Flexible routing.
- Improved traffic control.
- Supports network virtual appliances.
- Better security.

---

## Disadvantages

- Incorrect routes may block connectivity.
- Requires careful planning.

---

## Types of Routes

### System Routes

- Created automatically by Azure.

### User Defined Routes (UDR)

- Created by administrators.

### BGP Routes

- Learned through VPN Gateway or ExpressRoute.

---

## Workflow

```text
VM
 ↓
Subnet
 ↓
Route Table
 ↓
Next Hop
 ↓
Destination
```

---

## Real-world Example

A company routes all internet traffic through Azure Firewall using a custom Route Table.

---

## Interview Tip

"Route Tables control where network traffic goes by defining the next hop."

---

## Quick Revision

- Azure creates system routes automatically.
- Custom routes override default routes.
- Route Tables attach to subnets.
- UDR means User Defined Route.
- Next Hop determines packet destination.

---

## Important Interview Questions

1. What is a Route Table?
2. What are User Defined Routes?
3. Where are Route Tables associated?
4. What is the next hop?
5. When would you use custom routes?

---

# Network Security Groups (NSGs)

## Definition

- A Network Security Group (NSG) is a firewall-like service that filters inbound and outbound network traffic.
- It controls access using security rules.

---

## Why is it used?

- Protect Azure resources.
- Allow only required traffic.
- Block unauthorized access.
- Improve network security.

---

## Key Features

- Inbound and outbound rules.
- Allow or deny traffic.
- Uses priority numbers.
- Supports IP addresses, ports, and protocols.
- Can be associated with subnets or NICs.

---

## Advantages

- Easy to configure.
- Fine-grained traffic control.
- Improves security.
- No additional cost.

---

## Disadvantages

- Does not inspect application content.
- Large rule sets become difficult to manage.

---

## Components

### Priority

- Lower number = Higher priority.

### Source

- Incoming traffic source.

### Destination

- Target resource.

### Protocol

- TCP, UDP, or Any.

### Port

- Destination or source port.

### Action

- Allow or Deny.

---

## Workflow

```text
Incoming Packet
        ↓
NSG Rules Checked
        ↓
First Matching Rule
        ↓
Allow or Deny
```

---

## Real-world Example

An NSG allows HTTP (80) and HTTPS (443) traffic but blocks SSH from the internet.

---

## Interview Tip

"NSG acts like a firewall that filters traffic based on rules."

---

## Quick Revision

- Filters inbound and outbound traffic.
- Associated with subnet or NIC.
- Uses Allow and Deny rules.
- Lower priority number wins.
- Stops processing after first matching rule.

---

## Important Interview Questions

1. What is an NSG?
2. Can an NSG be attached to both subnet and NIC?
3. How are NSG rules evaluated?
4. What is the default behavior of NSGs?
5. What is the difference between inbound and outbound rules?

---

# Application Security Groups (ASGs)

## Definition

- Application Security Groups (ASGs) logically group virtual machines based on application roles.
- Instead of using IP addresses in NSG rules, ASGs allow rules based on application groups.

---

## Why is it used?

- Simplify NSG management.
- Reduce IP-based rules.
- Improve readability.
- Manage large applications easily.

---

## Key Features

- Logical grouping of VMs.
- Works with NSGs.
- Eliminates dependency on IP addresses.
- Easy rule management.
- Supports dynamic application scaling.

---

## Advantages

- Easier administration.
- Cleaner NSG rules.
- Better scalability.
- Reduces manual updates.

---

## Disadvantages

- Only works with resources inside a VNet.
- Depends on NSGs for traffic filtering.

---

## Workflow

```text
VM1, VM2
   ↓
Assign to Web ASG
   ↓
Create NSG Rule
   ↓
Allow Web ASG → App ASG
```

---

## Real-world Example

Instead of allowing traffic from multiple web server IP addresses, an administrator creates a "Web-ASG" and allows traffic from that group to the "App-ASG."

---

## Interview Tip

"ASGs simplify NSG rules by grouping virtual machines based on application roles instead of IP addresses."

---

## Quick Revision

- ASG is a logical grouping of VMs.
- Works together with NSGs.
- Reduces IP-based rules.
- Easier management.
- Useful for multi-tier applications.

---

## Important Interview Questions

1. What is an Application Security Group?
2. How is an ASG different from an NSG?
3. Why are ASGs useful?
4. Can ASGs filter traffic without an NSG?
5. When should you use ASGs?
