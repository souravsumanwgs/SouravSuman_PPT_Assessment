 – Azure VNet (Basic Networking Practical)
📌 Objective

To configure a Virtual Network (VNet), create subnets, and apply Network Security Group (NSG) rules in Microsoft Azure.
This task demonstrates the fundamentals of cloud networking in Azure.

🛠️ Services Used

Microsoft Azure Portal

Azure Virtual Network (VNet)

Subnets

Network Security Group (NSG)

🌐 Implementation Steps
Step 1: Create Virtual Network (VNet)

Logged into Azure Portal.

Searched for Virtual Networks and clicked Create.

Configured the VNet with:

Resource Group: [Your Resource Group]

VNet Name: [VNet-Name]

Region: [Region]

Address Space: 10.0.0.0/16

Created default subnet: 10.0.1.0/24

Clicked Review + Create and completed deployment successfully.

Step 2: Create Additional Subnet

Opened the created VNet.

Navigated to Subnets.

Clicked + Subnet and configured:

Subnet Name: Subnet-2

Address Range: 10.0.2.0/24

Saved configuration.

Step 3: Configure Network Security Group (NSG)

Created a new Network Security Group.

Added an Inbound Rule:

Allow SSH (Port 22) or RDP (Port 3389)

Source: Any

Action: Allow

Associated NSG with the subnet or VM network interface.

📷 Proof of Work

Screenshot showing VNet with address space and subnets

Screenshot showing NSG inbound rule configuration

(All screenshots saved inside the Screenshots folder)

🔍 Key Learnings

VNet is the foundation of Azure networking.

Subnets divide the network into smaller segments.

NSG controls inbound and outbound traffic.

CIDR notation defines IP address ranges.

Similar concept to AWS VPC.

🎯 Conclusion

A Virtual Network was successfully created with multiple subnets and security rules using NSG.
This demonstrates understanding of Azure networking fundamentals and cloud-based network segmentation.
The objective of learning basic networking in Azure was successfully achieved.v
