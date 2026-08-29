# Deployment Validation Checklist

This checklist documents the types of checks used to confirm that the AWS WordPress environment was functioning as intended.

## Application

- [ ] WordPress application loads successfully over HTTP/HTTPS.
- [ ] Application pages render without database connection errors.
- [ ] Administrative and public pages respond as expected.

## Compute and Scaling

- [ ] EC2 application instances are healthy.
- [ ] Load balancer target health is healthy.
- [ ] Traffic is distributed through the load-balancing layer.
- [ ] Auto Scaling environment maintains the desired application capacity.

## Database

- [ ] Application can connect to the managed RDS database.
- [ ] Database configuration is supplied without hardcoded credentials in source code.
- [ ] Application reads/writes expected WordPress data successfully.

## Storage

- [ ] Required S3 storage is reachable by the application or workflow using it.
- [ ] Object access behaves as intended for the project design.

## Monitoring

- [ ] CloudWatch shows infrastructure/application activity.
- [ ] Instance and environment health can be reviewed from AWS monitoring tools.

## Security

- [ ] HTTPS is functional with the configured TLS certificate.
- [ ] Browser certificate validation succeeds.
- [ ] Sensitive credentials are not committed to source files.
- [ ] Application configuration uses environment variables where appropriate.

## Troubleshooting Sequence

When a web request fails, validate the stack in this order:

1. DNS/URL and browser reachability.
2. TLS certificate and HTTPS configuration.
3. Load balancer and target health.
4. EC2/application service health.
5. Application configuration and environment variables.
6. RDS connectivity and database configuration.
7. S3 access where required.
8. CloudWatch activity and relevant logs/metrics.

This validation document is based on the technologies and troubleshooting scope demonstrated in the academic project; it does not claim specific production SLAs or benchmark results.
