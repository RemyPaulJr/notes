This is my first time using Airflow.

### What is Apache Airflow?

Apache Airflow is an open-source platform for developing, scheduling, and monitoring workflows. Specifically for programmatically scheduling and monitoring data pipelines.

**Key Features:**
- **Workflow Management**: Define workflows as code using Python
- **Scheduling**: Built-in scheduler for running tasks at specified intervals
- **Monitoring**: Web-based UI for monitoring pipeline execution
- **Extensibility**: Rich ecosystem of operators and hooks for various services
- **Scalability**: Can handle complex, multi-step data pipelines

### Why am I using Airflow for this project?

Mainly to reduce manual effort.

Without Airflow I have to:

1. Run Python script manually
2. Script fetches CoinGecko data
3. Saves to local parquet file
4. Uploads to GCS
5. (You want to add) Load to BigQuery

With Airflow:
