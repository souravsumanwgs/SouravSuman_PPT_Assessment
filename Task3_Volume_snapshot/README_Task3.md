# Task 3: Attach EBS Volume from Different AZ using Snapshot

**Objective:**  
Learn how to create an EBS snapshot and attach a restored volume to an EC2 instance in a different Availability Zone (AZ).

**Steps:**

1. **Create Snapshot**
   - Go to EC2 > Elastic Block Store > Volumes.
   - Select the volume and click **Create Snapshot**.
   - Name it meaningfully, e.g., `Task3-VolumeSnapshot`.

2. **Restore Snapshot in a Different AZ**
   - Go to Snapshots, select your snapshot, click **Create Volume**.
   - Choose a **different Availability Zone** than the original.
   - Note the **Volume ID**.

3. **Attach Volume to EC2**
   - Select the restored volume and click **Attach Volume**.
   - Choose the EC2 instance in the new AZ.
   - Verify attachment via SSH:
     ```bash
     lsblk
     sudo file -s /dev/xvdf
     sudo mount /dev/xvdf /mnt
     df -h
     ```

**Proof Required:**
- Screenshot of snapshot creation  
- Screenshot of volume creation in another AZ  
- Screenshot of volume attached to EC2 and mounted
