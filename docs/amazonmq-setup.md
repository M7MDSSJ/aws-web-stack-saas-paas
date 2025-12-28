# Amazon MQ (RabbitMQ) Setup and Configuration

## Overview

This guide explains how to create and configure an Amazon MQ broker using RabbitMQ for message brokering in your webstack.

---

## Steps to Create Amazon MQ RabbitMQ Broker

1. **Log in** to the [AWS Management Console](https://console.aws.amazon.com/).

2. Navigate to **Amazon MQ** service.

3. Click **Create a broker**.

4. Choose **RabbitMQ** as the broker engine.

5. Configure **Broker details**:
   - **Broker name**: e.g., `webstack-rabbitmq`
   - **Broker instance type**: choose based on expected message load (e.g., `mq.t3.micro` for testing).
   - **Storage type**: EBS, default settings usually fine.

6. Configure **Access and Security**:
   - Use the **VPC** where your other resources reside.
   - Attach the previously created security group (`webstack-services-sg`).

7. Set **Users and Passwords**:
   - Create at least one user with a strong password for broker access.

8. Configure **Encryption and Maintenance**:
   - Enable encryption if required.
   - Set maintenance windows as needed.

9. Click **Create broker**.

---

## After Creation

- Note the **Broker endpoints** (AMQP and MQTT) for your application to connect.

- Use these endpoints in your application to send/receive messages.

---

## Security and Access

- Ensure your Elastic Beanstalk environment security group can communicate with Amazon MQ on ports **5671** and **5672**.

---

## Monitoring and Scaling

- Monitor broker health and performance via Amazon MQ console and CloudWatch.

- You can scale by increasing broker instance type or enabling high availability (multi-AZ).

---

This managed message broker simplifies asynchronous communication between your webstack components.

