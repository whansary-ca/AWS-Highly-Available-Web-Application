# Security Notes

## Controls Demonstrated

### HTTPS / TLS
The application was secured with TLS/SSL using Let's Encrypt and Certbot so browser-to-application traffic could use HTTPS.

### Credential Handling
Sensitive configuration was kept out of application source code by using environment variables rather than hardcoding credentials.

### Managed Service Separation
Using a managed database service and object storage separated application data responsibilities from the compute layer.

## Production Hardening Opportunities

The following controls would strengthen a production implementation:

- place database resources in private subnets;
- restrict database security-group access to only the application tier;
- use IAM roles instead of static AWS access keys wherever possible;
- store application secrets in AWS Secrets Manager or Systems Manager Parameter Store;
- use ACM-managed certificates when appropriate for AWS-native TLS termination;
- enable CloudTrail for API auditing;
- configure CloudWatch alarms and centralized log retention;
- use AWS WAF in front of internet-facing web workloads;
- enable encryption at rest for RDS and S3;
- enable S3 Block Public Access unless public objects are explicitly required;
- apply least-privilege IAM policies;
- define backup and database-retention policies;
- patch and harden EC2 instances regularly;
- restrict administrative access to trusted paths rather than exposing management services broadly.

These items are documented as recommended improvements and are not presented as controls that were necessarily implemented in the original coursework environment.
