# Task 2: Disk Partitioning (MBR & GPT)

## Objective
To understand disk partitioning using:
- MBR (Master Boot Record) in Ubuntu
- GPT (GUID Partition Table) in Windows Server

---

# Part 1: MBR Partitioning in Ubuntu (fdisk)

## Environment
- AWS EC2 Ubuntu Instance
- Secondary 10GB EBS Volume attached

## Steps Performed

1. Verified attached disks
2. Created new MBR partition using fdisk
3. Formatted partition with ext4
4. Mounted partition
5. Verified using df -h

## Output
New partition successfully created and mounted at:

/mnt/mypartition

---

# Part 2: GPT Partitioning in Windows Server

## Environment
- AWS EC2 Windows Server Instance
- Secondary 10GB EBS Volume attached

## Steps Performed

1. Opened Server Manager
2. Navigated to:
   File and Storage Services → Disks
3. Initialized disk using GPT
4. Created new volume
5. Formatted with NTFS
6. Assigned drive letter

## Output
New GPT volume successfully created and accessible.

---

## Screenshots Included
- Ubuntu fdisk partition creation
- df -h output
- Windows GPT disk initialization
- New Volume creation

---

## Conclusion
MBR supports limited partitions (4 primary, 2TB max).  
GPT supports up to 128 partitions and larger disk sizes.  
GPT is recommended for modern systems.

Task completed successfully.
