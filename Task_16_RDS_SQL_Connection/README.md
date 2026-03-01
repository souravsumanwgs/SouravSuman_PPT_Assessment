 RDS Database + SQL Workbench Connection & Queries

## Objective
- Create and connect to a managed relational database using **Amazon RDS**.
- Understand how managed database services work and practice running SQL queries.
- Learn how to connect securely via **MySQL Workbench**, including using an **EC2 instance as a jump host** if needed.

## Simple Definition
Amazon RDS is a managed relational database service that handles database provisioning, patching, backups, and scaling. Using RDS, you can focus on data and queries without managing database servers.

---

## Steps Performed

### **1. Create RDS Database**
1. Open AWS Console → **RDS → Databases → Create database**.  
2. Selected **Engine**: MySQL Community.  
3. DB instance identifier: `database-1`  
4. DB instance class: `db.t4g.micro`  
5. Allocated storage: `20 GB`  
6. Master username: `admin`  
7. Set **Master password** and confirm.  
8. Ensure **Public accessibility**: **Yes** (if you want direct connection)  
9. Default VPC, security group `default`.  
10. Click **Create Database**. Wait until status is **Available**.

**Screenshot 1:** RDS Database creation page  
![RDS Creation](./screenshots/rds_creation.png)

---

### **2. Configure Security Groups**
1. Go to **EC2 → Security Groups → launch-wizard-6**  
2. Edit **Inbound rules**:  

| Type         | Protocol | Port | Source          |
|--------------|----------|------|----------------|
| SSH          | TCP      | 22   | 0.0.0.0/0      |
| HTTP         | TCP      | 80   | 0.0.0.0/0      |
| MySQL/Aurora | TCP      | 3306 | Your Laptop IP |

3. Save the changes.  
4. Make sure the **RDS security group** allows inbound **3306** from EC2 private IP if RDS is private.

**Screenshot 2:** Security group inbound rules with MySQL port  
![Security Group](./screenshots/security_group.png)

---

### **3. Connect via MySQL Workbench**

#### Option 1: Direct Connection (Public RDS)
1. Open MySQL Workbench → **New Connection**  
2. Use **Standard TCP/IP** method:

| Field       | Value |
|-------------|-------|
| Hostname    | `database-1.c2lsuo8gidj5.us-east-1.rds.amazonaws.com` |
| Port        | 3306  |
| Username    | admin |
| Password    | Your RDS master password |

3. Test connection → should succeed.  

#### Option 2: SSH Tunnel via EC2 (for private RDS)
1. Open MySQL Workbench → **New Connection → Standard TCP/IP over SSH**  
2. Fill in:

| Field           | Value |
|-----------------|-------|
| SSH Hostname    | `ec2-18-213-247-128.compute-1.amazonaws.com` |
| SSH Username    | ec2-user (Amazon Linux) / ubuntu (Ubuntu AMI) |
| SSH Key File    | Your `.pem` private key for EC2 |
| MySQL Hostname  | `database-1.c2lsuo8gidj5.us-east-1.rds.amazonaws.com` |
| MySQL Server Port | 3306 |
| Username        | admin |
| Password        | Your RDS master password |

3. Click **Test Connection** → should succeed.

**Screenshot 3:** MySQL Workbench connection successful  
![MySQL Connection](./screenshots/workbench_connection.png)

---

### **4. Run SQL Queries**
Once connected, run:

```sql
-- Create a new database
CREATE DATABASE StudentDB;
USE StudentDB;

-- Create a table
CREATE TABLE Students (
    ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT,
    Grade VARCHAR(5)
);

-- Insert data
INSERT INTO Students (ID, Name, Age, Grade) VALUES
(1, 'Alice', 18, 'A'),
(2, 'Bob', 19, 'B'),
(3, 'Charlie', 17, 'A');

-- Retrieve data
SELECT * FROM Students;
