# Access S3 from Ubuntu using IAM Roles & Policies

Configured an IAM Role and attached it to an Ubuntu EC2 instance to securely access Amazon S3 without using access keys.

## Project Structure
.
├── README.md
├── command.txt
└── Screenshots
    ├── 01_IAM_Role_Created.png
    └── 02_S3_Access_Command_Output.png

## IAM Role Details
| Field | Value |
|-------|-------|
| Role Name | EC2_S3_Access_Role |
| Trusted Entity | EC2 |
| Policy Attached | AmazonS3FullAccess |

## EC2 Instance Details
| Instance Name | Instance ID | Private IP | IAM Role |
|---------------|------------|------------|----------|
| ubuntu_s3 | i-xxxxxxxxxxxx | 172.31.xx.xx | EC2_S3_Access_Role |

## What Was Done

### Step 1 — Created IAM Role
AWS Console → IAM → Roles → Create Role  
Trusted entity: EC2  
Attached Policy: AmazonS3FullAccess  
Role Name: EC2_S3_Access_Role  

### Step 2 — Attached Role to EC2
EC2 → Instances → Select Ubuntu Instance  
Actions → Security → Modify IAM Role  
Selected: EC2_S3_Access_Role  

### Step 3 — Verified IAM Role from EC2
Checked role metadata and S3 access using AWS CLI.

### Step 4 — Tested S3 Access
Created bucket, uploaded file, and verified upload.

## Screenshots

**01 — IAM Role Created**  
Shows EC2_S3_Access_Role with AmazonS3FullAccess policy attached.

**02 — S3 Access Command Output**  
Shows `aws s3 ls` output and successful upload of `test.txt`.

## Result

Ubuntu EC2 instance successfully accessed Amazon S3 using IAM Role authentication.  
No access keys were used, demonstrating secure role-based access control.
