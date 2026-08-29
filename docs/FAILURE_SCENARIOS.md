# Failure Scenarios

These scenarios explain how to reason about failures in the AWS web-application architecture represented in this repository. They are portfolio analysis based on the services used in the project, not a claim that every scenario was executed in the original lab.

## Scenario 1: One Application Instance Fails

Expected behavior in a properly configured load-balanced environment:

1. Health checks begin failing for the affected target.
2. The load balancer stops sending new traffic to the unhealthy target.
3. Healthy targets continue serving requests.
4. Auto Scaling can replace failed capacity if its health and capacity settings require it.

Investigate instance status, application/web-server status, health-check configuration, security groups, and logs.

## Scenario 2: Newly Launched Auto Scaling Instance Is Unhealthy

Possible causes:

- incomplete bootstrap/application configuration
- missing environment variables
- wrong application artifact/version
- web service not starting
- health-check path not available
- network/security configuration mismatch

A resilient design needs repeatable configuration so a replacement instance does not depend on manual changes made only to the original server.

## Scenario 3: WordPress Cannot Connect to RDS

Symptoms may include application database errors or failed page loads.

Investigate:

- RDS health/status
- database endpoint and DNS resolution
- database port reachability
- application configuration
- security-group relationships
- credential source

Avoid solving the issue by opening the database publicly unless public exposure is a deliberate, justified requirement.

## Scenario 4: Load Balancer Has No Healthy Targets

The application can become unavailable even if instances are technically running.

Check:

- target registration
- health-check path/port
- web-server status
- security-group reachability
- whether the application returns an acceptable status for the health check

## Scenario 5: TLS Certificate Problem

Potential symptoms:

- browser certificate warning
- expired certificate
- hostname mismatch
- HTTPS service unreachable

For the project's Certbot-based implementation, verify certificate status, domain mapping, and web-server TLS configuration. A production ALB design could use AWS Certificate Manager to reduce certificate-management overhead.

## Scenario 6: S3 Object Is Missing or Inaccessible

Check whether the problem is:

- wrong bucket/key
- deleted object
- IAM denial
- bucket policy/public-access configuration
- application-side path/configuration problem

Use least privilege rather than making a bucket public simply to bypass an access problem.

## Scenario 7: CloudWatch Alarm Does Not Fire

Check:

- correct metric/dimension
- correct evaluation period
- threshold
- missing data behavior
- notification action
- whether the workload actually crossed the threshold

## Scenario 8: RDS Failure or Outage

A single database endpoint is a critical dependency for WordPress. Production planning should consider Multi-AZ where appropriate, backups, restore testing, monitoring, and clear recovery procedures.

## Scenario 9: Traffic Spike

A scalable design should consider:

- load balancer health
- application capacity
- Auto Scaling reaction time
- database capacity/connection limits
- cache/static-content strategy
- CloudWatch alarms

Scaling compute alone may not solve a bottleneck in the database or application layer.

## Scenario 10: Entire Availability Zone Has Problems

A truly highly available production design should avoid depending on a single Availability Zone. Application instances, load-balancer subnets, and database availability strategy should be designed with failure domains in mind.

## Interview Principle

For each failure, explain four things:

**symptom -> affected layer -> verification method -> corrective action.**

That is more valuable than memorizing isolated AWS console steps.