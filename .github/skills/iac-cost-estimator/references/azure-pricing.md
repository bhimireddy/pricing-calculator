# Azure Static Pricing Reference

> Region: East US — prices in USD/month (730 hrs)  
> Last updated: 2025. Always note to users that prices may vary by region.

---

## Virtual Machines
**Terraform**: `azurerm_virtual_machine`, `azurerm_linux_virtual_machine`, `azurerm_windows_virtual_machine`  
Key attributes: `size` (VM SKU)

| VM Size | vCPU | RAM | Monthly (Pay-as-you-go Linux) |
|---------|------|-----|-------------------------------|
| Standard_B1s | 1 | 1 GB | $7.59 |
| Standard_B1ms | 1 | 2 GB | $15.18 |
| Standard_B2s | 2 | 4 GB | $30.37 |
| Standard_B2ms | 2 | 8 GB | $60.74 |
| Standard_B4ms | 4 | 16 GB | $121.47 |
| Standard_D2s_v3 | 2 | 8 GB | $70.08 |
| Standard_D4s_v3 | 4 | 16 GB | $140.16 |
| Standard_D8s_v3 | 8 | 32 GB | $280.32 |
| Standard_D16s_v3 | 16 | 64 GB | $560.64 |
| Standard_E2s_v3 | 2 | 16 GB | $91.98 |
| Standard_E4s_v3 | 4 | 32 GB | $183.96 |
| Standard_E8s_v3 | 8 | 64 GB | $367.92 |
| Standard_F2s_v2 | 2 | 4 GB | $62.05 |
| Standard_F4s_v2 | 4 | 8 GB | $124.10 |
| Standard_NC6 | 6 | 56 GB | $657.00 |
| Standard_NC12 | 12 | 112 GB | $1,314.00 |

> Windows VMs add ~40% for OS licensing. Check `os_disk` or image reference for OS type.

---

## Azure SQL Database
**Terraform**: `azurerm_sql_database`, `azurerm_mssql_database`  
Key attributes: `sku_name`, `max_size_gb`

| SKU | vCores | Monthly |
|-----|--------|---------|
| Basic | — | $4.99 |
| S0 (Standard) | — | $14.65 |
| S1 (Standard) | — | $29.30 |
| S2 (Standard) | — | $73.00 |
| S3 (Standard) | — | $146.00 |
| GP_Gen5_2 (General Purpose) | 2 | $369.30 |
| GP_Gen5_4 (General Purpose) | 4 | $738.60 |
| GP_Gen5_8 (General Purpose) | 8 | $1,477.20 |
| BC_Gen5_2 (Business Critical) | 2 | $1,094.10 |
| BC_Gen5_4 (Business Critical) | 4 | $2,188.20 |

> Storage: ~$0.115/GB-month (usage-based, not included in total)

---

## Azure Database for PostgreSQL
**Terraform**: `azurerm_postgresql_server`, `azurerm_postgresql_flexible_server`  
Key attributes: `sku_name`

| SKU | vCores | RAM | Monthly |
|-----|--------|-----|---------|
| B_Gen5_1 | 1 | 2 GB | $25.55 |
| B_Gen5_2 | 2 | 4 GB | $51.10 |
| GP_Gen5_2 | 2 | 10 GB | $185.34 |
| GP_Gen5_4 | 4 | 20 GB | $370.68 |
| GP_Gen5_8 | 8 | 40 GB | $741.36 |
| MO_Gen5_2 | 2 | 10 GB | $342.34 |
| MO_Gen5_4 | 4 | 20 GB | $684.68 |

---

## Azure Database for MySQL
**Terraform**: `azurerm_mysql_server`, `azurerm_mysql_flexible_server`  
Key attributes: `sku_name`

| SKU | vCores | RAM | Monthly |
|-----|--------|-----|---------|
| B_Gen5_1 | 1 | 2 GB | $25.55 |
| B_Gen5_2 | 2 | 4 GB | $51.10 |
| GP_Gen5_2 | 2 | 10 GB | $185.34 |
| GP_Gen5_4 | 4 | 20 GB | $370.68 |
| GP_Gen5_8 | 8 | 40 GB | $741.36 |

---

## Azure Kubernetes Service (AKS)
**Terraform**: `azurerm_kubernetes_cluster`

| Resource | Monthly |
|----------|---------|
| AKS Control Plane (Free tier) | $0.00 |
| AKS Control Plane (Standard) | $73.00 |

> Worker nodes are separate VMs — price via `azurerm_linux_virtual_machine` / node pool.

---

## Azure Cache for Redis
**Terraform**: `azurerm_redis_cache`  
Key attributes: `family`, `capacity`, `sku_name`

| SKU | Size | Monthly |
|-----|------|---------|
| Basic C0 | 250 MB | $13.14 |
| Basic C1 | 1 GB | $54.02 |
| Standard C0 | 250 MB | $26.28 |
| Standard C1 | 1 GB | $108.04 |
| Standard C2 | 6 GB | $216.08 |
| Premium P1 | 6 GB | $383.28 |
| Premium P2 | 13 GB | $766.56 |

