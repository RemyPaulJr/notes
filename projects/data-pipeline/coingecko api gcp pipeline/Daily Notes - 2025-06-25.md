### **What I worked on today**
- Created Silver layer ddl. Created table in snowflake. Changed column names to be more consistent, meaningful, and well-labeled.
- Ran into an issue so to speak. That spawned another issue to speak.
	- 1st I noticed the entire ingestion_timestamp column was NULL. Parquet files can contain inconsistent date formats but Snowflake might have trouble interpreting some of them. So I decided to change the date format on the ingestion_timestamp column to match the other date type column's format. To do this i update the python script adding the timezone class from the datetime library and using datetime.now(timezone.utc) to generate the date and time with utc. This matches the other date time formats from the coin gecko api.
	- 2nd I noticed when pushing this file to the GCS bucket, replacing the bronze table, and copying the parquet file from the bronze sub folder to the bronze table, that snowflake tried to copy both files, yesterdays' and todays'. Which defaulted to the table containing the data from yesterday's file. As a workaround I decided to just remove yesterdays file from the bucket and do the process over. And the ingestion timestamp now shows properly. But, will need to implement a proper fix down the line as I am prioritizing automation.
	- Also just thought of the ingestion timestamp. it needs to be when the parquet file is ingested into snowflake rather than when the python script makes the http request. So the current timestamp will be for when the file is uploaded to GCS and need to create another timestamp column, likely somewhere in the copy process in snowflake. Need to research my options.  Need to prioritize this fix.
- Created Github repo for this Google Cloud Data Pipeline project finally.
- Worked on the Silver layer transformations, didn't get to complete everything today, but that's ok because there's tomorrow.
- Changed Github username to RemyPaulJr. This will help with SEO and when applying to jobs that my name is consistent across my online presence (LinkedIn, Github, need to update website still).
	- But I did purchase the remypaul.com domain from AWS Route 53.
	- Probably should've purchase remypauljr.com instead but whatever, can update this later, don't want to spend another $14 right now.
- Formatted the code for the create_integration, create_role, create_stages sql files. Used AI (ChatGPT) to help format, clean up the file with spacings, etc.
- Learned about SQL in Snowflake.
	- I'm used to SQL Server and PostgreSQL but Snowflake feels a bit different.
	- I learned how to use the TO_CHAR function.
- Examined the data further to see what transformations I need to make.

### **What's next?**
- Continue the silver transformations.
- Load the transformed data into the Silver table.
- Then start aggregating
- Also, practice VIM in fr