---
title : "Frontend S3 Hosting"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.6.1. </b> "
---

#### Provisioning UI Storage (Amazon S3)
Static Frontend assets such as HTML, CSS, JavaScript files, and images do not require EC2 compute capabilities. Therefore, hosting them on Amazon S3 represents the most secure and cost-effective architectural approach.

1. Navigate to the **Amazon S3 console**, and click **Create bucket**.
2. **Bucket name:** Define a globally unique identifier (e.g., `pawverse-frontend-production-bucket`).
3. **AWS Region:** Select `ap-southeast-1` (Singapore).
4. **Block Public Access settings for this bucket:** 
+ Contrary to basic S3 hosting tutorials, we will **KEEP the "Block all public access" checkbox ENABLED**. 
   + Rationale: We strictly forbid direct client access to the S3 bucket. Only the CloudFront CDN network will be granted specialized read permissions to access these assets, ensuring absolute perimeter security.
5. Retain all default parameters and click **Create bucket**.
6. Open the newly provisioned Bucket, select the **Objects** tab ---> click **Upload**. Upload all compiled production artifacts of the PawVerse Frontend project (including the core `index.html` file and `css`, `js`, `assets` directories).

![S3 Frontend Hosting](/images/5-Workshop/5.6-EdgeLayer/s3-bucket.png)
*Figure 5.6.1.1: Static source code artifacts uploaded to S3 while strictly enforcing the Not Public access barrier.*