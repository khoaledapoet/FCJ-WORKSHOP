---
title : "Live Demo & Reflection"
date : 2026-07-12
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

To conclude the Cloud infrastructure deployment journey, below are real-world visual proofs demonstrating the success of the PawVerse project. Accompanying these are critical technical reflections the team has gathered throughout operating the system on AWS.

### 1. Live Showcase

The PawVerse system is currently operating seamlessly 100% on the Cloud environment, distributed via a global CloudFront domain with ultra-low latency.

**Home & Shopping Cart - Edge Layer Speed Experience:**
The static interface and client-side computational logic are rendered almost instantly. Customers can experience smooth shopping, cart additions, and discount applications thanks to the power of Edge Caching.

![PawVerse Homepage](/images/home.png)
*Figure 5.8.1: PawVerse homepage with near-zero load time powered by Amazon S3 & CloudFront.*

![PawVerse Cart](/images/cart.png)
*Figure 5.8.2: Shopping cart interface handling high-speed logic directly in the browser.*

**Admin Gate & Dashboard - Compute Layer Power:**
Beyond static content, the Admin module proves that the dynamic API data flow operates perfectly. Product data, revenue charts, and order quantities are fetched directly from the Database via the Load Balancer (ALB) and EC2 architecture.

![Product Management Page](/images/product.png)
*Figure 5.8.3: Product management module loading real data from the RDS Database.*

![Admin Dashboard](/images/dashboard.png)
*Figure 5.8.4: Dashboard displaying business overview (Successful Backend API integration).*

---

### 2. Reflection

In the process of building the architecture from scratch to a fully functional Production system, we encountered various real-world technical challenges and formulated definitive solutions.

#### Challenges Encountered
1. **Cross-Origin Resource Sharing (CORS) Error:** When the Frontend (hosted on S3) attempted to call the API to fetch data from the Backend (hosted on ALB), the browser immediately blocked the request due to different Origins, preventing the Admin page data from displaying.
2. **Persistent CDN Caching Mechanism:** Upon updating new Frontend code to Amazon S3, users were still seeing the old interface. This occurred because CloudFront stores cache copies at Edge Locations for up to 24 hours by default.
3. **AWS WAF Configuration:** We faced difficulties in correctly identifying the Web Application Firewall (WAF) Region when attaching it to CloudFront, causing the firewall to fail during initial tests.

#### Solutions Implemented
1. **Smart Routing Planning (Behaviors):** Instead of loosening CORS policies, we utilized CloudFront as an intermediary Proxy. We routed the `/api/*` path to the Backend (ALB) and the `Default (*)` path to the Frontend (S3). Both utilize the same domain name, thereby fundamentally resolving CORS errors in the most secure manner possible.
2. **Proactive Cache Invalidation:** We established a routine of executing the `Create Invalidation /*` command on the CloudFront console immediately after uploading new source code to S3, forcing the system to clear the cache and serve the latest interface to users instantly.
3. **Adhering to the Global Principle:** By mastering system knowledge, we ensured that the AWS WAF Web ACL must be provisioned in the **Global (Asia Pacific - Singapore)** region to successfully integrate as a protective shield for CloudFront.

#### Future Development Roadmap
The current system successfully meets baseline standards for High Availability and Security. However, to prepare for larger enterprise scales, the project targets the following upgrades:
* **CI/CD Automation:** Integrate GitHub Actions so that whenever developers push new code, the system automatically builds and uploads it to S3/EC2, alongside triggering an automated CloudFront Invalidation command.
* **Application Modernization (Containerization):** Transition the Backend source code from running directly on EC2 instances to Docker containers managed by **Amazon ECS** or **Amazon EKS**, further optimizing resource utilization.
