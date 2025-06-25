Followed official Snowflake Docs to integrate with GCS:
https://docs.snowflake.com/en/user-guide/data-load-gcs-config

Step 1: Create a Cloud Storage integration in Snowflake
Step 2: Create Stages To Load Data Into Snowflake
Step 3: Create Role and map role to service account. Give Service Account permissions to interact with GCS bucket.
Step 4: Create an external stage

---

How to copy from Stage into table in Snowflake:
- To copy data from Google Cloud Storage (GCS) to a Snowflake table, you can utilize the

- `COPY INTO` command in Snowflake, which loads data from files in a staged location into your desired table. This process typically involves creating an external stage in Snowflake that points to your GCS bucket, and then using the `COPY INTO` command to load the data from that stage into your Snowflake table.
- **Example `COPY INTO` command using a named stage:** 

sql

```sql
COPY INTO mytable FROM @my_gcs_stage;
```

**Example `COPY INTO` command using a path and file format options:** 

sql

```
COPY INTO mytable FROM @my_gcs_stage/mybucket/data/files FILE_FORMAT = (FORMAT_NAME = my_csv_format);
```