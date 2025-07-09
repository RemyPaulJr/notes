#### **S3**
- Amazon S3 always returns the latest version of the object.
- Speed up uploading large file globally:
	- Muiltipart Upload - upload single object into multiple parts, improving throughput. faster file uploads
	- Amazon S3 Transfer Acceleration (Amazon S3TA) - Takes advantage of Cloudfront's global distribution and edge locations to optimize transfer speed.
- Fast way to stream existing and new files from S3 to Amazon Kinesis Data Streams (KDS):
	- Amazon Database Management (DMS) to act as a bridge between S3 and KDS by migrating data from source (S3) into KDS.

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

---
#### **GuardDuty**
- Analyzes data sources from VPC logs, CloudTrail events, Domain Name System (DNS) logs.

