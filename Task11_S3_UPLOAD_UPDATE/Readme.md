# Task 11: S3 Upload Email Notification (Lambda + SNS)

## Objective
Trigger an email notification automatically when a file is uploaded to an S3 bucket using Lambda and SNS.

## Environment
- AWS S3
- AWS Lambda (Python)
- Amazon SNS
- IAM Role

## Simple Definition
When a file is uploaded to S3, an event triggers a Lambda function, which sends an email notification using SNS. This demonstrates event-driven architecture in AWS.

---

## Architecture Flow

S3 (Upload Event) → Lambda Function → SNS Topic → Email Notification

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
  - Confirm subscription from email inbox

---

### 2. Create Lambda Function
- Go to AWS Console → Lambda
- Click "Create function"
- Choose Author from scratch
- Runtime: Python 3.x
- Attach IAM Role with:
  - AmazonSNSFullAccess (or custom publish policy)
  - S3 read permissions (if required)

---

### 3. Add Lambda Code

Replace default code with:

```python
import json
import boto3

sns = boto3.client('sns')
TOPIC_ARN = 'arn:aws:sns:us-east-1:200642811988:Email'

def lambda_handler(event, context):
    records = event.get('Records', [])
    
    messages = []
    for record in records:
        event_name = record['eventName']
        bucket = record['s3']['bucket']['name']
        object_key = record['s3']['object']['key']
        
        msg = f"Event: {event_name}\nBucket: {bucket}\nObject: {object_key}"
        messages.append(msg)
    
    final_message = "\n\n".join(messages)

    sns.publish(
        TopicArn=TOPIC_ARN,
        Subject='S3 Event Notification',
        Message=final_message
    )

    return {
        'statusCode': 200,
        'body': final_message
    }
```

Update `TOPIC_ARN` with your SNS Topic ARN.

Deploy the function.

---

### 4. Configure S3 Event Trigger
- Go to S3 → Select bucket
- Open Properties
- Scroll to Event notifications
- Click "Create event notification"
- Event type: All object create events
- Destination: Lambda function
- Select created Lambda
- Save configuration

---

### 5. Test the Setup
- Upload a file to the S3 bucket
- Lambda function is triggered automatically
- SNS sends email notification
- Check inbox for event details

---

## Key Concepts

- Event-Driven Architecture: Services react automatically to events.
- S3 Event Notification: Triggers Lambda on object upload.
- Lambda: Serverless compute service.
- SNS: Messaging and notification service.
- IAM Role: Grants permissions to Lambda.

---

## Learning Outcome
- Integration of S3, Lambda, and SNS
- Building serverless event-driven workflows
- Automated notifications using AWS services
- Practical implementation of cloud automation
