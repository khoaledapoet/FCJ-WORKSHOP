---
title : "Resource Cleanup"
date : 2026-07-08
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

#### Cost Management and Resource Decommissioning (FinOps)
Congratulations on successfully architecting the AWS infrastructure! The final and most critical rule of Cloud Computing is **Clean Up**. To prevent incurring unintended ongoing charges after concluding this Workshop, you must decommission all provisioned resources.

Please execute the deletion process in the exact outside-in sequence outlined below to prevent Dependency Errors:

#### 1. The Edge Layer
1. **CloudFront:** CDN state changes take time to propagate. Select your Distribution ---> click **Disable**. Wait 3-5 minutes until the status reflects *Disabled*, then you can safely click **Delete**.
2. **S3 Bucket:** Navigate to Amazon S3, select the Frontend Bucket. You must click **Empty** (to purge all underlying objects) first, before the system allows you to click **Delete** bucket.
3. **WAF:** Navigate to AWS WAF, select Web ACLs ---> Choose `pawverse-waf-protection` and click **Delete**.

#### 2. The Compute Layer
1. **Auto Scaling Group (ASG):** Access EC2 ---> Auto Scaling Groups ---> Select `pawverse-app-asg` and click **Delete**. This action automatically triggers the termination of all underlying EC2 instances.
2. **Load Balancer (ALB):** Navigate to Load Balancers ---> Select `pawverse-prod-alb` and click **Delete**. Proceed to **Target Groups** and delete `pawverse-tg`.
3. **Launch Templates:** Access Launch Templates, select the created template ---> Actions ---> **Delete template**.

#### 3. Database & Monitoring Tiers
1. **RDS:** Navigate to Amazon RDS ---> Databases ---> Select `pawverse-mysql-db` ---> Actions ---> **Delete**. (Note: Uncheck *Create final snapshot* and check the *Acknowledge* box to enforce permanent deletion).
2. **Secrets Manager:** Delete the `pawverse-prod-secrets` vault (It will be scheduled for permanent deletion following a 7-day retention period).
3. **CloudWatch & CloudTrail:** Delete the `CPU overload` Alarm within CloudWatch, and delete the `pawverse-management-trail` within CloudTrail.

#### 4. The Network Layer
1. **VPC:** Access Amazon VPC ---> Your VPCs ---> Select `PawVerse-VPC` ---> Actions ---> **Delete VPC**. 
*(AWS intelligence will automatically sweep and decommission all associated Subnets, Route Tables, and Internet Gateways attached to this VPC).*

**Completed!** You have thoroughly sanitized your account environment and are now prepared for future production-grade deployments. See you at the pinnacle of Cloud Computing!