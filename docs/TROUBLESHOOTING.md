# AWS Web Application Troubleshooting Guide

This guide documents a practical troubleshooting workflow for the AWS WordPress project represented in this repository. It focuses on the services evidenced in the project: EC2, RDS, S3, Elastic Beanstalk, Elastic Load Balancing, Auto Scaling, CloudWatch, and TLS/SSL with Certbot.

## 1. Application Does Not Load

Check the path from the client to the application in layers:

1. Confirm DNS/URL resolution.
2. Confirm the load balancer endpoint responds.
3. Check target health in the load balancer target group.
4. Confirm the EC2/application instance is running.
5. Verify the web service is active on the instance.
6. Confirm the application can connect to its database.
7. Review security-group and network reachability.
8. Review CloudWatch metrics and application logs.

## 2. Unhealthy Load Balancer Target

Possible causes include:

- web service not running
- incorrect health-check path
- wrong listener/target port
- instance not reachable from the load balancer
- application returning an error on the health-check URL

Validation steps:

- inspect target-group health status
- test the application locally from the instance
- verify the configured listener and target ports
- review web-server logs
- compare security-group rules with the expected traffic path

## 3. WordPress Cannot Reach RDS

Check:

- RDS instance status
- database endpoint and port
- application database settings
- security-group relationship between application and database tiers
- DNS resolution from the application host
- database credentials/configuration source

Do not place real database passwords in this repository. The project used environment-based configuration rather than hardcoded secrets.

## 4. TLS/SSL Problems

For the project configuration using Let's Encrypt and Certbot, inspect:

- certificate status and expiry
- web-server virtual-host configuration
- inbound HTTPS reachability
- HTTP-to-HTTPS redirection
- certificate hostname/domain match

Useful checks on a Linux host can include web-server configuration validation, service status, and Certbot certificate information.

## 5. Auto Scaling Does Not Behave as Expected

Check:

- desired/minimum/maximum capacity
- instance launch failures
- health-check results
- scaling policy configuration
- CloudWatch metric availability
- whether newly launched instances have the application configuration they need

## 6. CloudWatch Shows No Useful Data

Confirm that:

- the correct resource/metric is selected
- the time range is appropriate
- the resource is running
- the metric exists for the service
- alarms use the intended metric and threshold

## 7. S3/Application Asset Problems

If the application expects S3-backed objects, validate:

- bucket and object existence
- object key/path
- IAM permissions
- application configuration
- whether public access is intentionally required or should remain blocked

## Troubleshooting Method

Use a repeatable sequence:

**Observe -> isolate the affected layer -> inspect configuration/logs -> make one change -> retest -> document the result.**

This prevents random changes and makes troubleshooting easier to explain during technical interviews.