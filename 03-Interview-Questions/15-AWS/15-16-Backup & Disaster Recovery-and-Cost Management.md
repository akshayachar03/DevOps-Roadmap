# AWS Backup & Disaster Recovery & Cost Management Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What is AWS Backup, and why is it used?

**Answer**

AWS Backup is a fully managed service that centralizes and automates data backup across AWS services.

It supports backup for services such as:
- Amazon EC2 (EBS volumes)
- Amazon RDS
- Amazon EFS
- Amazon DynamoDB
- Amazon FSx
- AWS Storage Gateway

**Explanation**

Instead of configuring backups separately for each service, AWS Backup allows administrators to create centralized backup plans, schedules, retention policies, and recovery points.

**Where it is used in Production**

- Enterprise backup management
- Compliance requirements
- Disaster recovery planning
- Automated backup scheduling

**Common Mistake**

Many candidates think AWS Backup replaces snapshots. AWS Backup actually manages and automates snapshot creation for supported services.

---

### Question 2

**Question**

What is an EBS Snapshot?

**Answer**

An EBS Snapshot is a point-in-time backup of an Amazon EBS volume stored in Amazon S3.

Snapshots are:
- Incremental
- Durable
- Used for backup and recovery
- Used to create new EBS volumes

**Explanation**

Only changed blocks are saved after the first snapshot, making subsequent snapshots storage-efficient.

**Where it is used in Production**

- Backup before deployments
- Disaster recovery
- Volume restoration
- Data migration

**Common Mistake**

Thinking every snapshot is a full backup. After the initial snapshot, AWS stores only incremental changes.

---

### Question 3

**Question**

What is an Amazon Machine Image (AMI)?

**Answer**

An AMI is a template used to launch EC2 instances.

It contains:
- Operating system
- Installed software
- Application configuration
- Block device mappings

**Explanation**

AMIs allow engineers to launch identical EC2 instances quickly and consistently.

**Where it is used in Production**

- Golden images
- Auto Scaling Groups
- Disaster recovery
- Environment replication

**Common Mistake**

Confusing AMIs with snapshots. An AMI includes instance configuration, while a snapshot only backs up storage volumes.

---

### Question 4

**Question**

What is Cross-Region Backup?

**Answer**

Cross-Region Backup stores backup copies in another AWS Region to protect against regional outages.

**Explanation**

If an entire AWS Region becomes unavailable, backups stored in another Region can be used for recovery.

**Where it is used in Production**

- Disaster recovery
- Business continuity
- Regulatory compliance

---

### Question 5

**Question**

What are the AWS pricing models?

**Answer**

The major AWS pricing models are:

- On-Demand
- Reserved Instances
- Savings Plans
- Spot Instances
- Dedicated Hosts

**Explanation**

Each pricing model is designed for different workload requirements and cost optimization strategies.

**Where it is used in Production**

Organizations combine multiple pricing models to balance cost and flexibility.

**Common Mistake**

Using only On-Demand instances for long-running production workloads, resulting in unnecessary costs.

---

### Question 6

**Question**

What is the AWS Free Tier?

**Answer**

AWS Free Tier provides limited free usage of AWS services for learning and evaluation.

Examples include:
- EC2
- S3
- Lambda
- RDS
- CloudWatch

**Explanation**

It enables new users to explore AWS services without immediate charges, subject to usage limits.

**Where it is used in Production**

Primarily for learning, testing, and proof-of-concept environments.

---

### Question 7

**Question**

What is AWS Cost Explorer?

**Answer**

AWS Cost Explorer is a service that visualizes AWS spending and usage trends.

It provides:
- Cost analysis
- Usage reports
- Forecasting
- Service-wise spending
- Tag-based cost analysis

**Explanation**

It helps organizations identify spending patterns and opportunities for cost optimization.

**Where it is used in Production**

- Monthly cost reviews
- Budget planning
- Cost optimization

---

### Question 8

**Question**

What is AWS Budgets?

**Answer**

AWS Budgets allows organizations to create cost and usage budgets and receive alerts when thresholds are exceeded.

**Explanation**

Budgets help prevent unexpected AWS charges by notifying teams before spending exceeds planned limits.

**Where it is used in Production**

- Department budgets
- Project cost tracking
- Cloud governance

**Common Mistake**

Confusing AWS Budgets with Cost Explorer. Budgets generate alerts, while Cost Explorer analyzes spending.

---

### Question 9

**Question**

What is the difference between an EBS Snapshot and an AMI?

**Answer**

| EBS Snapshot | AMI |
|--------------|-----|
| Backs up a volume | Creates an EC2 template |
| Stores storage data | Stores OS, software, and configuration |
| Used for restoring disks | Used for launching instances |

