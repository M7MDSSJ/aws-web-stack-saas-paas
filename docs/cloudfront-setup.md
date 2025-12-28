# CloudFront CDN Setup with ACM SSL and Domain Configuration

## Overview

This guide explains how to create an Amazon CloudFront distribution with HTTPS enabled using an ACM SSL certificate and associate it with your domain registered on Namecheap.

---

## Steps to Create CloudFront Distribution

1. **Log in** to the [AWS Management Console](https://console.aws.amazon.com/).

2. Navigate to **CloudFront** service.

3. Click **Create Distribution** and select **Web**.

4. Configure **Origin Settings**:
   - **Origin Domain Name**: Use your Elastic Beanstalk environment’s ALB DNS name.
   - **Origin Protocol Policy**: Choose **HTTPS Only**.

5. Configure **Default Cache Behavior**:
   - Viewer Protocol Policy: **Redirect HTTP to HTTPS**.
   - Allowed HTTP Methods: Choose as per your app requirements (e.g., GET, HEAD, OPTIONS, POST).

6. Configure **Distribution Settings**:
   - **Alternate Domain Names (CNAMEs)**: Enter your custom domain (e.g., `www.example.com`).
   - **SSL Certificate**: Choose **Custom SSL Certificate (ACM)**.
     - Use an existing certificate or request a new one in ACM (must be in **us-east-1** region).
   - Enable **IPv6** (optional).
   - Leave other settings as default or customize as needed.

7. Click **Create Distribution**.

---

## ACM SSL Certificate

- If you don’t have an SSL certificate yet, request one via **AWS Certificate Manager (ACM)** in **us-east-1**.

- Validate your certificate via DNS or email as per ACM instructions.

- Wait until the certificate status is **Issued** before attaching it to CloudFront.

---

## Configure Your Domain on Namecheap

1. Log in to your [Namecheap account](https://www.namecheap.com/).

2. Go to **Domain List** and select your domain.

3. Click **Manage**, then navigate to the **Advanced DNS** tab.

4. Create a **CNAME record**:
   - **Host**: e.g., `www`
   - **Value**: Your CloudFront distribution domain name (e.g., `d1234abcdef.cloudfront.net`)
   - **TTL**: Automatic or as desired.

5. Save the changes.

6. (Optional) Set up URL redirect or forwarding if you want the root domain (`example.com`) to redirect to `www.example.com`.

---

## Notes

- DNS propagation may take some time (usually minutes to hours).

- After propagation, your users will access your webstack through the CloudFront CDN with HTTPS enabled.

---

This setup improves performance and security by caching content globally and securing traffic with SSL.

