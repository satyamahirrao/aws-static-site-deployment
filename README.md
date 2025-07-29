# 🌐 Deploy a Static Website on AWS S3 + CloudFront

This guide walks through deploying a static website globally using **Amazon S3** and **CloudFront**, ideal for company marketing sites, portfolios, or any static content. This documentation is created with AWS Free Tier in mind — no domain required.

---

## 📋 Prerequisites

- AWS account (Free Tier is sufficient)
- Basic static website files (HTML, CSS, JS)
- Internet connection and web browser

---

## 🪜 Step-by-Step Deployment

### 1️⃣ Upload Files to S3 Bucket

- Open AWS S3 Console
- Create a new bucket (e.g., `my-static-site-demo`)
- Uncheck "Block all public access" and acknowledge the warning
- Upload your `index.html`, stylesheets, scripts, etc.

**Screenshot:**
![S3 Uploaded Files](images/S3%20uploaded%20files.png)

---

### 2️⃣ Enable Static Website Hosting

- Go to **Properties** tab of the bucket
- Scroll to **Static Website Hosting** section
- Enable it and set:
  - **Index document**: `index.html`
  - **Error document**: leave blank or set `error.html`
- Save changes

**Screenshot:**
![S3 Website Hosting Settings](images/S3%20website%20hostinh%20setting.png)

---

### 3️⃣ Add Bucket Policy for Public Access

- Go to **Permissions** tab > **Bucket Policy**
- Paste the policy below (replace `your-bucket-name`):

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

