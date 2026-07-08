---
title : "Centralized Logs"
date : 2026-07-08
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

#### Remote Application Log Auditing
When an architecture scales horizontally across multiple parallel nodes (Auto Scaling), utilizing SSH to manually audit individual machine logs becomes an anti-pattern. Instead, our pre-configured CloudWatch Agent ingests all raw Spring Boot container logs and streams them to a unified aggregation point.

1. On the left navigation pane of CloudWatch, expand **Logs** ---> select **Log groups**.
2. Locate the designated Log Group matching the SSM parameter configuration (e.g., `/aws/ec2/pawverse-backend` or the associated agent configuration name).
3. Open the Log Group to view the underlying **Log streams** - each stream perfectly correlates to an individual active EC2 compute node.
4. Open any active Log stream. The entire Docker and Spring Boot console output (spanning bootstrap initialization, Database connection verifications, and HTTP 403/500 stack traces) is rendered chronologically.

![CloudWatch Log Streams](/images/5-Workshop/5.7-Monitoring/cw-logs.png)
*Figure 5.7.2.1: Retrieving and analyzing internal Spring Boot application traces via the centralized log management console.*