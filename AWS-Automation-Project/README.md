# AWS Automation Project

## Project Overview

Designed and implemented a scalable and fault-tolerant AWS infrastructure using EC2, AMI, Launch Templates, Auto Scaling Groups, Application Load Balancer, Target Groups, and CloudWatch.

## Architecture

Client → ALB → Target Group → Auto Scaling Group → EC2 Instances

## Services Used

- Amazon EC2
- AMI
- Launch Template
- Auto Scaling Group
- Application Load Balancer
- Target Group
- CloudWatch
- Windows Server IIS

## Key Features

✅ Automated VM deployment

✅ Auto Scaling based infrastructure

✅ Load balancing across instances

✅ Self-healing architecture

✅ High availability

✅ Health checks

## Project Workflow

1. Created EC2 Windows Server
2. Installed IIS and deployed application
3. Created custom AMI
4. Built Launch Template
5. Created Auto Scaling Group
6. Configured Target Group
7. Configured Application Load Balancer
8. Tested self-healing by terminating an instance

## Project Report

Detailed project documentation is available in:

AWS_Automation_Project_Report.pdf

## Screenshots

### EC2 Instance Running

Initial Windows EC2 instance successfully launched and configured.

![EC2](screenshots/ec2-running.png)


