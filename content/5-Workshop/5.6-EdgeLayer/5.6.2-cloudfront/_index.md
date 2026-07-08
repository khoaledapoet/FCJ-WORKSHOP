---
title : "CloudFront Delivery"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.6.2. </b> "
---

#### Content Delivery Network (CDN) - The Core of the Edge
Amazon CloudFront not only accelerates page load speeds via global edge caching but also functions as an intelligent Proxy architecture. It consolidates both Frontend (S3) and Backend (ALB) traffic pipelines under a unified domain footprint, completely mitigating Cross-Origin Resource Sharing (CORS) security exceptions.

1. Navigate to **Amazon CloudFront**, click **Create Distribution**.
2. **Origin 1 (S3 Frontend Target):**
   + **Origin domain:** Select the newly created `pawverse-frontend-production-bucket`.
   + **Origin access:** Enforce **Origin access control settings (OAC)**. Click *Create control setting*. This generates a cryptographic policy allowing CloudFront to bypass the S3 Block Public Access barrier.
3. **Default Cache Behavior:**
   + **Viewer protocol policy:** Select **Redirect HTTP to HTTPS** (Enforcing SSL/TLS encryption).
   + **Allowed HTTP methods:** Restrict to `GET, HEAD`.
4. Scroll to the bottom and click **Create Distribution**. Ensure you copy the generated *S3 Bucket Policy* and inject it back into the S3 Permissions configuration tab.
5. **Origin 2 (ALB Backend Target):**
   + Return to the active Distribution, navigate to the **Origins** tab ---> click **Create origin**.
   + **Origin domain:** Select the Application Load Balancer endpoint (`pawverse-prod-alb...`).
   + **Protocol:** Enforce `HTTP only` and click Create.
6. **Intelligent Routing (Behaviors):**
   + Switch to the **Behaviors** tab ---> click **Create behavior**.
   + **Path pattern:** Define `/api/*`. 
   + **Origin:** Map this path to the 2nd origin (the Backend ALB).
   + **Allowed HTTP methods:** Expand to `GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE`. Click Create.

![CloudFront Routing Behaviors](/images/5-Workshop/5.6-EdgeLayer/cloudfront-behaviors.png)
*Figure 5.6.2.1: Intelligent routing configurations splitting dynamic API payloads to the Load Balancer and static assets to S3.*