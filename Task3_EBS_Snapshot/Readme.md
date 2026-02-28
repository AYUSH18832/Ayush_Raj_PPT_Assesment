# Task 3: Attach EBS Volume from Different AZ using Snapshot

## Objective
Create an EBS snapshot and restore it in a different Availability Zone (AZ), then attach the new volume to an EC2 instance.

## Environment
- AWS EC2
- Amazon EBS
- Ubuntu Server

## Simple Definition
EBS volumes cannot be directly attached across different Availability Zones. To move data across AZs, a snapshot is created and then restored as a new volume in the target AZ.

---

## Implementation Steps

### 1. Create Snapshot of Existing Volume
- Open AWS Console
- Go to EC2 → Volumes
- Select the volume
- Click "Create Snapshot"
- Add description and create snapshot

### 2. Create New Volume in Different AZ
- Go to EC2 → Snapshots
- Select the created snapshot
- Click "Create Volume"
- Choose a different Availability Zone
- Create volume

### 3. Attach New Volume to EC2 Instance
- Go to EC2 → Volumes
- Select the newly created volume
- Click "Attach Volume"
- Choose EC2 instance in the same AZ
- Attach using device name (e.g., /dev/sdf)

- ## Learning Outcome
- Understanding of EBS snapshots
- Cross-AZ storage handling
- Volume attachment and mounting in Linux
- Practical AWS storage management
