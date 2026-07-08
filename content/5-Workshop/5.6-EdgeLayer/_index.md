---
title : "Edge Layer & Delivery"
date : 2026-07-07
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### Edge Delivery & Security Layer

If the VPC, EC2 nodes, and Databases constitute the core "internal organs" of the PawVerse platform, the Edge Layer acts as the protective outer perimeter, serving as the initial touchpoint for millions of global customers.

In modern cloud architecture, end-users are strictly prohibited from establishing direct connections to backend processing servers. Instead, all inbound traffic flows must traverse the Edge Layer to undergo speed optimization and malicious payload filtering routines.

In the final chapter of this Workshop, we will execute 3 deployment sequences:
1. **S3 Static Hosting:** Provision a low-cost, ultra-durable (99.999999999%) storage bucket to host the static Frontend UI artifacts (React/Vue/HTML).
2. **CloudFront Content Delivery (CDN):** Cache UI assets across global Edge Locations to minimize network latency, while unifying both Frontend and Backend traffic pipelines under a single cohesive domain.
3. **Web Application Firewall (AWS WAF):** Establish an active perimeter defense that inspects individual packets, neutralizing DDoS vectors, SQL Injections, and Cross-Site Scripting (XSS) attacks before they can penetrate the core VPC infrastructure.