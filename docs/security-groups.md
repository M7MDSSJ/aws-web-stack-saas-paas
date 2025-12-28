# Creating Security Groups for ElasticCache, RDS, AmazonMQ, and Elastic Beanstalk

## Overview

This document explains how to create a Security Group (SG) that allows secure communication between the following AWS services:

- ElastiCache (Memcache)
- Amazon RDS (MySQL Database)
- Amazon MQ (Message Broker)
- Elastic Beanstalk EC2 instances

---

## Security Group Design

- **Single SG** for ElastiCache, RDS, and Amazon MQ  
- This SG allows **all internal traffic between these services** on required ports.  
- The SG also allows inbound traffic from the **Elastic Beanstalk security group** to enable app communication.

---

## Steps to Create the Security Group

1. **Log in** to the [AWS Management Console](https://console.aws.amazon.com/).

2. Navigate to the **EC2** service and select **Security Groups** from the sidebar.

3. Click **Create security group**.

4. Enter a **name** (e.g., `webstack-services-sg`) and a **description**.

5. Assign the SG to the appropriate **VPC** used by your resources.

---

## Inbound Rules

| Type           | Protocol | Port Range | Source                             | Purpose                              |
|----------------|----------|------------|----------------------------------|------------------------------------|
| Custom TCP     | TCP      | 11211      | Self (the SG itself)              | Memcache (ElastiCache default port)|
| MySQL/Aurora   | TCP      | 3306       | Self                             | MySQL Database (RDS)                |
| Custom TCP     | TCP      | 5671, 5672 | Self                             | Amazon MQ (RabbitMQ ports)          |
| Custom TCP     | TCP      | All        | Elastic Beanstalk SG (by ID)     | Allow EB instances to access services|

---

## Outbound Rules

- Allow **all traffic** outbound (default in most SGs).

---

## Notes

- Replace port numbers if you use custom ports for these services.  
- Make sure Elastic Beanstalk instances have their own SG with outbound rules allowing traffic to this SG.

---

## Example AWS CLI Command to Create the SG (Optional)

```bash
aws ec2 create-security-group --group-name webstack-services-sg --description "SG for RDS, ElastiCache, AmazonMQ and EB communication" --vpc-id <vpc-id>
