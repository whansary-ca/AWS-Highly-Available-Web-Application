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

## Portfolio Documentation

- [`docs/architecture.md`](docs/architecture.md) — service roles and traffic flow
- [`docs/security.md`](docs/security.md) — security controls and production hardening ideas
- [`docs/validation.md`](docs/validation.md) — original deployment validation notes
- [`docs/TROUBLESHOOTING.md`](docs/TROUBLESHOOTING.md) — structured AWS/application troubleshooting workflow
- [`docs/INTERVIEW_NOTES.md`](docs/INTERVIEW_NOTES.md) — interview-ready project explanation and technical Q&A
- [`docs/PRODUCTION_IMPROVEMENTS.md`](docs/PRODUCTION_IMPROVEMENTS.md) — private-subnet, IAM, secret-management, HA, and monitoring improvements
- [`docs/COST_OPTIMIZATION.md`](docs/COST_OPTIMIZATION.md) — EC2, RDS, S3, load-balancer, Elastic Beanstalk, and CloudWatch cost considerations
- [`docs/FAILURE_SCENARIOS.md`](docs/FAILURE_SCENARIOS.md) — instance, target-health, RDS, TLS, S3, monitoring, and AZ failure analysis
- [`docs/DEPLOYMENT_CHECKLIST.md`](docs/DEPLOYMENT_CHECKLIST.md) — end-to-end deployment and evidence checklist
- [`docs/resume-bullets.md`](docs/resume-bullets.md) — concise resume-ready project bullets
- [`docs/evidence-status.md`](docs/evidence-status.md) — what original evidence has and has not been recovered

## Sanitized Configuration Examples

These files demonstrate safe configuration patterns and are explicitly examples rather than recovered exact production files:

- [`config/.env.example`](config/.env.example) — example environment variables with no real secrets
- [`config/wordpress-config-example.php`](config/wordpress-config-example.php) — WordPress environment-based database configuration pattern
- [`config/cloudwatch-monitoring-checklist.md`](config/cloudwatch-monitoring-checklist.md) — monitoring/evidence checklist

## Related AWS Security Coursework

Additional AWS lab material recovered from CYT160 is documented separately so it does not get confused with the WordPress high-availability project:

- [`related-aws-security-labs/dvwa-ec2-monitoring.md`](related-aws-security-labs/dvwa-ec2-monitoring.md) — EC2, CloudWatch, EventBridge, and SNS monitoring lab scope
- [`related-aws-security-labs/waf-guardduty-dvwa.md`](related-aws-security-labs/waf-guardduty-dvwa.md) — ALB, AWS WAF, and GuardDuty lab scope

These recovered files are lab specifications. They are intentionally labeled as related coursework rather than presented as completed-submission evidence unless implementation screenshots or results are recovered.

## Project Type

**Academic cloud project — Seneca Polytechnic**
