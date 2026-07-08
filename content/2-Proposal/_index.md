---
title : "Project Proposal"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### 1. Executive Summary
The PawVerse project is designed to resolve network performance and infrastructure security bottlenecks for a pet products e-commerce platform. The system is built with a Multi-AZ architecture on AWS, integrating strict network administration standards. The platform utilizes Auto Scaling to automatically expand EC2 server clusters during traffic spikes, integrates Amazon ElastiCache to optimize product data retrieval, and isolates data flows securely within Private Subnets. PawVerse ensures High Availability, low latency, and operational cost optimization.

#### 2. Current Problem
Basic e-commerce platforms often deploy static infrastructure and store source code together with security credentials (hard-coded). During promotional events, traffic spikes cause CPU/RAM resource exhaustion and database connection overloads. Additionally, the lack of a Content Delivery Network (CDN) and application-layer firewall makes the website slow in various regions and highly vulnerable to DDoS or botnet attacks, resulting in severe revenue loss.

#### 3. Solution & ROI
**Solution:** The platform deploys a 3-Tier architecture on AWS VPC. Network traffic is distributed by an Application Load Balancer (ALB) to the Auto Scaling Group. Static content is globally distributed via CloudFront, while product data is cached in Amazon ElastiCache (Redis) to offload the database. Amazon RDS acts as the core storage. Crucially, AWS WAF and Secrets Manager are deeply integrated to block malicious traffic and fully automate connection string management.
**ROI:** The solution provides a true Pay-as-you-go cost model: only paying for resources spun up during peak times. Automating monitoring and hiding security credentials minimizes operational risks, perfectly meeting the strict standards of an Enterprise Cloud Operations environment.

#### 4. Solution Architecture
The system applies a distributed Multi-AZ architecture. User requests are first inspected via WAF and accelerated by CloudFront. API traffic passes through the Internet Gateway into the Virtual Private Cloud (VPC), directed by the ALB. Compute capacity automatically scales based on CloudWatch monitoring metrics. All servers and core data are strictly protected inside Private Subnets, communicating internally via VPC Endpoints and outbound via NAT Gateways.

![diagram](/images/2-Proposal/diagram.png)

#### 5. AWS Services Used
+ **Amazon EC2 & Auto Scaling:** Process business logic and scale automatically.
+ **Application Load Balancer (ALB):** Distribute dynamic access traffic.
+ **Amazon RDS:** Manage core relational databases.
+ **Amazon ElastiCache:** Cache product data.
+ **AWS WAF & CloudFront:** Distribute global content and block attacks.
+ **Amazon S3:** Host static Frontend source code.
+ **AWS Secrets Manager & KMS:** Manage and encrypt passwords automatically.
+ **Amazon CloudWatch, CloudTrail & SNS:** Monitor, audit, and alert the system.
+ **VPC, NAT & Internet Gateway:** Manage network routing and Subnets.

#### 6. Technical Implementation
The project is divided into 4 main phases:
+ **Network & Security Design:** Configure VPC, divide Public/Private Subnets, setup Security Groups and VPC Endpoints.
+ **DB & Caching Deployment:** Provision Amazon RDS, ElastiCache, and set up the AWS Secrets Manager vault.
+ **Compute & Load Balancing Config:** Set up EC2 Launch Templates (integrating automated Secrets decryption in User Data), configure ALB and Auto Scaling.
+ **Edge Layer & Monitoring:** Deploy S3, CloudFront (with OAC), enable WAF, and configure CloudWatch monitoring and SNS alerts.

#### 7. Roadmap & Milestones
+ **Month 1:** Analyze requirements, design the overall architecture diagram, and deploy the core VPC network.
+ **Month 2:** Provision the data tier, security cache, and deploy the EC2 cluster along with the ALB.
+ **Month 3:** Configure the global CDN (CloudFront), WAF firewall, and set up the Auto Scaling system.
+ **Month 4:** Conduct Load Testing, perform security auditing, and write the technical acceptance report.

#### 8. Budget Estimation
The practical process maximizes the use of AWS Free Tier resources. Estimated costs for non-Free Tier services:
+ **NAT Gateway:** ~0.045 USD/hour.
+ **Application Load Balancer:** ~0.0225 USD/hour.
+ **AWS WAF:** ~5.00 USD/month.
+ **AWS Secrets Manager:** ~0.40 USD/secret/month.
**Total Lab Budget:** Approx 10 - 15 USD (Strictly controlled by deleting resources immediately after Demo and Testing).

#### 9. Risk Assessment
+ **Risks:** Network communication flaws causing components to fail to connect (High); Over budget due to uncontrolled Auto Scaling expansion (Medium).
+ **Mitigation:** Apply the Principle of Least Privilege for IAM Roles and Security Groups. Block all external SSH (port 22) access. Set a hard limit (Max capacity) for the Auto Scaling Group and setup AWS Billing Alarms via Email.

#### 10. Expected Outcomes
The system smoothly handles thousands of concurrent requests without crashing. Completely resolves security barriers by ensuring no passwords are hard-coded into the source code. Presents a highly valuable practical Use-case, clearly demonstrating system design thinking, network administration, and professional Cloud operation capabilities.