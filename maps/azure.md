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

## Management and governance

- Cost management
  - Pricing calculator. Estimated cost for provisioning resources in Azure
  - TCO calculator. Compare the costs for running an on-premises infrastructure compared to an Azure Cloud infrastructure
  - Cost Management
    - Budget alerts
    - Credit alerts
    - Department spending quota alerts
- Feature and tools for governance and compliance
  - Microsoft Purview
  - Azure Policies
    - Azure Policy initiative is a way of grouping related policies together
  - Resource locks. Prevent resources from being deleted or updated
  - Microsoft Service Trust Portal
- Azure Resource Manager (ARM) is the deployment and management service for Azure
  - ARM templates
  - Declarative syntax. Repeatable results. Orchestration. Modular files. Extensibility
  - Bicep is a language that uses declarative syntax to deploy Azure resources
- Monitoring tools
  - Azure Advisor. Recommendations to help improve reliability, security, and performance, achieve operational excellence, and reduce costs
  - Azure Status is a broad picture of the status of Azure globally.
  - Service Health provides a narrower view of Azure services and regions.
  - Resource Health is a tailored view of your actual Azure resources.
  - Azure Monitor is a platform for collecting data on your resources, analyzing that data, visualizing the information
  - Azure Log Analytics is the tool in the Azure portal where you’ll write and run log queries
  - Azure Monitor Alerts are an automated way to stay informed when Azure Monitor detects a threshold being crossed. 
  - Application Insights, an Azure Monitor feature, monitors your web applications.