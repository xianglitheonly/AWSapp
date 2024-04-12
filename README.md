## Project Description

using AWS-native tools such as CloudFormation for infrastructure provisioning and AWS CodePipeline, AWS CodeBuild, and AWS CodeDeploy for automating the deployment process. 

## CloudFormation

* Launch Configuration and Auto Scaling Group:

Define a Launch Configuration specifying the EC2 instance details.
Define an Auto Scaling Group referencing the Launch Configuration, specifying minimum, maximum, and desired capacity along with scaling policies.

* Application Load Balancer (ALB):

Define an Application Load Balancer resource specifying listeners, target groups, and routing rules.
Register the EC2 instances with the ALB's target group.

* CloudWatch Log Group and SNS:

Define a CloudWatch Log Group for your EC2 instances' logs.
Set up an SNS topic for receiving notifications/alerts.

* CloudWatch Alarm:

Create CloudWatch Alarms to monitor specific metrics (CPU utilization, network traffic, etc.) of your EC2 instances or ALB.
Set up actions for these alarms, such as triggering SNS notifications or Auto Scaling policies.

* Hosted Zone and Resource Records:

Define a Hosted Zone for your domain.
Specify Resource Records (such as A or CNAME records) within the Hosted Zone to route traffic to your ALB.

## Jenkins
* A multi-branch pipeline is used to automatically run Terraform apply and Ansible deploy.
* The public ssh key used to create the EC2 instances should be put in the docker volume called jenkins-docker-certs.
* All the credentials are stored in Jenkins credentails. There are tf-creds for Terraform cloud, github-cred for github
personal access, xiangli-admin for AWS CLI access, ec2-ssh-key for the ssh private key.
![alt text](image.png)

## Terraform

* Terraform cloud is used for Terraform state backend.
* Resources that Terraform will create include AWS VPC, subnets, rout tables, internet gateway, security groups and EC2 instances.
* With several .tfvars files for different environments.

## Ansible

* Two Ansible playbook files will be used. One for Grafana and Prometheus deployment and one for applications test
for ensuring the deployment is successful.
* There is no ansible.cfg file for configuration because it will be using the build-in function in Jenkins ansiblePlaybook() to specify the inventory file.
* The other configurations could be specified using Ansible environment variables at the top of the Jenkinsfile.
