 — IAM + RBAC + Least Privilege (AWS + Azure)

## Objective
Implement **role-based access control (RBAC)** with the **least privilege principle** in both **AWS** and **Azure**:
- AWS: Allow EC2 full access but deny S3 delete actions
- Azure: Assign Reader and Contributor roles to control access

---

## Part 1 — AWS IAM Setup

### Step 1: Create IAM User
- User Name: `Developer`
- Access Type: Programmatic and Console access

**Screenshot:**  
![AWS IAM User](screenshots/aws_user_creation.png)

---

### Step 2: Attach EC2 Full Access Policy
- Policy: `AmazonEC2FullAccess`

**Screenshot:**  
![AWS EC2 Full Access](screenshots/aws_ec2_policy.png)

---

### Step 3: Create Custom Policy to Deny S3 Delete
- Custom Policy JSON:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Deny",
      "Action": [
        "s3:DeleteObject",
        "s3:DeleteObjectVersion",
        "s3:DeleteBucket"
      ],
      "Resource": "*"
    }
  ]
}
