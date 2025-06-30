Moving between Storage Classes
- You can transition objects between storage classes
- For infrequently accessed objects, move them to Standard IA
- For archive objects that you don't need fast access to, move them to Glacier or Glacier Deep Archive
- Moving Objects can be automated using Lifecycle Rules

Lifecycle Rules
- Transition Actions - configure objects to transition to another storage class
	- Move objects to Standard IA class 60 days after creation
	- And move to Glacier for archiving after 6 months
- Expiration Actions - configure objects to expire/delete after specified time
	- Access log files can be set to delete after 365 days
	- can be used to delete old version of files if versioning is enabled
	- can be used to delete incomplete multi-part uploads (if parts of the upload is 2 weeks old delete because it should have been uploaded with this time frame)
- Rules can be created for certain prefix
	- s3:*//mybucket/mp3/*
- Rules can be created for specific object tags
	- *Department: Finance*

Amazon S3 Analytics - Storage Class Analysis
- Helps you decide when transition objects to the right storage class
- Recommendations for Standard and Standard IA
	- Does not work for One-Zone IA or Glacier
- Report is updated daily
- 24 to 48 hours to start seeing data analysis
- Good first step to put together Lifecycle Rules (or improve them)