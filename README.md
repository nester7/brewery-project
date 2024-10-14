# brewery-project

## Overview
This project retrieves data from the Open Brewery DB API, processes it using Apache Airflow, and stores it in AWS S3 buckets.

## Project Tools and Challenges

For this project, I chose to use **Apache Airflow** and **Docker**, even though I had never used either of them before, but I wanted to learn new tools commonly used for ELT processes. 

Learning both Airflow and Docker in less than a week presented a significant challenge, especially when implementing all the necessary tasks.

Initially, my plan was to use **PySpark** instead of **Pandas**. However, I encountered numerous errors related to Java dependencies in PySpark, and as time began to run out, I decided to switch libraries. I opted for a library with fewer imports, which ultimately simplified the implementation process.


## Resources
- **API**: [Open Brewery DB](https://api.openbrewerydb.org/breweries)
- **Airflow**: [Apache Airflow Documentation](https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html)
- **Docker**: [Docker Installation Guide](https://docs.docker.com/engine/install/)
- **AWS**: [Amazon Web Services](https://aws.amazon.com/)


## Monitoring and Alerting Suggestions

For monitoring, I suggest utilizing the **Airflow interface** to track task statuses, including:
- Running
- Succeeded
- Failed
- Skipped

It would also be beneficial to regularly check the status of DAG runs to identify any anomalies, such as execution times being longer or shorter than expected. 

Additionally, creating tasks to perform data quality checks is a good measure to ensure there are no missing values or unexpected schema changes.

For alerting, configuring email notifications using Airflow's tools (e.g., `email_on_failure`) would be ideal, particularly focusing on failed tasks and tasks that are taking too long to execute.


## AWS S3 Buckets
The project utilizes S3 buckets in AWS. The setup includes:
1. Creating an AWS account and setting up S3 buckets with default configurations.
2. Creating a new IAM user with default settings in IAM.
3. Generating an Access Key for the user under the 'Security Credentials' tab, which is essential for accessing the S3 buckets.
4. Granting the user permissions by navigating to 'Add Permissions' > 'Attach policies directly' > 'AmazonS3FullAccess'.

## Security
For enhanced security, a new connection named `connection-aws` was created in the Airflow UI. This connection securely stores the AWS Access Key ID and Secret Access Key.
