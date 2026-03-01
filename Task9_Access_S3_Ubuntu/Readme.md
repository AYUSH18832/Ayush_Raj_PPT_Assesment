# Task 9: Access S3 from Ubuntu using IAM Roles & Policies

## Objective
Access Amazon S3 securely from an EC2 Ubuntu instance using IAM Roles instead of access keys.

## Environment
- AWS EC2 (Ubuntu)
- AWS IAM Role
- Amazon S3
- AWS CLI

## Simple Definition
IAM Roles allow EC2 instances to securely access AWS services like S3 without storing access keys. Permissions are attached to the role and automatically inherited by the instance.

---

## Implementation Steps

### 1. Create IAM Role
- Go to AWS Console → IAM → Roles
- Click "Create role"
- Select Trusted Entity: EC2
- Attach required policy (e.g., AmazonS3FullAccess or custom S3 policy)
- Create role

---

### 2. Attach IAM Role to EC2 Instance
- Go to EC2 → Instances
- Select instance
- Click Actions → Security → Modify IAM Role
- Attach the created role
- Save changes

---

### 3. Install AWS CLI on Ubuntu

Update system:
```bash
sudo apt update
```

Download AWS CLI:
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

Install unzip:
```bash
sudo apt install unzip -y
```

Extract package:
```bash
unzip awscliv2.zip
```

Install AWS CLI:
```bash
sudo ./aws/install
```

Verify installation:
```bash
aws --version
```

---

### 4. Test S3 Access

List S3 buckets:
```bash
aws s3 ls
```

Create test file:
```bash
echo "Hello from EC2 IAM Role" > test.txt
```

Upload file to S3:
```bash
aws s3 cp test.txt s3://ec2tos3task9/
```

Verify upload:
```bash
aws s3 ls s3://ec2tos3task9/
```

If configured correctly, the file will be uploaded without configuring access keys.

---

## Key Concepts

- IAM Role: Temporary credentials assigned to EC2.
- Policy: Defines allowed actions on AWS resources.
- Role-based Access: Secure alternative to storing access keys.
- Least Privilege Principle: Grant only required S3 permissions.

---

## Learning Outcome
- Creation and attachment of IAM Role to EC2
- Secure S3 access without access keys
- AWS CLI installation and configuration
- Practical understanding of role-based access control in AWS
