# Deployment Checklist

This checklist provides a repeatable way to validate an AWS web-application deployment using the services represented in this project.

## Compute and Application

- [ ] EC2/application instances are running.
- [ ] Web service is active.
- [ ] WordPress/application page loads locally from the instance where appropriate.
- [ ] Application configuration contains no hardcoded secrets committed to source control.

## Database

- [ ] RDS database is available.
- [ ] Application uses the correct database endpoint.
- [ ] Database port is reachable from the application tier.
- [ ] Application successfully establishes a database connection.
- [ ] Database is not unintentionally exposed to the Internet.

## Load Balancing

- [ ] Load balancer exists and listener configuration is correct.
- [ ] Target group contains the intended application targets.
- [ ] Health-check path and port match the application.
- [ ] Targets report healthy before relying on the load-balancer endpoint.
- [ ] Application is reachable through the load-balancer endpoint.

## Auto Scaling

- [ ] Scaling group has valid minimum, desired, and maximum capacity.
- [ ] New instances can launch successfully.
- [ ] New instances receive the application/configuration required to become healthy.
- [ ] Health checks and replacement behavior are understood.

## S3

- [ ] Required bucket/object paths exist.
- [ ] IAM/bucket policies grant only the required access.
- [ ] Unintended public access is blocked.
- [ ] Application/object access works as designed.

## Monitoring

- [ ] Relevant CloudWatch metrics are visible.
- [ ] Monitoring uses the correct resource dimensions.
- [ ] Important alarms are defined where required.
- [ ] Alarm notification destinations are tested in production-style deployments.

## TLS/HTTPS

For the project's Certbot-based implementation:

- [ ] Certificate is installed.
- [ ] Certificate hostname matches the application domain.
- [ ] HTTPS responds successfully.
- [ ] Certificate expiry/renewal is understood.
- [ ] HTTP redirect behavior is verified if enabled.

## Security

- [ ] Credentials are not hardcoded into source files.
- [ ] Security-group access is limited to required traffic paths.
- [ ] Administrative access is restricted.
- [ ] Database access is limited to required application sources.
- [ ] IAM permissions follow least privilege where practical.

## End-to-End Validation

- [ ] Client reaches application endpoint.
- [ ] Load balancer sends traffic to healthy target(s).
- [ ] Application reaches RDS.
- [ ] Required S3 objects are accessible.
- [ ] HTTPS works.
- [ ] CloudWatch shows expected activity.
- [ ] Failure of one application target does not unnecessarily break all service when redundant healthy capacity exists.

## Evidence Collection

For a portfolio/demo, capture sanitized evidence of:

- load-balancer target health
- Auto Scaling group status
- RDS availability without exposing credentials
- CloudWatch metrics/alarms
- successful HTTPS application access
- architecture diagram

Never publish AWS account IDs, private keys, access keys, database passwords, tokens, personal identifiers, or other secrets in screenshots or repository files.