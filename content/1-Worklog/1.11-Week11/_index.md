---
title: "Week 11 Report"
date: 2026-07-05
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:
* Deploy the Edge Layer to globally distribute the static web UI.
* Completely mitigate CORS errors leveraging CDN Proxy architectures.
* Erect Application Layer firewalls to actively defend against malicious payloads.

### Tasks Executed:

| Day | Tasks Carried Out | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| **Mon** | **Static Hosting (S3):**<br>- Provisioned Amazon S3 Buckets hosting the PawVerse Frontend source code.<br>- Enforced absolute lockdown via the "Block all public access" configuration. | 06/29/2026 | 06/29/2026 |  |
| **Tue** | **CDN Distribution (CloudFront):**<br>- Provisioned a CloudFront Distribution to act as the global CDN network.<br>- Configured Origin Access Control (OAC) to cryptographically grant CloudFront read permissions over S3. | 06/30/2026 | 06/30/2026 |  |
| **Wed** | **Intelligent Routing:**<br>- Injected the ALB as the 2nd Origin within CloudFront.<br>- Established Behaviors to split traffic: `/api/*` routed to ALB, default wildcard routed to S3. | 07/01/2026 | 07/01/2026 |  |
| **Thu** | **Edge Security (WAF):**<br>- Activated the AWS WAF engine attached directly to the CloudFront distribution.<br>- Enforced AWS Managed Rules to automatically block malicious IP profiles. | 07/02/2026 | 07/02/2026 |  |
| **Fri** | **Database Protection:**<br>- Fine-tuned WAF rules, injecting SQL Injection shields to heavily fortify the internal RDS architecture. | 07/03/2026 | 07/03/2026 |  |

### Achievements:
* **Page Load Optimization:** The Frontend UI is successfully cached across global CloudFront Edge Locations, minimizing network latency for end-users worldwide.
* **Absolute Perimeter Security:** The architecture strictly prohibits direct client requests against S3 and EC2. The WAF engine operates as an active shield executing Deep Packet Inspection, dropping SQL Injection vectors aiming for the database.