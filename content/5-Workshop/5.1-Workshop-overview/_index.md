---
title: "Workshop Overview"
date: 2026-07-07
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### Real-World Problem Introduction
The legacy system of the **PawVerse** pet e-commerce platform frequently faced downtime risks during promotional events (Flash Sales) due to a rigid infrastructure, an inability to handle traffic spikes, and sensitive credentials hardcoded directly into the source code.

This workshop provides step-by-step guidance on building a distributed, auto-scaling, multi-layered secure, and cost-optimized cloud solution on AWS to definitively resolve these operational challenges.

#### Architecture Diagram
The PawVerse system is designed with a Multi-tier Architecture across multiple Availability Zones (Multi-AZ), ensuring High Availability and strict separation of data flows.

![PawVerse Architecture Diagram](/images/5-Workshop/5.1-Workshop-overview/diagram.png)
*Figure 5.1.1: Data flow diagram of the PawVerse architecture on AWS.*

#### Core Components Explanation
* **Edge Layer:** AWS WAF and CloudFront defend against DDoS attacks and SQL Injections while accelerating the delivery of static interfaces from Amazon S3 (secured via Origin Access Control - OAC).
* **Compute Layer:** The Application Load Balancer (ALB) distributes dynamic traffic to the EC2 instances cluster. The Auto Scaling Group dynamically scales the number of servers based on real-time CPU utilization metrics.
* **Data Layer:** Amazon ElastiCache (Redis) acts as a caching mechanism to offload direct read queries from the relational database, Amazon RDS (MySQL).
* **Security Layer:** EC2 instances automatically retrieve database credentials from AWS Secrets Manager using IAM Roles, completely eliminating the risk of hardcoded credentials.

#### Step-by-Step Implementation Roadmap
To actualize this architecture, the deployment workflow is categorized into specialized phases, corresponding to the project's structure:
1. **Environment Preparation:** Establish prerequisites and source code configuration.
2. **Network Infrastructure (VPC):** Plan IP CIDR blocks, configure Private/Public Subnets, and optimize internal routing.
3. **Storage & Database:** Provision Amazon RDS, ElastiCache, and enforce security via Secrets Manager.
4. **Compute Layer:** Bundle initialization scripts (User Data), deploy the ALB, and configure the Auto Scaling Group.
5. **Delivery & Firewall:** Host static assets on S3, integrate CloudFront CDN, and enable AWS WAF protection.
6. **System Monitoring:** Implement CloudWatch, CloudTrail auditing, and SNS alerting mechanisms.
7. **Acceptance & Reflection:** Evaluate real-world performance (Live Demo) and analyze technical lessons learned.
8. **System Cleanup:** Decommission resources following Cost Optimization (FinOps) standards.