## **My Notes**

- Currently working on a DataPipeline
	- Extracting Data from API via Python requests library
	- Load Data into Google Cloud Storage (GCS)
	- Extract Data from GCS and cop/load into Snowflake raw table
	- Transform Data in silver table
	- Aggregate data in Gold table/layer
	- Load Data into GCS again
	- Load Data into BigQuery
	- Load Data into PowerBI maybe, will decide once I get closer to this step
	- Automate Pipeline via Airflow. Batch processing Jobs on set intervals