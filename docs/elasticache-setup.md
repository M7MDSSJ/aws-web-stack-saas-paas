# Amazon ElastiCache (Memcache) Setup and Configuration

## Overview

This document guides you through creating and configuring an Amazon ElastiCache cluster using Memcached as the caching layer for your webstack.

---

## Steps to Create an ElastiCache Memcached Cluster

1. **Log in** to the [AWS Management Console](https://console.aws.amazon.com/).

2. Navigate to **ElastiCache** service.

3. Click **Create**.

4. Choose **Memcached** as the cluster engine.

5. Configure **Cluster Details**:
   - **Cluster name**: e.g., `webstack-memcache`
   - **Description**: optional
   - **Engine version compatibility**: choose the latest stable version.

6. Configure **Node Type**:
   - Choose instance type based on your caching needs (e.g., `cache.t3.medium`).

7. Set **Number of Nodes**:
   - For development, 1 node is enough. For production, consider multiple nodes for better availability.

8. Configure **Subnet Group**:
   - Select the subnet group matching your VPC.

9. **Security Groups**:
   - Attach the security group created earlier (`webstack-services-sg`) to allow communication.

10. **Advanced Settings** (optional):
    - Parameter groups, maintenance windows, notifications.

11. Click **Create** to launch the cluster.

---

## After Creation

- Note the **Endpoint** of the ElastiCache cluster.

- Use this endpoint in your application to connect to Memcached.

---

## Important Notes

- ElastiCache Memcached does not support persistence — data is stored in memory only.

- Ensure your application handles cache misses appropriately.

- Make sure Elastic Beanstalk instances’ SG can access the ElastiCache SG on port **11211** (default Memcached port).

---

## Monitoring and Scaling

- Use CloudWatch to monitor cache performance and usage.

- You can scale your cluster by adding or removing nodes.

---

This caching layer improves performance by reducing database load and speeding up data retrieval.

