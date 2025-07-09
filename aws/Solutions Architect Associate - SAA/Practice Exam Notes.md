#### **S3**
- Amazon S3 always returns the latest version of the object.

---
#### **EC2**
-  solution with the LEAST amount of development effort for email notifications and notifications on CPU Utilization on EC2 instances
	- Amazon Simple Notification Service (SNS) - fully managed pub/sub messaging service that enables you to decouple microservices, distributed systems, and serverless applications. Amazon SNS provides topics for high-throughput, push-based, many-to-many messaging.
	- CloudWatch - Amazon CloudWatch provides you with data and actionable insights to monitor your applications, respond to system-wide performance changes, optimize resource utilization, and get a unified view of operational health.

---
#### **cost-optimization solution**
- startup is incurring costs that seem too high for their business requirements. cloud infrastructure consists of a few Amazon EC2 instances, Amazon RDS instances and Amazon S3 storage.
	- Use AWS Cost Explorer Resource Optimization to get a report of Amazon EC2 instances that are either idle or have low utilization and use AWS Compute Optimizer to look at instance type recommendations.
		- AWS Cost Explorer helps you identify under-utilized Amazon EC2 instances that may be downsized on an instance
		- Optimizer recommends optimal AWS Compute resources for your workloads to reduce costs and improve performance by using machine learning to analyze historical utilization metrics.

---
#### **Amazon Kinesis Data Streams (KDS)**
- big data analytics company is using Amazon Kinesis Data Streams (KDS) to process IoT data from the field devices of an agricultural sciences company. consumer applications are using the incoming data streams and the engineers have noticed a performance lag for the data delivery speed between producers and consumers of the data streams.
	- Use Enhanced Fanout feature of Amazon Kinesis Data Streams
		- 