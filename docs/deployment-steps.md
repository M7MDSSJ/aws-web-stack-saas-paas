# Deployment Steps and Health Check Configuration

## Overview

This document describes how to deploy your application artifact to Elastic Beanstalk and configure proper health checks for your webstack components.

---

## Deploying Artifact to Elastic Beanstalk

1. Package your application as a WAR file (for Tomcat).

2. **Using AWS Console:**

   - Navigate to **Elastic Beanstalk**.
   - Select your environment.
   - Click **Upload and Deploy**.
   - Choose your WAR file and deploy.

3. **Using EB CLI (optional):**

   - Initialize EB CLI in your project folder:

     ```bash
     eb init
     ```

   - Deploy the artifact:

     ```bash
     eb deploy
     ```

---

## Configuring Health Checks

### Elastic Beanstalk / Application Load Balancer (ALB)

- Set the **Health Check Path** to a lightweight endpoint (e.g., `/health` or `/`) that returns HTTP 200 when the app is healthy.

- Configure health check settings such as:
  - Interval: e.g., 30 seconds
  - Timeout: e.g., 5 seconds
  - Unhealthy threshold: e.g., 2 failed checks
  - Healthy threshold: e.g., 5 successful checks

- These settings help ALB and EB determine instance health and trigger auto-scaling or replacement as needed.

---

### Other Services

- **RDS**: AWS manages health internally; monitor via RDS console and CloudWatch.

- **ElastiCache**: Monitor node status and metrics via CloudWatch.

- **Amazon MQ**: Monitor broker health via Amazon MQ console.

---

## Additional Configurations

- **Auto Scaling Group (ASG):** Ensure min/max instance counts fit expected load.

- **Security Groups:** Confirm proper inbound/outbound rules for traffic between services.

- **Logging:** Enable logging in EB and other services for easier troubleshooting.

---

## Summary

Proper deployment and health check configuration ensure your application is resilient, scalable, and highly available.

