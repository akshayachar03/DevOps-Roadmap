# Azure Engineering Handbook

# Azure DevOps / Azure Cloud / Platform Engineering Roadmap

## Goal

Become a Production Ready

- Azure Cloud Engineer
- Azure DevOps Engineer
- Platform Engineer
- Site Reliability Engineer (SRE)

---

# Stage 0 - Foundation

## Duration

2 Weeks

## Prerequisites

Already Completed (Review Only)

### Operating Systems

- Linux Administration
- Windows Server
- Process Management
- Services
- Package Management
- File System
- Permissions
- Systemd
- Logs

### Networking

- OSI Model
- TCP/IP
- IP Addressing
- CIDR
- Routing
- Switching
- NAT
- DNS
- DHCP
- HTTP
- HTTPS
- SSL/TLS
- Firewalls
- Reverse Proxy
- Load Balancing

### Virtualization

- Hypervisors
- VMware
- Hyper-V
- VirtualBox
- KVM

### Scripting

- Bash
- PowerShell Basics
- Python Basics

### Data Formats

- JSON
- YAML
- XML

### APIs

- REST API
- HTTP Methods
- Status Codes
- Authentication

---

## Hands-on

- Configure Apache
- Configure Nginx
- Configure IIS
- Generate SSL Certificate
- Configure DNS
- Analyze Logs
- Packet Capture
- Curl
- SSH

---

## Mini Project

Deploy a LAMP Stack manually.

---

# Stage 1 — Azure Administrator

Estimated Duration: 8–10 Weeks

---

# Phase 1 — Azure Fundamentals

Duration: 2 Weeks

## Learn

### Cloud Computing

- Evolution of Cloud
- Characteristics
- Public Cloud
- Private Cloud
- Hybrid Cloud
- Multi Cloud

### Cloud Service Models

- IaaS
- PaaS
- SaaS
- FaaS

### Azure Basics

- Azure Portal
- Azure CLI
- Azure PowerShell
- Azure Resource Manager (ARM)
- Azure Subscription
- Resource Groups
- Azure Regions
- Region Pairs
- Availability Zones
- Availability Sets
- Resource Locks
- Tags

### Cost Management

- Pricing Calculator
- Cost Analysis
- Budgets
- Reservations
- Azure Hybrid Benefit

### Azure Advisor

### Azure Service Health

### Azure Resource Graph

---

## Hands-on

- Create Subscription
- Create Resource Group
- Deploy VM
- Create Storage
- Apply Tags
- Apply Locks
- Azure CLI
- PowerShell

---

## Mini Project

Deploy a Production Linux VM using Azure Portal and CLI.

---

## Interview Checkpoint

You should confidently explain:

- ARM
- Resource Group
- Subscription
- Availability Zone
- Region Pair
- Shared Responsibility Model
- Azure Pricing

---

# Phase 2 — Azure Architecture

Duration: 2 Weeks

## Learn

- Azure Global Infrastructure
- ARM Architecture
- Azure Landing Zones
- Cloud Adoption Framework
- Azure Well-Architected Framework
- Management Groups
- Resource Organization
- Naming Conventions
- Enterprise Design
- High Availability
- Disaster Recovery
- Scalability
- Fault Tolerance
- Reliability
- Performance
- Cost Optimization

---

## Hands-on

- Design Landing Zone
- Configure Management Groups
- Create Naming Standards
- Design Multi-Region Architecture

---

## Mini Project

Design Enterprise Azure Architecture.

---

## Interview Checkpoint

- Landing Zones
- CAF
- Well-Architected Framework
- Region Pair
- Availability Zone
- HA vs DR

---

# Phase 3 — Azure Compute

Duration: 2 Weeks

## Learn

### Virtual Machines

- VM Sizes
- VM Series
- Availability Sets
- Availability Zones
- VM Scale Sets
- Managed Disks
- Ephemeral Disks
- Custom Images
- Shared Image Gallery
- Extensions
- Azure Bastion

### App Services

- Web Apps
- API Apps
- Deployment Slots
- Scaling
- Custom Domains
- SSL

### Azure Functions

### Container Apps

### Azure Batch

---

## Hands-on

- Deploy Linux VM
- Deploy Windows VM
- Configure Bastion
- Create VMSS
- Deploy Web App
- Configure Autoscaling

---

## Mini Project

Deploy Highly Available Web Application.

---

# Phase 4 — Azure Networking

Duration: 3 Weeks

## Learn

### Networking Basics

- Virtual Network
- Address Space
- Subnets
- NIC
- Public IP
- Private IP

### Security

- NSG
- ASG
- Azure Firewall
- DDoS Protection
- WAF

### Connectivity

