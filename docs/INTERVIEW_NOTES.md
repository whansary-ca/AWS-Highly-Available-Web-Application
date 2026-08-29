# AWS Project Interview Notes

Use these notes to explain the project accurately in interviews. The repository represents an academic AWS deployment project, not paid production experience.

## 30-Second Explanation

I deployed a WordPress application using AWS services including EC2, RDS, S3, Elastic Beanstalk, Elastic Load Balancing, Auto Scaling, and CloudWatch. The project focused on separating compute, database, and storage responsibilities, improving availability through load balancing and scaling, monitoring the environment with CloudWatch, and securing web traffic with TLS using Let's Encrypt and Certbot. I also kept credentials out of application code by using environment-based configuration.

## Why Use EC2?

EC2 provides the virtual compute layer where the application can run. It gives control over the operating system, installed packages, web server, and application configuration.

## Why Use RDS Instead of a Database on EC2?

RDS moves database administration into a managed service. It separates the database tier from the application host and provides AWS-managed capabilities around database operations, backups, and availability depending on the selected configuration.

## What Does S3 Do?

S3 provides durable object storage. In a web architecture it can be used for files, assets, backups, exports, or other objects that should not depend on the local disk of one application server.

## What Is Elastic Beanstalk?

Elastic Beanstalk is a managed application deployment service. It can orchestrate underlying AWS resources while allowing the developer/operator to focus more on the application than manually building every infrastructure component.

## Why Use a Load Balancer?

A load balancer provides a stable application entry point and distributes requests across healthy application targets. It can remove unhealthy targets from service and supports architectures with more than one application instance.

## What Does Auto Scaling Add?

Auto Scaling changes application capacity based on configuration and scaling policies. It also helps maintain a desired number of instances when instances fail or demand changes.

## What Did CloudWatch Provide?

CloudWatch was used for monitoring application/infrastructure activity. In a production environment it can support metrics, alarms, dashboards, logs, and automated operational responses.

## How Was HTTPS Implemented?

The project used Let's Encrypt and Certbot for TLS/SSL. A production AWS design might instead terminate HTTPS at an Application Load Balancer using AWS Certificate Manager, depending on architecture requirements.

## How Were Credentials Protected?

Credentials were kept out of application source code using environment-based configuration. A stronger production implementation would use IAM roles and a managed secret service such as AWS Secrets Manager or Systems Manager Parameter Store.

## Availability vs. Disaster Recovery

Load balancing and Auto Scaling improve service availability, but they do not automatically provide complete disaster recovery. Production DR would also consider database recovery, backups, regional failure, infrastructure recreation, DNS strategy, and recovery objectives.

## Likely Follow-Up Questions

Be ready to explain:

- what happens when a load balancer target becomes unhealthy
- how an application instance connects to RDS
- the difference between EC2 and Elastic Beanstalk
- why Auto Scaling needs health checks and metrics
- why a database should not be publicly exposed unnecessarily
- how CloudWatch can alert operators
- how you would improve the architecture for production

## Important Accuracy Statement

Describe this as **hands-on academic/project experience**. Do not describe it as production AWS employment or claim exact configurations that are not preserved in the recovered project evidence.