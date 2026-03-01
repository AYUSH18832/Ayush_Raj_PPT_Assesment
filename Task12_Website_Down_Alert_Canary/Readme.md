# Task 12: Website Down Alert using Lambda (Canary) + SNS

## Objective
Monitor website availability and automatically send alerts when the website is down using CloudWatch Synthetics Canary, Lambda, and SNS.

## Environment
- AWS CloudWatch Synthetics (Canary)
- AWS Lambda
- Amazon SNS
- IAM Role

## Simple Definition
A Canary continuously checks website uptime at fixed intervals. If the website becomes unavailable, a Lambda function triggers an SNS notification to send an alert email.

---

## Architecture Flow

CloudWatch Canary → CloudWatch Alarm → Lambda → SNS → Email Alert

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
  - Confirm subscription from inbox

---

### 2. Create Canary (Website Monitoring)

- Go to CloudWatch → Synthetics Canaries
- Click "Create canary"
- Choose blueprint: Heartbeat monitoring
- Enter website URL
- Set schedule (e.g., every 1 or 5 minutes)
- Create or attach IAM role
- Deploy canary

The Canary will continuously check website response status.

---

### 3. Create CloudWatch Alarm

- Go to CloudWatch → Alarms
- Create alarm for Canary metric:
  - Metric: Failed executions or 5XX errors
- Set threshold (e.g., ≥ 1 failure)
- Configure alarm action:
  - Trigger Lambda function

---

### 4. Create Lambda Function for Alert

- Go to AWS Console → Lambda
- Create function (Python runtime)
- Attach IAM Role with SNS publish permissions
- Add code:

```python
import boto3

sns = boto3.client('sns')
TOPIC_ARN = 'your-sns-topic-arn'

def lambda_handler(event, context):
    message = "Website is DOWN. Immediate attention required."
    
    sns.publish(
        TopicArn=TOPIC_ARN,
        Subject='Website Down Alert',
        Message=message
    )

    return {
        'statusCode': 200,
        'body': message
    }
```

Replace `your-sns-topic-arn` with actual ARN.

Deploy function.

---

### 5. Link Alarm to Lambda
- Edit CloudWatch Alarm
- Add Lambda function as alarm action
- Save configuration

---

### 6. Test the System
- Stop web server or provide incorrect URL
- Canary detects failure
- Alarm triggers
- Lambda executes
- SNS sends email alert

---

## Key Concepts

- Canary Monitoring: Synthetic uptime testing
- CloudWatch Alarm: Monitors metrics and triggers actions
- Lambda: Serverless alert logic
- SNS: Notification delivery system
- Automated Monitoring: No manual intervention required

---

## Learning Outcome
- Implementing website uptime monitoring
- Configuring automated alert systems
- Integrating CloudWatch, Lambda, and SNS
- Understanding event-driven monitoring architecture
