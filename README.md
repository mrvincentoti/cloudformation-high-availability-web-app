### DEPLOY A HIGHLY AVAILABLE WEB APPLICATION ON AWS WITH CLOUDFORMATION

![This is an image](infrastructure-diagram/HA-Infrastructure.png)

#### THE BUSINESS GOAL

A company is creating an Instagram clone called Udagram.
Developers want to deploy a new application to the AWS infrastructure.
This repository contains code to provisioning the required infrastructure and deploying the application,
along with the necessary supporting software.

#### PROJECT REQUIREMENTS

1. AWS Account
2. Install and configure AWS CLI
3. Create an s3 bucket
4. Upload a simple static website as a zip file to the s3 bucket (Launch config will copy this file to your ec2 instances)

#### PROJECT FILES

1. network-stack.yaml file - code to setup the network infrastructure (VPC -Public and Private Subnets -Internet Gateway -NAT Gateway -Elastic IP address and -Route Tables)
2. server-stack.yaml file - code to create the compute resources (Load Balancer -Autoscaling Group - IAM roles - Target Groups -EC2 Launch configuration)
3. network-parameters.json file - Network parameters
4. server-parameters.json file - Compute parameters

##### STEPS

1. clone repository
2. navigate to the cloned folder
3. run this command `aws cloudformation create-stack --stack-name network-stack --region us-east-1 --template-body file://network-stack.yml --parameters file://network-params.json` to create the network infrastructure
4. run this command `aws cloudformation create-stack --stack-name compute-stack --region us-east-1 --template-body file://server-stack.yml --parameters file://server-params.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM"` to create the compute infrastructure
