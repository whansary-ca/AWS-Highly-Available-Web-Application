# AWS Highly Available Web Application

A hands-on AWS cloud project completed through Seneca Polytechnic coursework. The project focused on deploying and securing a scalable WordPress application using managed AWS services for compute, database, storage, elasticity, monitoring, and availability.

## Project Scope

The environment used the following AWS services and supporting tools:

- **Amazon EC2** for compute
- **Amazon RDS** for managed database services
- **Amazon S3** for object storage
- **AWS Elastic Beanstalk** for application deployment and environment management
- **Elastic Load Balancing** for distributing application traffic
- **Auto Scaling** for elasticity and availability
- **Amazon CloudWatch** for infrastructure and application monitoring
- **Let's Encrypt / Certbot** for TLS/SSL
- **Environment variables** to keep credentials out of application code

## What Was Implemented

- Deployed a WordPress web application using AWS compute, database, storage, and managed application services.
- Configured load balancing and Auto Scaling to improve availability and support changing demand.
- Used CloudWatch to monitor infrastructure and application activity.
- Secured web traffic with TLS/SSL using Let's Encrypt and Certbot.
- Avoided hardcoded credentials by using environment variables for sensitive configuration.

## Architecture

```text
                    Internet / HTTPS
                           |
                   Elastic Load Balancer
                           |
                 +---------+---------+
                 |                   |
              EC2 / App          EC2 / App
                 \                   /
                  \   Auto Scaling  /
                   +-------+-------+
                           |
                    WordPress Layer
                     /            \
                    /              \
                 Amazon RDS      Amazon S3
                 Database        Object Storage

               Monitoring: Amazon CloudWatch
               TLS: Let's Encrypt / Certbot
```

> The diagram represents the logical service relationships demonstrated in the project and is intended as portfolio documentation, not as a claim of a production deployment.

## Skills Demonstrated

- AWS cloud application deployment
- Highly available application design concepts
- EC2, RDS, S3, and Elastic Beanstalk administration
- Load balancing and Auto Scaling
- CloudWatch monitoring
- WordPress deployment and troubleshooting
- TLS/SSL configuration
- Credential-handling and configuration hygiene
- Cloud infrastructure documentation

## Documentation

- [`docs/architecture.md`](docs/architecture.md) — service roles and traffic flow
- [`docs/security.md`](docs/security.md) — security controls and production hardening ideas
- [`docs/validation.md`](docs/validation.md) — deployment validation checklist
- [`docs/resume-bullets.md`](docs/resume-bullets.md) — concise resume-ready project bullets

## Project Type

**Academic cloud project — Seneca Polytechnic**
