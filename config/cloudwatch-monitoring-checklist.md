# CloudWatch Monitoring Checklist

This is a generic monitoring checklist for the AWS services represented in this portfolio project. Exact alarms and thresholds should be chosen from workload requirements and measured behavior rather than copied blindly.

## Application / EC2

- [ ] CPU utilization is visible.
- [ ] Instance status checks are healthy.
- [ ] Application/web-server logs are available where configured.
- [ ] Resource pressure or repeated restarts are investigated.

## Elastic Load Balancing

- [ ] Healthy/unhealthy target count is reviewed.
- [ ] Request and error behavior is monitored where available.
- [ ] Target-response problems are investigated against application logs.

## Auto Scaling

- [ ] Desired, minimum, and maximum capacity are reviewed.
- [ ] Launch/termination activity is visible.
- [ ] Scaling events are correlated with application demand and target health.

## RDS

- [ ] CPU utilization is reviewed.
- [ ] Database connections are reviewed.
- [ ] Storage and I/O pressure are monitored where relevant.
- [ ] Database availability is verified when application errors occur.

## Alarm Design

For each important alarm, document:

- metric
- resource/dimension
- threshold
- evaluation period
- missing-data behavior
- notification destination
- operator response

## Portfolio Evidence

When screenshots become available, prioritize sanitized evidence showing:

1. CloudWatch metric for a project resource
2. healthy load-balancer targets
3. Auto Scaling group state
4. RDS availability/monitoring
5. application reachable over HTTPS

Do not expose AWS account identifiers, credentials, email addresses, tokens, database passwords, or other private data in public screenshots.