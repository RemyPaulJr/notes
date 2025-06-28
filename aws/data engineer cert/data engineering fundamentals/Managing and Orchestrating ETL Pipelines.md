ETL Pipelines:
- Stands for Extract, Transform, Load. It's a process used to move data from source systems into a data warehouse.
- Extract:
	- Retrieve raw data from source systems. which can be databases, CRMs, flat files, APIs, or other data repositories.
	- Ensure data integrity during the extraction phase.
	- Velocity. Can be done in real-time or in batches, depending on the requirements.
- Transform:
	- Convert the extracted data into a format suitable for the target data warehouse.
	- Can involve various operations such as:
		- Data cleansing (remove duplicates, fixing errors)
		- Data enrichment (adding additional data from other sources)
		- Format changes (date formatting, string manipulation)
		- Aggregations or computations (calculating totals or averages)
		- Encoding or decoding data
		- Handling missing values
	- Load
		- Move the transformed data into the target data warehouse or another data repository.
		- Can be done in batches (all at once) or in a streaming manner (as data becomes available)
		- Ensure that data maintains its integrity during the loading phase.

#### **Managing ETL Pipelines**
- This process must be automated in some reliable way
- AWS Glue - can automatically due ETL or ELT on data as its received
- Orchestration Services:
	- EventBridge
	- Amazon Managed Workflows for Apache Airflow [Amazon MWAA]
	- AWS Step Functions
	- Lambda
	- Glue Workflows