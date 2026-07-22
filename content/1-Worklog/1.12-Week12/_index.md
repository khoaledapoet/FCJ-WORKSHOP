---
title: "Week 12 Report"
date: 2026-07-08
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:
* Finalize the Full-stack Observability pipeline for the PawVerse platform.
* Establish automated Alarm triggers and audit trails.
* Execute financial resource management (FinOps Cleanup) and wrap up documentation.

### Tasks Executed:

| Day | Tasks Carried Out | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| **Mon** | **Metrics Monitoring:**<br>- Accessed CloudWatch and built a centralized Single Pane of Glass Dashboard.<br>- Streamed granular CPU data via CWAgent, Request Counts via ALB, and DB Connections via RDS. | 07/06/2026 | 07/06/2026 | |
| **Tue** | **Centralized Log Auditing:**<br>- Inspected Log Groups, remotely retrieving Spring Boot and Docker console traces without requiring direct EC2 SSH access. | 07/07/2026 | 07/07/2026 |  |
| **Wed** | **System Alarms:**<br>- Configured CloudWatch Alarms to trigger when EC2 CPU loads breach 80%.<br>- Integrated Amazon SNS to dispatch automated critical Emails to Administrators. | 07/08/2026 | 07/08/2026 |  |
| **Thu** | **Auditing & Fault Testing:**<br>- Activated CloudTrail to record infrastructure API actions (Audit Logs).<br>- Utilized AWS CloudShell (CLI) to force trigger the Red Alarm, validating the SNS Email pipeline. | 07/09/2026 | 07/09/2026 |  |
| **Fri** | **Reporting:**<br>- Packaged the Hugo documentation repository and submitted the final internship report. | 07/10/2026 | 07/10/2026 |  |

### Achievements:
* **Automated Telemetry:** The CloudWatch dashboard provides high-fidelity operational awareness regarding infrastructure health. The Incident Response pipeline functions flawlessly via SNS.
* **Operational Transparency:** Every architectural modification is meticulously recorded by CloudTrail, satisfying strict Security and Compliance mandates.
* **Cost Governance:** Mastered and executed resource cleanup protocols, ensuring zero unintended ongoing charges following the project deployment lifecycle.