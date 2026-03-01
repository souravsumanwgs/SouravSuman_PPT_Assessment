 CloudWatch Alarm – Auto Stop EC2 on High CPU

## Objective
Monitor EC2 CPU utilization and automate instance stop with email notification using CloudWatch and SNS.

## Steps Completed
1. Created SNS topic `EC2_CPU_ALERT` and subscribed email.  
2. Configured CloudWatch Alarm for CPU utilization > 70% on EC2 instance `i-03ef4ebf687fea8e9` (task7).  
3. Added automatic action to **stop EC2 instance** when CPU > 70%.  
4. Tested alarm by generating CPU load using `stress` command on the Linux instance.  
5. Received email notification confirming alarm triggered.

## Proof (Screenshots)
1. **CloudWatch Alarm Configuration** – showing threshold >70%, instance, and actions.  
   ![Screenshot1](screenshot1.png)  

2. **EC2 instance stopped + Email received** – confirming automation worked.  
   ![Screenshot2](screenshot2.png)  

## Notes
- Ensure SNS subscription is confirmed via email.  
- CPU load was simulated using:  
  ```bash
  sudo apt update
  sudo apt install -y stress
  stress --cpu 2 --timeout 300
