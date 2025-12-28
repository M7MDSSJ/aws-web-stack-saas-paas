# AWS Webstack Deployment Project

![Architecture Diagram](architecture-diagram.jpg)

## Project Overview

This project demonstrates deploying a scalable webstack on AWS using PaaS and SaaS models. The webstack includes:

- **Tomcat** application server (deployed via Elastic Beanstalk)
- **Memcache** (in-memory cache) via ElastiCache
- **MySQL Database** via Amazon RDS
- **Message Broker** via Amazon MQ

## Deployment Models Explained

### IaaS vs PaaS & SaaS

- **IaaS (Infrastructure as a Service)** provides raw computing resources (VMs, networking, storage). You manage OS, runtime, middleware, and app.  
- **PaaS (Platform as a Service)** offers managed platforms where you deploy your code without handling OS or middleware (e.g., Elastic Beanstalk).  
- **SaaS (Software as a Service)** delivers ready-to-use software solutions (e.g., Amazon MQ as a managed message broker).

### Why Use PaaS & SaaS?

- Simplifies deployment and management  
- Handles scaling, patching, and availability  
- Reduces operational overhead

### When to Use IaaS?

- When you need full control over the environment  
- Custom OS or middleware requirements  
- Complex legacy applications

## Components & AWS Services Used

| Component        | Deployment Model       | AWS Service        |
|------------------|-----------------------|--------------------|
| Tomcat + ALB + ASG| PaaS                  | Elastic Beanstalk  |
| MySQL Database    | SaaS                  | Amazon RDS         |
| Memcache         | SaaS                  | ElastiCache        |
| Message Broker    | SaaS                  | Amazon MQ          |

## Project Scope

- Creating Key Pair for Beanstalk instance login  
- Security Group creation for RDS, ElastiCache, Amazon MQ, and Beanstalk with proper traffic rules  
- Deploying RDS, ElastiCache, Amazon MQ services  
- Creating Elastic Beanstalk environment with ALB, ASG, health checks, and HTTPS (port 443) listener  
- EC2 instance for database initialization  
- Deploying the artifact to Elastic Beanstalk  
- Setting up CloudFront CDN with ACM SSL certificate  
- Associating CloudFront distribution with Namecheap domain  

---

For detailed step-by-step deployment instructions, please see the `/docs` folder.

---

*Made with ❤️ for clear and organized AWS webstack deployment*
