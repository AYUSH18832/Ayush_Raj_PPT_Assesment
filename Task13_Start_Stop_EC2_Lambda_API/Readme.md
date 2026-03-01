# Task 13: Start/Stop EC2 using Lambda + API Gateway

## Objective
Automate EC2 instance start and stop operations using AWS Lambda triggered through API Gateway.

## Environment
- AWS Lambda (Python)
- API Gateway (HTTP API)
- Amazon EC2
- IAM Role

## Simple Definition
An API endpoint triggers a Lambda function that starts or stops an EC2 instance based on the request body. This demonstrates serverless automation using API Gateway and Lambda.

---

## Architecture Flow

Client (HTTP Request) → API Gateway → Lambda → EC2

---

## Implementation Steps

### 1. Create IAM Role for Lambda
- Go to IAM → Roles
- Create role for Lambda
- Attach policy:
  - AmazonEC2FullAccess (or custom policy allowing StartInstances and StopInstances)
- Create role

---

### 2. Create Lambda Function

- Go to AWS Console → Lambda
- Click "Create function"
- Runtime: Python 3.x
- Attach IAM role created above

Replace default code with:

```python
import json
import boto3

ec2 = boto3.client('ec2')

def lambda_handler(event, context):
    
    instance_id = "i-0a76180e666adf0c8"  # Replace with your instance ID
    
    body = json.loads(event.get("body", "{}"))
    action = body.get("action")
    
    if action == "start":
        ec2.start_instances(InstanceIds=[instance_id])
        return {
            'statusCode': 200,
            'body': json.dumps("EC2 instance started successfully")
        }
    
    elif action == "stop":
        ec2.stop_instances(InstanceIds=[instance_id])
        return {
            'statusCode': 200,
            'body': json.dumps("EC2 instance stopped successfully")
        }
    
    else:
        return {
            'statusCode': 400,
            'body': json.dumps("Invalid action. Use start or stop.")
        }
```

Deploy the function.

---

### 3. Create API Gateway

- Go to API Gateway
- Create HTTP API
- Add integration → Select Lambda function
- Create route:
  - Method: POST
  - Path: /control
- Deploy API
- Copy the Invoke URL

---

### 4. Test API using Curl

Start EC2 instance:

```bash
curl -X POST https://your-api-id.execute-api.us-east-1.amazonaws.com/control \
-H "Content-Type: application/json" \
-d '{"action":"start"}'
```

Stop EC2 instance:

```bash
curl -X POST https://your-api-id.execute-api.us-east-1.amazonaws.com/control \
-H "Content-Type: application/json" \
-d '{"action":"stop"}'
```

Successful response example:

```
"EC2 instance stopped successfully."
```

---

## Key Concepts

- API Gateway: Creates REST/HTTP endpoints.
- Lambda: Executes serverless logic.
- IAM Role: Grants EC2 control permissions.
- EC2 Automation: Start/Stop without manual console access.
- Event-driven architecture: Triggered via API call.

---

## Learning Outcome
- Creating Lambda functions with EC2 control logic
- Integrating Lambda with API Gateway
- Implementing serverless automation
- Managing EC2 instances programmatically
- Understanding role-based permission control
