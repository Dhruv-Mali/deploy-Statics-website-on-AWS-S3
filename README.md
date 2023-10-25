# deploy-Statics-website-on-AWS-S3


Deploying a static website on AWS S3 is a straightforward process, and it's a cost-effective way to host your site. Here's a step-by-step guide to help you deploy your static website on AWS S3:

**Prerequisites:**
- An AWS account.
- Your static website files (HTML, CSS, JavaScript, images, etc.).

**Step 1: Create an S3 Bucket**
1. Sign in to your AWS Management Console.
2. Go to the S3 service.
3. Click the "Create bucket" button.
4. Provide a unique name for your bucket (e.g., my-static-website). Bucket names must be globally unique within AWS.
5. Choose the AWS region where you want to host your static website.
6. Under "Block Public Access settings for this bucket," uncheck "Block all public access" and acknowledge the warning.
7. Click "Create bucket."

**Step 2: Upload Your Website Files**
1. Inside your newly created S3 bucket, click the "Upload" button.
2. Add your static website files to the bucket. You can either drag and drop files or use the "Add files" button.
3. Ensure your main HTML file is named "index.html" as this will be the default document S3 serves.

**Step 3: Configure Bucket Properties**
1. Select your S3 bucket.
2. Click on the "Properties" tab.
3. In the "Static website hosting" card, click "Edit."
4. Choose the "Use this bucket to host a website" option.
5. Set the "Index document" to "index.html" (or your main HTML file).
6. Optionally, set the "Error document" to a custom error page, if you have one.
7. Click "Save changes."

**Step 4: Set Bucket Permissions**
1. In the bucket properties, click on the "Permissions" tab.
2. Click "Bucket Policy" and add a policy that grants public read access to the objects in your bucket. You can use a policy like this (replace `my-static-website` with your bucket name):

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::my-static-website/*"
        }
    ]
}
```

3. Click "Save."

**Step 5: Enable Static Website Hosting**
1. Return to the "Static website hosting" settings under the "Properties" tab.
2. Note the endpoint URL for your static website. It will be in the "Endpoint" field.

**Step 6: Test Your Website**
1. Open a web browser and enter the endpoint URL from the previous step.
2. Your static website should now be accessible from the provided URL.

**Step 7 (Optional): Configure a Custom Domain**
If you want to use a custom domain (e.g., www.yourwebsite.com), you can set up Amazon Route 53 or another domain registrar to point to your S3 bucket. This involves configuring DNS settings and possibly SSL certificates if you want HTTPS.

That's it! Your static website is now hosted on AWS S3 and accessible to the public. Make sure to monitor your costs and security settings, and consider setting up CloudFront for CDN distribution and Route 53 for domain management for a more robust setup.
