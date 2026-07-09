---
title : "Compute & Load Balancing"
date : 2026-07-07
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Compute & Traffic Orchestration Layer
With a secure network framework and an isolated data tier successfully established, we now proceed to deploy the application's runtime processing logic (Backend Application).

To meet rigorous enterprise standards for High Availability, Self-healing, and dynamic scaling during sudden traffic spikes, the PawVerse compute layer bypasses standalone, fixed servers. Instead, we architect a resilient infrastructure leveraging the combined capabilities of three core services: Launch Templates, Application Load Balancers (ALB), and Auto Scaling Groups (ASG).

In this chapter, we will sequentially execute 4 practical deployment steps:
1. **Provision Launch Template:** Define the standardized hardware blueprint and write automated bootstrap scripts (User Data).
2. **Setup Application Load Balancer:** Configure a load balancer within the Public Subnets to distribute incoming internet traffic.
3. **Configure Auto Scaling Group:** Establish a dynamically scaling server cluster isolated deep within the Private Subnets.
4. **Testing High Availability (HA & Auto Scaling Test):** Actively simulating a CPU resource exhaustion event (CPU Stress) to validate the automated scaling and self-healing capabilities of the entire infrastructure.