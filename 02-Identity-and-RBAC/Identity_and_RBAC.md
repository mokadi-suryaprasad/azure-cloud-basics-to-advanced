
# Identity and RBAC

## Overview
Azure **Identity and Access Management (IAM)** is handled using **Microsoft Entra ID** (formerly Azure Active Directory) along with **Role-Based Access Control (RBAC)**.

Identity and RBAC together ensure:
- The right people have access
- To the right resources
- With the right permissions
- At the right scope

---

## Microsoft Entra ID (Azure AD) – Detailed Explanation

### What is Microsoft Entra ID?
Microsoft Entra ID is a cloud-based identity and access management service used to:
- Authenticate users
- Manage identities
- Secure access to Azure resources and applications

### What Entra ID Manages
- Users
- Groups
- Service Principals
- Managed Identities
- Applications

### Authentication vs Authorization
| Term | Meaning |
|---|---|
| Authentication | Who are you? |
| Authorization | What can you do? |

---

## Identity Types in Azure

### Users
Human identities such as employees and external users.

### Groups
Used to manage permissions efficiently by grouping users.

### Service Principals
Non-human identities used by applications, automation, and CI/CD pipelines.

### Managed Identities
Azure-managed identities with no credentials to store.

---

## Role-Based Access Control (RBAC)

### What is RBAC?
RBAC defines who can do what on Azure resources. It controls authorization.

### RBAC Components
- Security Principal
- Role Definition
- Scope

---

## RBAC Scopes

| Scope | Example |
|---|---|
| Management Group | Entire organization |
| Subscription | All resources |
| Resource Group | Specific workload |
| Resource | Single resource |

---

## Built-in Roles

| Role | Permissions |
|---|---|
| Owner | Full access + assign roles |
| Contributor | Manage resources |
| Reader | View-only |
| User Access Administrator | Manage RBAC |

---

## Custom Roles
Used when built-in roles are too broad and fine-grained permissions are required.

---

## Principle of Least Privilege
Always assign the minimum permissions required at the lowest possible scope.

---

## Real-Time Example: Enterprise Web Application

### Scenario
An enterprise hosts a web application in Azure with DevOps, Developers, QA, and CI/CD pipelines.

### Groups
- DevOps-Team
- Developers-Team
- QA-Team

### RBAC Assignment
| Identity | Role | Scope |
|---|---|---|
| DevOps-Team | Contributor | Subscription |
| Developers-Team | Contributor | Resource Group |
| QA-Team | Reader | Resource Group |

---

## Service Principal for CI/CD
CI/CD pipelines use service principals instead of personal credentials.

---

## Managed Identity Example
Azure VM accesses Key Vault securely using managed identity.

---

## Hands-on (Optional)

### Assign RBAC Role
```bash
az role assignment create   --assignee devuser@company.com   --role Contributor   --resource-group ecommerce-dev-rg
```

### Create Service Principal
```bash
az ad sp create-for-rbac   --name cicd-sp   --role Contributor   --scopes /subscriptions/<subscription-id>
```

---

## Azure Services Used
- Microsoft Entra ID
- Azure RBAC
- Azure CLI
- Azure Resource Manager (ARM)

---

## Key Interview Takeaways
- Entra ID handles authentication
- RBAC handles authorization
- Use groups instead of individual users
- Prefer managed identity over service principals
- Follow least privilege principle
