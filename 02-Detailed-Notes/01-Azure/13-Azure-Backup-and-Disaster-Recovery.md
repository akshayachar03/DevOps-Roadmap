# Backup & Disaster Recovery (BDR)

## Definition

- Backup and Disaster Recovery (BDR) are strategies used to protect data and ensure business operations continue during failures or disasters.
- **Backup** helps recover lost or deleted data, while **Disaster Recovery (DR)** restores entire applications or infrastructure after a major outage.
- Azure provides services like Azure Backup and Azure Site Recovery (ASR) for BDR.

---

## Why is it used?

- Protect critical business data.
- Recover from accidental deletion.
- Recover from ransomware attacks.
- Minimize downtime.
- Ensure business continuity.
- Meet compliance requirements.

---

## Key Features

- Automated backups.
- Secure recovery.
- Geo-redundant storage.
- Disaster recovery replication.
- Centralized management.
- Long-term retention.

---

## Advantages

- Protects business-critical data.
- Reduces downtime.
- Supports compliance.
- Fully managed service.
- Easy restoration process.

---

## Disadvantages

- Backup storage incurs additional cost.
- Recovery time depends on backup size and configuration.

---

## Components

- Recovery Services Vault
- Azure Backup
- Backup Policies
- Restore Points
- Azure Site Recovery
- Geo-Replication

---

## Workflow

```text
Azure Resources
        ↓
Azure Backup
        ↓
Recovery Services Vault
        ↓
Backup Storage
        ↓
Restore When Needed
```

---

## Real-world Example

A company backs up its Azure Virtual Machines daily. If a VM is accidentally deleted, it is restored from the Recovery Services Vault.

---

## Interview Tip

"Backup protects data, while Disaster Recovery restores business operations after a major outage."

---

## Quick Revision

- Backup protects data.
- DR restores applications and infrastructure.
- Azure Backup handles backups.
- ASR handles disaster recovery.
- Recovery Services Vault stores backups.
- Supports business continuity.

---

## Important Interview Questions

1. What is Backup and Disaster Recovery?
2. What is the difference between Backup and Disaster Recovery?
3. Which Azure services support BDR?
4. Why is Disaster Recovery important?
5. What is Business Continuity?

---

# Recovery Services Vault

## Definition

- Recovery Services Vault is an Azure resource that stores and manages backup data and disaster recovery configurations.
- It acts as the central management point for Azure Backup and Azure Site Recovery.

---

## Why is it used?

- Store backup data securely.
- Manage VM backups.
- Configure Azure Site Recovery.
- Centralize recovery management.
- Apply backup policies.

---

## Key Features

- Secure backup storage.
- Backup monitoring.
- Backup policies.
- Soft Delete protection.
- Encryption.
- Integration with Azure Backup and ASR.

---

## Advantages

- Centralized backup management.
- Secure storage.
- Easy recovery.
- Built-in monitoring.

---

## Disadvantages

- Backup storage costs apply.
- Requires proper backup planning.

---

## Components

### Backup Items

- Resources being protected.

### Backup Policies

- Schedule and retention settings.

### Recovery Points

- Available restore versions.

### Site Recovery

- Disaster recovery configuration.

---

## Workflow

```text
Virtual Machine
      ↓
Recovery Services Vault
      ↓
Backup Stored
      ↓
Restore if Needed
```

---

## Real-world Example

An organization stores daily backups of its production Virtual Machines in a Recovery Services Vault.

---

## Interview Tip

"Recovery Services Vault is the central repository for Azure Backup and Azure Site Recovery."

---

## Quick Revision

- Central backup repository.
- Stores backups.
- Stores recovery points.
- Supports ASR.
- Secure and encrypted.

---

## Important Interview Questions

1. What is Recovery Services Vault?
2. Why is it required for Azure Backup?
3. What services use Recovery Services Vault?
4. Can one vault protect multiple resources?
5. What is stored inside the vault?

---

# Azure Backup

## Definition

- Azure Backup is a fully managed backup service that protects Azure and on-premises workloads.
- It automatically creates backups and allows easy restoration when data is lost.

---

## Why is it used?

- Protect Virtual Machines.
- Protect databases.
- Backup Azure Files.
- Recover deleted data.
- Meet compliance requirements.

---

## Key Features

- Automatic backups.
- Incremental backups.
- Long-term retention.
- Encryption.
- Soft Delete.
- Policy-based backups.

---

## Advantages

