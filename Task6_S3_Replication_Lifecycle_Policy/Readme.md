# Task 6: S3 Replication and Lifecycle Policy

## Objective
Configure S3 Replication and Lifecycle policies to understand backup strategies and cost optimization in AWS.

## Environment
- AWS S3
- Versioning enabled buckets
- IAM Role for replication

## Simple Definition
S3 Replication automatically copies objects from one bucket to another (same or different region) for backup and disaster recovery.  
Lifecycle policies automatically transition or delete objects based on defined rules to reduce storage costs.

---

## Implementation Steps

### 1. Create Source and Destination Buckets
- Go to AWS Console → S3
- Create two buckets (source and destination)
- Ensure bucket names are globally unique

---

### 2. Enable Versioning
- Open both buckets
- Go to Properties
- Enable "Bucket Versioning"
- Save changes

Versioning is mandatory for replication.

---

### 3. Configure Replication

- Open Source Bucket
- Go to Management → Replication Rules
- Click "Create replication rule"
- Select destination bucket
- Create or select IAM Role for replication
- Choose objects to replicate (entire bucket or specific prefix)
- Save rule

After configuration, new objects uploaded to the source bucket will automatically replicate to the destination bucket.

---

### 4. Configure Lifecycle Policy

- Open Source Bucket
- Go to Management → Lifecycle Rules
- Click "Create lifecycle rule"
- Define rule scope (entire bucket or prefix)
- Configure actions such as:
  - Transition to Standard-IA after X days
  - Transition to Glacier after X days
  - Expire objects after X days
- Save rule

---

## Verification
- Upload a file to source bucket
- Confirm object appears in destination bucket (replication)
- Verify lifecycle transition status in object properties after defined period

---

## Key Concepts

- Versioning: Maintains multiple versions of objects.
- Replication: Automatic backup to another bucket.
- Lifecycle Policy: Automated storage class transition and deletion.
- Cost Optimization: Moving infrequently accessed data to cheaper storage classes.

---

## Learning Outcome
- Implementation of cross-bucket replication
- Understanding of disaster recovery strategy
- Automated storage cost management using lifecycle rules
- Practical experience with S3 data management
