---
title: "Week 10 Worklog"
date: 2026-06-27
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:

* Begin the Implementation phase for the Capstone Project: **Serverless Feedback Pipeline**.
* Provision the NoSQL database and establish API communication endpoints.
* Develop core processing logic and set up an automated notification system.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| :--- | :--- | :--- | :--- | :--- |
| **Mon** | **Database Provisioning:**<br>- Provision Amazon DynamoDB tables to store user feedback.<br>- Configure Partition Keys and necessary Indexes. | 06/22/2026 | 06/22/2026 | AWS Docs |
| **Tue** | **API Gateway Setup:**<br>- Set up Amazon API Gateway as the entry point for the system.<br>- Configure HTTP methods (POST/GET) to receive payload from the Frontend. | 06/23/2026 | 06/23/2026 | AWS Docs |
| **Wed** | **Lambda Function Development:**<br>- Develop Backend code for AWS Lambda to process incoming feedback.<br>- Assign IAM roles granting Lambda permissions to write to DynamoDB. | 06/24/2026 | 06/24/2026 | AWS Docs |
| **Thu** | **Integration & Testing:**<br>- Integrate API Gateway with the Lambda function (Lambda Proxy Integration).<br>- Perform API testing using Postman (API Gateway -> Lambda -> DynamoDB). | 06/25/2026 | 06/25/2026 | AWS Docs |
| **Fri** | **Notification System:**<br>- Configure Amazon SNS to create notification Topics.<br>- Update Lambda code to trigger SNS and send emails upon new feedback submission. | 06/26/2026 | 06/26/2026 | AWS Docs |
| **Sat** | **End-to-End Testing:**<br>- Conduct end-to-end testing of the entire data pipeline.<br>- Log bugs and optimize the backend source code. | 06/27/2026 | 06/27/2026 | AWS Docs |

### Week 10 Achievements:

* **Practical Infrastructure Deployment:** Successfully translated the architecture diagram into active AWS resources. Established seamless data flow from API Gateway to Lambda.
* **Serverless Backend Processing:** Effectively wrote processing logic to handle payloads and securely store them in DynamoDB.
* **Notification System:** Completed real-time email notification capabilities via SNS, ensuring administrators are alerted immediately when new user feedback is submitted, meeting core project requirements.