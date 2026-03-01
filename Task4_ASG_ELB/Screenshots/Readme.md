# Task 4: ASG and ELB in EC2

## Objective
Configure an Auto Scaling Group (ASG) with a Load Balancer to understand high availability and automatic scaling in AWS.

## Environment
- AWS EC2
- Launch Template
- Auto Scaling Group (ASG)
- Elastic Load Balancer (ELB)

## Simple Definition
Auto Scaling Group automatically adjusts the number of EC2 instances based on demand, while a Load Balancer distributes incoming traffic across multiple instances to ensure high availability.

---

## Implementation Steps

### 1. Create Launch Template
- Go to EC2 → Launch Templates
- Click "Create launch template"
- Select Amazon Machine Image (AMI)
- Choose instance type
- Configure key pair and security group (allow HTTP and SSH)
- Add User Data (optional for automatic web server setup)
- Create launch template

Example User Data (optional):
```bash
#!/bin/bash
sudo apt update -y
sudo apt install nginx -y
sudo systemctl start nginx
```

---

### 2. Create Load Balancer
- Go to EC2 → Load Balancers
- Click "Create Load Balancer"
- Choose "Application Load Balancer"
- Select VPC and at least two subnets (different AZs)
- Configure security group (allow HTTP)
- Create Target Group
- Complete Load Balancer creation

---

### 3. Create Auto Scaling Group (ASG)
- Go to EC2 → Auto Scaling Groups
- Click "Create Auto Scaling Group"
- Select previously created Launch Template
- Choose VPC and subnets
- Attach to existing Load Balancer
- Configure desired, minimum, and maximum capacity
- Set scaling policies (optional)
- Create ASG

---

### 4. Verification
- Check that instances are launched automatically
- Confirm instances are registered in Target Group
- Access Load Balancer DNS name in browser
- Verify traffic is distributed across instances

---

## Key Concepts

- High Availability: Instances deployed across multiple Availability Zones.
- Load Balancing: Traffic distributed evenly across instances.
- Auto Scaling: Automatic increase or decrease of instances based on load.

---

## Learning Outcome
- Launch Template creation
- Load Balancer configuration
- Auto Scaling Group setup
- Understanding of scalability and fault tolerance in AWS
