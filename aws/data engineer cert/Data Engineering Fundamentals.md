### **Type of Data**

- Structured
	- Data that is organized in a define manner of schema, typically found in relational databases.
	- Characteristics:
		- Easily queryable
		- Organized in Rows and Columns
		- Has a consistent Structure
	- Examples:
		- Database tables
		- CSV files with consistent columns
		- Excel spreadsheets
- Unstructured Data
	- Data that does not have a predefined structured or schema.
	- Characteristics:
		- Not easily queryable without preprocessing
		- May come in various formats
	- Examples:
		- Text files without a fixed format
		- Videos and audio files
		- Images
		- Emails and word processing documents
- Semi-Structured
	- **Data that is not consistent throughout the document.** Somewhere in the middle. Bit of a grey area. Data that is not organized as structured data but has some levels of structure in the form of tags, hierarchies, or other patterns.
	- Characteristics:
		- Elements that might be tagged or characterized in some way
		- More flexible than structured data but not as chaotic as unstructured data
	- Examples:
		- XML and JSON files
		- Email headers (which have a mix of structured and unstructured fields)
		- Log files with varied formats
---
### **Properties of Data**

- Volume
	- How much data are we talking?
	- Characteristics:
		- Range from gigabytes to petabytes or even more
		- challenges in storing, processing, and analyzing high volumes of data
	- Examples:
		- Social media platform processing terabytes of data daily from user posts, images, and videos
		- Retailers collecting year's worth of transaction data, amounting to several petabytes
	- Volume of data will determine how you store and process your data pipeline.
- Velocity
	- Speed at which new data is generated, collected, and processed.
	- Characteristics:
		- High velocity requires real-time or near-real-tinme processing capabilities
		- Rapid ingestion and processing can be critical for certain applications
	- Examples:
		- Sensor data from IoT devices streaming readings every millisecond
		- High-frequency trading systems where milliseconds make the difference
- Variety
	- Type of data, structures, and sources of data.
	- Characteristics:
		- Data can be structured, unstructured, or semi-structured
		- Can come from multiple sources in various formats
	- Example:
		- business analyzing data from a rds (structured), emails (unstructured), and JSON logs (semi-structured)
		- Healthcare systems collecting data from electronic medical records, wearable health devices, and patient feedback forms
---
### **Data Warehouse VS Data Lake VS Lakehouses**

Data Warehouse
- Centralized reposistory optimized for analysis where data from different sources is stored in a **structured format**.
- Characteristics:
	- Designed for complex queries and analysis
	- Data is cleaned, transformed, and loaded (ETL process)
	- Typically uses star or snowflake schema
	- Optimized for read-heavy operations
- Examples:
	- Redshift
	- BigQuery
	- Azure SQL Data Warehouse
Data Lake
- Storage repository that holds **vast amounts of raw data in its native format**, including **structured, semi-structured, and unstructured data**.
- Characteristics:
	- Can store large volumes of raw data without predefined schema.
	- Data is loaded as-is, no need for preprocessing
	- Supports batch, real-time, and stream processing
	- Can be queried fir data transformation or exploration purposes
- Examples:
	- S3 when used as a data lake
	- Azure Data Lake Storage
	- Hadoop Distributed File System (HDFS)
Comparing the two:
- Schema
	- Data Warehouse: Schema-on-write (predefined schema before writing data)
		- Extract --> Transform --> Load (ETL)
	- Data Lake: Schema-on-read (schema is defined at a time of reading data)
		- Extract --> Load --> Transform (ELT)
- Data Types
	- Data Warehouse: Primarily structured data
	- Data Lake: Both structured and unstructured
- Agility
	- Data Warehouse: Less agile due to predefined schema
		- If you decide to change schema then that would involve a data migration project. this is harder to maintain as you have to follow the predefined structure of the data
	- Data Lake: More agile as it accepts raw data without a predefined structure
		- More flexible
- Processing
	- Data Warehouse: ETL (Extract, Transform, Load)
	- Data Lake: ELT (Extract, Load, Transform) or just Load for storage purposes
- Cost
	- Data Warehouse: Typically more expensive because of optimizations for complex queries
	- Data Lake: Cost-effective storage solutions, but costs can rise when processing large amounts of data

#### **Choosing a Warehouse VS a Lake**

Use a Data Warehouse when:
- You have structured data source and require fast and complex queries
- Data integration from different sources is essential
- Business Intelligence and analytics are the primary use cases
Use a Data Lake when:
- You have a mix of data
- You need scalable and cost-effective solution to store massive amounts of data
- future needs for data are uncertain, and you want flexibility in storage and processing
- advanced analytics, machine learning, or data discovery are key goals
It's okay to use both. Ingesting raw data into a data lake and then processing and moving redefined data into a warehouse for analytics
#### **Data Lakehouse**

Made popular by Databricks

Hybrid architecture that combines the best features of data lakes and data warehouses, aiming to provide the performance, reliability, and capabilities of a data warehouse while maintaining the flexibility, scale, and low-cost storage of data lakes.

Characteristics:
- Supports all structure of data
- Allows for schema-on-write and on-read
- Provides capabilities for both machine learning and analytics
- Typically built on top of cloud or distributed architectures
- Benefits from technologies like Delta Lake, which bring ACID transactions to big data

Examples:
- AWS Lake Formation (with S3 and Redshift Spectrum)
- Delta Lake: An open-source storage layer that brings ACID transactions to Apache Spark and big data workloads
- Databricks Lakehouse Platform: A unified platform that combines the capabilities of data lakes and data warehouses
- Azure Synapse Analytics: Microsoft's analytics service that brings together big data and data warehousing
---
### **Data Mesh**

- More about governance and organization rather than technologies.
- Individual teams own "data products" within a given domain.
>[!NOTE]
> This is more about the ownership and resposibility of data within a larger organization. For ex  