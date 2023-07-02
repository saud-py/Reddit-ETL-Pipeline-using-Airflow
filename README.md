# Creating a Simple ETL Pipeline Using Airflow and Reddit API


## Architecture Diagram

![Airflow_ETL](https://user-images.githubusercontent.com/100070155/231428004-992b0287-439f-49ef-b486-f56df73a552b.png)


## Key Points and Overview

+ The goal of this project is to demonstrate how to create a simple ETL pipeline using Airflow and Reddit API. In this pipeline, we will extract data from Reddit API, transform it, and load it into an AWS S3 bucket using s3fs. 

+ We'll use an AWS EC2 instance to configure Airflow, and create a DAG with a task to schedule the ETL script to run. 

+ An IAM Role is assigned to the AWS EC2 instance with a policy to allow AWS S3 access. Finally the Airflow DAG is set to run on EC2 instance which initiates the ETL Pipeline.

## Architecture Overview

The pipeline is designed to run on an Amazon EC2 instance and utilizes the following components:

- Apache Airflow: Used for workflow management and scheduling.
- Reddit API: Provides access to Reddit's data.
- Amazon S3: Serves as the storage destination for the processed data.

## Prerequisites

Before running this project, make sure you have the following prerequisites:

- Amazon Web Services (AWS) account with access to EC2 and S3.
- Python 3.x installed on the EC2 instance.
- Reddit API credentials (client ID, client secret, username, and password).

## Installation

1. Launch an Amazon EC2 instance:

   - Set up an EC2 instance with the desired specifications.
   - Make sure the instance has internet access and can communicate with the Reddit API and S3.

2. Install Apache Airflow on the EC2 instance:

   - Follow the installation instructions for Airflow on EC2 from the official documentation.

3. Clone the repository on the EC2 instance:

   ```bash
   git clone https://github.com/your-username/reddit-etl-pipeline.git
   ```
1. nstall the required Python dependencies:
  ```bash
  pip install -r requirements.txt
  ```
2. Configure Airflow:

Update the Airflow configuration file (airflow.cfg) with the necessary settings, such as the executor, database connection, and parallelism.
Configure Reddit API credentials:

Create a Reddit developer account (if you haven't already) and generate API credentials.
Update the reddit_credentials.json file in the repository with your Reddit API credentials.
Configure S3 storage:

Set up an S3 bucket in your AWS account to store the processed data.
Update the s3_credentials.json file in the repository with your S3 bucket credentials.
Initialize the Airflow database:

```bash
airflow initdb
```
## Files

reddit_etl.py: This file contains the Python ETL script for extracting, transforming, and loading data from Reddit API to AWS S3 using s3fs.

reddit_dag.py: This file contains the DAG and task definitions for Airflow.