- VNet Peering
- VPN Gateway
- ExpressRoute
- Virtual WAN

### DNS

- Azure DNS
- Private DNS

### Routing

- Route Tables
- UDR
- BGP

### Load Balancing

- Azure Load Balancer
- Application Gateway
- Front Door
- Traffic Manager

### Private Connectivity

- Service Endpoints
- Private Endpoint
- Private Link

---

## Hands-on

- Build Hub-Spoke
- Configure Firewall
- Configure VPN
- Configure Application Gateway
- Configure Private Endpoint

---

## Mini Project

Enterprise Hub-Spoke Network

---

# Phase 5 — Azure Storage

Duration: 2 Weeks

## Learn

- Storage Accounts
- Blob Storage
- File Storage
- Queue Storage
- Table Storage
- Managed Disks
- Azure Files
- Azure NetApp Files
- Replication
- Access Tiers
- SAS
- Shared Keys
- Lifecycle Management
- Storage Security
- Private Endpoint
- Backup
- Azure Backup
- Azure Site Recovery

---

## Hands-on

- Create Storage
- Mount Azure Files
- Configure Backup
- Configure Lifecycle

---

## Mini Project

Enterprise Backup Storage

---

# Phase 6 — Identity

Duration: 2 Weeks

## Learn

- Microsoft Entra ID
- Tenant
- Users
- Groups
- RBAC
- Managed Identity
- Service Principal
- App Registration
- Conditional Access
- MFA
- PIM
- Hybrid Identity
- Azure AD Connect

---

## Hands-on

- Configure RBAC
- Configure Managed Identity
- Configure MFA
- Configure Conditional Access

---

## Mini Project

Enterprise Identity Solution

---

# Phase 7 — Security

Duration: 2 Weeks

## Learn

- Azure Key Vault
- Defender for Cloud
- Microsoft Sentinel
- Azure Policy
- Azure Blueprints (Concepts)
- Encryption
- JIT Access
- Secrets
- Certificates
- Compliance
- Secure Score

---

## Hands-on

- Configure Key Vault
- Store Secrets
- Enable Defender
- Create Policies

---

## Mini Project

Secure Azure Subscription

# Stage 2 — DevOps Engineer

**Estimated Duration:** 10–12 Weeks

---

# Phase 8 — Azure Monitoring & Governance

**Duration:** 2 Weeks

## Learn

### Azure Monitor

* Metrics
* Logs
* Alerts
* Action Groups
* Diagnostic Settings
* Data Collection Rules
* VM Insights
* Container Insights

### Log Analytics

* Workspaces
* KQL Basics
* Saved Queries
* Workbooks

### Application Insights

* Availability Tests
* Live Metrics
* Dependency Tracking
* Performance Monitoring

### Governance

* Azure Policy
* Management Groups
* Resource Locks
* Tags
* Cost Management
* Budgets
* Reservations
* Azure Advisor

---

## Hands-on

* Configure Azure Monitor
* Create Alerts
* Configure Log Analytics
* Build Dashboard
* Enable VM Insights
* Create Azure Policies

---

## Mini Project

Implement centralized monitoring and governance for an Azure subscription.

---

# Phase 9 — Git

**Duration:** 1 Week

## Learn

### Git Basics

* Version Control
* Repository
* Commit
* Clone
* Init
* Status
* Log

### Branching

* Branch
* Merge
* Rebase
* Cherry Pick
* Squash

### Collaboration

* Pull Request
* Merge Conflict
* Tags
* Releases

### Advanced Git

* Stash
* Reflog
* Reset
* Revert
* Hooks

---

## Hands-on

* Create Repository
* Branching
* Merge
* Resolve Conflicts
* Cherry Pick
* Rebase

---

## Mini Project

Maintain Infrastructure Code using Git.

---

# Phase 10 — GitHub

**Duration:** 1 Week

## Learn

* Repository Management
* Branch Protection
* Pull Requests
* Code Reviews
* Issues
* Projects
* Discussions
* Wiki
* GitHub CLI
* GitHub Secrets
* GitHub Packages
* GitHub Actions (Basics)

---

## Hands-on

* Create Repository
* Configure Branch Protection
* Review Pull Request
* Configure Secrets

---

## Mini Project

Host an Infrastructure Repository with proper Git workflow.

---

# Phase 11 — Azure DevOps

**Duration:** 3 Weeks

## Learn

### Azure DevOps Organization

### Azure Repos

* Git Repository
* Branch Policies
* Pull Requests

### Azure Boards

* Epic
* Feature
* User Story
* Task
* Sprint
* Kanban

### Azure Pipelines

