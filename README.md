python -m venv venv
venv/Scripts/activate
pip install -r requirements.txt


1) install boto3
2) install AWS CLI 
3) create IAM user and give him access administrator access , or else we give administrator access for EC2 , S3 ... etc
4) then click on user and create secret access key for cli.
5) you will get user access key and secret access key store it in the ENV.
6) folder cli - enter aws cli before that install awscli package python
7) .pem file is used to create user and user access key and secret access key is used to create instances , s3 buckets ... etc.
8) aws cli will ask for user access key and secret access key and default region , give it to the cli it will configure aws into that folder

for EC2 checkout the folder C:\projects\aws\AWS_EC2
create an EC2 instance
launch an EC2 instance 
create security groups
attach security groups to Ec2 instance 
dettach security groups to Ec2 instance 
check EC2 instance status
Start , stop and terminate Ec2 in python

for S3 
i have created a sample folder C:\projects\aws\Sample
with 3 folders - folder1 , folder2 , folder3
1) create a S3 bucket
2) upload file to s3 bucket
3) list s3 objects or files in the bucket
4) download s3 files to local system
5) upload all files in dir to S3
6) download full s3dir to local
7) delete all files in an S3 bucket

