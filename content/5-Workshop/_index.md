---
title: "Workshop"
date: 2026-07-07
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# PawVerse Cloud Infrastructure Deployment

#### Overview

In the modern e-commerce landscape, maintaining a resilient, highly scalable system that strictly protects user data is vital for any enterprise.

In this Workshop, you will gain hands-on experience blueprinting, configuring, and deploying the entire AWS cloud infrastructure for the **PawVerse** platform. The system utilizes a distributed Multi-tier architecture, seamlessly integrating a global content delivery network, web application firewalls, caching clusters, and dynamic auto-scaling mechanisms.

Specifically, this lab emphasizes Cloud Operations thinking and core security by rigorously enforcing the Principle of Least Privilege, completely isolating resources within Private Subnets, and automating the encryption of sensitive credentials.

#### Core Services Utilized
+ **Networking & Security:** Amazon VPC, NAT/IGW Gateway, S3 Gateway Endpoint, AWS IAM, AWS KMS, AWS Secrets Manager.
+ **Compute & Scaling:** Amazon EC2, EC2 Launch Templates, Auto Scaling Group, Application Load Balancer (ALB).
+ **Storage & Database:** Amazon RDS (MySQL), Amazon ElastiCache (Redis), Amazon S3.
+ **Edge Delivery & Protection:** Amazon CloudFront, AWS WAF.
+ **Observability & Management:** Amazon CloudWatch, AWS CloudTrail, Amazon SNS.

#### Workshop Content

1. **[Workshop Overview](5.1-Workshop-overview/):** Understand the real-world business problem and analyze the Solution Architecture Diagram.
2. **[Prerequisites](5.2-Prerequiste/):** Prepare the AWS environment, IAM Roles, deployment region, and source code.
3. **[VPC & Network Infrastructure](5.3-vpc-network/):** Build the core internal network framework, configure Public/Private routing, and optimize bandwidth using Gateway Endpoints.
4. **[Storage & Credentials Security](5.4-Database-Security/):** Deploy Secrets Manager vaults, Amazon RDS, ElastiCache, and audit network isolation (DNS Simulation).
5. **[Compute & Load Balancing](5.5-Compute-ALB/):** Write automated bootstrap scripts (User Data), setup the ALB, and configure the Auto Scaling Group.
6. **[Edge Layer (CloudFront & WAF)](5.6-EdgeLayer/):** Host Frontend on S3, configure global CDN distribution, and set up the web application firewall.
7. **[Monitoring & Alerting](5.7-Monitoring/):** Configure the CloudWatch Agent for metrics collection, set up SNS alerts, and enable system auditing via CloudTrail.
8. **[Live Demo & Reflection](5.8-Reflection/):** Admire the real-world system and extract critical technical lessons learned during operations.
9. **[Resource Cleanup](5.9-Cleanup/):** Safely decommission the infrastructure following FinOps procedures to eliminate unintended costs.