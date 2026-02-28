# Task 4: ASG and ELB in EC2

**Objective:**  
Understand how to configure an Auto Scaling Group (ASG) with an Elastic Load Balancer (ELB) for high availability.

**Steps:**

1. **Create Launch Template**
   - EC2 > Launch Templates > Create launch template.
   - Configure AMI, instance type, key pair, and security groups.
   - Name it, e.g., `Task4-LaunchTemplate`.

2. **Create Auto Scaling Group (ASG)**
   - EC2 > Auto Scaling Groups > Create ASG.
   - Select the launch template.
   - Choose at least 2 subnets in different AZs.
   - Set min, max, and desired instance count.

3. **Create ELB and Attach**
   - EC2 > Load Balancers > Create Application Load Balancer.
   - Configure listeners and a target group.
   - Attach ASG instances to the target group.
   - Verify instances are healthy under the ELB.

**Proof Required:**
- Screenshot of Launch Template creation  
- Screenshot of ASG configuration  
- Screenshot of ELB showing registered instances