* YAML Pipelines
* Classic Pipelines
* Build Pipeline
* Release Pipeline
* Variables
* Variable Groups
* Secure Files
* Library
* Templates
* Self-hosted Agents
* Microsoft-hosted Agents
* Deployment Jobs
* Environments
* Approvals
* Gates

### Azure Artifacts

### Azure Test Plans

### CI/CD

* Continuous Integration
* Continuous Delivery
* Continuous Deployment

### Deployment Strategies

* Rolling
* Blue/Green
* Canary

---

## Hands-on

* Build Pipeline
* Release Pipeline
* YAML Pipeline
* Deploy to Azure
* Configure Self-hosted Agent

---

## Mini Project

Deploy a multi-stage CI/CD pipeline using Azure DevOps.

---

# Phase 12 — Infrastructure as Code

**Duration:** 4 Weeks

## Learn

### Terraform

* Installation
* Providers
* Resources
* Variables
* Outputs
* Locals
* Modules
* Remote State
* Backend
* State Locking
* Workspaces
* Lifecycle
* Data Sources
* Provisioners
* Functions
* Loops
* Dynamic Blocks

### Bicep

* Syntax
* Parameters
* Modules
* Outputs
* Conditions
* Loops

### ARM Templates

* Template Structure
* Parameters
* Variables
* Outputs
* Linked Templates

### Packer

* Image Creation
* Azure Image Builder

---

## Hands-on

* Deploy VM
* Deploy VNet
* Create Modules
* Configure Remote State
* Build Custom Images

---

## Mini Project

Provision a complete Azure environment using Terraform.

---

# Stage 3 — Cloud Native Engineering

**Estimated Duration:** 10–12 Weeks

---

# Phase 13 — Docker

**Duration:** 2 Weeks

## Learn

* Containers
* Images
* Docker Engine
* Docker Desktop
* Docker CLI
* Dockerfile
* Image Layers
* Volumes
* Bind Mounts
* Networks
* Docker Compose
* Multi-stage Builds
* Image Optimization
* Docker Registry
* Azure Container Registry (ACR)

---

## Hands-on

* Build Images
* Push Images
* Docker Compose
* Connect Containers
* Use ACR

---

## Mini Project

Containerize a web application and push it to Azure Container Registry.

---

# Phase 14 — Kubernetes

**Duration:** 4 Weeks

## Learn

### Core Concepts

* Cluster
* Control Plane
* Worker Node
* kubelet
* kube-proxy
* etcd

### Objects

* Pod
* ReplicaSet
* Deployment
* StatefulSet
* DaemonSet
* Job
* CronJob

### Networking

* Service
* Ingress
* Network Policy

### Storage

* Persistent Volume
* Persistent Volume Claim
* Storage Class

### Configuration

* ConfigMap
* Secret

### Scheduling

* Node Selector
* Affinity
* Taints
* Tolerations

### Security

* RBAC
* Service Account
* Pod Security

---

## Hands-on

* Deploy Pods
* Deploy Applications
* Configure Ingress
* Persistent Storage
* Secrets
* Autoscaling

---

## Mini Project

Deploy a three-tier application on Kubernetes.

---

# Phase 15 — Azure Kubernetes Service (AKS)

**Duration:** 2 Weeks

## Learn

* AKS Architecture
* Node Pools
* Cluster Autoscaler
* HPA
* ACR Integration
* Azure CNI
* Kubenet
* Azure Policy for AKS
* Monitoring
* Upgrades
* Backup
* Security
* Managed Identity
* Private AKS
* Azure AD Integration

---

## Hands-on

* Create AKS Cluster
* Deploy Applications
* Configure HPA
* Configure Monitoring
* Upgrade Cluster

---

## Mini Project

Deploy a production-ready AKS cluster integrated with Azure Container Registry.

---

# Phase 16 — Helm & GitOps

**Duration:** 2 Weeks

## Learn

### Helm

* Charts
* Templates
* Values
* Releases
* Repositories
* Hooks

### GitOps

* GitOps Principles
* Argo CD
* FluxCD

### Kubernetes Package Management

* Kustomize
* Helm Best Practices

---

## Hands-on

* Deploy Helm Charts
* Install Argo CD
* Deploy using GitOps

---

## Mini Project

Automate Kubernetes deployments using GitOps.

---

# Interview Readiness Checkpoint 2

You should now be able to:

* Use Git professionally
* Design Git branching strategies
* Build Azure DevOps pipelines
* Write YAML pipelines
* Implement CI/CD
* Provision Azure using Terraform
* Build Docker images
* Manage Kubernetes clusters
* Deploy production workloads on AKS
* Use Helm for application packaging
* Implement GitOps workflows

At this point, you are ready for many **Azure DevOps Engineer** interviews in service-based companies and junior-to-mid level cloud engineering roles.
