 Start/Stop EC2 using Lambda + API (Function URL)

## Objective
Automate starting and stopping an EC2 instance using a Lambda function triggered via HTTP (Lambda Function URL).  
This demonstrates **serverless automation** and how to integrate Lambda with EC2.

---

## Architecture
1. **EC2 Instance**: Ubuntu instance to control.  
2. **Lambda Function (`EC2ControlLambda`)**: Handles `start` and `stop` actions via Boto3.  
3. **Lambda Function URL**: Public URL to trigger Lambda via HTTP GET request with query parameter `action=start` or `action=stop`.  

---

## Lambda Function Code (Python)

```python
import json
import boto3

# Replace with your EC2 instance ID
INSTANCE_ID = 'i-0123456789abcdef0'

ec2 = boto3.client('ec2')

def lambda_handler(event, context):
    action = event.get('queryStringParameters', {}).get('action')
    
    if action == 'start':
        ec2.start_instances(InstanceIds=[INSTANCE_ID])
        return {"message": f"EC2 Instance {INSTANCE_ID} is starting."}
    elif action == 'stop':
        ec2.stop_instances(InstanceIds=[INSTANCE_ID])
        return {"message": f"EC2 Instance {INSTANCE_ID} is stopping."}
    else:
        return {"message": "Invalid action. Use ?action=start or ?action=stop"}
