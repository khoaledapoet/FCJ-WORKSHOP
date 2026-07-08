---
title : "Monitoring & Alarms"
date : 2026-07-08
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

#### Operational Observability via Amazon CloudWatch
A robust Cloud architecture must not only function reliably but also possess self-reporting diagnostic capabilities. Without an observability framework, system engineers operate entirely blind to critical failure vectors such as CPU bottlenecks, memory exhaustion, or silent application crashes.

This principle drove our decision to actively inject the **CloudWatch Agent** into the EC2 bootstrap sequence (Section 5.5). This agent acts as a telemetry daemon, continuously streaming runtime application logs and hardware performance metrics back to the centralized control plane.

In this concluding chapter, we will configure an operational dashboard focusing on 3 core pillars:
1. **Metrics:** Visualizing the health signatures of EC2 (CPU, Network I/O), ALB (Request metrics), and RDS (Database connection pools).
2. **Centralized Logs:** Remotely auditing the Spring Boot Backend application traces without requiring direct SSH node access.
3. **Proactive Alarms:** Configuring automated threshold triggers designed to dispatch Email/SMS notifications during anomalous CPU spikes or system overload events.