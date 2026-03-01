 S3 Upload Email Notification (Lambda + SNS)

## Objective
Trigger an email notification whenever a file is uploaded to an S3 bucket using AWS Lambda and SNS. This demonstrates event-driven architecture.


## Architecture
- **S3 Bucket**: Source of file uploads (`destinationbucketwgs`).
- **Lambda Function**: `S3UploadNotification` triggered by S3 events.
- **SNS Topic**: `S3UploadNotification` sends email notifications to subscribed users.


## Steps Performed

1. **Create SNS Topic**
   - Name: `S3UploadNotification`
   - Created email subscription and confirmed it.

2. **Create Lambda Function**
   - Name: `S3UploadNotification`
   - Runtime: Python 3.11
   - Attached IAM role with `sns:Publish` permission.
   - Added S3 trigger for **All object create events**.

3. **Lambda Code**
   - Reads S3 event for bucket and file name.
   - Publishes message to SNS topic.
   - Returns `"Notification sent!"`.

4. **Test Lambda**
   - Created a test event simulating S3 upload.
   - Verified execution in CloudWatch logs.

5. **Real Test**
   - Uploaded file `example.txt` to S3 bucket.
   - Received email notification confirming upload.


## Proof (Screenshots)

1. **SNS Subscription Confirmed Email** – shows subscription is active.  
2. **Lambda Code with S3 Trigger** – shows Lambda configured correctly.  
3. **Email Notification Received** – confirms file upload notification.


## Notes

- Make sure SNS subscription email is **confirmed**, otherwise notifications will not arrive.
- Lambda execution role must include **sns:Publish** permission for the SNS topic.
- Test Lambda with a simulated S3 event before real uploads.

