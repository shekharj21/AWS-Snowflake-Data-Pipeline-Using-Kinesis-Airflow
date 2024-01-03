## AWS-Snowflake-Data-Pipeline-Using-Kinesis-Airflow

## AWS Tools Used :
1. IAM
2. EC2
3. Kinesis Firehose
4. Cloud Watch
5. Kinesis Agent
6. AWS Mangaged Airflow


## IAM Roles & Policy :
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
![Screenshot (474)](https://github.com/shekharj21/AWS-Snowflake-Data-Pipeline-Using-Kinesis-Airflow/assets/54074505/413f9f92-c0bc-4c58-8702-81ea7b447bcf)

## Create EC2 Instance :
1. select EC2 from services
2. try to create S3 bucket and EC2 Instance in a same region (Asia/Mumbai)
3. name : snowflakedppw
4. amazon linux
5. Amazon Machine image : free tier
6. instance type : t3.micro
7. Select and name key pair with .pem file
8. In Advanced setting, select IAM instance profile to the name given in IAM roles : pwsnowflakerole
9. Launch Instance
