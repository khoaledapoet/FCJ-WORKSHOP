---
title : "CloudTrail Auditing"
date : 2026-07-08
weight : 4
chapter : false
pre : " <b> 5.7.4. </b> "
---

#### System API Auditing via AWS CloudTrail
While CloudWatch functions as the health monitoring system, CloudTrail acts as the definitive security camera, logging all human and system-level behaviors. CloudTrail records all AWS API calls, allowing Operations Engineers to precisely trace *Who* performed *What* action, *Where*, and *When*. This is a mandatory compliance standard in enterprise architectures.

1. Navigate to the **AWS CloudTrail** console, select **Trails** from the left pane ---> click **Create trail**.
2. **Trail name:** `pawverse-management-trail`.
3. **Storage location:** Select *Create new S3 bucket* (AWS will automatically provision a dedicated, secure bucket for audit logs). Retain default KMS encryption configurations. Click **Next**.
4. **Choose log events:** Check **Management events** (Capturing infrastructure modifications such as EC2 provisioning or Security Group alterations).
5. Scroll down, click **Next**, review the configurations, and click **Create trail**.
6. To audit historical operations, navigate to the **Event history** tab. Every infrastructure adjustment executed during this Workshop (e.g., VPC creation, EC2 scaling, WAF configurations) is meticulously logged, detailing the executor's IAM identity and origin IP address.

![CloudTrail Event History](/images/5-Workshop/5.7-Monitoring/cloudtrail-logs.png)
*Figure 5.7.4.1: CloudTrail Event History interface capturing comprehensive infrastructure audit trails to enforce operational transparency.*