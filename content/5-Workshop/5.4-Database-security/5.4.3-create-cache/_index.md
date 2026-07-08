---
title : "Provision Redis Cache"
date : 2026-07-07
weight : 3
chapter : false
pre : " <b> 5.4.3. </b> "
---

#### Accelerating Performance via Amazon ElastiCache Redis
During high-volume e-commerce spikes, concurrent users fetching product catalogs generate thousands of duplicate query loops. Forcing the primary relational DB engine to process disk I/O routines continuously results in catastrophic performance degradation. We deploy an in-memory database tier using Amazon ElastiCache Redis inside Private Subnets to mitigate heavy read constraints.

1. Open the **Amazon ElastiCache console**, navigate to **Redis OSS clusters** ---> click **Create Redis OSS cluster**.
2. **Cluster deployment option:** Choose **Design your own cluster** and enforce **Cluster mode enabled** to optimize data scalability and flexible sharding.
3. **Cluster info:** Identify the cluster as `pawverse-redis`.
4. **Location:** Select AWS Cloud environment, choosing the high-performance, cost-effective Node type tier `cache.t4g.micro`.
5. **Connectivity:**
   + Bind to the target `pawverse-vpc`.
   + Select the cache Subnet Group containing our internal **Private Subnets**.
6. To safeguard internal data traffic, Encryption in transit is enabled to fulfill corporate information security compliance.

![ElastiCache Redis Cluster](/images/5-Workshop/5.4-Database-Security/elasticache-redis.png)
*Figure 5.4.3.1: The operational Redis cache node cluster showing its status active and ready.*

7. Click **Create**. Once the environment state transitions to a healthy **Available** status, record the **Configuration Endpoint** address string (which acts as the centralized routing entry point when Cluster mode is active). This endpoint parameter will be dynamically passed to the EC2 application environment parameters later to activate distributed application caching.