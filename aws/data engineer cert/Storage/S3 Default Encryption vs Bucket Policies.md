SSE-S3 encryption is automatically applied to new objects stored in S3 bucket.

Optionally, you can "force encryption" using a bucket policy and refuse any API call to PUT an S3 object without encryption headers (SSE-KMS or SSE-C).

>[!NOTE]
>Bucket policies are evaluated before "Default Encryption"

