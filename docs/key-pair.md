# Creating a Key Pair for Elastic Beanstalk Instance Login

## Purpose

A key pair is required to securely SSH into your Elastic Beanstalk EC2 instances for troubleshooting and management.

---

## Steps to Create a Key Pair in AWS Console

1. **Log in** to the [AWS Management Console](https://console.aws.amazon.com/).

2. Navigate to **EC2** service.

3. In the sidebar, click **Key Pairs** under **Network & Security**.

4. Click **Create key pair**.

5. Enter a **name** for the key pair (e.g., `eb-webstack-key`).

6. Select the **PEM** format for Linux/macOS or **PPK** for Windows (if using PuTTY).

7. Click **Create key pair**.

8. The private key file (`.pem` or `.ppk`) will be **downloaded automatically**. Store it securely.

---

## Using the Key Pair with Elastic Beanstalk

- When creating your Elastic Beanstalk environment, select this key pair under **EC2 instance settings** to enable SSH access.

- Use this private key to SSH into your Elastic Beanstalk instances:

  ```bash
  ssh -i /path/to/eb-webstack-key.pem ec2-user@<instance-public-ip>
