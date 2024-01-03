# AWS-Snowflake-Data-Pipeline-Using-Kinesis-Airflow

AWS Tools Used 
1. IAM
2. EC2
3. Kinesis Firehose
4. Cloud Watch
5. Kinesis Agent
6. AWS Mangaged Airflow



We need to create the IAM policy because we are going to use EC2 instance further ddown the road in the project where we need to assign IAM policy to it.

1. Click IAM in all service
2. Click on roles to create roles
3. Create a new role
4. select trusted entity type as AWS Service & EC2 in coomon use cases & click on next
5. We need to attach 4 policies 
    cloud watch full access
    Cloud Watch Logs Full Access
    Amazon kinesis firehose full access
    cloud watch Event Full Access
5. role name : pwsnowflakerole
6. create

