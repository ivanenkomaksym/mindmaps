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
  - storage optimized
- Amazon EC2 pricing
  - On-Demand Instances
  - Reserved Instances
  - EC2 Instance Savings Plans
  - Spot Instances
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
- Edge locations
- AWS Outposts
- AWS Elastic Beanstalk
- AWS CloudFormation

## Networking

- VPC - Virtual Private Cloud
  - Internet gateway, or IGW
  - Virtual private gateway
  - Direct Connect
  - Public/Private subnets
  - Network access control list (ACL)(opens in a new tab). Stateless. Allows all inbound and outbound traffic
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
  - People
  - Governance
  - Platform
  - Security
  - Operations
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
  - Security
  - Reliability
  - Performance efficiency
  - Cost optimization
  - Sustainability
- Advantages of cloud computing
  - Trade upfront expense for variable expense.
  - Benefit from massive economies of scale.
  - Stop guessing capacity.
  - Increase speed and agility.
  - Stop spending money running and maintaining data centers.
  Go global in minutes.