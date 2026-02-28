 Static Website Hosting in S3

Objective:
Host a static website using Amazon S3 to learn serverless hosting.

1. Create an S3 Bucket
   - Go to AWS Console → S3 → Create bucket.
   - Bucket Name:** Must be globally unique 
   - Region:** Choose your preferred region.
   - Block Public Access
   - Click **Create bucket.

2. Upload Website Files
   - Open your bucket → Upload → Add Files / Add Folder.
   - Upload your website files 

3. Enable Static Website Hosting
   - Go to Properties → Static website hosting → Enable.
   - Index document:
   - Error document (optional):
   - Save changes.

4. Set Bucket Policy for Public Access
   - Go to Permissions → Bucket Policy → Edit.
   - Add the following JSON (replace `your-bucket-name` with your bucket name):
   ```json
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Sid": "PublicReadGetObject",
               "Effect": "Allow",
               "Principal": "*",
               "Action": "s3:GetObject",
               "Resource": "arn:aws:s3:::your-bucket-name/*"
           }
       ]
   }
