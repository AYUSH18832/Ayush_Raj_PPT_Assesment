# Task 1: Static Web Hosting on EC2 (Ubuntu + Nginx)

## Objective
Deploy a static website on an Ubuntu EC2 instance using Nginx.

## Environment
- AWS EC2 (Ubuntu Server)
- Nginx Web Server
- SSH Access

## Steps Performed

### 1. Connect to EC2 via SSH
```bash
ssh -i key.pem ubuntu@<public-ip>
```

### 2. Update System
```bash
sudo apt update
```

### 3. Install Nginx
```bash
sudo apt install nginx -y
```

### 4. Clone Project Repository
```bash
git clone https://github.com/AYUSH18832/codelab0.1.git
```

### 5. Deploy Website Files
```bash
sudo cp -r codelab0.1/* /var/www/html/
```

### 6. Restart Nginx
```bash
sudo systemctl restart nginx
```

## 🌐 Output
- EC2 instance running
- HTTP (Port 80) enabled
- Website accessible via Public IP
