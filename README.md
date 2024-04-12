## Project Description

Using AWS-native tools such as CloudFormation for infrastructure provisioning and AWS CodePipeline, AWS CodeBuild, and AWS CodeDeploy for automating the deployment process. 

## CloudFormation

* Launch Configuration and Auto Scaling Group:

  Define a Launch Configuration specifying the EC2 instance details.
  Define an Auto Scaling Group referencing the Launch Configuration, specifying minimum, maximum, and desired capacity along with scaling policies.

* Application Load Balancer (ALB):

  Define an Application Load Balancer resource specifying listeners, target groups, and routing rules.
  Register the EC2 instances with the ALB's target group.

* CloudWatch Log Group:

  Define a CloudWatch Log Group for Rout53 hosted zone access log.

* CloudWatch Alarm:

  Create a CloudWatch Alarm to monitor CPU utilization of ASG.
  Set up action for the alarms to trigger SNS notifications.

* Hosted Zone and Resource Records:

  Define a Hosted Zone in Route53 and specify Resource Records (CNAME records) within the Hosted Zone to route traffic to the ALB.

## CodePipeline

  A CodePipeline including a CodeBuild stage to simply build and test the source code and and a CodeDeploy stage to deploy the app to EC2 instances.
