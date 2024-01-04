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

## SSH Connection :
1. Open Putty Key generator.
2. click file and load private key
3. load the prm key pair
4. save Private Key
5. name the new PPK file
6. now open the putty
7. copy Public IPv4 DNS and paste it in host name (make sure to add 'ec2-user@' before copying the address.
8. click on SSH on left category
9. click on auth
10. click on credential
11. click on private authentication and browsw the PPK generated file
12. click open

![Screenshot (475)](https://github.com/shekharj21/shekharj21/assets/54074505/14c5bc56-8690-49b2-99d2-268ed41dcc02)

## Create Kinesis Firehose :
1. select kinesis firehose and create delivery stream.
2. we need 2 delivery streams as we have 2 datasets customers and orders.

### First Delivery Stream (Customers):
3. choose source as direct put and destination as S3.
4. Delivery Stream Name : CustomerData
5. choose S3 Bucket which we created : snowflakedatapipelinepw
6. set bucket prefix : firehose/customers/landing
7. Set Error Prefix : firehose/error/customers

### Second Delivery Stream (Orders):
8. name : Orders_data
9. choose S3 Bucket which we created : snowflakedatapipelinepw
10. set bucket prefix : firehose/orders/landing
11. Set Error Prefix : firehose/error/orders

![Screenshot (476)](https://github.com/shekharj21/shekharj21/assets/54074505/f5072cba-0c4b-4c86-84a8-d1b99f02c934)


## Installing kinesis Agent and sending data to firehose :
1. kinesis agent will help us to send the data from EC2 machine to firehose.
2. open putty
3. type the coomand :  sudo yum install -y aws-kinesis-agent
4. cd /etc
5. cd aws-kinesis
6. ls (will see agent.json) which will help us configure the delivery stream
7. open it : sudo vi agent.json and press i to edit firehose.endpoint
8. modify the file as given below

![Screenshot (478)](https://github.com/shekharj21/shekharj21/assets/54074505/d29cf61d-c482-4117-a51c-2313efcdfcda)

