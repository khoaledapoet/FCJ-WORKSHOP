---
title : "Performance Metrics"
date : 2026-07-08
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

#### Visualizing System Telemetry
Metrics provide real-time situational awareness regarding resource consumption across the stack. We will aggregate the most critical telemetric data from our dispersed infrastructure into a unified Single Pane of Glass dashboard.

1. Navigate to the **Amazon CloudWatch** console, select **Dashboards** ---> click **Create dashboard**.
2. Name the dashboard `PawVerse-Production-Dashboard`.
3. Click **Add widget** ---> Select **Line** chart ---> **Metrics**.
4. **Advanced EC2 CPU Telemetry (via CWAgent):**
   + Instead of default EC2 metrics, we leverage the high-fidelity data streamed by the CloudWatch Agent provisioned in step 5.5.
   + Under Custom Namespaces, select `CWAgent` ---> `AutoScalingGroupName, InstanceId, cpu`.
   + Check the `cpu_usage_active` metric for the `pawverse-app-asg` cluster. This visualization delivers granular insights into core compute utilization. Click **Create widget**.
5. **Monitor Load Balancer Traffic (ALB):**
   + Add a new widget ---> Click **All** (Navigate to root namespaces) ---> `ApplicationELB` ---> `Per AppELB Metrics`.
   + Select the `pawverse-prod-alb` entity and check the `RequestCount` metric (Tracking active inbound client requests).
6. **Monitor Database Tier (RDS):**
   + Add a new widget ---> `RDS` ---> `Per-Database Metrics`.
   + Select the `pawverse-mysql-db` instance, checking `DatabaseConnections` (Ensuring database connection pools remain within safe thresholds).

![CloudWatch Dashboard](/images/5-Workshop/5.7-Monitoring/cw-metrics.png)
*Figure 5.7.1.1: The centralized monitoring dashboard integrating in-depth OS-level telemetry via CWAgent alongside network services.*