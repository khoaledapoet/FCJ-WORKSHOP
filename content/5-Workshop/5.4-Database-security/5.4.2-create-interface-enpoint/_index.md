---
title : "Deploy Database"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.4.2. </b> "
---

#### 1. Provision RDS DB Subnet Group
To ensure compute redundancy and isolate the storage engine from public access routers, we must aggregate our dedicated internal database subnets.

1. Open the **Amazon RDS console**, select **Subnet groups** from the left-hand navigation pane ---> click **Create DB subnet group**.
2. **Name:** `pawverse-db-subnet-group`.
3. **VPC:** Select the designated `pawverse-vpc`.
4. **Availability Zones:** Select both `ap-southeast-1a` and `ap-southeast-1b`.
5. **Subnets:** Carefully select the 2 specific CIDR blocks belonging to the isolated `Private DB Subnet` tier mapped in the networking lab.

![Create RDS Subnet Group](/images/5-Workshop/5.4-Database-Security/rds-subnet.png)
*Figure 5.4.2.1: Clustering distinct Private DB subnets to enforce storage layer encapsulation.*

6. Click **Create**.

#### 2. Provision Amazon RDS MySQL Instance
1. Navigate to the **Databases** tab --> click **Create database**.
2. **Database creation method:** Select **Standard create**.
3. **Engine options:** Select **MySQL**.
4. **Templates:** Choose **Free Tier** or **Dev/Test** to eliminate unnecessary operational lab expenses.
5. **Settings:**
   + **DB instance identifier:** `pawverse-mysql-db`.
   + **Master username:** `pawverse`.
   + **Master password:** `pawverse123Secret` *(Must correspond 100% with the keys declared in the secure vault)*.
6. **Instance configuration:** Select the scalable `db.t3.micro` instance class tier.
7. **Connectivity:**
   + Bind to the `pawverse-vpc` architecture.
   + **DB Subnet group:** Link the newly mapped `pawverse-db-subnet-group`.
   + **Public access:** Explicitly enforce **No** *(Strictly blocking inbound traffic origin vectors from the public Internet)*.
8. Scroll to the footer and click **Create database**. The initialization sequence takes approximately 3 to 5 minutes to complete.