**Explanation**

Snapshots protect storage, while AMIs simplify server deployment.

**Where it is used in Production**

Both are commonly used together for backup and disaster recovery.

---

### Question 10

**Question**

Why are backups important in AWS?

**Answer**

Backups protect against:

- Accidental deletion
- Hardware failures
- Application corruption
- Ransomware
- Regional outages

**Explanation**

A proper backup strategy ensures data can be restored quickly after failures.

**Where it is used in Production**

Business continuity and disaster recovery planning.

---

### Question 11

**Question**

How can AWS costs be optimized?

**Answer**

Common cost optimization techniques include:

- Right-sizing EC2 instances
- Using Reserved Instances or Savings Plans
- Using Spot Instances for fault-tolerant workloads
- Deleting unused resources
- Lifecycle policies for S3
- Monitoring costs with Cost Explorer
- Setting budgets and alerts

**Explanation**

Continuous monitoring and optimization help reduce unnecessary cloud expenses.

**Where it is used in Production**

Enterprise FinOps and cloud governance.

---

### Question 12

**Question**

What is the difference between AWS Cost Explorer and AWS Budgets?

**Answer**

| Cost Explorer | AWS Budgets |
|---------------|-------------|
| Analyzes spending | Monitors budget thresholds |
| Forecasts costs | Sends alerts |
| Creates reports | Tracks budget compliance |

**Explanation**

Cost Explorer explains where money is being spent, while AWS Budgets helps control future spending.

**Where it is used in Production**

Most organizations use both services together.

---

## Scenario-Based Interview Questions

### Scenario 1

**Question**

An EC2 instance becomes corrupted after an operating system update. How would you recover it?

**Answer**

Restore the EBS volume from the latest snapshot or launch a new EC2 instance using a previously created AMI.

**Explanation**

Snapshots restore data, while AMIs recreate complete server environments quickly.

---

### Scenario 2

**Question**

Your company requires disaster recovery in another AWS Region. What solution would you recommend?

**Answer**

Implement Cross-Region Backup using AWS Backup or copy EBS snapshots and AMIs to another AWS Region.

**Explanation**

Regional backup copies protect against complete regional outages.

---

### Scenario 3

**Question**

Your monthly AWS bill suddenly doubles. How would you investigate?

**Answer**

Review:

- AWS Cost Explorer
- Service-wise costs
- Resource usage
- Recently launched resources
- Unused infrastructure

**Explanation**

Cost Explorer identifies which services contributed to the increased spending.

---

### Scenario 4

**Question**

Management wants an alert whenever monthly cloud spending exceeds ₹50,000. Which AWS service would you use?

**Answer**

AWS Budgets.

**Explanation**

AWS Budgets sends notifications when actual or forecasted costs exceed predefined thresholds.

---

### Scenario 5

**Question**

A developer accidentally deletes an important EBS volume. How can you recover the data?

**Answer**

Restore the volume from the latest EBS Snapshot and attach it to an EC2 instance.

**Explanation**

Snapshots provide point-in-time recovery for EBS volumes.

---

### Scenario 6

**Question**

Your organization needs identical production servers across multiple Availability Zones. What AWS feature would you use?

**Answer**

Create an Amazon Machine Image (AMI) and launch multiple EC2 instances from it.

**Explanation**

AMIs ensure consistent server configuration across deployments.

---

### Scenario 7

**Question**

A finance team wants to know which AWS service generated the highest cost last month. Which tool would you use?

**Answer**

AWS Cost Explorer.

**Explanation**

Cost Explorer provides detailed spending analysis by service, account, region, and tags.

---

### Scenario 8

**Question**

A DevOps engineer creates manual snapshots but often forgets to perform backups. How would you improve this process?

**Answer**

Implement automated backup plans using AWS Backup.

**Explanation**

Automated backup schedules reduce human error and improve compliance.

---

### Scenario 9

**Question**

Your company wants to reduce EC2 costs for workloads that run continuously throughout the year. Which pricing model would you recommend?

**Answer**

Reserved Instances or Savings Plans.

**Explanation**

These pricing models provide significant discounts compared to On-Demand pricing for predictable workloads.

---

### Scenario 10

**Question**

Your production database must be recoverable after accidental deletion or a regional disaster. What backup strategy would you recommend?

**Answer**

Use automated AWS Backup with scheduled backups, cross-region backup copies, defined retention policies, and regular recovery testing.

**Explanation**

A comprehensive backup strategy ensures both local recovery and disaster recovery while meeting business continuity requirements.
