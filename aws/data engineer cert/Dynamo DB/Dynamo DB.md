NoSQL Database

Can have empty attributes.

Must define a partition key (primary key) and a sort key is optional.
Partition Key + Sort key allows you to partition data by the partition key.
For example, can have multiple userids with separate orders

---
Write Capacity Unites (WCU)
- One WCU represents one write per second for an item up to 1KB in size
- If the items are larger than 1KB more WCUs are consumed
- Example:
	- write 10 items per second, with item size 2KB
		- 10*(2KB/1KB) = 20 WCUs
	- write 6 items per second, with item size 4.5KB
		- 6*(5KB/1KB) = 30 WCUs (4.5 gets rounded to the upper KB)
	- write 120 items per minute, with item size 2KB
		- (120/60) * (2KB/1KB) = 4 WCUs
---
Read Capacity Units (RCU)

DynamoDB is a serverless DB but behind the scenes AWS manages the servers.
So when you write to DB behind the scenes the Data is replicated to other servers.
- Eventually Consistent Reads - there's a chance that as soon as you write data to a DB, there's a chance you will not be able to read the data as the data might not be replicated instantly.
- Strongly Consistent Reads - guaranteed if we read after a write, we will get the correct data. To do so you must set the "ConsistentRead" parameter to True in API calls. 

One RCU represents one Strongly Consistent Read per second, or two Eventually Consistent Reads per second, for an item up to 4 KB in size.
If the items are larger than 4 KB, more RCUs are consumed.
- Example:
	- 10 Strongly Consistent Reads per second, with item size 4 KB
		- 10 * (4KB/4KB) = 10 RCUs
	- 16 Eventually Consistent Reads per second, with item size 12 KB
		- (16/12) * (12KB/4KB) = 24 RCUs
	- 10 SCR per second, with item size 6 KB
		- 10 * (8KB/4KB) = 20 RCUs (we must round up 6KB to 8KB, to the nearest 4 KB)
---
Partitions
- Data is stored in partitions
- partition keys go through a hashing algorithm to know which partition they go to
- **WCUs and RCUs are spread evenly across partitions**
	- Divided and split evenly across partitions
---
Throttling
- If exceed provisioned RCU or WCUs, we get "ProvisionedThroughputExceededException"
- Solutions:
	- Exponential backoff when exception is encountered (already in SDK)
	- Distribute partition keys as much as possible
	- If RCU issue, use DynamoDB Accelerator (DAX)
---
Read/Write Capacity Mode - On-Demand
- R/W automatically scale up/down with your workloads
- No capacity planning needed (WCU / RCU)
- Unlimited WCU & RCU, no throttle, more expensive
- Charged for reads/writes that you use in terms of RRU and WRU
- Read Request Units (RRU) - throughput for reads (same as RCU)
- Write Request Units (WRU) - throughput for writes (same as WCU)
- 2.5x more expensive that provisioned capacity
- Use cases:
	- unknown workloads
	- unpredictable application traffic