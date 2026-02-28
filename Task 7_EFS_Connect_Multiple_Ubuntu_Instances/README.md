# Task 7: Create EFS and Connect to Multiple Ubuntu Instances

Objective  
Mount a shared file system across multiple Ubuntu EC2 instances using Amazon EFS (Elastic File System).

 **Steps

1. Create an EFS File System
   - Go to AWS Console → EFS → Create file system
   - Name `Task7-EFS`.
   - Select the VPC where Ubuntu EC2 instances exist.
   - Select subnets/AZs for mount targets.
   - Leave Performance mode: General Purpose and Throughput mode Bursting.
   - Click Create and wait until the EFS is Available

2. Configure Security Group
   - Go to EC2 → Security Groups of Ubuntu instances.
   - Edit Inbound Rules
     - Type NFS
     - Port 2049
     - Source:Security group of EC2 instances (or subnet CIDR)
   - Save rules.

3. Mount EFS on Ubuntu Instances
   - Connect to each Ubuntu instance via SSH.
   - Install NFS client:
     ```bash
     sudo apt update
     sudo apt install nfs-common -y
     ```
   - Create a mount point:
     ```bash
     sudo mkdir /mnt/efs
     ```
   - Mount the EFS file system (replace `fs-xxxxxxxx` with your EFS ID):
     ```bash
     sudo mount -t nfs4 -o nfsvers=4.1 fs-xxxxxxxx.efs.us-east-1.amazonaws.com:/ /mnt/efs
     ```
   - Repeat for all Ubuntu instances.

4. **Test Shared Storage**
   - On Instance 1
     ```bash
     sudo touch /mnt/efs/testfile.txt
     ```
   - On **Instance 2**:
     ```bash
     ls /mnt/efs/
     ```
   - If the file is visible on all instances, EFS is successfully shared.

---

### **Proof Required**
1. Screenshot of **EFS created** in AWS Console.  
2. Screenshot of **security group allowing NFS port 2049**.  
3. Screenshot of **EFS mounted on multiple Ubuntu instances** showing the shared file.
