# Task 2 — Azure Global Infrastructure + High Availability

## Objective
Deploy a highly available virtual machine infrastructure using **Availability Sets**, **Availability Zones**, **Azure Load Balancer**, and **Azure Monitor**. This ensures high availability, redundancy, and monitoring of resources.

---

## Step-by-Step Guide

### **Step 1: Create a Resource Group**
1. Login to [Azure Portal](https://portal.azure.com/).  
2. Navigate to **Resource Groups** → **Create**.  
3. Enter:
   - Name: `RG-HA-Demo`
   - Region: `Central US`  
4. Click **Review + Create** → **Create**.  

---

### **Step 2: Create Virtual Network (VNet) and Subnets**
1. Navigate to **Virtual Networks** → **Create**.  
2. Enter:
   - Name: `HA-VNet`
   - Region: `Central US`
   - Address space: `172.16.0.0/16`  
3. Create a subnet:
   - Name: `snet-centralus-1`
   - Address range: `172.16.0.0/24`  
4. Review and create the VNet.

---

### **Step 3: Deploy 2 Virtual Machines in an Availability Set**
1. Navigate to **Virtual Machines** → **Create → Azure Virtual Machine**.  
2. Enter VM details:
   - Name: `VM1` and `VM2`
   - Region: `Central US`
   - Image: Ubuntu Server 24.04 LTS
   - Size: `B1s` (or as per quota)
   - Availability options: **Availability Set** → `HA-AV-Set`
3. Configure Networking:
   - Virtual Network: `HA-VNet`
   - Subnet: `snet-centralus-1`
   - Public inbound ports: SSH (22)
4. Review and create the VMs.

---

### **Step 4: Deploy 2 Virtual Machines in a Different Availability Zone**
1. Create 2 new VMs:
   - Name: `VM3` and `VM4`
   - Region: `Central US`
   - Availability options: **Availability Zone** → Zone 1 & 2 (different zones)
2. Configure same network settings as above.  
3. Review and create.

---

### **Step 5: Create a Public Azure Load Balancer**
1. Navigate to **Load Balancers** → **Create**.  
2. Basics:
   - Name: `LLb`
   - Region: `Central US`
   - SKU: Standard
   - Type: Public
   - Tier: Regional
3. Frontend IP configuration:
   - Name: `LB-Frontend`
   - Public IP: Create new → Name: `LB-PublicIP` → Static
4. Click **Next** → Backend Pools.

---

### **Step 6: Add all VMs to Backend Pool**
1. Backend pool:
   - Name: `VMSS-BackendPool`
   - Backend pool type: **Virtual Machine Scale Set**
   - Attach existing VMSS or Availability Set VMs
2. Click **Add** → **Save**.

---

### **Step 7: Configure Health Probe and Load Balancing Rule**
1. Navigate to **Inbound Rules** → **Add**:
   - Rule 1 (HTTP):
     - Frontend IP: `LB-Frontend`
     - Backend pool: `VMSS-BackendPool`
     - Protocol: TCP
     - Port: 80
     - Backend port: 80
     - Health probe: TCP → Port 80
   - Rule 2 (SSH):
     - Port: 22
     - Backend port: 22
     - Health probe: TCP → Port 22
2. Click **Add**.

---

### **Step 8: Enable Azure Monitor and Create Alert Rule**
1. Navigate to **Azure Monitor → Alerts → New alert rule**.  
2. Select **VMSS / VMs** as resource.  
3. Condition / Metric: CPU %, VM Health, or Disk usage.  
4. Action: Email / Notification.  
5. Name: `HA-CPU-Alert`  
6. Click **Create**.

---

### **Step 9: Create Storage Account and Enable Diagnostic Logs**
1. Navigate to **Storage Accounts → Create**:
   - Name: `hastoragecentralus`
   - Region: `Central US`
   - Performance: Standard
   - Replication: LRS
2. After creation:
   - Navigate to **Diagnostic settings** → Add diagnostic log
   - Send logs to **Storage Account**  
   - Enable metrics, activity logs, and VM insights.

---

### **Step 10: Test Public IP and High Availability**
1. Open the Load Balancer public IP in browser → check web server or VM response.  
2. SSH into one VM → stop the VM (`sudo shutdown now`)  
3. Reload the Load Balancer public IP → traffic should route to remaining VMs automatically.  
4. Confirm HA is working as expected.

---

## ✅ Conclusion
- Task 2 **Azure Global Infrastructure + High Availability** is successfully deployed.  
- Infrastructure includes:
  - 2 VMs in Availability Set  
  - 2 VMs in Availability Zones  
  - Azure Load Balancer with Backend Pool  
  - Health probes and Inbound rules  
  - Azure Monitor Alerts  
  - Storage Account with diagnostic logs  
- Tested Public IP with VM shutdown → High Availability verified.

---

## 📌 References
- [Azure VM Availability Sets](https://learn.microsoft.com/en-us/azure/virtual-machines/availability)  
- [Azure VM Scale Sets](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/overview)  
- [Azure Load Balancer](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview)  
- [Azure Monitor Alerts](https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-overview)