---

## Load Balancer
**Terraform**: `azurerm_lb`  
Key attribute: `sku`

| SKU | Monthly |
|-----|---------|
| Basic | $0.00 |
| Standard | $18.25 |

> Data processing is usage-based and excluded.

---

## Application Gateway
**Terraform**: `azurerm_application_gateway`  
Key attribute: `sku` → `tier` (Standard, WAF, Standard_v2, WAF_v2)

| Tier | Monthly (base, no traffic) |
|------|---------------------------|
| Standard Small | $18.25 |
| Standard Medium | $91.25 |
| Standard Large | $365.00 |
| WAF Medium | $182.50 |
| Standard_v2 | $182.50 |
| WAF_v2 | $292.00 |

---

## Azure Container Registry
**Terraform**: `azurerm_container_registry`  
Key attribute: `sku`

| SKU | Monthly |
|-----|---------|
| Basic | $5.00 |
| Standard | $20.00 |
| Premium | $50.00 |

---

## Azure Key Vault
**Terraform**: `azurerm_key_vault`

| Resource | Monthly |
|----------|---------|
| Key Vault (base) | $0.00 (pay per operation) |

> Operations are usage-based — mark as UNPRICEABLE.

---

## Storage Account
**Terraform**: `azurerm_storage_account`

| Resource | Pricing |
|----------|---------|
| Storage Account | Usage-based (capacity + transactions) |

> Mark as UNPRICEABLE — usage-based.

---

## Azure Functions
**Terraform**: `azurerm_function_app`, `azurerm_linux_function_app`

| Resource | Pricing |
|----------|---------|
| Function App (Consumption) | Usage-based (executions + GB-seconds) |

> Mark as UNPRICEABLE — usage-based.

---

## Azure Service Bus
**Terraform**: `azurerm_servicebus_namespace`  
Key attribute: `sku`

| SKU | Monthly |
|-----|---------|
| Basic | $0.05/million operations (usage-based) — UNPRICEABLE |
| Standard | $9.81 base + usage |
| Premium (1 MU) | $677.61 |

---

## Azure Virtual Network
**Terraform**: `azurerm_virtual_network`, `azurerm_subnet`, `azurerm_network_security_group`

| Resource | Monthly |
|----------|---------|
| Virtual Network | $0.00 |
| Subnet | $0.00 |
| Network Security Group | $0.00 |
| VNet Peering (intra-region, per GB) | Usage-based — UNPRICEABLE |

---

## Public IP Address
**Terraform**: `azurerm_public_ip`  
Key attribute: `sku`, `allocation_method`

| Type | Monthly |
|------|---------|
| Basic Dynamic | $0.00 |
| Basic Static | $2.63 |
| Standard Static | $3.65 |

---

## NAT Gateway
**Terraform**: `azurerm_nat_gateway`

| Resource | Monthly |
|----------|---------|
| NAT Gateway | $32.85 |

> Data processing ($0.045/GB) is usage-based and excluded.

---

## Azure DNS
**Terraform**: `azurerm_dns_zone`, `azurerm_private_dns_zone`

| Resource | Monthly |
|----------|---------|
| Public DNS Zone | $0.50 |
| Private DNS Zone | $0.50 |
| DNS queries | Usage-based — UNPRICEABLE |

---

## Azure Monitor / Log Analytics
**Terraform**: `azurerm_log_analytics_workspace`, `azurerm_monitor_metric_alert`

| Resource | Monthly |
|----------|---------|
| Log Analytics (ingestion) | Usage-based — UNPRICEABLE |
| Monitor Alert Rule | $0.10 per alert/month |

---

## Azure App Service
**Terraform**: `azurerm_app_service_plan`, `azurerm_service_plan`  
Key attribute: `sku_name`

| SKU | Monthly |
|-----|---------|
| F1 (Free) | $0.00 |
| B1 (Basic) | $12.41 |
| B2 (Basic) | $24.82 |
| B3 (Basic) | $49.64 |
| S1 (Standard) | $58.40 |
| S2 (Standard) | $116.80 |
| S3 (Standard) | $233.60 |
| P1v2 (Premium) | $73.00 |
| P2v2 (Premium) | $146.00 |
| P3v2 (Premium) | $292.00 |
| P1v3 (Premium v3) | $111.69 |
| P2v3 (Premium v3) | $223.38 |

---

## Azure Cosmos DB
**Terraform**: `azurerm_cosmosdb_account`

| Resource | Pricing |
|----------|---------|
| Cosmos DB | Usage-based (RU/s + storage) |

> Mark as UNPRICEABLE — usage-based.

---

## Azure Event Hub
**Terraform**: `azurerm_eventhub_namespace`  
Key attribute: `sku`

| SKU | Monthly |
|-----|---------|
| Basic | $9.22 base + usage |
| Standard | $21.91 base + usage |
| Premium (1 PU) | $730.00 |
