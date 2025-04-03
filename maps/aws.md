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
- Security
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
- Monitoring and Analytics
  - Amazon CloudWatch. CloudWatch alarms
  - AWS CloudTrail. CloudTrail Insights
  - AWS Trusted Advisor. Pillars: cost optimization, performance, security, fault tolerance, and service limits

- VPC - Virtual Private Cloud
  - Internet gateway, or IGW
  - Virtual private gateway
  - Direct Connect
  - Public/Private subnets
  - Network access control list (ACL)(opens in a new tab). Stateless. Allows all inbound and outbound traffic
  - Security groups. Stateful. Denies all inbound traffic and allows all outbound traffic
- Route 53

## Features

Note that if blocks and lists appear at the same level, the lists will be ignored.

### Lists

- **strong** ~~del~~ *italic* ==highlight==
- `inline code`
- [x] checkbox
  - [More Katex Examples](#?d=gist:af76a4c245b302206b16aec503dbe07b:katex.md)
- Now we can wrap very very very very long text based on `maxWidth` option
- Ordered list
  1. item 1
  2. item 2

### Blocks

```js
console.log('hello, JavaScript')
```

| Products | Price |
|-|-|
| Apple | 4 |
| Banana | 2 |

![](https://markmap.js.org/favicon.png)