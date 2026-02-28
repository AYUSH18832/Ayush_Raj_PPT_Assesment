# Task 5: Static Website Hosting in S3

## Objective
Host a static website using Amazon S3 bucket and understand serverless website hosting.

## Environment
- AWS S3
- Static HTML/CSS files

## Simple Definition
Amazon S3 allows hosting static websites (HTML, CSS, JS) without managing servers by enabling static website hosting on a bucket.

---

## Implementation Steps

### 1. Create S3 Bucket
- Open AWS Console
- Go to S3
- Click "Create bucket"
- Provide unique bucket name
- Select region
- Disable "Block all public access"
- Create bucket

### 2. Upload Website Files
- Open created bucket
- Click "Upload"
- Upload HTML, CSS, JS files
- Ensure `index.html` is present

### 3. Enable Static Website Hosting
- Go to Bucket → Properties
- Scroll to "Static website hosting"
- Click "Edit"
- Enable static hosting
- Set:
  - Index document: `index.html`
  - Error document: `error.html` (optional)
- Save changes

### 4. Set Bucket Policy for Public Access

Go to Permissions → Bucket Policy and add:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Statement1",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:*",
            "Resource": "arn:aws:s3:::webbucket455678/*"
        }
    ]
}
```

---

## Verification
- Copy the S3 Website Endpoint URL
- Open in browser
- Website loads successfully

---

## Proof Required
- Screenshot 1: S3 bucket with static hosting enabled
- Screenshot 2: Website opened using S3 endpoint URL

---

## Learning Outcome
- Understanding of S3 bucket configuration
- Static website hosting without EC2
- Bucket policy and public access configuration
- Serverless hosting concept
