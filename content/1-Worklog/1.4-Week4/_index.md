---
title: "Week 4 Worklog"
date: 2026-05-16
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Master automation and resource governance via AWS Systems Manager and Infrastructure as Code (CloudFormation).
* Implement strict security boundaries (IAM Permission Boundary, WAF, KMS, Security Hub).
* Build scalable inter-network architectures (Transit Gateway, VPC Peering) and establish highly reliable backup plans (AWS Backup).

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| :--- | :--- | :--- | :--- | :--- |
| **Mon** | **Resource Governance:**<br>- Manage resources in groups with Tag and Resource Groups.<br>- Manage EC2 service access with Tag through IAM. | 05/11/2026 | 05/11/2026 | AWS Study Group |
| **Tue** | **Management & Automation:**<br>- Service management and task automation using AWS Systems Manager.<br>- Connect securely via AWS Systems Manager - Session Manager.<br>- Initialize Infrastructure as Code with AWS CloudFormation. | 05/12/2026 | 05/12/2026 | AWS Study Group |
| **Wed** | **Identity Security:**<br>- Set Single Sign-On (Amazon SSO / Identity Center) for the Organization.<br>- Limit User Permissions with IAM Permission Boundary.<br>- Limiting Role Transfer by Condition. | 05/13/2026 | 05/13/2026 | AWS Study Group |
| **Thu** | **Advanced Security:**<br>- Key Management with Key Management Service (AWS KMS).<br>- Securing Applications and APIs with Web Application Firewall (AWS WAF).<br>- Check security benchmarks with AWS Security Hub. | 05/14/2026 | 05/14/2026 | AWS Study Group |
| **Fri** | **System Reliability:**<br>- Implement a system backup plan with AWS Backup to ensure data durability. | 05/15/2026 | 05/15/2026 | AWS Study Group |
| **Sat** | **Advanced Networking:**<br>- Linking Virtual Private Clouds (VPCs) with VPC Peering.<br>- Centrally manage connections with AWS Transit Gateway. | 05/16/2026 | 05/16/2026 | AWS Study Group |

### Week 4 Achievements:

* **Automation & IaC:** Mastered provisioning infrastructure programmatically using CloudFormation rather than manual web console clicks. Effectively utilized Systems Manager (Session Manager) for secure instance connectivity without exposing port 22 or managing SSH keys.
* **Security & Identity:** Comprehended multi-layered security concepts. Established maximum permission caps using IAM Permission Boundary and SSO. Gained practical ability to protect real-world applications using WAF and encrypt sensitive data with KMS.
* **Reliability & Backup:** Leveraged AWS Backup for automated scheduling, ensuring the architecture is highly resilient and capable of Disaster Recovery.
* **Advanced Networking:** Progressed beyond isolated designs by building complex network topologies. Successfully interlinked multiple VPCs using Peering and centralized routing via Transit Gateway—a highly sought-after engineering skill.