# Task 2: Disk Partitioning (MBR – Linux & GPT – Windows)

## Objective
Create and manage disk partitions using MBR (Linux) and GPT (Windows).

---

## Linux – MBR Partitioning (Using fdisk)

### 1. Check Available Disks
```bash
lsblk
```

### 2. Open Disk
```bash
sudo fdisk /dev/nvme1n1
```

### 3. Create New Partition (Inside fdisk)
```
m        # help
n        # new partition
1        # partition number
+10G     # partition size
w        # write changes & exit
```

### 4. Verify Partition
```bash
lsblk
```

---

## Windows – GPT Partitioning

### Steps:
1. Open Disk Management  
2. Right-click unallocated space  
3. Select "New Simple Volume."  
4. Assign size and drive letter  
5. Format with NTFS  
6. (If required) Convert disk to GPT  

---

## MBR vs GPT Comparison

| Feature | MBR | GPT |
|----------|------|------|
| Max Partitions | 4 Primary | 128+ |
| Max Disk Size | 2 TB | 9.4 ZB |
| Boot Mode | BIOS | UEFI |

---

## Learning Outcome
- EC2 configuration and SSH access
- Nginx web server deployment
- Linux disk partitioning using fdisk
- Windows disk management (GPT)
