User-Based
- IAM Policies - authorize which API calls should be allowed for a specific user from IAM
Resource-Based
- Bucket Policies - bucket wide rules you can assign from the S3 console - allow specific user or user from other accounts to access (cross account)
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
	- Resources: buckets and objects
	- Effect: Allow / Deny
	- Actions: Set of API to Allow or Deny
	- Principle: The account or user to apply the policy to
- Use S3 bucket for policy to:
	- Grant public access to the bucket
	- Force objects to be encrypted at upload
	- Grant access to another account (cross account)
- There are bucket settings for Block Public Access
	- These settings were created to prevent company data leaks
	- If you know your bucket should never be public, leave these on
	- Can be set at the account level