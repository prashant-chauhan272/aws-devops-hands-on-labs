

# AWS Auto Scaling & Load Balancing Project

## 📌 Project Overview

This project demonstrates the implementation of a scalable and highly available web infrastructure on AWS using Linux EC2 instances.

The main objective of this project was to practically understand how AWS Auto Scaling automatically increases and decreases EC2 capacity according to workload.

I generated CPU load on an Amazon Linux EC2 instance using the `stress` utility to practically test both **Scale-Out** and **Scale-In** behavior.

---

## 🏗️ Architecture

```text
                    Internet
                       |
                       v
        Application Load Balancer (ALB)
                       |
                       v
                  Target Group
                       |
                       v
              Auto Scaling Group
                 /           \
                v             v
          Linux EC2       Linux EC2
             Instances managed by ASG
```

---

## 🛠️ AWS Services & Tools Used

- Amazon EC2
- Amazon Machine Image (AMI)
- Launch Template
- Auto Scaling Group (ASG)
- Application Load Balancer (ALB)
- Target Group
- CloudWatch Metrics
- Amazon Linux
- Linux Stress Utility

---

## ⚙️ Implementation

### 1. Linux EC2 Web Server

Created an Amazon Linux EC2 instance and configured it as the base server for the project.

### 2. Custom AMI

Created a custom AMI from the configured EC2 instance so that Auto Scaling could launch identical instances automatically.

### 3. Launch Template

Created a Launch Template using the custom AMI. The Launch Template acts as a blueprint for new EC2 instances launched by the Auto Scaling Group.

### 4. Auto Scaling Group

Configured an Auto Scaling Group to automatically manage EC2 capacity.

Configuration used during the project:

- Minimum Capacity: 1
- Desired Capacity: 2
- Maximum Capacity: 4

### 5. Application Load Balancer

Configured an internet-facing Application Load Balancer to distribute incoming traffic across healthy EC2 instances.

### 6. Target Group

Created an HTTP Target Group and integrated it with the Application Load Balancer and Auto Scaling Group.

Health checks were used to determine whether registered EC2 instances were healthy.

---

## 📈 Scale-Out Testing

To test Scale-Out behavior, I installed the `stress` utility on the Linux EC2 instance and generated CPU load.

Example command used:

```bash
stress --cpu 8 --timeout 900
```

As CPU utilization increased, the scaling mechanism increased EC2 capacity by launching additional instances.

This demonstrated how Auto Scaling can respond to increased application workload.

---

## 📉 Scale-In Testing

After testing Scale-Out, I stopped the CPU stress workload:

```bash
pkill stress
```

After CPU utilization decreased and the scaling conditions were met, Auto Scaling reduced unnecessary EC2 capacity.

This demonstrated **Scale-In**, which helps avoid running unnecessary compute resources when demand decreases.

---

## ♻️ Auto Scaling & Self-Healing

The Auto Scaling Group maintains the configured desired capacity.

If an instance becomes unhealthy or is terminated, Auto Scaling can launch a replacement instance to restore the required capacity.

---

## 🔄 Project Workflow

```text
Linux EC2
    ↓
Configure Web Server
    ↓
Create Custom AMI
    ↓
Create Launch Template
    ↓
Create Auto Scaling Group
    ↓
Create Target Group
    ↓
Configure Application Load Balancer
    ↓
Generate CPU Load
    ↓
Scale-Out
    ↓
Stop CPU Load
    ↓
Scale-In
```

---

## 📸 Project Screenshots

### Auto Scaling Group
![Auto Scaling Group](screenshots/04-auto-scaling-group.png)

### Application Load Balancer
![Application Load Balancer](screenshots/05-application-load-balancer.png)

### Target Group
![Target Group](screenshots/06-target-group.png)

### CPU Stress Test
![CPU Stress Test](screenshots/07-stress-test.png)

### Scale-Out
![Scale-Out](screenshots/08-scale-out.png)

### Stop CPU Stress
![Stop Stress](screenshots/09-stop-stress.png)

### Scale-In
![Scale-In](screenshots/10-scale-in.png)

---

## 🎯 Key Learnings

Through this project, I gained hands-on experience with:

- Creating and managing Linux EC2 instances
- Creating custom AMIs
- Working with Launch Templates
- Configuring Auto Scaling Groups
- Understanding Minimum, Desired and Maximum capacity
- Configuring Application Load Balancers
- Working with Target Groups and Health Checks
- Generating CPU load for scaling tests
- Understanding Scale-Out and Scale-In
- Understanding self-healing infrastructure
- Understanding how AWS dynamically manages compute capacity

---

## 🚀 Conclusion

This project provided practical experience in building and testing an automated and scalable AWS infrastructure.

Instead of manually adding or removing servers, Auto Scaling can dynamically adjust EC2 capacity according to workload, while the Application Load Balancer distributes traffic across healthy instances.
