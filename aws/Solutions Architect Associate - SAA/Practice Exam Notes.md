#### **S3**
- Amazon S3 always returns the latest version of the object.

---
#### **EC2**
- User data
	- User data is a script or file that **by default**:
		- runs as root user
		- and runs only on first boot when launching an instance
	- My definition - specifies what to do when an instance is first launched (download package, updates), and CAN BE configured to run each time a instance is launched.