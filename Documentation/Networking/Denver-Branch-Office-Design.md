# Denver Branch Office Azure Design

## Business Scenario

Contoso Manufacturing is opening a new office in Denver with an initial workforce of approximately 50 employees.

The Azure environment must support:

- Secure employee access
- Identity management
- Departmental separation
- Future growth to approximately 200 employees
- Secure administrative access
- Monitoring and governance

---

# Business Requirements

The environment must provide:

- Secure authentication
- Role-based authorization
- Secure administrator access
- Segmented networking
- Centralized monitoring
- Cost management
- Scalability

---

# Proposed Azure Architecture

## Resource Groups

The environment will be organized into dedicated Resource Groups.

| Resource Group | Purpose |
|---------------|---------|
| rg-denver-network | Networking resources |
| rg-denver-compute | Virtual Machines |
| rg-denver-storage | Storage Accounts |
| rg-denver-monitoring | Azure Monitor and Log Analytics |

This organization improves lifecycle management, RBAC assignment, and operational management.

---

## Virtual Network

Create one production Virtual Network.

Example:

```
vnet-denver-prod
10.20.0.0/16
```

The address space allows future expansion while supporting subnet segmentation.

---

## Subnet Design

| Subnet | Purpose |
|---------|----------|
| Management | Administrative resources |
| Servers | Windows and Linux Servers |
| Clients | Client workloads |
| PrivateEndpoints | Private Azure service access |
| AzureBastionSubnet | Secure administrative access |

Each subnet has a dedicated purpose to reduce risk and improve management.

---

## Identity Design

Authentication will be provided through Microsoft Entra ID.

Administrative permissions will be assigned to security groups instead of individual users.

Example groups:

- Denver-Cloud-Admins
- Denver-HelpDesk
- Denver-Finance
- Denver-Auditors

This follows the Principle of Least Privilege.

---

## Security Design

The environment will use:

- Network Security Groups
- Azure Bastion
- Microsoft Entra ID
- Role-Based Access Control (RBAC)
- Resource Tags
- Resource Locks

Administrative RDP access will not be exposed directly to the Internet.

---

## Monitoring

Azure Monitor

Log Analytics Workspace

Activity Logs

Alerts

These services provide operational visibility into the environment.

---

## Governance

Resource Tags

Resource Locks

RBAC

Azure Policy (future implementation)

Governance improves consistency across Azure resources.

---

# Validation

The design will be considered successful when:

- Users authenticate successfully.
- Finance users only access Finance resources.
- Administrators connect through Azure Bastion.
- Azure Monitor collects diagnostic data.
- Resources are tagged according to organizational standards.

---

# Lessons Learned

Good Azure environments are designed before they are deployed.

Identity, networking, governance, monitoring, and security should be planned together rather than added later.

Resource Groups organize resources.

RBAC controls authorization.

Network Security Groups control network traffic.

Azure Bastion reduces the attack surface by eliminating public RDP access.

---

# Future Improvements

Implement:

- Azure Firewall
- Azure Policy
- Microsoft Defender for Cloud
- Backup Strategy
- Site Recovery
- Private DNS Zones
- Hub-and-Spoke Networking

---

# Interview Talking Points

This project demonstrates the ability to:

- Design Azure infrastructure based on business requirements.
- Apply network segmentation.
- Implement least-privilege access.
- Organize Azure resources for governance.
- Plan for scalability and future growth.
- Secure administrative access using Azure Bastion.
