# Architecture Overview

## Logical Design

The project combined AWS managed and compute services to host a WordPress application with improved availability, scalability, monitoring, and separation of application data from the compute layer.

```text
User
  |
 HTTPS
  |
Elastic Load Balancer
  |
Auto Scaling application instances
  |
WordPress
  |\
  | \__ Amazon S3 — object storage
  |
  +____ Amazon RDS — managed database

Amazon CloudWatch — monitoring
Elastic Beanstalk — application/environment management
Let's Encrypt / Certbot — TLS certificate configuration
```

## Component Roles

### Amazon EC2
Provided the compute layer used to run the web application workload.

### Amazon RDS
Provided a managed database service so the application database could be separated from the web/compute layer.

### Amazon S3
Provided managed object storage as part of the application architecture.

### AWS Elastic Beanstalk
Used as a managed application deployment/environment service in the project.

### Elastic Load Balancing
Distributed incoming traffic across application capacity and supported the high-availability design.

### Auto Scaling
Supported horizontal scaling and replacement/addition of application capacity based on environment needs.

### Amazon CloudWatch
Provided monitoring of application and infrastructure activity.

### TLS/SSL
Let's Encrypt and Certbot were used to secure web traffic with HTTPS.

## Design Goals

The project was built to practice:

1. separating compute, database, and storage responsibilities;
2. reducing dependence on a single application instance;
3. introducing elasticity through Auto Scaling;
4. distributing traffic through a load balancer;
5. monitoring the environment through CloudWatch; and
6. protecting application traffic and credentials.
