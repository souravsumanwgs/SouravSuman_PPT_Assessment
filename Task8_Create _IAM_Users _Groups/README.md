# IAM — Users and Groups

Created an IAM group and added users to manage permissions securely.

 Project Structure
.
├── README.md
└── Screenshots
    ├── 01_IAM_Group_Created.png
    └── 02_IAM_Users_Created.png

 IAM Group
| Field | Value |
|-------|-------|
| Group Name | Developers |
| Attached Policy | AmazonS3FullAccess |

IAM Users
| User | Group | Access Type |
|------|-------|-------------|
| dev_user1 | Developers | Programmatic & Console |
| dev_user2 | Developers | Programmatic & Console |

 What Was Done

Step 1 — Created IAM Group  
AWS Console → IAM → User Groups → Create group  
Name: Developers, Policy: AmazonS3FullAccess

Step 2 — Created IAM Users  
AWS Console → IAM → Users → Add users  
Usernames: dev_user1, dev_user2  
Access Type: Programmatic & Console  
Added to group: Developers

## Screenshots
1. **IAM Group Created** – Shows Developers group with AmazonS3FullAccess policy  
2. **IAM Users Created** – Shows dev_user1 and dev_user2 added to Developers group

## Result
Users dev_user1 and dev_user2 successfully created and added to the Developers group with proper access policies attached.
