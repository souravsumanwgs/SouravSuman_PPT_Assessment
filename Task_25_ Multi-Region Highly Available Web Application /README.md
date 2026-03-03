 — Multi-AZ Highly Available Web Application (AWS)

## 📌 Objective

Deploy a fault-tolerant web application across multiple Availability Zones using:

* Amazon VPC
* Internet Gateway
* NAT Gateway
* Amazon EC2
* Application Load Balancer
* Auto Scaling Group
* Amazon S3
* Amazon CloudWatch

Region Used: US East (N. Virginia)

---

# 🏗 Architecture Overview

High Availability architecture designed across **2 Availability Zones**.

### AZ us-east-1a

* Public Subnet (10.0.1.0/24)
* Private Subnet (10.0.3.0/24)
* NAT Gateway

### AZ us-east-1b

* Public Subnet (10.0.2.0/24)
* Private Subnet (10.0.4.0/24)

### Traffic Flow

User → ALB → EC2 (Private Subnets)
Private EC2 → NAT Gateway → Internet

---

# 🔹 Step 1 — Create Custom VPC

VPC CIDR:
10.0.0.0/16

Name:
HA-vpc

---

# 🔹 Step 2 — Create Public Subnets

Public-Subnet-1
AZ: us-east-1a
CIDR: 10.0.1.0/24

Public-Subnet-2
AZ: us-east-1b
CIDR: 10.0.2.0/24

---

# 🔹 Step 3 — Create Private Subnets

Private-Subnet-1a
AZ: us-east-1a
CIDR: 10.0.3.0/24

Private-Subnet-1b
AZ: us-east-1b
CIDR: 10.0.4.0/24

---

# 🔹 Step 4 — Attach Internet Gateway

Created Internet Gateway and attached to HA-vpc.

Configured Public Route Table:

0.0.0.0/0 → Internet Gateway

Associated with:

* Public-Subnet-1
* Public-Subnet-2

---

# 🔹 Step 5 — Create NAT Gateway

Created NAT Gateway in:

Public-Subnet-1 (us-east-1a)

Allocated Elastic IP.

---

# 🔹 Step 6 — Configure Private Route Table

Added Route:

0.0.0.0/0 → NAT Gateway

Associated with:

* Private-Subnet-1a
* Private-Subnet-1b

---

# 🔹 Step 7 — Launch EC2 Instances

Launched 2 EC2 instances inside Private Subnets.

Security Group Rules:

* Allow HTTP (80) from ALB Security Group
* Allow SSH (optional for testing)

---

# 🔹 Step 8 — Create Application Load Balancer

* Internet-facing ALB
* Placed in Public Subnets
* Created Target Group
* Registered EC2 instances

---

# 🔹 Step 9 — Configure Auto Scaling Group

* Minimum capacity: 2
* Desired capacity: 2
* Multi-AZ deployment
* Attached to Target Group

---

# 🔹 Step 10 — Create S3 Bucket

Used for storing static assets (images, CSS, etc.)

---

# 🔹 Step 11 — Configure CloudWatch Alarm

Configured CPU Utilization Alarm:

Trigger Condition:
CPU > 70%

Linked with Auto Scaling policy.

---

# ✅ Final Result

✔ Multi-AZ High Availability Architecture
✔ Public access via ALB DNS
✔ Private EC2 instances secured
✔ NAT for outbound internet
✔ Auto Scaling enabled
✔ Monitoring via CloudWatch

---

# 📊 Key Learnings

* Proper CIDR planning prevents subnet overlap
* NAT Gateway must be deployed in Public Subnet
* Private Subnets require dedicated Route Table
* Multi-AZ improves fault tolerance
* Load Balancer distributes traffic efficiently

---

# 📷 Proof Required (Screenshots)

* VPC & Subnet configuration
* Route Table with NAT route
* NAT Gateway (Available state)
* ALB DNS working
* Auto Scaling Group running
* CloudWatch Alarm configured

---

# 🎯 Conclusion

Successfully deployed a highly available and fault-tolerant web application architecture on AWS using industry best practices and multi-AZ design principles.