- Fully managed.
- Easy restoration.
- Secure backups.
- Supports Azure and on-premises resources.
- Scalable.

---

## Disadvantages

- Backup storage costs.
- Large restores take longer.

---

## Supported Workloads

- Azure Virtual Machines
- Azure Files
- SQL Server
- SAP HANA
- On-premises Servers

---

## Workflow

```text
Configure Backup
        ↓
Azure Backup
        ↓
Recovery Services Vault
        ↓
Scheduled Backup
```

---

## Real-world Example

A company backs up its SQL Server every night using Azure Backup.

---

## Interview Tip

"Azure Backup is a managed backup service that protects Azure and on-premises workloads."

---

## Quick Revision

- Managed backup service.
- Incremental backups.
- Policy-based.
- Encryption.
- Recovery Services Vault.

---

## Important Interview Questions

1. What is Azure Backup?
2. Which workloads are supported?
3. What are incremental backups?
4. Where are Azure backups stored?
5. Why use Azure Backup?

---

# Backup Policies

## Definition

- Backup Policies define when backups are taken and how long they are retained.
- Policies ensure backups occur automatically according to business requirements.

---

## Why is it used?

- Automate backups.
- Define retention periods.
- Standardize backup schedules.
- Meet compliance.

---

## Key Features

- Daily, weekly, monthly backups.
- Retention rules.
- Automatic execution.
- Policy reuse.

---

## Advantages

- Automation.
- Consistency.
- Reduced manual work.
- Compliance support.

---

## Disadvantages

- Incorrect policies may waste storage.
- Requires planning.

---

## Workflow

```text
Create Policy
      ↓
Assign to Resource
      ↓
Automatic Backup
```

---

## Real-world Example

A company creates a policy to back up all production VMs every night and retain backups for 90 days.

---

## Interview Tip

"Backup Policies automate backup scheduling and retention."

---

## Quick Revision

- Backup schedule.
- Retention period.
- Automation.
- Policy-based.

---

## Important Interview Questions

1. What is a Backup Policy?
2. Why are Backup Policies important?
3. What does retention mean?
4. Can multiple resources share one policy?
5. How are Backup Policies applied?

---

# Restore Points

## Definition

- Restore Points are snapshots of data captured during backups.
- They allow recovery of data to a specific point in time.

---

## Why is it used?

- Recover deleted files.
- Recover Virtual Machines.
- Restore databases.
- Roll back after failures.

---

## Key Features

- Multiple recovery versions.
- Point-in-time recovery.
- Secure storage.
- Fast recovery.

---

## Advantages

- Flexible recovery.
- Data protection.
- Supports business continuity.

---

## Disadvantages

- Older restore points consume storage.
- Availability depends on retention policy.

---

## Workflow

```text
Backup
     ↓
Restore Point Created
     ↓
Failure Occurs
     ↓
Restore Selected Version
```

---

## Real-world Example

An administrator restores yesterday's VM backup after a software update causes system failure.

---

## Interview Tip

"A Restore Point allows recovery of data from a specific backup time."

---

## Quick Revision

- Point-in-time recovery.
- Multiple restore versions.
- Depends on Backup Policy.
- Used during recovery.

---

## Important Interview Questions

1. What is a Restore Point?
2. Why are Restore Points important?
3. How are Restore Points created?
4. Can multiple Restore Points exist?
5. How is a Restore Point used?

---

# Azure Site Recovery (ASR)

## Definition

- Azure Site Recovery (ASR) is a Disaster Recovery service that replicates workloads to another Azure region or site.
- It enables automatic failover and failback during disasters.

---

## Why is it used?

- Disaster recovery.
- Reduce downtime.
- Protect critical applications.
- Replicate Virtual Machines.
- Improve availability.

---

## Key Features

- Continuous replication.
- Automatic failover.
- Planned failover.
- Test failover.
- Failback support.

---

## Advantages

- Minimal downtime.
- Business continuity.
- Automated disaster recovery.
- Supports Azure and on-premises workloads.

---

## Disadvantages

- Replication storage costs.
- Requires DR planning.

---

## Workflow

```text
Primary Site
      ↓
Continuous Replication
      ↓
Secondary Azure Region
      ↓
Failover
      ↓
Business Continues
```

---

## Real-world Example

If an entire Azure region becomes unavailable, ASR automatically starts replicated Virtual Machines in another Azure region.

---

## Interview Tip

"Azure Site Recovery replicates workloads to another location and enables automatic failover during disasters."

