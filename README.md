# AWS-Snowflake-Data-Pipeline-Using-Kinesis-Airflow

AWS Tools Used 
1. IAM
2. EC2
3. Kinesis Firehose
4. Cloud Watch
5. Kinesis Agent
6. AWS Mangaged Airflow

We need to create the IAM policy because we are going to use EC2 instance further ddown the road in the project where we need to assign IAM policy to it.

---Click IAM in all service
---Click on roles to create roles
---Create a new role
--- select trusted entity type as AWS Service & EC2 in coomon use cases & click on next
--- We need to attach 4 policies 
    1. cloud watch full access
    2. Cloud Watch Logs Full Access
    3. Amazon kinesis firehose full access
    4. cloud watch Event Full Access
---- role name : pwsnowflakerole
---- create
