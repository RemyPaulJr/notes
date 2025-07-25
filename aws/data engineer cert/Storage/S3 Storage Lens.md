- Understand, analyze, and optimize storage across entire AWS Org
- Discover anomalies, identify cost efficiencies, and apply data protection best practices across entire AWS org (30 days usage & activity metrics)
- Aggregate data for Org, specific accs, regions, buckets, or prefixes
- Default dashboard or create your own dashboards
- Can be configured to export metrics daily to an S3 bucket (CSV, Parquet)
---
Default Dashboard
- Visualize summarized insights and trends for both free and advanced metrics
- Default dashboard shows Multi-Region and Multi-Account data
- Preconfigured by Amazon S3
- Can't be deleted, but can be disabled
---
Metrics
- Summary Metrics
	- General insights about your S3 storage
	- StorageBytes, ObjectCount...
	- Use Cases: identify fastest-growing (or not used) buckets and prefixes
- Cost-Optimization or Metrics
	- Provide insights to manage and optimize your storage costs
	- NonCurrentVersionStorageBytes, IncompleteMultipartUploadStorageBytes...
	- Use Cases: identify buckets with incomplete multipart uploaded older than 7 days, identify which objects could be transitioned to lower-cost storage class
- Data-Protection Metrics
	- Provide insights for data protection features
	- VersioningEnabledBucketCount, MFADeleteEnabledBucketCount, SSEKMSEnabledBucketCount, CrossRegionReplicationRuleCount...
	- Use Cases: identify buckets that aren't following data-protection best practices
