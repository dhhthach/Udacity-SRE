# Infrastructure

## AWS Zones
AWS us-east-2 (3 AZs) and us-west-1 (2 AZs)

## Servers and Clusters

### Table 1.1 Summary
| Asset      | Purpose           | Size                                                                   | Qty                                                             | DR                                                                                                           |
|------------|-------------------|------------------------------------------------------------------------|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Web server | Running Flask applications | t3.micro | 6 instances | Deployed to 2 regions |
| Load balancer | Balance request to given web server | | 2 instance | Deployed to 2 regions |
| K8s cluster | Running Prometheus stack for monitoring | t3.medium | 2 clusters (4 instances) | Deployed to 2 regions |
| VPC | Host cloud infastructure | | 2 VPC | Deployed to 2 regions |
| RDS | Application database | db.t3.micro | 2 clusters (4 instances) | Deployed replication to 2 regions |


### Descriptions
More detailed descriptions of each asset identified above.

## DR Plan
### Pre-Steps:
Ensure the infrastructure is set up and working in the DR site.

## Steps:
- Activate the secondary region by bringing up the necessary infrastructure, including network connections, firewalls, load balancers, and VPNs.
- Bring up the replicated database instances in the secondary region, and ensure that they are fully synchronized with the primary database instances.
- Bring up the replicated application instances in the secondary region, and ensure that they are fully synchronized with the primary application instances.
- Redirect incoming traffic from the primary region to the secondary region, using a global load balancer or DNS switch.
