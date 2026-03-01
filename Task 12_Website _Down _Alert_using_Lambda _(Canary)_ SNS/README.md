 Website Down Alert using Lambda (Canary) + SNS

## Objective
Monitor a website's uptime using AWS CloudWatch Synthetics Canary and send alerts via SNS when the website is down.

## Architecture
- **CloudWatch Synthetics Canary** (`websiteuptimecheck`): Monitors the website at regular intervals.
- **SNS Topic** (`WebsiteDownAlert`): Sends email notifications when the website fails a check.
- **Email Subscription**: Receives alerts in case of downtime.

## Steps Performed
1. Created SNS topic `WebsiteDownAlert` and confirmed email subscription.
2. Created Canary `websiteuptimecheck`:
   - URL: `https://example.com`
   - Runtime: `syn-nodejs-puppeteer-14.0`
   - Schedule: Run every 5 minutes
   - Browser: Chrome enabled
   - IAM Role: CloudWatchSyntheticsRole with SNS publish permissions
   - Data storage: Default S3 bucket for artifacts
3. Configured SNS alarm for Canary failure metric.
4. Canary executed successfully (first run passed).

## Proof (Screenshots)
1. SNS subscription confirmed email  
2. Canary configuration screen (URL, runtime, schedule, role)  
3. Email notification received when simulating website downtime (test by using invalid URL or stopping website temporarily)

## Notes
- The Canary only sends alerts if the website is down or fails the status code check.  
- Ensure SNS subscription is **confirmed** for emails to arrive.  
- Canary artifacts (logs/screenshots) are stored in S3.  
- CloudWatch Logs can be used for troubleshooting Canary runs.
