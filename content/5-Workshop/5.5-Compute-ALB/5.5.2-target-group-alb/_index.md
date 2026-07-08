---
title : "Setup Load Balancer"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.5.2. </b> "
---

#### 1. Provision Target Group
Before initializing the load balancer layer, we must construct a logical group abstraction that encapsulates target compute resources and dictates target node Health Check evaluations.

1. From the EC2 Dashboard, scroll to **Load Balancing** ---> select **Target Groups** ---> click **Create target group**.
2. **Target type:** Choose **Instances**.
3. **Target group name:** `pawverse-app-tg`.
4. **Protocol & Port:** Select **HTTP** and define your active application runtime binding port (e.g., `8080`).
5. **VPC:** Map to the core `pawverse-vpc`.
6. **Health checks:** Retain standard HTTP protocols, mapping the baseline verification path to `/` or modify to match system endpoints (e.g., `/health`). Click **Next**.
7. Bypass direct structural node registrations (The Auto Scaling cluster logic automates node lifecycle tracking subsequently). Click **Create target group**.

#### 2. Deploy Application Load Balancer (ALB)
The Application Load Balancer represents our primary routing sentinel positioned at the edge of the Public Subnet tier, receiving WAN traffic spikes and intelligently routing packages down to secure computing nodes.

1. Select the **Load Balancers** navigation node ---> click **Create load balancer**.
2. Locate the **Application Load Balancer** template card ---> click **Create**.
3. **Load balancer name:** `pawverse-prod-alb`.
4. **Scheme:** Enforce **Internet-facing** *(Accepting public external connections over the standard WAN network interface)*.
5. **Network mapping:**
   + Select the underlying target VPC: `pawverse-vpc`.
   + **Mappings:** Check both active Availability Zones, explicitly assigning traffic entry paths to the mapped **2 Public Subnets**. This enables public internet accessibility routers.

![ALB Network Configuration](/images/5-Workshop/5.5-Compute-ALB/alb.png)
*Figure 5.5.2.1: Mapping routing and subnet topologies to the Application Load Balancer interface.*

6. **Security Groups:** Bind the dedicated ALB security framework, opening public interface ingress parameters (allowing HTTP Port `80` and HTTPS Port `443` access profiles to global vectors `0.0.0.0/0`).
7. **Listeners and routing:** Under the default HTTP:80 Listener profile, map the forward action rule to distribute traffic directly to the newly provisioned target pool **`pawverse-app-tg`**.
8. Scroll to the bottom and click **Create load balancer**.