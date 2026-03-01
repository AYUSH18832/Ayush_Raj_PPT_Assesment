# Task 8: Create IAM Users and Groups

## Objective
Create IAM users and groups, and assign appropriate policies to understand access control and security management in AWS.

## Environment
- AWS IAM (Identity and Access Management)

## Simple Definition
IAM allows you to securely manage users, groups, and permissions in AWS by attaching policies that define what actions are allowed or denied.

---

## Implementation Steps

### 1. Create IAM Group
- Open AWS Console → IAM
- Go to "User Groups"
- Click "Create group"
- Provide group name (e.g., Developers or Admins)
- Attach required policies (e.g., AmazonS3FullAccess, AmazonEC2ReadOnlyAccess)
- Create group

---

### 2. Create IAM User
- Go to IAM → Users
- Click "Create user"
- Enter username
- Select access type:
  - Management Console access
  - Programmatic access (optional)
- Add user to previously created group
- Create user

---

### 3. Attach Policies (If Required Individually)
- Open the user
- Go to "Permissions"
- Click "Add permissions"
- Attach policy directly if needed

---

### 4. Verify Access
- Sign in using IAM user credentials
- Confirm access based on assigned permissions
- Test allowed and restricted actions

---

## Key Concepts

- IAM User: Individual identity with specific permissions.
- IAM Group: Collection of users with shared permissions.
- Policy: JSON document defining allowed or denied actions.
- Principle of Least Privilege: Grant only required permissions.

---

## Learning Outcome
- User and group creation in IAM
- Policy attachment and permission management
- Understanding of access control and security best practices
- Practical experience with AWS identity management
