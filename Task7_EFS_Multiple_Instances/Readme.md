# Task 7: Create EFS and Connect to Multiple Ubuntu Instances

## Objective
Create an Amazon EFS file system and mount it across multiple EC2 instances to enable shared storage.

## Environment
- AWS EC2 (Amazon Linux & Ubuntu)
- Amazon EFS
- NFS Protocol

## Simple Definition
Amazon EFS (Elastic File System) provides scalable shared storage that can be mounted simultaneously on multiple EC2 instances.

---

## Implementation Steps

### 1. Create EFS File System
- Go to AWS Console → EFS
- Click "Create file system"
- Select VPC
- Configure mount targets in required Availability Zones
- Attach security group allowing NFS (Port 2049)

---

### 2. Mount EFS on Amazon Linux Instance

Update system:
```bash
sudo yum update -y
```

Install EFS utilities:
```bash
sudo yum install -y amazon-efs-utils
```

Create mount directory:
```bash
mkdir disk
```

Mount EFS:
```bash
sudo mount -t efs -o tls fs-024a48b682043418e:/ disk
```

Create test file:
```bash
cd disk
sudo nano a.txt
```

---

### 3. Mount EFS on Ubuntu Instance

Update system:
```bash
sudo apt update
```

Install NFS client:
```bash
sudo apt-get -y install nfs-common
```

Create mount directory:
```bash
mkdir disk
```

Mount EFS:
```bash
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-024a48b682043418e.efs.us-east-1.amazonaws.com:/ disk
```

Verify shared file:
```bash
cd disk
ls
cat a.txt
```

If configuration is correct, the file created in Amazon Linux will be visible in Ubuntu instance.

---

## Key Concepts

- EFS: Managed scalable file storage.
- NFS: Network File System protocol used to mount EFS.
- Shared Storage: Multiple EC2 instances access same data.
- High Availability: EFS supports multi-AZ access.

---

## Learning Outcome
- Creation and configuration of EFS
- Mounting shared storage on multiple EC2 instances
- Understanding scalable and distributed file systems in AWS
- Practical implementation of shared storage architecture
