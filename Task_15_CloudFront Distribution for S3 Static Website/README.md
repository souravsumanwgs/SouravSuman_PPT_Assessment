# CloudFront Distribution for S3 Static Website

## Simple Definition
CloudFront is a Content Delivery Network (CDN) service by AWS that caches your website content in multiple locations worldwide. Linking a static website hosted on S3 with CloudFront ensures faster content delivery, reduced latency, and improved user experience.

## Objective
- Use **CloudFront CDN** to serve a static website hosted on **S3**.
- Learn global content distribution for faster website delivery.
- Understand how to configure S3 and CloudFront for secure access.

## Steps Performed

### 1. S3 Bucket Setup
- Created bucket `destinationbucketwgs`.
- Enabled **public read access** via bucket policy.
- Verified that website files (e.g., `index.html`) are present.

### 2. CORS Configuration
Configured S3 CORS to allow cross-origin requests:

```json
[
    {
        "AllowedHeaders": ["*"],
        "AllowedMethods": ["GET", "PUT", "POST", "DELETE", "HEAD"],
        "AllowedOrigins": ["*"],
        "ExposeHeaders": [],
        "MaxAgeSeconds": 3000
    }
]
