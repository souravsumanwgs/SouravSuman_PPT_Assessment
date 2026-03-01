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



# CloudFront Distribution for S3 Static Website

## Simple Definition
CloudFront is a Content Delivery Network (CDN) service by AWS that caches your website content in multiple locations globally. Using CloudFront for your S3-hosted static website ensures faster content delivery to users, reducing latency and improving user experience.

## Objective
- Learn how to distribute content globally using AWS CloudFront.
- Understand linking S3 buckets to CloudFront distributions.
- Enable secure and fast access to static website content.

## Steps to Create CloudFront Distribution

1. **Login to AWS Management Console**
   - Navigate to **CloudFront** under the “Services” menu.

2. **Create a CloudFront Distribution**
   - Click **Create Distribution** → **Web**.
   - Under **Origin Settings**, select your **S3 bucket** hosting the static website as the origin.
   - Configure **Default Cache Behavior** (e.g., allow GET/HEAD requests).
   - Set **Distribution Settings** (enable SSL, default root object like `index.html`).

3. **Review and Create**
   - Click **Create Distribution**.
   - Wait for the status to become **Deployed** (may take several minutes).

4. **Access Your Website**
   - Use the **CloudFront Domain Name** to access your website globally.
   - Test if your website loads faster and content is served from the nearest edge location.

## Proof Required (Screenshots)
1. **Screenshot 1:** CloudFront Distribution Created  
   *(Show your CloudFront distribution list with your S3 origin)*

2. **Screenshot 2:** Accessing Website via CloudFront URL  
   *(Show your static website loading using the CloudFront domain)*

## Notes / Tips
- Ensure your S3 bucket permissions allow CloudFront to access objects.
- For HTTPS, use **CloudFront SSL certificate** (default or custom).
- You can monitor performance in the **CloudFront Reports & Metrics** section.
