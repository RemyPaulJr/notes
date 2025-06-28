User-Based
- IAM Policies - authorize which API calls should be allowed for a specific user from IAM
Resource-Based
- Bucket Policies - bucket wide rules you can assign from the S3 console - allow specific user or user from other accs to access (cross account)
- Object Access Control List (ACL) - finer grain (can be disabled)
- Bucket Access Control List (ACL) - less common (can be disabled)

> [!NOTE]
> an IAM principal can access an S3 object if:
> The user IAM permissions allow it or the resource policy allows it
> and there's no explicit deny

Encryption
- encrypt objects in Amazon S3 using encryption keys

S3 Bucket Policies
- JSON based policies
	- Resources: bu