# Task 17: DynamoDB Table Creation (Basic)

## Objective
Create a DynamoDB table and insert sample items to understand NoSQL and serverless database concepts.

## Environment
- Amazon DynamoDB
- AWS Management Console
- AWS CLI (optional)

## Simple Definition
Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability.

---

## Implementation Steps

### 1. Create DynamoDB Table

- Go to AWS Console → DynamoDB
- Click **Create Table**
- Table Name: `Employees`
- Partition Key: `EmployeeID` (Number or String)
- Leave default settings (On-Demand capacity mode recommended)
- Click **Create Table**

Wait until table status becomes **Active**.

---

### 2. Insert Sample Items (Console Method)

- Open the created table
- Go to **Explore Table Items**
- Click **Create Item**
- Add sample data:

Example Item 1:
```
EmployeeID: 1
Name: Ayush
Department: Security
Salary: 60000
```

Example Item 2:
```
EmployeeID: 2
Name: Rahul
Department: DevOps
Salary: 55000
```

---

### 3. Insert Items Using AWS CLI (Optional)

```bash
aws dynamodb put-item \
--table-name Employees \
--item '{
  "EmployeeID": {"N": "3"},
  "Name": {"S": "Priya"},
  "Department": {"S": "Cloud"},
  "Salary": {"N": "65000"}
}'
```

---

## Key Concepts

- NoSQL Database: Non-relational database model
- Partition Key: Primary key used to uniquely identify items
- On-Demand Mode: Automatic scaling based on traffic
- Serverless: No server management required

---

## Learning Outcome

- Creating DynamoDB table
- Understanding partition keys
- Inserting and managing items
- Basic understanding of NoSQL and serverless databases
