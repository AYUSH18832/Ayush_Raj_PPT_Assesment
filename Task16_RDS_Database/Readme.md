# Task 16: RDS Database + SQL Workbench Connection & Queries

## Objective
Create and connect to an Amazon RDS managed relational database and execute basic SQL queries using MySQL Workbench.

## Environment
- Amazon RDS (MySQL)
- MySQL Workbench
- EC2 (optional for testing connectivity)
- VPC & Security Groups

## Simple Definition
Amazon RDS is a managed relational database service that simplifies database setup, operation, scaling, and maintenance in the cloud.

---

## Implementation Steps

### 1. Launch RDS Instance

- Go to AWS Console → RDS
- Click **Create Database**
- Engine: MySQL
- Deployment: Free Tier (if applicable)
- Configure:
  - DB Instance Identifier
  - Master Username & Password
- Enable Public Access (if connecting from local system)
- Configure Security Group:
  - Allow inbound MySQL (Port 3306)
- Create database

Wait until status shows **Available**.

---

### 2. Connect Using MySQL Workbench

- Open MySQL Workbench
- Create new connection:
  - Hostname: RDS Endpoint
  - Port: 3306
  - Username: Master username
  - Password: Configured password
- Test connection
- Connect to database

---

## SQL Queries Executed

```sql
CREATE DATABASE company;
USE company;

CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    department VARCHAR(100),
    salary INT
);

INSERT INTO employees (name, department, salary)
VALUES 
('Ayush', 'Security', 60000),
('Rahul', 'DevOps', 55000),
('Priya', 'Cloud', 65000);

SELECT * FROM employees;
```

---

## Query Output

```
+----+--------+------------+--------+
| id | name   | department | salary |
+----+--------+------------+--------+
|  1 | Ayush  | Security   | 60000  |
|  2 | Rahul  | DevOps     | 55000  |
|  3 | Priya  | Cloud      | 65000  |
+----+--------+------------+--------+
```

---

## Key Concepts

- RDS: Managed relational database service
- Endpoint: Database connection URL
- Security Group: Controls database access
- Port 3306: Default MySQL port
- Managed Service: AWS handles backups, patching, and maintenance

---

## Learning Outcome

- Launching and configuring Amazon RDS
- Connecting to managed database using MySQL Workbench
- Creating database and tables
- Performing INSERT and SELECT operations
- Understanding managed database architecture
```
