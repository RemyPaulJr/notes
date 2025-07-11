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
### **AWS Direct Connect**
- is a networking service that provides an alternative to using the internet to connect to AWS Services. Data is delivered through a private network between on-premises data center and AWS.

---
#### **Amazon RDS**
- We have EC2 web based servers that use RDS PostgreSQL as the data store. How can we encrypt the data in transit.
	- Using SSL/TSL - RDS creates and installs the SSL certificate when the DB instance is provisioned.

---
#### **AWS Certificate Manager (ACM)**
- Certificates created in ACM are automatically renewed.
- Certificates imported into ACM:
	- To notify before expiration data:
		- AWS Config - provides detailed view of AWS resources