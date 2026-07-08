---
title : "Configure Auto Scaling"
date : 2026-07-07
weight : 3
chapter : false
pre : " <b> 5.5.3. </b> "
---

#### Establishing Elastic Compute Clusters (Auto Scaling Group)
The Auto Scaling Group (ASG) manages cluster resilience and lifecycle tasks. It continuously monitors system degradation vectors, initiates immediate replacement routines if a node drops out of the network matrix, and handles cluster expansions to accommodate fluid user demand waves.

1. From the EC2 Dashboard, choose **Auto Scaling Groups** from the lower section of the left pane ---> click **Create Auto Scaling group**.
2. **Auto Scaling group name:** `pawverse-app-asg`.
3. **Launch template:** Link the standardized `pawverse-app-template` blueprint defined in module 5.5.1. Click **Next**.
4. **Network settings:**
   + **VPC:** Assign to the target architecture `pawverse-vpc`.
   + **Availability Zones and subnets:** Exclusively choose the specific **2 Private EC2 Subnets** (Do not bind to public WAN or database tiers). This layout encapsulates application processing logic away from directly exposed routes. Click **Next**.
5. **Configure advanced options:**
   + Under the **Load balancing** parameter box, check **Attach to an existing load balancer**.
   + Select your active target interface pool: `pawverse-app-tg`.
   + Under **Health checks**, add an extra check parameter by selecting **Elastic Load Balancing (ELB)** to sync instance eviction alerts with load balancer endpoint drops. Click **Next**.
6. **Configure group size and scaling policies:**
   + **Desired capacity:** `2` *(Ensuring an active cluster state distributed over parallel nodes to handle traffic redundancy)*.
   + **Minimum capacity:** `2`.
   + **Maximum capacity:** `5` *(Capping peak system scale boundaries to mitigate structural resource budget overruns during anomaly event cycles)*.

![Configure ASG Capacity](/images/5-Workshop/5.5-Compute-ALB/asg-capacity.png)
*Figure 5.5.3.1: Defining resource scaling capacity threshold parameters for the PawVerse application cluster.*

7. Click **Next** through standard tags and settings configurations, then finalize by clicking **Create Auto Scaling group**. The system immediately reads the template directives to automate the initialization of the first 2 EC2 nodes.