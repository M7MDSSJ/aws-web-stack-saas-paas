# EC2 Instance Setup for Database Initialization

## Overview

This guide describes creating an EC2 instance used to initialize the RDS MySQL database with necessary schemas, tables, or seed data before application deployment.

---

## Steps to Create EC2 Instance for DB Initialization

1. **Log in** to the [AWS Management Console](https://console.aws.amazon.com/).

2. Navigate to **EC2** service.

3. Click **Launch Instance**.

4. Choose an **Amazon Machine Image (AMI)**:
   - Use an Amazon Linux 2 or your preferred Linux distro.

5. Select **Instance Type**:
   - e.g., `t3.micro` for light initialization tasks.

6. Configure **Instance Details**:
   - Select the **VPC** and **Subnet** where RDS resides.
   - Enable **Auto-assign Public IP** if you need SSH access from outside.
   - Attach an **IAM Role** if you plan to use AWS CLI or SDK with permissions.

7. Add **Storage** as needed.

8. Configure **Security Group**:
   - Use an existing security group that allows outbound traffic to RDS on port 3306.
   - Allow inbound SSH from your IP for access.

9. Add a **Key Pair** for SSH access (can use the same key as Elastic Beanstalk).

10. Launch the instance.

---

## Initializing the Database

- SSH into the EC2 instance by running:

  `ssh -i /path/to/key.pem ec2-user@<ec2-instance-ip>`

- Install the MySQL client if not already installed:

  `sudo yum install -y mysql`

- Connect to the RDS instance using the endpoint, username, and password:

  `mysql -h <rds-endpoint> -u <username> -p`

- Run your SQL scripts to create schemas, tables, and seed data.

- Alternatively, you can upload SQL scripts and execute them via shell commands.

---

## Important Notes

- Once initialization is complete, the EC2 instance can be terminated or reused as needed.

- Ensure secure handling of database credentials.
