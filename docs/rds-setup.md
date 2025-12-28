# Amazon RDS (MySQL) Setup and Configuration

## Overview

This guide covers the creation and configuration of an Amazon RDS MySQL database instance for your webstack.

---

## Steps to Create RDS MySQL Instance

1. **Log in** to the [AWS Management Console](https://console.aws.amazon.com/).

2. Navigate to **RDS** service.

3. Click **Create database**.

4. Choose **Standard Create**.

5. Select **Engine type**: **MySQL**.

6. Select the **version** you want (preferably latest stable).

7. Choose **Templates**:
   - For production or demo, select **Production** or **Dev/Test** based on your use case.

8. Configure **Settings**:
   - **DB instance identifier**: e.g., `webstack-mysql-db`
   - **Master username**: e.g., `admin`
   - **Master password**: set and remember this securely.

9. Configure **DB instance size**:
   - Choose instance class based on load (e.g., `db.t3.medium`).

10. Set **Storage**:
    - Use General Purpose SSD (gp3) or as required.
    - Enable storage autoscaling if preferred.

11. Configure **Connectivity**:
    - Select the **VPC** matching your Elastic Beanstalk environment.
    - Set **Subnet group** if applicable.
    - Enable **Public access**: *No* (recommended for security).
    - Select the **Security Group** created earlier (`webstack-services-sg`).

12. Configure **Additional configuration**:
    - Initial database name (optional)
    - Enable backups and set retention period as needed.
    - Enable Multi-AZ deployment for high availability (optional).

13. Click **Create database**.

---

## After Creation

- Note the **endpoint URL** of the RDS instance.

- Use this endpoint in your application configuration to connect to the MySQL database.

---

## Security and Access

- Ensure your Elastic Beanstalk instances' SG can connect to the RDS SG on port 3306.

- Use IAM roles and Secrets Manager if you want to manage credentials securely (optional).

---

## Connecting to the Database for Initialization

- You may use an EC2 instance (see `ec2-db-init.md`) with access to this RDS instance to run initialization scripts.

---

If you plan to automate this process, consider using AWS CloudFormation or Terraform.

