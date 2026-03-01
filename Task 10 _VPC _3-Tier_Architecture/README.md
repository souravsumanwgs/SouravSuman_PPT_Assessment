# VPC — 3-Tier Architecture

Designed a 3-tier VPC network with public and private subnets demonstrating secure networking with IGW, NAT Gateway, route tables, and tiered access.

## Project Structure
.
├── README.md
└── Screenshots
    ├── 01_VPC_Created.png
    ├── 02_EC2_Instances_3Tiers.png
    └── 03_Route_Tables_NAT_IGW.png

## VPC Details
| Field | Value |
|-------|-------|
| VPC Name | Task10-3Tier-VPC |
| VPC ID | vpc-00c1d123783857bf2 |
| CIDR Block | 10.0.0.0/16 |
| Availability Zones | us-east-1a, us-east-1b, us-east-1c |

## Subnets
| Tier | Subnet Name | CIDR Block | AZ | Type |
|------|-------------|------------|----|------|
| Web  | Public-Subnet  | 10.0.1.0/24 | us-east-1a | Public |
| App  | Private-App-Subnet | 10.0.2.0/24 | us-east-1b | Private |
| DB   | Private-DB-Subnet  | 10.0.3.0/24 | us-east-1c | Private |

## Components
- **Internet Gateway (IGW):** igw-01f643bb1f6f3264f → Public subnet Internet access  
- **NAT Gateway:** nat-1ef389af24db14fd0 → Private subnets outbound Internet access  
- **Route Tables:**  
  - Public Route Table: rtb-0979df272cb8ccd7c → routes: 0.0.0.0/0 → IGW  
  - Private Route Table: Private-RTB → routes: 0.0.0.0/0 → NAT Gateway  
- **Security Groups:** Tiered access  
  - Web → HTTP/HTTPS from Internet, SSH from your IP  
  - App → Traffic only from Web subnet  
  - DB → Traffic only from App subnet  
- **NACLs:** Optional subnet-level access control  

## What Was Done

**Step 1 — Created VPC**  
Task10-3Tier-VPC, CIDR 10.0.0.0/16  

**Step 2 — Created Subnets**  
Web, App, DB with respective CIDRs and AZs  

**Step 3 — Created IGW and attached to VPC**  

**Step 4 — Configured Public Route Table**  
Web subnet → route 0.0.0.0/0 → IGW  

**Step 5 — Created NAT Gateway**  
nat-1ef389af24db14fd0 in Public subnet with Elastic IP 52.205.246.28  

**Step 6 — Configured Private Route Table**  
Private subnets → route 0.0.0.0/0 → NAT Gateway  

**Step 7 — Launched EC2 Instances in Each Tier**  
- Web (Public-Subnet) → Internet accessible  
- App (Private-Subnet) → Accessible only from Web  
- DB (Private-Subnet) → Accessible only from App  

**Step 8 — Verified Connectivity**  
- Web → App → DB connections successful  
- App → Internet via NAT Gateway  
- DB → Internet blocked  

## Screenshots
1. **VPC Created** – Shows Task10-3Tier-VPC with CIDR block  
2. **EC2 Instances 3-Tiers** – Instances launched in Web, App, DB subnets  
3. **Route Tables, NAT Gateway, IGW** – Shows public/private route tables and NAT association  

## Result
A fully functional 3-tier VPC architecture:  
- Public Web tier accessible from Internet  
- Private App and DB tiers isolated  
- Private instances access Internet via NAT Gateway  
