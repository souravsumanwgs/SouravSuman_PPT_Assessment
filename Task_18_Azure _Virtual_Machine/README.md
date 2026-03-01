Azure Virtual Machine (Easy Task)

## 🎯 Objective
Launch and configure a basic Azure Virtual Machine and access it using SSH from Command Prompt.

---

## 🛠️ Steps Performed

### Step 1: Login to Azure Portal
- Opened https://portal.azure.com
- Logged in using Azure account

---

### Step 2: Create Resource Group
- Navigated to **Resource Groups**
- Clicked **Create**
- Resource Group Name: `ppt-rg`
- Region: Central India
- Clicked **Review + Create**
- Resource group created successfully

---

### Step 3: Create Virtual Machine
- Searched for **Virtual Machines**
- Clicked **Create → Azure Virtual Machine**

#### Basic Configuration:
- Subscription: Azure Subscription 1
- Resource Group: `ppt-rg`
- Virtual Machine Name: `ppt-vm`
- Region: Central India
- Availability Options: No infrastructure redundancy required
- Security Type: Standard
- Image: Ubuntu Server 22.04 LTS (x64 Gen2)
- VM Architecture: x64
- Size: Standard B1s
- Authentication Type: SSH Public Key
- Username: azureuser
- Inbound Ports: Allow SSH (22)

Clicked **Review + Create** and then **Create**

---

### Step 4: Deployment
- Deployment completed successfully
- VM Status: Running

---

### Step 5: Connect to Virtual Machine

Used SSH from Command Prompt:

```bash
ssh azureuser@<Public-IP-Address>
