---
title : "Workshop Overview"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Real-world Business Problem
The legacy system of the **PawVerse** pet e-commerce platform frequently faced severe network downtime during promotional events (Flash Sales) due to rigid infrastructure, poor load capacity, and hard-coded sensitive credentials.

This workshop will guide you step-by-step on how to build a distributed, auto-scaling, multi-layer secure, and cost-optimized cloud solution on AWS to thoroughly resolve the aforementioned issues.

#### Architecture Diagram
The PawVerse system is designed with a 3-Tier architecture across multiple Availability Zones (Multi-AZ), ensuring High Availability and clear separation of data flows.

![PawVerse Architecture Diagram](/images/5-Workshop/5.1-Workshop-overview/diagram.png)
*Figure 5.1: PawVerse AWS cloud infrastructure data flow diagram.*

#### Core Components Explanation
+ **Edge Layer:** AWS WAF and CloudFront protect against DDoS and SQL Injection attacks while accelerating the delivery of static interfaces from Amazon S3 (secured by OAC).
+ **Compute Layer:** The Application Load Balancer (ALB) distributes dynamic traffic to the EC2 cluster. The Auto Scaling Group dynamically adjusts the number of servers based on real-time CPU metrics.
+ **Data Layer:** Amazon ElastiCache (Redis) acts as an in-memory buffer, offloading 80% of direct queries to the Amazon RDS (MySQL) relational database.
+ **Security Layer:** EC2 instances automatically retrieve database passwords from AWS Secrets Manager via IAM Roles, completely eliminating hard-coded credentials.

#### Step-by-Step Workshop Roadmap
To complete this infrastructure, we will walk through 5 main phases in the Workshop:
1. **VPC & Network:** Establish Private/Public Subnets, NAT Gateways, and VPC Endpoints.
2. **Database & Security:** Provision RDS, ElastiCache, and Secrets Manager vaults.
3. **Compute & ALB:** Configure EC2 Launch Templates, Auto Scaling, and Load Balancers.
4. **Edge Layer:** Deploy the frontend to S3, and connect CloudFront along with WAF.
5. **Clean-up:** Safely terminate resources to optimize costs after the Lab concludes.