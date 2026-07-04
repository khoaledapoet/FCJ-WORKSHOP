---
title: "Proposal"
date: 2024-07-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Go Flashsale System for E-Commerce Environment
## AWS scalable and high-load solution for flash sale events

### 1. Executive Summary
The Go Flashsale system is designed to solve network and server infrastructure bottlenecks during e-commerce events with spike traffic. The platform is built with a Golang backend, combined with a Multi-AZ architecture on AWS. The system utilizes Auto Scaling to automatically expand from 2 to dozens of EC2 servers as load increases, Amazon ElastiCache to optimize product information retrieval, and Amazon RDS with a read/write split mechanism. The platform ensures High Availability, low latency, and operational cost optimization.

### 2. Current Problem
Traditional e-commerce systems often use static infrastructure (fixed number of servers). During Flash Sale events, traffic and purchase requests spike within minutes, leading to CPU/RAM resource exhaustion, database connection overload, and system crashes. Customers are unable to access the site, causing severe revenue and reputation loss.

### 3. Solution & ROI
*   **Solution:** The platform deploys a 3-Tier architecture on AWS VPC. Network traffic is distributed by an Application Load Balancer (ALB) to the Auto Scaling Group. Static data and product information are cached in Amazon ElastiCache (Redis) to offload the database. Amazon RDS is configured with a Primary and Read Replica to separate the order writing flow and product reading flow. WAF and Secrets Manager are integrated to prevent bot attacks and secure credentials.
*   **ROI:** The solution provides a true Pay-as-you-go cost model: businesses only pay for the scaled resources during the exact 1-2 hours of the Flash Sale. Fully automating the scaling process reduces manual monitoring workload, perfectly meeting Cloud Operation environment standards.

### 4. Solution Architecture
The platform applies a Multi-AZ distributed architecture to manage large data flows. User requests are inspected via WAF before entering the Virtual Private Cloud (VPC). Compute capacity is automatically scaled based on CPU monitoring metrics. Data is strictly protected within Private Subnets.

![Flash Sale Architecture](/images/2-Proposal/flashsale_architecture.jpeg)

### 5. AWS Services Used
*   **Amazon EC2 & Auto Scaling:** Process Golang business logic.
*   **Application Load Balancer (ALB):** Distribute access traffic.
*   **Amazon RDS:** Manage transactions, Read/Write split.
*   **Amazon ElastiCache:** Cache product data.
*   **AWS WAF & CloudFront:** Distribute content and block Bots.
*   **AWS Secrets Manager:** Manage connection strings.
*   **Amazon CloudWatch & SNS:** Monitor and alert.
*   **NAT & Internet Gateway:** Manage VPC routing.

### 6. Technical Implementation
The project is divided into 4 main phases:
1.  **Network & Security Design:** Configure VPC, divide Public/Private Subnets, set up Security Groups (Weeks 1-3).
2.  **DB & Caching Deployment:** Deploy RDS, ElastiCache, set up Secrets Manager (Weeks 4-6).
3.  **Compute & Load Balancing Config:** Deploy source code to EC2, set up ALB and Auto Scaling (Weeks 7-9).
4.  **Testing & Automation:** Simulate Flash Sale requests, configure CloudWatch (Weeks 10-12).

**Requirements:** Deep understanding of networking (Subnetting, CIDR), EC2 automation using User Data, and utilizing load-test tools (minimum 5000 requests/second).

### 7. Roadmap & Milestones
*   **Month 0:** Analyze Golang source code, design architecture.
*   **Month 1:** Deploy VPC network frame, configure WAF and Database.
*   **Month 2:** Integrate ElastiCache, deploy EC2 and ALB.
*   **Month 3:** Configure Auto Scaling, conduct Load Testing, and write report.

### 8. Budget Estimation
The practice process mainly utilizes AWS Free Tier (EC2 t2.micro, RDS t3.micro). Estimated non-Free Tier costs:
*   **NAT Gateway:** ~$0.045/hour.
*   **ALB:** ~$0.0225/hour.
*   **AWS WAF:** ~$5.00/month.
*   **AWS Secrets Manager:** $0.40/secret/month.
*   **Total Lab Budget:** Approx $15 - $20/month (strictly controlled by deleting resources after Load Testing).

### 9. Risk Assessment
*   **Risks:** Security data leakage (Low probability due to Secrets Manager). Over budget due to Auto Scaling (High probability if Max limit is forgotten).
*   **Mitigation:** Apply the Principle of Least Privilege. Close SSH port (22). Set a hard limit (Max instance = 5) for Auto Scaling. Configure AWS Billing Alarms.

### 10. Expected Outcomes
The system responds to thousands of concurrent requests without crashing. Completely resolves bottlenecks by separating Database Read/Write flows and utilizing Cache. Builds a highly valuable practical Use-case, clearly demonstrating system design thinking and Cloud operation capabilities.