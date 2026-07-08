---
title : "Routing & Associations"
date : 2026-07-07
weight : 3
chapter : false
pre : " <b> 5.3.3. </b> "
---

#### Step 1: Configure Routing
We define the "destinations" for each route table.

1. **Public Route Table (`pawverse-rtb-public`):**
   + **Routes** tab -> **Edit routes** -> Add `0.0.0.0/0` pointing to the **Internet Gateway**.
   ![Public Route](/images/5-Workshop/5.3-vpc-network/public-route.png)
   *Figure 5.3.3.1: Routing public traffic out via the Internet Gateway.*

2. **Private Route Table (`pawverse-rtb-private`):**
   + **Routes** tab -> **Edit routes** -> Add `0.0.0.0/0` pointing to the **NAT Gateway**.
   ![Private Route](/images/5-Workshop/5.3-vpc-network/private-route.png)
   *Figure 5.3.3.2: Routing private traffic out via the NAT Gateway.*

#### Step 2: Configure Subnet Associations
With routes defined, we must "associate" the Subnets with the correct route tables.

1. **Public Subnet Association:**
   + In `pawverse-rtb-public` -> **Subnet associations** tab -> **Edit subnet associations**.
   + Check the 2 **Public Subnets**.
   ![Public Assoc](/images/5-Workshop/5.3-vpc-network/public-assoc.png)
   *Figure 5.3.3.3: Associating Public Subnets with the Public route table.*

2. **Private Subnet Association:**
   + In `pawverse-rtb-private` -> **Subnet associations** tab -> **Edit subnet associations**.
   + Check all 4 **Private Subnets**.
   ![Private Assoc](/images/5-Workshop/5.3-vpc-network/private-assoc.png)
   *Figure 5.3.3.4: Associating all Private Subnets with the Private route table.*

> **💡 Note:** Skipping this step forces Subnets to use the VPC's Main Route Table, leading to critical network configuration errors.