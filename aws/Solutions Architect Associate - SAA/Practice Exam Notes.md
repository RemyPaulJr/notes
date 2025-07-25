#### **S3**
- Amazon S3 always returns the latest version of the object.
- Speed up uploading large file globally:
	- Muiltipart Upload - upload single object into multiple parts, improving throughput. faster file uploads
	- Amazon S3 Transfer Acceleration (Amazon S3TA) - Takes advantage of Cloudfront's global distribution and edge locations to optimize transfer speed.
- Fast way to stream existing and new files from S3 to Amazon Kinesis Data Streams (KDS):
	- Amazon Database Management (DMS) to act as a bridge between S3 and KDS by migrating data from source (S3) into KDS.
- One-time transfer of 1 petabyte of data to another S3 bucket in a different region:
	- S3 Sync - Copies latest version of object to from source bucket to target bucket, by comparing what's in the source bucket and not in the target bucket (command).
	- Batch Replication then delete the configuration after - allows you to copy objects that existed before replication was enabled
- Adequate protection against accidental delete of S3 objects
	- Bucket versioning - keeping multiple variants of an object, means you can retrieve an object in the case of accidental delete.
	- MFA on delete - user must provide secondary authentication to perform a delete action.
- See who is making changes to a bucket:
	- Cloudtrail to analyze API calls - CloudTrail is great for governance, security, and monitoring. Provides details logs of calls made to S3.
- 5 PB data transfer from on-premise to AWS Cloud:
	- One time transfer
	- Durable long term storage
	- Most cost optimal way:
		- Multiple AWS Snowball Edge Storage Optimized devices, to copy to S3 bucket and use lifecycle policy to move to Glacier Storage
			- Cannot directly copy from Snowball Edge Storage to Glacier Storage.

---
#### **EC2**
- User data
	- User data is a script or file that **by default**:
		- runs as root user
		- and runs only on first boot when launching an instance
	- My definition - specifies what to do when an instance is first launched (download package, updates), and CAN BE configured to run each time a instance is launched.
- Amazon Elastic Block Store (EBS Volumes)
	- Regarding Security
		- EBS Volumes are encrypted.
			- This includes:
				- Data at rest.
				- Data moving between volume and instance.
				- Snapshots of the volume.
- Reboot Ec2 instance:
	- In case of ec2 instance failure need manually restarts. to automate we can use CloudWatch Alarms to monitor the health status. And in case of a failure (instance stop), we can use **CloudWatch EC2 Reboot Alarm Action** to stop and start the instance.
- Placement Groups:
	- Spread Placement Group:
		- Has a max of 7 instances per AZ.
		- Meant to spread out instances on distinct hardware.
		- reduces the risk of simultaneous failures that might occur when instances share the same racks.
		- can span multiple AZs in the same Region.

---
#### **GuardDuty**
- Analyzes data sources from VPC logs, CloudTrail events, Domain Name System (DNS) logs.
- Used to detect malicious activity on data stored in S3.

---
#### **Simple Queue Service (SQS)**
- Convert from standard SQS to FIFO (First-in-First-out).
	- Migration Checklist:
		- Messages cannot exceed 3000 messages per second.
		- File names must end with .fifo suffix.
		- Delete old standard queue and recreate it as a FIFO queue.

---
#### **IAM Access**
- Org wants to provide access to another AWS account for its users. How?
	- Create IAM role with access they need and assign to users.

---
#### **Amazon ElastiCache for Redis/Memcached**
- Use to take load off of Relational and NoSQL DBs.
- Blazing fast, and supports caching results of SQL queries.
- In-memory db.
- HIPAA Eligible.
- Highly Available.

---
#### **Amazon Kinesis Data Streams (KDS)**
- Company wants to build custom applications that process and analyze streaming data for its specialized needs.
	- Kinesis is the choice here as kinesis is used for rapidly moving data off producers, and continuously processing the data for things like analytics. 

---
#### **Amazon Redshift**
- Company built data warehouse in Redshift. For cost optimization they want to move any data older than a year into S3. However, analysts would like to be able to cross reference this historical data along with daily reports. What's the LEAST amount of effort and MINIMUM cost solution here?
	- Redshift Spectrum - is a layer between your Redshift tables (cluster) and Amazon S3, where you can query and retrieve data without having to load the data in your Redshift tables.

---
#### **AWS Direct Connect**
- is a networking service that provides an alternative to using the internet to connect to AWS Services. Data is delivered through a private network between on-premises data center and AWS.

---
#### **Amazon RDS**
- We have EC2 web based servers that use RDS PostgreSQL as the data store. How can we encrypt the data in transit.
	- Using SSL/TSL - RDS creates and installs the SSL certificate when the DB instance is provisioned.
- Company would like to deal with high volume of read traffic, reduce latency, and also downsize the instance size to cut costs.
	- Amazon ElastiCache in front of Amazon RDS.
		- Ideal for data stores in front of RDS, especially for high request rates and low latency requirements. Caching is minimally invasive to implement.

---
#### **AWS Certificate Manager (ACM)**
- Certificates created in ACM are automatically renewed.
- Certificates imported into ACM:
	- To notify before expiration data:
		- AWS Config - provides detailed view of AWS resources and how they interact with one another. Can use Config to check the status of the expiration.
		- AWS SNS - using Config Managed Rule on expiration can tell SNS to send a notification to email users when certificate is expiring.

---
#### **Auto-Scaling Group**
- Launch Configuration:
	- Instance configuration template that an Auto Scaling Group uses to launch EC2 instances.
	- You cannot modify a launch configuration after it's already been created.

---
#### **AWS Global Accelerator**
- Routes user traffic to optimal endpoints based off users locations, and a number of other factors like application health.
- Way of reducing latency for incoming users.

---
#### **AWS Consolidated Billing**
- Way to pay monthly fee once for a AWS Service that you have enabled across multiple AWS accounts.

---
#### **Key:Value Pair data processing and storage in AWS Cloud with high availability**
- Lambda
	- Lambda allows us to run code to process data.
- Dynamo DB
	- Great for storing Key Value pair data and is highly available.

---
#### **AWS Transit Gateway**
- Way to interconnect VPC together along with on-premises data center.
- If we have 5 VPCs and we want them to all be interconnected then we can use transit gateway.

---
#### **AWS Macie**
- Used to identify sensitive data store in S3.

---
#### **AWS VPN CloudHub**
- A way for multiple AWS site-to-site vpn connected on premises data centers to transfer communicate and not just with the VPC.
- Sites that use AWS Direct Connect connections to the virtual private gateway can also be part of the AWS VPN CloudHub.

---
#### **Amazon Global Accelerator**
- Company wants to test blue-green deployments (blue is older version of the application and green is the newer version we want to test before fully implementing), and they want to test globally within 48 hours. Their users are primarily mobile app users which are prone to DNS Caching. What can they use to test as many users as possible within the time frame?
	- Global Accelerator - this will allow you to setup both blue and green env as endpoints and route the traffic according to the weight you specify.

---
#### **Amazon Machine Image (AMI)**
- Can be used to lessen boot time of EC2 instances as it "pre-bakes" your app and all required installations into a custom AMI. When a new instance is launched, it uses the AMI with everything pre-installed.

---
#### **The Two AWS Services that support Gateway Endpoints**
- Amazon S3
- Amazon DynamoDB
https://docs.aws.amazon.com/vpc/latest/privatelink/gateway-endpoints.html
