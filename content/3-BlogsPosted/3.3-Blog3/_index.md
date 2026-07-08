---
title: "Blog 3"
date: 2026-07-08
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---


# HOW CRESCONET REDUCED THEIR AWS BILL BY OVER 40% WITHOUT SACRIFICING PERFORMANCE

One of the biggest challenges when operating large-scale cloud systems is balancing cost, scalability, and reliability. As applications grow, cloud spending can increase rapidly if the architecture isn't continuously optimized.

CrescoNet, a leading provider of smart metering solutions in Australia, faced this exact challenge. Processing more than 4.5 billion smart meter readings every day, the company needed to scale its data platform while keeping operational costs under control.

Instead of simply reducing resources, CrescoNet worked closely with AWS to optimize every layer of its architecture. The result was impressive: more than a 40% reduction in overall AWS costs, with an 80% reduction in costs for their meter-to-cash data pipeline, all without compromising performance or reliability.

Key optimization strategies
Using data to identify optimization opportunities

Before making any architectural changes, CrescoNet analyzed AWS Cost and Usage Reports (CUR), Amazon QuickSight dashboards, Prometheus, and Grafana metrics to identify where money was actually being spent.

Rather than relying on assumptions, every optimization was validated using real operational data.

Migrating from AWS Glue to Amazon EMR on EKS

AWS Glue was an excellent starting point because of its serverless architecture and ease of use.

However, as workloads continued to grow, CrescoNet migrated their ETL pipeline to Amazon EMR on Amazon EKS, allowing them to:

Take advantage of Amazon EMR runtime optimizations.
Use Amazon EC2 Spot Instances for significant compute savings.
Gain greater control over Kubernetes-based infrastructure.

This migration alone reduced ETL compute costs by more than USD $50,000 per month.

Reducing Amazon S3 request costs with Apache Iceberg

Although Amazon S3 storage itself was relatively inexpensive, CrescoNet discovered that GET and PUT request charges were significantly higher than storage costs because millions of small files were being created.

By adopting Apache Iceberg and regularly compacting small files into larger ones, they achieved:

A 27× reduction in S3 request costs.
Faster query performance.
More efficient storage management.
Optimizing AWS Lambda

CrescoNet runs over 110 million Lambda invocations every month.

Using Amazon CloudWatch metrics, they identified Lambda functions that were either oversized or running outdated runtimes.

By upgrading from Python 3.8/3.9 to Python 3.11 and right-sizing memory allocations, Lambda execution time decreased by approximately 30%, reducing both execution time and overall compute costs.

Managing DynamoDB storage with Time to Live (TTL)

Not all application data requires low-latency storage forever.

By enabling Amazon DynamoDB Time To Live (TTL) for older records and moving less frequently accessed data into their data lake, CrescoNet achieved:

A 66% reduction in DynamoDB storage.
Approximately $3,000 per month in storage savings.
Around 10% lower write throughput costs.
Optimizing Amazon MSK

Amazon Managed Streaming for Apache Kafka (MSK) forms the backbone of CrescoNet's streaming platform.

Two key optimizations included:

Enabling Tiered Storage to reduce message retention costs while improving scalability.
Consolidating multiple non-production Kafka clusters into shared environments to reduce broker costs.
Batch processing Amazon SQS messages

Instead of sending individual SQS requests, CrescoNet compressed and batched multiple messages together.

This simple optimization reduced the total number of SQS requests dramatically, lowering Amazon SQS costs by more than 20 times.

Using Amazon RDS Reserved Instances

After analyzing long-term database usage, CrescoNet purchased Amazon RDS Reserved Instances (RI) with size flexibility.

This allowed them to significantly reduce database costs while retaining the flexibility to resize instances within the same family.

Automatically shutting down non-production environments

Development and testing environments often remain running even when nobody is using them.

By implementing the AWS Instance Scheduler, CrescoNet automatically shut down non-production workloads outside business hours, reducing unnecessary compute and database expenses without affecting developers.

Practical perspective

One of the biggest lessons from CrescoNet's journey is that cloud cost optimization isn't about using fewer AWS services—it's about using them more efficiently.

Rather than making one large architectural change, CrescoNet continuously monitored usage, identified inefficiencies, and optimized each service individually. Small improvements across compute, storage, messaging, streaming, databases, and serverless workloads combined to produce substantial long-term savings.

This case study also demonstrates that improving cloud cost efficiency often goes hand in hand with better scalability, operational performance, and system reliability.

Original article:

https://aws.amazon.com/blogs/aws-cloud-financial-management/how-cresconet-optimized-their-architecture-and-reduced-their-aws-bill-by-over-40/

Conclusion

CrescoNet's success highlights the importance of adopting a data-driven approach to cloud cost optimization. By continuously analyzing workloads and selecting the right AWS services for each use case, the company reduced its AWS bill by more than 40% while simultaneously improving performance, scalability, and operational resilience.

For organizations running large-scale cloud workloads, this case study serves as an excellent example that meaningful cost savings don't necessarily come from reducing infrastructure—they come from designing smarter architectures and continuously optimizing them over time.

![ Blog 3](/images/Blog3.png)