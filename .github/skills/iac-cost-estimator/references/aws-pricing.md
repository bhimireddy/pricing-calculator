# AWS Static Pricing Reference

> Region: us-east-1 (N. Virginia) — prices in USD/month (730 hrs)  
> Last updated: 2025. Always note to users that prices may vary by region.

---

## EC2 Instances
**Terraform**: `aws_instance`  
**CloudFormation**: `AWS::EC2::Instance`  
Key attribute: `instance_type`

| Instance Type | vCPU | RAM | Monthly (On-Demand Linux) |
|---------------|------|-----|--------------------------|
| t3.nano | 2 | 0.5 GB | $3.80 |
| t3.micro | 2 | 1 GB | $7.59 |
| t3.small | 2 | 2 GB | $15.18 |
| t3.medium | 2 | 4 GB | $30.37 |
| t3.large | 2 | 8 GB | $60.74 |
| t3.xlarge | 4 | 16 GB | $121.47 |
| t3.2xlarge | 8 | 32 GB | $242.94 |
| m5.large | 2 | 8 GB | $70.08 |
| m5.xlarge | 4 | 16 GB | $140.16 |
| m5.2xlarge | 8 | 32 GB | $280.32 |
| m5.4xlarge | 16 | 64 GB | $560.64 |
| c5.large | 2 | 4 GB | $62.05 |
| c5.xlarge | 4 | 8 GB | $124.10 |
| c5.2xlarge | 8 | 16 GB | $248.20 |
| r5.large | 2 | 16 GB | $91.98 |
| r5.xlarge | 4 | 32 GB | $183.96 |
| r5.2xlarge | 8 | 64 GB | $367.92 |
| p3.2xlarge | 8 | 61 GB | $2,234.40 |
| g4dn.xlarge | 4 | 16 GB | $379.49 |

---

## RDS Instances
**Terraform**: `aws_db_instance`  
**CloudFormation**: `AWS::RDS::DBInstance`  
Key attributes: `db_instance_class`, `engine`

| Instance Class | Engine | Monthly |
|----------------|--------|---------|
| db.t3.micro | MySQL/Postgres | $12.41 |
| db.t3.small | MySQL/Postgres | $24.82 |
| db.t3.medium | MySQL/Postgres | $49.64 |
| db.t3.large | MySQL/Postgres | $99.28 |
| db.m5.large | MySQL/Postgres | $120.45 |
| db.m5.xlarge | MySQL/Postgres | $240.90 |
| db.m5.2xlarge | MySQL/Postgres | $481.80 |
| db.r5.large | MySQL/Postgres | $175.20 |
| db.r5.xlarge | MySQL/Postgres | $350.40 |
| db.t3.micro | SQL Server SE | $103.58 |
| db.m5.large | SQL Server SE | $357.01 |
| db.r5.large | Oracle EE | $730.00 |

> Storage: add ~$0.115/GB-month for gp2, $0.125/GB-month for gp3 (usage-based, not included in total)

---

## ElastiCache
**Terraform**: `aws_elasticache_cluster`, `aws_elasticache_replication_group`  
**CloudFormation**: `AWS::ElastiCache::CacheCluster`  
Key attribute: `cache_node_type`

| Node Type | Monthly |
|-----------|---------|
| cache.t3.micro | $11.52 |
| cache.t3.small | $23.04 |
| cache.t3.medium | $46.08 |
| cache.m5.large | $92.16 |
| cache.m5.xlarge | $184.32 |
| cache.r5.large | $146.00 |
| cache.r5.xlarge | $292.00 |

---

## EKS
**Terraform**: `aws_eks_cluster`  
**CloudFormation**: `AWS::EKS::Cluster`

| Resource | Monthly |
|----------|---------|
| EKS Cluster (control plane) | $73.00 |

> Worker nodes are separate EC2 instances — price those via `aws_instance` or node group.

---

## ECS / Fargate
**Terraform**: `aws_ecs_cluster`  
**CloudFormation**: `AWS::ECS::Cluster`

| Resource | Monthly |
|----------|---------|
| ECS Cluster | $0.00 (free, pay for tasks) |

**Fargate Tasks** (`aws_ecs_task_definition`):
- vCPU: $0.04048/vCPU-hour → ~$29.55/vCPU/month
- Memory: $0.004445/GB-hour → ~$3.24/GB/month

---

## Load Balancers
**Terraform**: `aws_lb`, `aws_alb`, `aws_elb`  
**CloudFormation**: `AWS::ElasticLoadBalancingV2::LoadBalancer`  
Key attribute: `load_balancer_type`

