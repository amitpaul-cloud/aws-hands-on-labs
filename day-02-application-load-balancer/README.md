# Day 2 - AWS Application Load Balancer (ALB)

## Objective

Learn how to configure an AWS Application Load Balancer (ALB) to distribute HTTP traffic across multiple Amazon EC2 instances.

---

## Services Used

- Amazon EC2
- Application Load Balancer (ALB)
- Target Group
- Security Groups
- Amazon Linux 2023
- Apache HTTP Server (httpd)

---

## Architecture


                Client
                   │
                   ▼
     Application Load Balancer (ALB)
                   │
        ┌──────────┼──────────┐
        ▼          ▼          ▼
     Server A    Server B    Server C
     (Apache)    (Apache)    (Apache)


---

## Practical Steps

### Step 1

Created three Amazon Linux 2023 EC2 instances.

---

### Step 2

Installed and started the Apache Web Server on all EC2 instances.

```bash
sudo yum install httpd -y
sudo systemctl enable --now httpd
```

---

### Step 3

Created different web pages on each EC2 instance.

#### Server A

Welcome to Server A
---

#### Server B

Welcome to Server B
---

#### Server C

Welcome to Server C
---

### Step 4

Created a Target Group with the following configuration:

- **Target Type:** Instance
- **Protocol:** HTTP
- **Port:** 80

---

### Step 5

Registered all three EC2 instances with the Target Group.

---

### Step 6

Verified the Target Group health checks.

- All registered targets became **Healthy**.

---

### Step 7

Created an Internet-facing Application Load Balancer.

Configuration:

- **Scheme:** Internet-facing
- **Listener:** HTTP (Port 80)

---

### Step 8

Associated the Target Group with the Application Load Balancer.

---

### Step 9

Accessed the ALB DNS name from a web browser.

Observed that incoming requests were distributed across all three EC2 instances:

- Welcome to Server A
- Welcome to Server B
- Welcome to Server C

---

## Commands Used

sudo yum install httpd -y

sudo systemctl enable --now httpd

echo "Welcome to Server A" > /var/www/html/index.html

echo "Welcome to Server B" > /var/www/html/index.html

echo "Welcome to Server C" > /var/www/html/index.html

systemctl status httpd

---

## Key Learnings

- Learned how an Application Load Balancer distributes incoming traffic.
- Understood the purpose of Target Groups.
- Configured Apache Web Server on multiple EC2 instances.
- Registered EC2 instances with a Target Group.
- Verified target health using Health Checks.
- Tested load balancing using the ALB DNS name.
- Understood how ALB improves application availability and scalability.

---

## Result

Successfully configured an AWS Application Load Balancer (ALB) to distribute HTTP traffic across multiple Amazon EC2 instances. Verified that traffic was routed successfully to all healthy targets.

---
