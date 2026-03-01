# Task 10: VPC 3-Tier Architecture

## Objective
Design and implement a secure 3-tier architecture in AWS to understand networking components such as VPC, subnets, Internet Gateway, NAT Gateway, NACL, and SSH tunneling.

## Environment
- AWS VPC
- EC2 Instances
- Internet Gateway (IGW)
- NAT Gateway
- Route Tables
- Network ACL (NACL)
- Security Groups

## Simple Definition
A 3-tier architecture separates the application into three layers:
- Presentation Tier (Public Subnet)
- Application Tier (Private Subnet)
- Database Tier (Private Subnet)

This improves security, scalability, and availability.

---

## Architecture Overview

- Public Subnet:
  - Contains Bastion Host / Web Server
  - Connected to Internet via Internet Gateway (IGW)

- Private Subnet (Application Tier):
  - Hosts application servers
  - Internet access via NAT Gateway

- Private Subnet (Database Tier):
  - Hosts database server
  - No direct internet access

---

## Implementation Steps

### 1. Create VPC
- Go to VPC → Create VPC
- Define CIDR block (e.g., 10.0.0.0/24)

---

### 2. Create Subnets
- Public Subnet (e.g., 10.0.0.0/27)
- Private Subnet – App (e.g., 10.0.0.32/27)
- Private Subnet – DB (e.g., 10.0.0.64/27)
- Place subnets in different Availability Zones (recommended)

---

### 3. Create and Attach Internet Gateway (IGW)
- Create IGW
- Attach to VPC
- Update Public Route Table:
```
Destination: 0.0.0.0/0
Target: Internet Gateway
```

---

### 4. Create NAT Gateway
- Allocate Elastic IP
- Create NAT Gateway in Public Subnet
- Update Private Route Table:
```
Destination: 0.0.0.0/0
Target: NAT Gateway
```

This allows private instances to access the internet without being publicly accessible.

---

### 5. Configure Route Tables
- Associate Public Route Table with Public Subnet
- Associate Private Route Table with Private Subnets

---

### 6. Launch EC2 Instances
- Bastion Host in Public Subnet
- Application Server in Private Subnet
- Database Server in Private Subnet

Configure Security Groups:
- Allow SSH (22) only to Bastion from your IP
- Allow SSH from Bastion to Private Instances
- Restrict DB access only from Application Server

---

### 7. Configure Network ACL (NACL)
- Define inbound and outbound rules
- Allow required ports (22, 80, 443, etc.)
- Deny unnecessary traffic for added security

---

### 8. SSH Tunneling to Private Instance

Connect to Bastion:
```bash
ssh -i key.pem ec2-user@<public-ip>
```

From Bastion to Private Instance:
```bash
ssh -i key.pem private-user@<private-ip>
```

Or direct tunneling:
```bash
ssh -i key.pem -J ec2-user@<public-ip> private-user@<private-ip>
```

---

## Key Concepts

- VPC: Isolated virtual network in AWS
- Public Subnet: Connected to Internet via IGW
- Private Subnet: No direct internet access
- NAT Gateway: Outbound internet access for private instances
- Bastion Host: Secure jump server
- NACL: Stateless subnet-level firewall
- Security Group: Stateful instance-level firewall

---

## Learning Outcome
- Designing secure multi-tier architecture
- Configuring routing and gateways
- Understanding public vs private subnet isolation
- Implementing secure SSH tunneling
- Practical AWS networking and security management
