
# Subscription and Resource Groups

## Overview
In Microsoft Azure, **Subscriptions** and **Resource Groups** are the core building blocks used to organize, manage, secure, and bill cloud resources.

- **Subscription** → Billing and access boundary  
- **Resource Group** → Logical container for related resources  

Every Azure resource must belong to a resource group, and every resource group must belong to a subscription.

---

## Azure Subscription – Detailed Explanation

### What is an Azure Subscription?
An **Azure Subscription** is a logical unit that:
- Tracks billing
- Controls access permissions
- Defines service limits (quotas)

### Why Subscriptions Are Important
- Separate **Production and Non-Production**
- Control access using **RBAC**
- Track costs per team or project
- Apply **security policies**

### Common Subscription Types
- Free
- Pay-As-You-Go
- Enterprise Agreement (EA)
- Cloud Solution Provider (CSP)

---

## Resource Groups – Detailed Explanation

### What is a Resource Group?
A **Resource Group (RG)** is a logical container that holds related Azure resources for:
- A single application
- A specific environment (Dev / Test / Prod)
- A business unit or team

### Key Rules of Resource Groups
- Resources can be moved between RGs (most services)
- Resource Groups do not incur cost
- Deleting an RG deletes **all** resources inside it
- Resources in an RG can be in different regions

---

## Resource Lifecycle Management

| Phase | Description |
|-----|------------|
| Creation | Deploy all resources together |
| Management | Apply RBAC, policies, and tags |
| Monitoring | View logs and health |
| Deletion | Clean removal of all resources |

---

## Naming Conventions (Best Practice)

```
<project>-<environment>-<resource>
```

**Examples**
- ecommerce-prod-rg
- ecommerce-dev-vm01
- ecommerce-prod-vnet

---

## Tagging Strategy

Tags are **key-value pairs** used for:
- Cost tracking
- Ownership
- Environment identification

| Key | Example |
|---|---|
| Environment | Prod |
| Project | Ecommerce |
| Owner | DevOps-Team |
| CostCenter | FIN-001 |

---

## Cost Management Basics
- Costs are tracked at the **subscription level**
- Tags allow **cost breakdown per project/team**
- Azure Cost Management provides:
  - Daily/monthly spend
  - Forecast
  - Budget alerts

---

## Real-Time Example: E-Commerce Application

### Scenario
A company deploys an **E-Commerce application** with **Dev** and **Prod** environments.

### Subscription Design
| Subscription | Purpose |
|---|---|
| Ecommerce-Dev-Sub | Development and testing |
| Ecommerce-Prod-Sub | Production workload |

### Resource Group Design

**Dev**
```
Subscription: Ecommerce-Dev-Sub
Resource Group: ecommerce-dev-rg
Resources:
- Virtual Network
- Dev VM
- Storage Account
- Azure SQL Database
```

**Prod**
```
Subscription: Ecommerce-Prod-Sub
Resource Group: ecommerce-prod-rg
Resources:
- Virtual Network
- VM Scale Set
- Load Balancer
- Azure SQL Database
- Application Gateway
```

### Tagging Example
Environment : Production  
Project : Ecommerce  
Owner : DevOps  
CostCenter : CC-102  

### Lifecycle Advantage
```bash
az group delete --name ecommerce-dev-rg
```

---

## Azure Services Used
- Azure Portal
- Azure CLI
- Azure Resource Manager (ARM)
- Azure Cost Management

---

## Key Interview Takeaways
- Subscription = Billing + access boundary
- Resource Group = Lifecycle management
- Tags = Cost visibility
- Deleting RG deletes everything
- Always separate Dev and Prod
