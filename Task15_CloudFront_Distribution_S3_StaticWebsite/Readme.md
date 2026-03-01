# Task 15: CloudFront Distribution for S3 Static Website

## Objective
Configure a CloudFront distribution to deliver an S3-hosted static website globally with low latency and improved performance.

## Environment
- Amazon S3 (Static Website Hosting)
- Amazon CloudFront
- IAM (optional for restricted access)

## Simple Definition
CloudFront is a Content Delivery Network (CDN) that caches website content at edge locations worldwide to deliver faster performance and high availability.

---

## Architecture Flow

User → CloudFront Edge Location → S3 Bucket (Origin)

---

## Implementation Steps

### 1. Configure S3 Static Website
- Go to AWS Console → S3
- Create or use existing bucket
- Upload website files (ensure `index.html` exists)
- Enable Static Website Hosting
- Configure public access or proper bucket policy

---

### 2. Create CloudFront Distribution

- Go to AWS Console → CloudFront
- Click "Create distribution"
- Origin Domain: Select S3 bucket
- Origin Access:
  - Public bucket OR
  - Configure Origin Access Control (recommended)
- Default Root Object: `index.html`
- Viewer Protocol Policy:
  - Redirect HTTP to HTTPS (recommended)
- Create distribution

Wait for distribution status to change to "Deployed".

---

### 3. Access Website via CloudFront

- Copy CloudFront Distribution Domain Name
- Open in browser
- Website should load via CDN

---

## Key Concepts

- CDN (Content Delivery Network): Delivers content from nearest edge location.
- Edge Locations: Global data centers for caching content.
- Origin: Primary source of content (S3 bucket).
- HTTPS: Secure content delivery.
- Caching: Improves speed and reduces load on origin.

---

## Learning Outcome
- Configuring CloudFront with S3
- Understanding global content distribution
- Implementing CDN-based website acceleration
- Enhancing performance and availability of static websites
