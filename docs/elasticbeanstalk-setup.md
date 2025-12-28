# Elastic Beanstalk Environment Setup

## Overview

This guide covers setting up an Elastic Beanstalk (EB) environment running Tomcat, including Application Load Balancer (ALB), Auto Scaling Group (ASG), health checks, and HTTPS listener configuration.

---

## Steps to Create Elastic Beanstalk Environment

1. **Log in** to the [AWS Management Console](https://console.aws.amazon.com/).

2. Navigate to **Elastic Beanstalk** service.

3. Click **Create a new environment** and select **Web server environment**.

4. Choose the **Platform**:
   - Select **Tomcat** (choose appropriate version).

5. Upload your application **artifact** (WAR file) or you can deploy later.

6. Configure **Environment settings**:

   - **Environment name**: e.g., `webstack-eb-env`
   - **Domain**: Set a unique subdomain or leave default.

7. Under **Instances**, select **EC2 key pair** you created earlier for SSH access.

8. Configure **Load Balancer**:

   - Use an **Application Load Balancer (ALB)**.
   - Configure **Listeners**:
     - Add HTTP listener on port 80.
     - Add HTTPS listener on port 443 (see HTTPS setup below).
   - Set **Health Check Path** to your application health endpoint (e.g., `/health` or `/`).

9. Configure **Auto Scaling**:

   - Set minimum and maximum instance counts (e.g., min: 2, max: 4).
   - Configure scaling triggers if desired.

10. Configure **Security Groups**:

    - Assign the Beanstalk security group.
    - Ensure it allows inbound traffic on ports 80 and 443 from the internet.

11. **Create environment**.

---

## HTTPS Listener Setup (ALB)

- To enable HTTPS, use **AWS Cert**
