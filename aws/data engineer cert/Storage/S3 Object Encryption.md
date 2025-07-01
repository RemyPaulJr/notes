- you can encrypt objects in S3 buckets using one of 4 methods
- Server-Side Encryption (SSE)
	- Server-Side Encryption with Amazon S3-Managed Keys (SSE-S3) - enabled by default
		- encrypts s3 objects using keys handled, managed, and owned by AWS
	- Server-Side Encryption with KMS Keys stored in AWS KMS (SSE-KMS)
		- Leverage AWS Key Management service (AWS KMS) to manage encryption keys
	- Server-Side Encryption with Customer-Provided Keys (SSE-C)
		- When you want to manage your own encryption keys
- Client-Side Encryption
- It's important to understand which ones are for which scenario for the exam
---
Server-Side Encryption with Amazon S3-Managed Keys SSE-S3
- encryption using keys handled, managed, and owned by AWS
- object is encrypted server-side
- encryption type is AES-256
- must set header "x-amz-server-side-encryption": "AES256"
- enabled by default for new buckets & new objects
---
Server-Side Encryption with KMS Keys stored in AWS KMS (SSE-KMS)
- encryption using keys handled and managed by AWS KMS
- advantage is user control + audit key usage using CloudTrail
- object is encrypted server side
- header "x-amz-server-side-encryption": "aws:kms"
- Limitations
	- you may be impacted by the KMS limits
	- when you upload, it calls the GenerateDataKey KMS API
	- when you download, it calls the Decrypt KMS API
	- counts towards the KMS quota per second (5500,10000,3000 req/s based on region)
	- you can request a quota increase using the Service Quotas Console
---
Server-Side Encryption with Customer-Provided Keys (SSE-C)
- Server-Side Encryption using keys fully managed by the customer outside of AWS
- Amazon S3 does not store the encryption key you provide
- HTTPS must be used
- Encryption key must be provided in HTTP headers, for every HTTP request made
---
Client-Side Encryption
- use client libraries such as Amazon S3 Client-Side Encryption Library
- clients must encrypt data themselves before sending to Amazon S3
- clients must decrypt data themselves when retrieving from Amazon S3
- customer fully manages the keys and encryption cycle
---
Encryption in transit (SSL/TLS)
- encryption in flight is also called SSL/TLS
- amazon s3 exposes two endpoints:
	- HTTP Endpoint - non encrypted
	- HTTPS Endpoint - encryption in flight
- HTTPS is recommended
- HTTPS is mandatory for SSE-C
- Most clients would use the HTTPS endpoint by default
---
>[!NOTE] Must enable versioning on the bucket to edit the encryption and change it later on, as editing the encryption type creates a new version of the existing object/s
