---
title : "Alarm Testing (SNS)"
date : 2026-07-08
weight : 5
chapter : false
pre : " <b> 5.7.5. </b> "
---

#### Validating the Incident Response Pipeline
To guarantee that the CloudWatch Alarm and SNS notification mechanisms function correctly during a real crisis, we will execute an active Fault Injection test. Instead of intentionally overloading the production compute nodes, we will safely force the alarm state transition via the AWS CLI.

1. Launch the **AWS CloudShell** environment (via the Terminal icon in the upper-right corner of the AWS Console).
2. Execute the following AWS CLI command to simulate a critical CPU utilization breach, forcing the `PawVerse-High-CPU-Alert` into an active trigger state:
   ```bash
   aws cloudwatch set-alarm-state \
       --alarm-name "CPU overload" \
       --state-value ALARM \
       --state-reason "Testing SNS email integration for PawVerse Project"
   ```
3. **Expected Results:** + The Alarm status on the CloudWatch dashboard immediately transitions to a critical red **(In alarm)** state.
   + Audit the registered administrator Email inbox. You will receive an automated critical notification from `AWS Notifications` detailing the CPU threshold breach within the PawVerse infrastructure.
   + This successful validation proves that the automated Incident Response pipeline is fully operational and capable of safeguarding the system 24/7.

![SNS Email Validation](/images/5-Workshop/5.7-Monitoring/sns-email.png)
*Figure 5.7.5.1: Automated infrastructure alert successfully triggered and delivered to the administrator's inbox via AWS SNS.*