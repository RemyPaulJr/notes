JDBC
- Java Database Connectivity
- Platform independent - because it is based on Java
- Language Dependent - because it is based on Java again
ODBC
- Open Database Connectivity
- Platform-dependent (thanks to drivers)
- Language independent
Raw logs
API's
Streams

#### **Common Data Formats**

**CSV (Comma-Separated Values)**
- Text-based format that represents data in a tabular form where each line corresponds to a row and values within a row are separated by commas.
- Can be pipe separated or tab separated as well.
- When to use:
	- For small to medium datasets
	- For data interchange between systems with different technologies
	- For human-readable and editable data storage
	- Importing/Exporting data from databases or spreadsheets
- Systems:
	- Databased (SQL-based), Excel, Pandas in Python, R, many ETL tools

**JSON (JavaScript Object Notation)**
- Lightweight, text-based, and human-readable data interchange format that represents structured or semi-structured data based on key-value pairs.
- When to use:
	- Data interchange between a web server and a web client
	- Configurations and settings for software applications.
	- Use cases that need a flexible schema or nested data structures.
- Systems:
	- Web browsers, many programming languages (like JavaScript, Python, Java, etc.), RESTful APIs, NoSQL databases (like MongoDB).

Avro
- Binary format that stores both the data and its schema, allowing it to be processed later with different systems without needing the original system's context.
- When to use:
	- With big data and real-time processing systems.
	- When schema evolution (changes in data structure) is needed.
	- Efficient serialization for data transport between systems.
- Systems:
	- Apache Kafka, Apache Spark, Apache Flink, Hadoop ecosystem.

Parquet
- Columnar storage format optimized for analytics. Allows for efficient compression and encoding schemes.
- When to use:
	- Analyzing large datasets with analytics engines.
	- Use cases where reading specific columns instead of entire records is beneficial.
	- Storing data on distributed systems where I/O operations and storage needs optimization.
- Systems:
	- Hadoop ecosystem, Apache Spark, Apache Hive, Apache Impala, Amazon Redshift Spectrum.