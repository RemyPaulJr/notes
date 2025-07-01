Define ways to access buckets and prefix. 

Access Points simplify security management for S3 buckets.
Each Access Point has:
- its own DNS name (Internet Origin or VPC Origin)
- an access point policy (similar to bucket policy) - allows you to manage security at scale
---
Access Points - VPC Origin

We can define them to be accessible only from within the VPC
