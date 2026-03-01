# Task 18: Azure Virtual Machine (Easy Task)

## Objective
Launch and configure a basic Azure Virtual Machine and access it via SSH or RDP.

## Environment
- Microsoft Azure Portal
- Azure Virtual Machine
- SSH (Linux) / RDP (Windows)

## Simple Definition
Azure Virtual Machine is an on-demand scalable compute resource that allows users to run applications in the cloud.

---

## Implementation Steps

### 1. Create Virtual Machine
- Go to Azure Portal → Virtual Machines
- Click **Create**
- Choose:
  - Subscription
  - Resource Group
  - VM Name
  - Region
  - Image (Ubuntu/Windows)
- Select Size (Free tier if available)
- Configure Authentication:
  - SSH key (Linux) or
  - Username & Password (Windows)
- Review and Create

---

### 2. Connect to VM
- For Linux: Use SSH
- For Windows: Use RDP
- Verify successful login

---

## Learning Outcome
- Understanding Azure compute service
- Creating and managing VMs
- Secure remote access configuration
