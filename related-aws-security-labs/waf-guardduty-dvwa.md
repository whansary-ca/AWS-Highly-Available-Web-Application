# Related AWS Coursework: WAF and GuardDuty on DVWA

This document summarizes recovered CYT160 lab material related to AWS application security and threat monitoring. It is included as related coursework and is **not presented as completion evidence for the WordPress high-availability project**.

## Lab Scope

The recovered lab specification covered:

- Creating an internet-facing Application Load Balancer (ALB)
- Registering an EC2-hosted DVWA instance in a target group
- Configuring a health-check path for the application
- Associating AWS WAF with the ALB
- Enabling AWS managed rules for SQL-injection protection
- Configuring account-takeover protection for the login page
- Reviewing WAF logging and metrics
- Enabling Amazon GuardDuty
- Verifying the GuardDuty detector
- Generating controlled reconnaissance traffic in a training environment
- Reviewing GuardDuty findings such as EC2 port-scan detections

## Security Architecture

```text
Internet
   |
Application Load Balancer
   |
AWS WAF
   |
EC2-hosted DVWA

GuardDuty ---> threat findings / investigation
```

## Concepts Demonstrated by the Lab

- Application Load Balancer configuration
- Target groups and health checks
- Web application firewall deployment
- AWS managed WAF rule groups
- SQL-injection request filtering
- Account-takeover and brute-force protection concepts
- GuardDuty threat detection
- Cloud security logging and finding analysis

## Responsible Use

DVWA is intentionally vulnerable and was designed for controlled security training. Attack strings and scanning activity described by the source lab are treated as lab-only validation techniques. No production targets, credentials, or secrets are included in this repository.
