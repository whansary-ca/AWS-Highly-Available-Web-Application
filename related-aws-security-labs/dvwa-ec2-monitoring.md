# Related AWS Coursework: DVWA on EC2 with Monitoring

This document summarizes recovered CYT160 lab material related to AWS operations and monitoring. It is included as related coursework and is **not presented as completion evidence for the WordPress high-availability project**.

## Lab Scope

The recovered lab specification covered:

- Launching an Ubuntu 22.04 LTS EC2 instance
- Restricting SSH, HTTP, and HTTPS security-group access to the user's IP
- Installing Apache, MySQL, PHP, and DVWA
- Configuring a local DVWA database
- Testing the intentionally vulnerable application in a controlled training environment
- Creating an SNS topic for EC2 notifications
- Creating an EventBridge rule for EC2 instance state changes
- Creating a CloudWatch CPUUtilization alarm for an idle EC2 instance
- Testing stop-state and idle notifications

## Monitoring Architecture

```text
EC2 (Ubuntu + DVWA)
        |
        +--> EventBridge rule --> SNS topic --> Email notification
        |
        +--> CloudWatch CPUUtilization alarm --> SNS topic --> Email notification
```

## Operational Concepts Demonstrated by the Lab

- EC2 provisioning and security-group configuration
- Linux web-server administration
- Application deployment on EC2
- CloudWatch metric-based alerting
- Event-driven EC2 state monitoring with EventBridge
- SNS notification workflows
- Basic service validation and alert testing

## Security Note

The source lab used intentionally vulnerable software and example credentials for training. Those credential values are deliberately omitted here. This repository does not publish reusable passwords, private keys, or account-specific secrets.