| Type | Monthly (base, no traffic) |
|------|---------------------------|
| Application Load Balancer (ALB) | $16.43 |
| Network Load Balancer (NLB) | $16.43 |
| Classic Load Balancer (CLB) | $18.25 |

> LCU/NLCU charges are usage-based and excluded from totals.

---

## NAT Gateway
**Terraform**: `aws_nat_gateway`  
**CloudFormation**: `AWS::EC2::NatGateway`

| Resource | Monthly |
|----------|---------|
| NAT Gateway (hourly charge) | $32.85 |

> Data processing ($0.045/GB) is usage-based and excluded.

---

## VPC / Networking
**Terraform**: `aws_vpc`, `aws_subnet`, `aws_internet_gateway`  
**CloudFormation**: `AWS::EC2::VPC`, `AWS::EC2::Subnet`

| Resource | Monthly |
|----------|---------|
| VPC | $0.00 |
| Subnet | $0.00 |
| Internet Gateway | $0.00 |
| Elastic IP (unattached) | $3.65 |
| VPN Connection | $36.50 |
| Transit Gateway | $36.50 |

---

## S3
**Terraform**: `aws_s3_bucket`  
**CloudFormation**: `AWS::S3::Bucket`

| Resource | Pricing |
|----------|---------|
| S3 Bucket | Usage-based (storage + requests) |

> Mark as UNPRICEABLE — usage-based.

---

## Lambda
**Terraform**: `aws_lambda_function`  
**CloudFormation**: `AWS::Lambda::Function`

| Resource | Pricing |
|----------|---------|
| Lambda Function | Usage-based (invocations + GB-seconds) |

> Mark as UNPRICEABLE — usage-based.

---

## CloudFront
**Terraform**: `aws_cloudfront_distribution`  
**CloudFormation**: `AWS::CloudFront::Distribution`

| Resource | Pricing |
|----------|---------|
| CloudFront Distribution | Usage-based (requests + data transfer) |

> Mark as UNPRICEABLE — usage-based.

---

## SQS / SNS
**Terraform**: `aws_sqs_queue`, `aws_sns_topic`  
**CloudFormation**: `AWS::SQS::Queue`, `AWS::SNS::Topic`

| Resource | Pricing |
|----------|---------|
| SQS Queue | Usage-based (requests) |
| SNS Topic | Usage-based (publishes + deliveries) |

> Mark as UNPRICEABLE — usage-based.

---

## DynamoDB
**Terraform**: `aws_dynamodb_table`  
**CloudFormation**: `AWS::DynamoDB::Table`

| Billing Mode | Pricing |
|--------------|---------|
| PAY_PER_REQUEST | Usage-based |
| PROVISIONED | $0.00065/RCU-hr + $0.00065/WCU-hr (usage-based) |

> Mark as UNPRICEABLE — usage-based.

---

## Secrets Manager
**Terraform**: `aws_secretsmanager_secret`  
**CloudFormation**: `AWS::SecretsManager::Secret`

| Resource | Monthly |
|----------|---------|
| Per secret | $0.40 |

---

## CloudWatch
**Terraform**: `aws_cloudwatch_log_group`, `aws_cloudwatch_metric_alarm`  
**CloudFormation**: `AWS::CloudWatch::Alarm`

| Resource | Monthly |
|----------|---------|
| CloudWatch Alarm | $0.10 per alarm |
| Log Group | Usage-based (ingestion + storage) — UNPRICEABLE |

---

## Route 53
**Terraform**: `aws_route53_zone`, `aws_route53_record`  
**CloudFormation**: `AWS::Route53::HostedZone`

| Resource | Monthly |
|----------|---------|
| Hosted Zone | $0.50 |
| DNS queries | Usage-based — UNPRICEABLE |

---

## ECR
**Terraform**: `aws_ecr_repository`  
**CloudFormation**: `AWS::ECR::Repository`

| Resource | Monthly |
|----------|---------|
| ECR Repository | $0.10/GB-month stored (usage-based) — UNPRICEABLE |

---

## IAM
**Terraform**: `aws_iam_role`, `aws_iam_policy`, `aws_iam_user`  
**CloudFormation**: `AWS::IAM::Role`, `AWS::IAM::Policy`

| Resource | Monthly |
|----------|---------|
| IAM Role / Policy / User | $0.00 (free) |

---

## SSM Parameter Store
**Terraform**: `aws_ssm_parameter`  
**CloudFormation**: `AWS::SSM::Parameter`

| Tier | Monthly |
|------|---------|
| Standard | $0.00 (free up to 10,000) |
| Advanced | $0.05 per parameter |
