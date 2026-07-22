---
title: "Week 10 Report"
date: 2026-06-28
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:
* Configure the Compute Layer for the PawVerse project.
* Automate the internal software bootstrap and installation sequences.
* Establish traffic orchestration mechanisms and elastic auto-scaling infrastructure.

### Tasks Executed:

| Day | Tasks Carried Out | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| **Mon** | **IAM Permissions:**<br>- Generated IAM Roles allowing EC2 instances to retrieve Secrets Manager payloads and push Logs to CloudWatch. | 06/22/2026 | 06/22/2026 |  |
| **Tue** | **Server Standardization (Launch Template):**<br>- Designed Launch Templates utilizing Amazon Linux 2023 AMIs.<br>- Coded Bash Scripts (User Data) to automate Docker installation, source code retrieval, and CWAgent configuration. | 06/23/2026 | 06/23/2026 | |
| **Wed** | **Internal Routing:**<br>- Provisioned Target Groups to execute Health Checks against internal Spring Boot backend servers. | 06/24/2026 | 06/24/2026 |  |
| **Thu** | **Load Balancing (ALB):**<br>- Deployed an Application Load Balancer (ALB) to ingest external perimeter traffic.<br>- Bound the ALB to the Target Group to distribute inbound request flows. | 06/25/2026 | 06/25/2026 |  |
| **Fri** | **Elastic Scaling (Auto Scaling):**<br>- Deployed an Auto Scaling Group attached to the ALB.<br>- Validated the system's capability to dynamically provision 2 Healthy instances and cross-connect successfully. | 06/26/2026 | 06/26/2026 |  |

### Achievements:
* **Bootstrap Automation:** Successfully applied User Data scripts, granting newly spawned EC2 instances the capability to automatically fetch source code, decrypt secrets, and spin up Docker containers without manual intervention.
* **High Availability (HA) Guarantee:** The ALB network flow evenly distributed payloads across EC2 nodes. The Auto Scaling Group ensured the PawVerse platform maintained absolute stability even during volatile traffic spikes.