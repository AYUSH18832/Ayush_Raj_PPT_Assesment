# Task 20: Azure VNet (Basic Networking Practical)

## Objective
Configure a Virtual Network with subnets and basic NSG rules.

## Environment
- Azure Virtual Network (VNet)
- Subnets
- Network Security Group (NSG)

## Simple Definition
Azure Virtual Network enables secure communication between Azure resources and the internet.

---

## Implementation Steps

### 1. Create Virtual Network
- Go to Azure Portal → Virtual Networks
- Click **Create**
- Configure:
  - Address space (e.g., 10.0.0.0/16)
  - Subnet (e.g., 10.0.1.0/24)

---

### 2. Configure NSG
- Create Network Security Group
- Add inbound rule:
  - Allow SSH (Port 22) or RDP (Port 3389)
- Associate NSG with subnet or VM

---

## Learning Outcome
- Understanding Azure networking basics
- Creating subnets
- Managing traffic using NSG rules
