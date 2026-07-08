---
title : "NAT Gateway & Endpoint"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

#### 1. Setup NAT Gateway for Private Subnets
EC2 instances in Private Subnets lack Public IPs, meaning they cannot route through the Internet Gateway. To allow them to securely download updates (outbound only, no inbound), we use a NAT Gateway.

1. Select **NAT Gateways** -> **Create NAT gateway**.
2. Place the NAT Gateway in `pawverse-subnet-public1-ap-southeast-1a` (It must reside in a Public Subnet).
3. Click **Allocate Elastic IP** to assign a static IP.

![Create NAT Gateway](/images/5-Workshop/5.3-vpc-network/nat-gateway.png)
*Figure 5.3.2.1: Provisioning a NAT Gateway for one-way outbound Internet access.*

#### 2. Optimization via S3 Gateway Endpoint
If EC2 pushes files to Amazon S3 via the NAT Gateway, the data loops through the public Internet, incurring bandwidth charges. An S3 Gateway Endpoint creates a direct internal "tunnel" within AWS.

1. From the VPC Dashboard, select **Endpoints** -> **Create endpoint**.
2. Name tag: `pawverse-s3-endpoint`.
3. Search for `s3` and select **`com.amazonaws.ap-southeast-1.s3`** (Type: **Gateway**).

![Configure S3 Gateway Endpoint](/images/5-Workshop/5.3-vpc-network/s3-endpoint.png)
*Figure 5.3.2.2: Selecting the S3 Gateway Endpoint service in the ap-southeast-1 region.*

4. Select the `pawverse-vpc`, check the **Private Route Tables** for automatic routing, and click **Create endpoint**.