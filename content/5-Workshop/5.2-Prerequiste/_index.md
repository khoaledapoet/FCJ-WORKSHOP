---
title : "Prerequisites"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### 1. AWS Account & Permissions (IAM)
To fully deploy the services in the PawVerse architecture (VPC, EC2, RDS, CloudFront, WAF, etc.), you must use an AWS account with the highest administrative privileges (**AdministratorAccess**) or the sandbox account provided by the FCAJ program.

![IAM Administrator Access](/images/5-Workshop/5.2-Prerequisite/iam.png)
*Figure 5.2.1: Ensure the AWS account has sufficient permissions to provision infrastructure resources.*

#### 2. Deployment Region
To minimize network latency for users in Vietnam and ensure consistent service operation, all core resources (VPC, EC2, RDS) will be deployed in the **Singapore (ap-southeast-1)** region. Note that CloudFront and WAF operate as Global services.

![Select Singapore Region](/images/5-Workshop/5.2-Prerequisite/region.png)
*Figure 5.2.2: Select the ap-southeast-1 (Singapore) region on the AWS Console.*

#### 3. Application Source Code Preparation
The PawVerse system has been pre-packaged to facilitate automated deployment:
+ **Backend:** The Spring Boot/Golang source code has been built into a Docker Image and is readily hosted on Docker Hub (`khoaledapoet/pawverse-backend:latest`).
+ **Frontend:** The ReactJS interface has been compiled into static assets (HTML, CSS, JS) ready for Amazon S3 upload.

#### 4. Required Tools
+ A modern web browser (Chrome, Edge, Firefox).
+ (Optional) **AWS CLI** installed and configured via `aws configure` to support automated resource querying if needed.
+ **Apache Benchmark (ab)** or **Postman** installed on your local machine to execute Load Testing at the end of this Lab.