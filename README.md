## Project Title - Deploy a high-availability web app using CloudFormation

#### The business goal

A company is creating an Instagram clone called Udagram.
Developers want to deploy a new application to the AWS infrastructure.

You have been tasked with provisioning the required infrastructure and deploying the application, along with the necessary supporting software.

This needs to be automated so that the infrastructure can be discarded and created as many times as possible.

Good to have - Once the project is completed, a user should be able to deploy a sample website files located in a public S3 Bucket to the Apache Web Server running on an EC2 instance.

#### Project requirements

##### Server specs

###### 1. You'll need to create a Launch Configuration for your application servers in order to deploy four servers, two located in each of your private subnets. The launch configuration will be used by an auto-scaling group.

###### 2. You'll need two vCPUs and at least 4GB of RAM. The Operating System to be used is Ubuntu 18. So, choose an Instance size and Machine Image (AMI) that best fits this spec.

###### 3. Be sure to allocate at least 10GB of disk space so that you don't run into issues.

##### Security Groups and Roles

###### 1. Since you will be downloading the application archive from an S3 Bucket, you'll need to create an IAM Role that allows your instances to use the S3 Service.

###### 2. Udagram communicates on the default HTTP Port: 80, so your servers will need this inbound port open since you will use it with the Load Balancer and the Load Balancer Health Check. As for outbound, the servers will need unrestricted internet access to be able to download and update their software.

###### 3. The load balancer should allow all public traffic (0.0.0.0/0) on port 80 inbound, which is the default HTTP port. Outbound, it will only be using port 80 to reach the internal servers.

###### 4. The application needs to be deployed into private subnets with a Load Balancer located in a public subnet.

###### 5. One of the output exports of the CloudFormation script should be the public URL of the LoadBalancer. Bonus points if you add http:// in front of the load balancer DNS Name in the output, for convenience.

This repository contains the following iac and parameters files:

##### 1. network-stack.yaml file

##### 2. servver-stack.yaml file

##### 3. network-parameters.json file

##### 4. server-parameters.json file
