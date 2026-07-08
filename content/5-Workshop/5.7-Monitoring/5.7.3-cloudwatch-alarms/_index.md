---
title : "Alarms & Alerting"
date : 2026-07-08
weight : 3
chapter : false
pre : " <b> 5.7.3. </b> "
---

#### Triggering Automated Incident Response
To instruct the Auto Scaling Group when to dynamically provision additional nodes, and to immediately notify Site Reliability Engineers (SREs) of midnight anomalies, we construct an Alarm matrix utilizing AWS SNS (Simple Notification Service).

1. Navigate to the **Alarms** section within CloudWatch ---> select **All alarms** ---> click **Create alarm**.
2. **Select metric:** Navigate to `EC2` ---> `By Auto Scaling Group` ---> Select `CPUUtilization` for the `pawverse-app-asg` cluster.
3. **Conditions:**
   + Threshold type: **Static**.
   + Operator: **Greater/Equal (>=)**
   + Define value: `80` (Triggers if the cluster CPU footprint hits 80% saturation).
4. **Configure actions:**
   + Under the **Notification** block, select *Create new topic*.
   + Define Topic name: `PawVerse-Alerts`.
   + **Email endpoints:** Input your administrative Email address to receive diagnostic threat alerts.
   + Click *Create topic*. (Note: You must access your Email inbox and confirm the AWS Subscription link to authorize message delivery).
5. Click **Next**, naming the Alarm `PawVerse-High-CPU-Alert`.
6. Click **Create alarm**. Moving forward, the PawVerse architecture is completely self-sufficient, capable of automating both observability tracking and critical incident response protocols!

![CloudWatch Alarm Creation](/images/5-Workshop/5.7-Monitoring/cw-alarm.png)
*Figure 5.7.3.1: Proactive alerting mechanism configured to dispatch Email notifications to administrators when compute loads breach safety parameters.*