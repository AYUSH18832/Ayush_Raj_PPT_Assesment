# Task 14: CloudWatch Alarm (70% CPU → Auto Stop + Email)

## Objective
Create a CloudWatch Alarm that monitors EC2 CPU utilization and automatically stops the instance and sends an email notification when CPU usage exceeds 70%.

## Environment
- Amazon EC2
- Amazon CloudWatch
- Amazon SNS
- IAM Role

## Simple Definition
A CloudWatch Alarm monitors EC2 CPU usage. When CPU exceeds 70%, the alarm triggers two actions:
1. Stops the EC2 instance automatically.
2. Sends an email alert using SNS.

---

## Architecture Flow

EC2 → CloudWatch Metric → CloudWatch Alarm → (EC2 Stop Action + SNS Email)

---

## Implementation Steps

### 1. Create SNS Topic
- Go to AWS Console → SNS
- Click "Create topic"
- Select Standard
- Provide topic name
- Create topic
- Create subscription:
  - Protocol: Email
  - Enter email address
  - Confirm subscription

---

### 2. Create CloudWatch Alarm

- Go to CloudWatch → Alarms
- Click "Create alarm"
- Select metric:
  - EC2 → Per-Instance Metrics → CPUUtilization
- Select your EC2 instance
- Configure threshold:
  - Static threshold
  - CPU ≥ 70%
  - For 2 consecutive periods (recommended)
- Click Next

---

### 3. Configure Alarm Actions

Add two actions:

1. EC2 Action:
   - Choose "Stop this instance"

2. SNS Notification:
   - Select created SNS topic

Complete alarm creation.

---

### 4. Test the Alarm

- Generate CPU load on EC2 (e.g., stress tool)
- Wait until CPU exceeds 70%
- Alarm changes to ALARM state
- EC2 instance stops automatically
- Email notification is sent via SNS

---

## Key Concepts

- CloudWatch Metric: Monitors resource performance.
- Alarm: Triggers actions based on thresholds.
- SNS: Sends notifications.
- Automated Response: No manual intervention required.
- Infrastructure Monitoring: Proactive system management.

---

## Learning Outcome
- Monitoring EC2 performance metrics
- Creating automated infrastructure actions
- Integrating CloudWatch with SNS
- Implementing self-healing and automated shutdown mechanisms
- Understanding cloud-based monitoring and alerting systems
