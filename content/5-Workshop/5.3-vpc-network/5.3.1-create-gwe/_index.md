---
title : "VPC & Internet Gateway"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### 1. Provision Virtual Private Cloud (VPC)
We will use the **VPC and more** wizard to automate the blueprinting of our core network infrastructure.

1. Navigate to the **VPC Dashboard**, click **Create VPC** -> Select the **VPC and more** option.
2. **Name tag:** `pawverse`.
3. **IPv4 CIDR block:** `10.0.0.0/16`.
4. **Availability Zones (AZs):** Select **2** (`ap-southeast-1a` and `1b`) to ensure High Availability redundancy.
5. **Subnets:** Configure **2 Public subnets** (for the ALB) and **4 Private subnets** (for EC2 instances and Databases).

![Provision VPC](/images/5-Workshop/5.3-vpc-network/vpc.png)
*Figure 5.3.1.1: Configuring network ranges and subnetting for the PawVerse project.*

#### 2. Verify Internet Gateway (IGW)
The Internet Gateway is the sole "doorway" allowing the VPC to communicate with the external Internet. Although the wizard auto-generates it, a Cloud Engineer must always verify its attachment status.

1. On the left VPC menu, select **Internet gateways**.
2. Locate the IGW named `pawverse-igw`.
3. Check the **State** column; it must be **Attached** to the `pawverse-vpc`. If it is Detached, select *Actions -> Attach to VPC*.

![Verify IGW](/images/5-Workshop/5.3-vpc-network/igw.png)
*Figure 5.3.1.2: Confirming the Internet Gateway is successfully attached to the VPC.*