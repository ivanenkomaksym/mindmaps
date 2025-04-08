---
title: Azure
markmap:
  colorFreezeLevel: 2
---

## Cloud concepts

- Shared responsibility model
  - SaaS
  - PaaS
  - IaaS
  - On-premise
- Cloud models
  - Public
  - Private
  - Hybrid
- Consumption-based model
  - Capital expenditure (CapEx)
  - Operational expenditure (OpEx)

## Azure architecture

- Azure physical infrastructure
  - Geography > Region Pair > Azure Region > Availability Zone > Data Center
- Azure management infrastructure
  - Root Management Group > Management Groups > Subscriptions > Resource Groups > Resources
- Virtual Machines
  - Virtual machine scale sets
  - Virtual machine availability sets
  - Azure Container Instances
  - Azure Container Apps
  - Azure Kubernetes Service (AKS)
  - Azure Functions
  - Azure App Service 
- Virtual Network
  - Virtual private network (VPN)
  - VPN Gateway
  - ExpressRoute
  - ExpressRoute Gateway

## Storage
  - Azure Blobs
  - Azure Files
  - Azure Queues
  - Azure Disks
  - Azure Tables
  - Access tiers
    - Hot
    - Cool. Stored for at least 30 days
    - Cold. Stored for at least 90 days
    - Archive. Stored for at least 180 days
  - Redundancy
    - Locally redundant storage (LRS). At least 11 nines (99.999999999%) 
    - Zone-redundant storage (ZRS). At least 12 nines (99.9999999999%)
    - Geo-redundant storage (GRS). at least 16 nines (99.99999999999999%)
    - Geo-zone-redundant storage (GZRS). At least 16 nines (99.99999999999999%)
  
## IAM

- Microsoft Entra Domain Services  
- Single sign-on (SSO)
- Multifactor authentication
- Passwordless authentication
  - Windows Hello for Business
  - Microsoft Authenticator app
  - FIDO2 security keys
- FIDO2 security keys
- B2B direct connect
- Conditional Access
  - Role. Has an associated set of access permissions
  - Scopes include:
    - A management group (a collection of multiple subscriptions).
    - A single subscription.
    - A resource group.
    - A single resource.
- Zero Trust
  - Verify explicitly
  - Use least privilege access
  - Assume breach
- Defense-in-depth
  - Physical security
  - Identity & Access
  - Perimeter
  - Network
  - Compute
  - Application
  - Data
- Defender for Cloud