 CloudFront Distribution for S3 Static Website

## Objective
- Use **CloudFront CDN** to serve a static website hosted on **S3**.
- Learn global content distribution and faster website delivery.

## Steps Performed

1. **S3 Bucket Setup**
   - Created bucket `destinationbucketwgs`.
   - Enabled **public read access** via bucket policy.
   - Verified objects are present (`index.html`).

2. **CORS Configuration**
- Configured S3 CORS to allow cross-origin requests:

```json
[
    {
        "AllowedHeaders": ["*"],
        "AllowedMethods": ["GET","PUT","POST","DELETE","HEAD"],
        "AllowedOrigins": ["*"],
        "ExposeHeaders": [],
        "MaxAgeSeconds": 3000
    }
]
