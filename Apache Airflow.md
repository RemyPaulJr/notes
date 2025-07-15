This is my first time using Airflow.

### What is Apache Airflow?

Apache Airflow is an open-source workflow orchestration platform that helps you schedule, monitor and manage complex data pipelines. Like a sophisticated cron job scheduler.

**Key concepts**:
•  **DAG** (Directed Acyclic Graph): A collection of tasks with dependencies
•  **Tasks**: Individual units of work (like running a Python script, SQL query, or API call)
•  **Operators**: Templates for tasks (PythonOperator, BashOperator, etc.)
•  **Scheduler**: Runs your DAGs on schedule
•  **Web UI**: Visual interface to monitor and manage your pipelines

Why is Airflow Helpful?

1. Automation & Scheduling
	•  Run tasks on schedules (daily, hourly, weekly)
	•  No more manual cron jobs or remembering to run scripts

2. Dependency Management
	•  Tasks run in the right order
	•  If Task A fails, Task B won't run (preventing cascading failures)

3. Monitoring & Alerting
	•  Visual dashboard showing pipeline status
	•  Get notifications when things fail
	•  Retry failed tasks automatically

4. Scalability
	•  Can run on multiple machines
	•  Handles complex workflows with many steps
### Why am I using Airflow for this project?

Mainly to reduce manual effort.

Without Airflow I have to:

1. Run Python script manually
2. Script fetches CoinGecko data
3. Saves to local parquet file
4. Uploads to GCS
5. (You want to add) Load to BigQuery

With Airflow:

Daily at 9 AM:
├── Task 1: Fetch CoinGecko data → parquet
├── Task 2: Upload to GCS (depends on Task 1)
└── Task 3: Load GCS parquet to BigQuery (depends on Task 2)

