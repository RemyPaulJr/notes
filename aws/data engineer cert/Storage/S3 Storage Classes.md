When you create an object in S3 you can choose its class, modify it manually, or using S3 lifecycle policies to move objects automatically.

S3 Durability and Availability:
Durability:
- High Durability: 99.999999999%, 11 9's) of objects across multiple AZ
- If you store 10,000,000 objects with Amazon S3, you can on average expect to incur a loss of a single object once every 10,000 years.
- Same for all storage classes
Availability:
- Measures how readily available a service is
- Varies depending on storage class
- Example: S3 standard has 99.99% availability = not available for 53 minutes a year
S3 Standard - General Purpose
- 99.99% availability
- Used for frequently accessed data
- Low latency and high throughput
- Sustain 2 concurrent facility failures
- Use Cases: Big Data Analytics, mobile & gaming applications, content distribution...
S3 Storage Classes - Infrequent Access
- For data that is less frequently accessed, but requires rapid access when needed
- Lower cost than S3 standard
- Amazon S3 Standard-Infrequent Access (S3 Standard-IA)
	- 99.9% Availability
	- Use Cases: Disaster recovery, backups
- Amazon S3 One Zone-