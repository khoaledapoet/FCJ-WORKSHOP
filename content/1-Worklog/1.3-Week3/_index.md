---
title: "Week 3 Worklog"
date: 2026-05-08
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Integrate AI assistant (AWS Kiro) into the development process.
* Manage, allocate, and optimize AWS costs combined with resource tagging (Tag/Resource Groups).
* Practice infrastructure migration (VM & Database), establish visual monitoring with Grafana, and automate server startup/shutdown workflows.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| :--- | :--- | :--- | :--- | :--- |
| **Mon** | **Generative AI for Builders:**<br>- Understand the impact of Gen AI (AWS Kiro) on SDLC and Spec-driven development methods.<br>- Familiarize with Kiro IDE, Kiro CLI, and the Kiro Power ecosystem. | 04/05/2026 | 04/05/2026 | Module 01-03 Gen AI on AWS - Kiro |
| **Tue** | **Cost Optimization & Resource Management:**<br>- Research cost optimization strategies: Right-sizing, Spot Instances, Reserved/Savings Plans.<br>- Practice: Manage resources and allocate costs centrally using Tags and Resource Groups. | 05/05/2026 | 05/05/2026 | Module 01-04 Cost optimization on AWS |
| **Wed** | **Infrastructure & Database Migration:**<br>- Migrate virtual servers from local environments to the cloud.<br>- Convert schemas and migrate databases. | 06/05/2026 | 06/05/2026 | [Reference 1](https://000014.awsstudygroup.com/)<br>[Reference 2](https://000043.awsstudygroup.com/) |
| **Thu** | **Advanced System Monitoring:**<br>- Integrate CloudWatch data into Grafana to build visual dashboards.<br>- Set up real-time system health tracking. | 07/05/2026 | 07/05/2026 | [Reference 1](https://000029.awsstudygroup.com/) |
| **Fri** | **Cost Optimization via Automation:**<br>- Apply cost optimization lessons practically by writing automated functions to shut down servers outside working hours.<br>- Set up alerts and status notifications via Slack. | 08/05/2026 | 08/05/2026 | [Reference 1](https://000022.awsstudygroup.com/) |

### Week 3 Achievements:

* **Gen AI Integration:** Understood AWS Kiro's capabilities in coding assistance, CI/CD automation via terminal, and Spec-driven application building.
* **Cost Governance & Optimization:** Effectively applied FinOps theories (reducing resource waste) practically. Utilized Tagging techniques to organize resources, ensuring accurate cost measurement on AWS Budgets per project/department.
* **Migration:** Mastered the workflow of packaging local virtual servers and successfully importing them to Amazon EC2. Configured AWS DMS and SCT to ensure data integrity during database conversion.
* **Automation & Visual Monitoring:** Overcame CloudWatch Dashboard limitations by integrating Grafana. Successfully programmed AWS Lambda with Webhooks to automatically shut down EC2 systems for cost savings and report directly to the Slack chat application.