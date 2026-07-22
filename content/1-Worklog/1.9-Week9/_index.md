---
title: "Week 9 Report"
date: 2026-06-21
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:
* Initiate Phase 2: PawVerse Real-world Project Deployment.
* Fully provision the core network architecture (VPC) ensuring High Availability (HA) and network isolation.
* Configure secure Data Tiers (Databases) hidden within Private subnets and encrypt authentication credentials.

### Tasks Executed:

| Day | Tasks Carried Out | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| **Mon** | **Architecture Analysis:**<br>- Received PawVerse project requirements from Mentors.<br>- Designed the 5-tier infrastructure logical architecture blueprint. | 06/15/2026 | 06/15/2026 |  |
| **Tue** | **Core Networking (VPC):**<br>- Provisioned PawVerse-VPC with standardized CIDR blocks.<br>- Allocated Public and Private Subnets across 2 Availability Zones. | 06/16/2026 | 06/16/2026 |  |
| **Wed** | **Network Routing & Gateways:**<br>- Attached Internet Gateways to Public Subnets.<br>- Deployed NAT Gateways to grant internet access for Private Subnets.<br>- Configured S3 Gateway Endpoints for bandwidth optimization. | 06/17/2026 | 06/17/2026 |  |
| **Thu** | **Firewalls & Secrets Management:**<br>- Defined Security Group perimeters for both Web and Database Tiers.<br>- Initialized AWS Secrets Manager to securely vault DB passwords. | 06/18/2026 | 06/18/2026 | AWS  |
| **Fri** | **Database Deployment:**<br>- Configured Amazon RDS MySQL inside the Private Subnet.<br>- Provisioned ElastiCache Redis clusters for high-speed caching. | 06/19/2026 | 06/19/2026 |  |

### Achievements:
* **Robust Network Infrastructure:** Successfully deployed a VPC strictly adhering to AWS Best Practices, fully isolating internal/external environments while guaranteeing Multi-AZ redundancy.
* **Data Security:** Successfully obfuscated the Database within the Private Subnet. Entirely mitigated source code credential leak risks by integrating AWS Secrets Manager instead of hard-coding passwords in configuration files.