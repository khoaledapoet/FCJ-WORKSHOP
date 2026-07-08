---
title : "Provision Launch Template"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.5.1. </b> "
---

#### Standardizing the Compute Blueprint (Launch Template)
A Launch Template operates as an immutable blueprint. When the architecture demands horizontal expansion or triggers a replacement for an unhealthy node, the Auto Scaling Group references this configuration matrix to instantly instantiate uniform compute configurations.

1. Navigate to the **EC2 Dashboard**, select **Launch Templates** from the left pane ---> click **Create launch template**.
2. **Launch template name:** `pawverse-app-template`.
3. **Application and OS Images (AMI):** Select the default **Amazon Linux 2023 AMI** (Engineered for optimal cloud performance and security configurations).
4. **Instance type:** Select standard `t3.micro` or `t4g.micro` computing sizes to manage environment execution budgets.
5. **Key pair:** Link your existing cryptographic Key pair to maintain secure backup administrative bridge connectivity.
6. **Network settings:**
   + Set Subnet options to **Don't include in launch template** (Subnet assignment topologies will be managed by the Auto Scaling logic subsequently).
   + **Security Groups:** Bind the dedicated application security boundary, ensuring internal runtime application ports (e.g., `8080` or `3000`) exclusively accept inbound flows routed via the Application Load Balancer.
7. **Advanced Details:**
   + **IAM instance profile:** Explicitly bind the trusted machine role profile identified as **`lab`** audited in previous security labs.
   + **User data:** Inject the following structural automation shell script into the configuration container block. This sequence triggers under `root` execution rights upon node boot phase:

```bash
#!/bin/bash
# 1. Update OS repositories and install required operational packages
dnf update -y
dnf install -y jsonfilter jq awscli wget

# 2. Package acquisition and extraction for PawVerse Backend
mkdir -p /app && cd /app
# Emulating production artifact deployment pull sequence
wget -O pawverse-backend [https://github.com/thienluhoan/fcj-workshop/raw/main/artifacts/backend-app](https://github.com/thienluhoan/fcj-workshop/raw/main/artifacts/backend-app)
chmod +x pawverse-backend

# 3. Dynamic Runtime Credentials extraction from AWS Secrets Manager
REGION="ap-southeast-1"
SECRET_RAW=$(aws secretsmanager get-secret-value --secret-id pawverse-prod-secrets --region $REGION --query SecretString --output text)

# Parse raw JSON structures into active OS environment parameters
export DB_USER=$(echo $SECRET_RAW | jq -r '.DB_USER')
export DB_PASS=$(echo $SECRET_RAW | jq -r '.DB_PASS')
export JWT_SECRET=$(echo $SECRET_RAW | jq -r '.JWT_SECRET')

# Map the active infrastructure internal Endpoint properties here
export DB_HOST="pawverse-mysql.cpseu6iqs3oe.ap-southeast-1.rds.amazonaws.com"
export REDIS_HOST="clustercfg.pawverse-redis.ckq3fs.apse1.cache.amazonaws.com"

# 4. Initiate standalone background daemon execution loop
nohup ./pawverse-backend > /var/log/pawverse.log 2>&1 &
```

![Configure Launch Template](/images/5-Workshop/5.5-Compute-ALB/launch-template.png)
![Configure Launch Template](/images/5-Workshop/5.5-Compute-ALB/launch-template1.png)
*Figure 5.5.1.1: Binding the 'lab' IAM Role configuration and injecting the automated User Data bootstrap shell script.*

8. Click **Create launch template** to finalize the compute standardization blueprint.