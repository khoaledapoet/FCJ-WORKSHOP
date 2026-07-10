---
title : "CloudFront Distribution"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.6.2. </b> "
---

#### Content Delivery Network (CDN) - The Heart of the Edge Layer
Amazon CloudFront not only enables blazing-fast website loading through global caching but also acts as a smart Proxy. It merges both the Frontend (S3) and Backend (ALB) traffic under a single domain name, completely resolving Cross-Origin Resource Sharing (CORS) errors.

1. Navigate to **Amazon CloudFront**, click **Create Distribution**.
2. **Origin 1 (S3 Frontend Origin):**
   + **Origin domain:** Select the newly created S3 Bucket `pawverse-frontend-production-bucket`.
   + **Origin access:** Select **Origin access control settings (OAC)**. Click *Create control setting*. This configuration generates a special Policy allowing CloudFront to "pierce through" the S3 Block Public Access wall.
3. **Default Cache Behavior:**
   + **Viewer protocol policy:** Select **Redirect HTTP to HTTPS** (Enforce security encryption).
   + **Allowed HTTP methods:** Select `GET, HEAD`.
4. Scroll down and click **Create Distribution**. Make sure to copy the newly generated *S3 Bucket Policy* and paste it back into the S3 Permissions configuration.
5. **Origin 2 (ALB Backend Origin):**
   + Go back to the created Distribution, switch to the **Origins** tab ---> Click **Create origin**.
   + **Origin domain:** Select the Application Load Balancer domain name (`pawverse-prod-alb...`).
   + **Protocol:** Check `HTTP only` and click Create.
6. **Smart Routing (Behaviors):**
   + Switch to the **Behaviors** tab ---> Click **Create behavior**.
   + **Path pattern:** Enter `/api/*`. 
   + **Origin:** Select the second origin, the ALB Backend.
   + **Allowed HTTP methods:** Expand to `GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE`. Click Create.

![CloudFront Behaviors Routing](/images/5-Workshop/5.6-EdgeLayer/cloudfront-behaviors.png)
*Figure 5.6.2.1: Smart routing configuration, separating the API traffic to the Load Balancer and static traffic to S3.*

#### Step 7: Admire the System Results (Show off)
At this point, all routing configurations are complete. It's time to enjoy the fruits of our labor!

1. In the CloudFront management console, under the **General** tab, locate the **Distribution domain name** line.
2. Copy and paste the domain `d34pgctiih4me1.cloudfront.net` into your web browser.


![PawVerse Result on CloudFront](/images/5-Workshop/5.6-EdgeLayer/pawverse-cloudfront-result.png)
*Figure 5.6.2.2: The PawVerse application interface running smoothly via the CloudFront global distribution URL.*