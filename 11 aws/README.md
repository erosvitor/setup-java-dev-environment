
# About
Preparing the AWS environment.

# Steps

## Install AWS CLI
```
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
$ sudo ./aws/install
```

## Configure AWS CLI
```
$ aws configure

  AWS Access Key ID:
  AWS Secret Access Key:
  Default region name:
  Default output format: text|json

$ aws configure list

$ cat ~/.aws/config

$ cat ~/.aws/credentials

$ aws sts get-caller-identity
```

# Setting an Application Load Balance

- VPC
- Security group for EC2
- Two or more EC2
- Target group
- Security group for Load Balance
- Application Load balance
