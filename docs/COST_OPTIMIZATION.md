# AWS Cost Optimization Notes

This document describes cost-management practices that would be relevant to the AWS services used in this project. These are optimization recommendations, not claims about the exact billing configuration of the original academic environment.

## EC2 and Auto Scaling

- Right-size instance types based on observed CPU, memory, and application demand.
- Avoid maintaining more minimum capacity than the availability requirement needs.
- Use Auto Scaling to add capacity only when required.
- Stop or terminate unused lab resources when testing is complete.
- For predictable long-term workloads, evaluate commitment-based pricing separately from short academic workloads.

## RDS

- Select a database class appropriate to actual workload demand.
- Monitor CPU, connections, storage, and I/O before increasing capacity.
- Remove unused test databases and snapshots when they are no longer required and retention rules allow it.
- Balance backup retention and high-availability requirements against cost.

## S3

- Store only required objects and logs.
- Use lifecycle policies to transition or expire older objects where appropriate.
- Review duplicate or abandoned artifacts.
- Choose storage classes based on access patterns rather than placing all objects in one tier indefinitely.

## Load Balancing

Load balancers have their own operating and usage costs. In a production environment they can be justified by availability, health checking, and traffic distribution. For temporary labs, unused load balancers should be deleted after testing.

## CloudWatch

CloudWatch costs can grow with excessive logs, high-cardinality custom metrics, dashboards, and long retention periods.

Useful practices include:

- retain logs only as long as operational/compliance needs require
- avoid collecting unnecessary custom metrics
- remove obsolete alarms and dashboards
- monitor logging volume

## Elastic Beanstalk

Elastic Beanstalk itself manages underlying AWS resources, so cost optimization requires reviewing the EC2 instances, load balancers, storage, database resources, and other services created or used by the environment.

## Cost Review Checklist

Before leaving an AWS lab environment:

1. Check running EC2 instances.
2. Check Elastic Beanstalk environments.
3. Check load balancers and target groups.
4. Check RDS databases and snapshots.
5. Check S3 objects that should be removed.
6. Check CloudWatch log groups and retention.
7. Check unattached storage/resources.
8. Confirm resources are intentionally retained before ending the session.

Cost optimization should never remove redundancy, monitoring, backups, or security controls without first understanding the business requirement they support.