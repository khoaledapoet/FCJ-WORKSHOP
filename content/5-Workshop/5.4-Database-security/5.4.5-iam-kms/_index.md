---
title : "IAM & KMS Security"
date : 2026-07-07
weight : 5
chapter : false
pre : " <b> 5.4.5. </b> "
---

#### 1. Data Encryption at Rest Architecture (AWS KMS)
The storage components deployed via Secrets Manager and the RDS relational clusters refuse to preserve system details in raw plaintext formats. To safeguard business entities against physical data breaches inside AWS infrastructure facilities, robust Server-Side Encryption (Encryption at Rest) is enforced.

Upon the deployment of `pawverse-prod-secrets`, the system encapsulates parameters using the **AWS Key Management Service (KMS)** layer. By utilizing the default managed encryption alias key `aws/secretsmanager`, any baseline data extraction attempts executed by unauthenticated system entities failing key validation will yield only scrambled, indecipherable binary streams.

![KMS Encryption](/images/5-Workshop/5.4-Database-Security/kms-key.png)
*Figure 5.4.5.1: Encryption configurations integrating native AWS KMS keys to reinforce data tier confidentiality.*

#### 2. Enforcing Least-Privilege Identity via IAM Roles
To mitigate access credential theft risks and implement the **Principle of Least Privilege**, compute nodes must never store or hard-code long-term AWS Root or IAM User Access Keys/Secret Keys within application parameters. Instead, EC2 nodes dynamically lease short-term cryptographic credentials by executing commands under an assigned **IAM Role** profile.

For this functional deployment phase, we leverage a pre-provisioned trusted machine role profile identified as **`lab`**. Audit validations confirm this role wraps 4 essential cloud operation management policies:
+ **`SecretsManagerReadWrite`**: Empowers the containerized backend logic to perform runtime API invocations to retrieve and decrypt database structural properties securely upon container bootstrap sequence.
+ **`AmazonSSMManagedInstanceCore`**: Grants Cloud Operations personnel secure interactive console shell access via Systems Manager Session Manager interface, entirely eliminating the requirement to expose high-risk traditional SSH network ports (Port 22).
+ **`CloudWatchAgentServerPolicy`**: Authorizes system monitoring daemons to securely pipe local event logs and OS-level compute performance data (CPU usage, RAM overhead percentage) directly to the centralized CloudWatch observability pipeline.

![IAM Role lab](/images/5-Workshop/5.4-Database-Security/iam-role.png)
*Figure 5.4.5.2: Comprehensive permission policies mapped to the active 'lab' IAM Role bound to the compute layer.*