# Build, test, and deploy an app to AWS ECS

[![CircleCI](https://circleci.com/gh/daumie/circleci-ecs.svg?style=svg)](https://circleci.com/gh/daumie/circleci-ecs)

```bash
aws ec2 create-default-vpc
aws ec2 create-security-group --group-name circleci-demo-sg --description "Circle CI Demo Security Group"
```

Now create an ECS Cluster called `circleci-demo-cluster` and the ec2 instance that belongs to the ECS Cluster. Use the `circleci-demo-sg` security group that was created. You can get the id of the security group from the EC2 Console / Network & Security / Security Groups. It is important to select a Key pair so you can ssh into the instance later to verify things are working.

For the Networking VPC settings, I used the default VPC and all the Subnets associated with the account to keep this tutorial simple. For the IAM Role use ecsInstanceRole. If ecsInstanceRole does not yet exist, create it per AWS docs. All the my settings are provided in the screenshot. You will need to change the settings according to your own account and default VPC and Subnets.

Wait a few minutes and the confirm that the Container Instance has successfully registered to the `circleci-demo-cluster` ECS cluster. You can confirm it by clicking on the ECS Instances tab under Clusters / `circleci-demo-cluster`.

2. Create a task definition that will be blueprint to start a Go Application


