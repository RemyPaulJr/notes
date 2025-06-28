- You can version your files in Amazon S3.
- It is enables at the bucket level
- same key overwrite will change the "version": 1,2,3....
- it is best practice to version your buckets
	- protects against unintended deltes (ability to restore a version)
	- easy to roll back to a previous version
>[!NOTE]
>Any file that is not versioned prior to enabling versioning wil