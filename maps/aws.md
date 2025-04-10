---
title: AWS
markmap:
  colorFreezeLevel: 2
---

## Compute in the Cloud

- Amazon Elastic Compute Cloud (Amazon EC2)
  - General purpose
  - Compute optimized
  - Memory optimized
  - Accelerated computing
  - Storage optimized
- Amazon EC2 pricing
  - On-Demand Instances
  - Reserved Instances
  - EC2 Instance Savings Plans
  - Spot Instances
  - Dedicated Hosts
- AWS Lambda
- Amazon Elastic Container Service (Amazon ECS)
- Amazon EKS
- AWS Fargate

## Global Infrastructure

- Factors
  - Compliance
  - Proximity
  - Feature availability
  - Pricing
- AWS Region > Availability Zone AZ > Data center
- Amazon CloudFront (CDN)
- Edge locations
- AWS Outposts
- AWS Elastic Beanstalk (PaaS)
- AWS CloudFormation (IaC)

## Networking

- VPC - Virtual Private Cloud
  - Internet gateway, or IGW
  - Virtual private gateway
  - Direct Connect
  - Public/Private subnets
  - Network access control list (ACL). Stateless. Allows all inbound and outbound traffic
  - Security groups. Stateful. Denies all inbound traffic and allows all outbound traffic
- Route 53

## Storage and Databases

- Storage
  - Instance stores. if you stop or terminate your EC2 instance, all data written to the instance store volume will be deleted
  - Amazon Elastic Block Store (Amazon EBS)
  - Amazon Simple Storage Service (Amazon S3)
    - S3 Standard
    - S3 Standard-Infrequent Access (S3 Standard-IA)
    - S3 One Zone-Infrequent Access (S3 One Zone-IA)
    - S3 Intelligent-Tiering
    - S3 Glacier Instant Retrieval
    - S3 Glacier Flexible Retrieval
    - S3 Glacier Deep Archive
    - S3 Outposts
  - Amazon Elastic File System (Amazon EFS)
- Database
  - Amazon Relational Database Service (Amazon RDS)
  - Amazon Aurora
  - Amazon DynamoDB
  - Amazon Redshift
  - AWS Database Migration Service (AWS DMS)
  - Amazon DocumentDB
  - Amazon Neptune
  - Amazon Quantum Ledger Database (Amazon QLDB)
  - Amazon Managed Blockchain
  - Amazon ElastiCache
  - Amazon DynamoDB Accelerator

## Security

  - Shared Responsibility Model
  - User Permissions And Access
    - Root user
    - Users/Groups
    - Policies
    - Roles
  - AWS Organizations
    - Service control policies (SCPs). Applied on organization root, an individual member account, or an OU
    - Policies applied on IAM users, groups, or roles
  - Compliance. AWS Artifact
    - AWS Artifact Agreements
    - AWS Artifact Reports
  - DDoS. AWS Shield Standard and AWS Shield Advanced
  - Additional Security Services
    - AWS Key Management Service (AWS KMS)
    - AWS WAF
    - Amazon Inspector
    - Amazon GuardDuty

## Monitoring and Analytics

  - Amazon CloudWatch. CloudWatch alarms
  - AWS CloudTrail. CloudTrail Insights
  - AWS Trusted Advisor. Pillars: cost optimization, performance, security, fault tolerance, and service limits
  - Amazon Inspector

## Pricing

 - AWS Free Tier
   - Always free. AWS lambda free up to 1 million invocations per month
   - Free for 12 months. AWS S3 for up to 5GB of storage
   - Trials
 - AWS Pricing Concepts
   - AWS Pricing Calculator
   - Compute Savings Plan
   - Amazon S3
     - Storage 
     - Requests and data retrievals 
     - Data transfer 
     - Management and replication
 - Billing Dashboard
 - Consolidated Billing
 - AWS Budgets
 - AWS Cost Explorer
 - AWS Support Plans
   - Basic
   - Developer
   - Business
   - Enterprise On-Ramp
   - Enterprise

## Migration and Innovation

- AWS Cloud Adoption Framework (AWS CAF)
  - Business
    - Your investments in the cloud propel your digital transformation goals and business results
  - People
    - Link between technology and business, speeding up the cloud journey to help organizations quickly evolve into a culture of continuous growth and learning
  - Governance
    - Helps coordinate cloud initiatives while maximizing organizational benefits and minimizing risks
  - Platform
    - Helps construct an enterprise-grade, scalable, hybrid cloud platform, modernize existing workloads, and implement new cloud-native solutions.
  - Security
    - Helps achieve the confidentiality, integrity, and availability of data and cloud workloads.
  - Operations
    - Helps ensure that cloud services are delivered at a level that meets the business needs.
- Benefits of Using AWS CAF
  - Risk Reduction
  - Improve environmental, social, and governance performance
  - Revenue Growth
  - Increased Operational Efficiency
- Cloud Transformation Phases in AWS CAF
  - Envision, Align, Launch, Scale
- AWS CAF Use Cases
  - Technology, Process, Organization, Product
- Migration Strategies
  - Rehosting
  - Replatforming
  - Refactoring/re-architecting
  - Repurchasing
  - Retaining
  - Retiring
- AWS Snow Family
  - AWS Snowcone
  - AWS Snowball
  - AWS Snowmobile
- Innovation with AWS
  - Amazon Textract
  - Amazon Lex
  - AWS DeepRacer
  - Amazon SageMaker
  - Amazon Q Developer

## The Cloud Journey
  
- The AWS Well-Architected Framework
  - Operational excellence
    - The ability to run and monitor systems to deliver business value
    - AWS CloudFormation for creating templates
  - Security
    - AWS Identity and Access Management (IAM)
  - Reliability
    - Recover from infrastructure or service disruptions
    - Amazon CloudWatch
  - Performance efficiency
    - The ability to use computing resources efficiently to meet system requirements
    - Amazon CloudWatch
  - Cost optimization
    - Cost Explorer
  - Sustainability
    - The ability to increase efficiency across all components of a workload by maximizing the benefits from the provisioned resources.
    - Amazon EC2 Auto Scaling
- Advantages of cloud computing
  - Trade upfront expense for variable expense.
  - Benefit from massive economies of scale.
  - Stop guessing capacity.
  - Increase speed and agility.
  - Stop spending money running and maintaining data centers.
  Go global in minutes.
- AWS Design Principles
  - Scalability
  - Disposable Resources Instead of Fixed Servers
  - Automation
  - Loose Coupling
  - Services, Not Servers
  - Database
  - Managing Increasing Volumes of Data
  - Removing Single Points of Failure
  - Optimize for Cost
  - Caching
  - Security
- Cloud Architecture Best Practices
  - Decouple your components 
  - Think parallel
  - Implement elasticity
  - Design for failure
- AWS Disaster Recovery
  - Backup and Restore
  - Pilot Light
  - Warm Standby Solution
  - Multi-Site

## Job Roles in the Cloud

- AWS Cloud for Business
  - Speed, Scale, Innovation, Productivity
  - Cloud Architect, System Administrator, Security Administrator, DevOps Administrator