---

## Quick Revision

- Disaster Recovery.
- Replication.
- Failover.
- Failback.
- Test Failover.

---

## Important Interview Questions

1. What is Azure Site Recovery?
2. What is Failover?
3. What is Failback?
4. What is Test Failover?
5. How does ASR improve availability?

---

# Disaster Recovery (DR)

## Definition

- Disaster Recovery is the process of restoring applications, infrastructure, and services after a major failure.
- It focuses on minimizing downtime and data loss.

---

## Why is it used?

- Continue business operations.
- Recover after disasters.
- Reduce downtime.
- Protect customer services.

---

## Key Features

- Failover.
- Replication.
- Recovery planning.
- Secondary site.

---

## Advantages

- High availability.
- Business continuity.
- Reduced downtime.

---

## Disadvantages

- Additional infrastructure costs.
- Requires regular testing.

---

## Workflow

```text
Primary Site Failure
        ↓
Failover
        ↓
Secondary Site
        ↓
Business Continues
```

---

## Real-world Example

An online banking application automatically switches to another Azure region after a regional outage.

---

## Interview Tip

"Disaster Recovery restores applications and infrastructure after a major outage."

---

## Quick Revision

- Failover.
- Secondary site.
- Replication.
- High availability.
- Business continuity.

---

## Important Interview Questions

1. What is Disaster Recovery?
2. How is DR different from Backup?
3. What is Failover?
4. Why is DR important?
5. What Azure service provides DR?

---

# Geo-Replication

## Definition

- Geo-Replication copies data from one Azure region to another geographically separate region.
- It protects against regional failures.

---

## Why is it used?

- Improve durability.
- Protect against regional disasters.
- Increase availability.
- Support Disaster Recovery.

---

## Key Features

- Automatic replication.
- Multiple Azure regions.
- High durability.
- Supports Azure Storage redundancy options.

---

## Advantages

- Regional protection.
- High availability.
- Better disaster recovery.

---

## Disadvantages

- Additional storage costs.
- Replication delay may occur.

---

## Workflow

```text
Primary Region
      ↓
Geo Replication
      ↓
Secondary Region
```

---

## Real-world Example

Azure Storage replicates business documents from East US to West US using Geo-Redundant Storage (GRS).

---

## Interview Tip

"Geo-Replication protects data by copying it to another Azure region."

---

## Quick Revision

- Multiple regions.
- Disaster protection.
- High durability.
- Automatic replication.

---

## Important Interview Questions

1. What is Geo-Replication?
2. Why is Geo-Replication important?
3. What Azure service uses Geo-Replication?
4. Does Geo-Replication improve availability?
5. What is GRS?

---

# Business Continuity

## Definition

- Business Continuity is the ability of an organization to continue operating during and after unexpected disruptions.
- It combines Backup, Disaster Recovery, high availability, and operational planning.

---

## Why is it used?

- Reduce downtime.
- Protect business operations.
- Meet compliance.
- Improve customer trust.
- Ensure service availability.

---

## Key Features

- Backup.
- Disaster Recovery.
- High Availability.
- Recovery planning.
- Risk management.

---

## Advantages

- Continuous operations.
- Better customer satisfaction.
- Reduced financial loss.
- Improved resilience.

---

## Disadvantages

- Requires planning.
- Additional infrastructure costs.
- Regular testing is necessary.

---

## Components

### Backup

- Protects data.

### Disaster Recovery

- Restores infrastructure.

### High Availability

- Minimizes downtime.

### Monitoring

- Detects failures.

---

## Workflow

```text
Normal Operations
        ↓
Unexpected Failure
        ↓
Backup + DR Activated
        ↓
Business Continues
```

---

## Real-world Example

A global e-commerce company uses Azure Backup, Azure Site Recovery, Load Balancers, and Geo-Replication to ensure customers can continue shopping even if one Azure region becomes unavailable.

---

## Interview Tip

"Business Continuity combines backup, disaster recovery, and high availability to keep business services running during disruptions."

---

## Quick Revision

- Backup protects data.
- DR restores infrastructure.
- High Availability minimizes downtime.
- Geo-Replication protects against regional failures.
- Business Continuity combines all recovery strategies.

---

## Important Interview Questions

1. What is Business Continuity?
2. How is Business Continuity different from Disaster Recovery?
3. Why is Business Continuity important?
4. Which Azure services support Business Continuity?
5. What is the relationship between Backup, High Availability, and Disaster Recovery?
