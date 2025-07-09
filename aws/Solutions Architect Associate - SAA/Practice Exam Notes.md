#### **S3**
- Amazon S3 always returns the latest version of the object.
- Speed up uploading large file globally:
	- Muiltipart Upload - improved throughput

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