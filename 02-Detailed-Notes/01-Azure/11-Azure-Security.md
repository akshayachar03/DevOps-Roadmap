# Azure Security

## Definition

- Azure Security is a collection of services and features that protect Azure resources, data, identities, and applications.
- It follows a **shared responsibility model**, where Microsoft secures the cloud infrastructure, and customers secure their workloads and data.

---

## Why is it used?

- Protect Azure resources.
- Prevent unauthorized access.
- Secure applications and data.
- Meet compliance requirements.
- Detect and respond to security threats.

---

## Key Features

- Identity and Access Management (IAM).
- Microsoft Defender for Cloud.
- Azure Key Vault.
- Azure Policy.
- Microsoft Sentinel.
- Disk Encryption.
- Network Security Groups (NSGs).
- Resource Locks.

---

## Advantages

- Multi-layer security.
- Centralized security management.
- Continuous threat monitoring.
- Compliance support.
- Integration with Azure services.

---

## Disadvantages

- Requires proper configuration.
- Advanced security features may require additional licensing.

---

## Components

- Microsoft Entra ID
- Microsoft Defender for Cloud
- Azure Key Vault
- Azure Policy
- Microsoft Sentinel
- Azure Firewall
- NSGs

---

## Real-world Example

A company stores encryption keys in Azure Key Vault, enables Microsoft Defender for Cloud for threat detection, and uses Azure Policy to enforce security standards.

---

## Interview Tip

"Azure Security combines identity, encryption, monitoring, governance, and threat protection to secure cloud resources."

---

## Quick Revision

- Shared responsibility model.
- Identity protection.
- Data encryption.
- Threat detection.
- Governance.
- Compliance.

---

## Important Interview Questions

1. What is Azure Security?
2. What services are included in Azure Security?
3. What is the Shared Responsibility Model?
4. How does Azure protect customer data?
5. Why is Azure Security important?

---

# Microsoft Defender for Cloud

## Definition

- Microsoft Defender for Cloud is a Cloud Security Posture Management (CSPM) and Cloud Workload Protection Platform (CWPP).
- It continuously assesses Azure resources for security risks and provides recommendations.

---

## Why is it used?

- Improve security posture.
- Detect threats.
- Monitor Azure resources.
- Provide security recommendations.
- Ensure compliance.

---

## Key Features

- Secure Score.
- Security recommendations.
- Vulnerability assessment.
- Threat detection.
- Regulatory compliance dashboard.
- Workload protection.

---

## Advantages

- Continuous monitoring.
- Centralized security dashboard.
- Easy security recommendations.
- Integration with Azure services.

---

## Disadvantages

- Advanced protection requires paid plans.
- Large environments may generate many recommendations.

---

## Workflow

```text
Azure Resources
        ↓
Defender for Cloud
        ↓
Security Assessment
        ↓
Recommendations
        ↓
Threat Alerts
```

---

## Real-world Example

Microsoft Defender detects that a VM has port 22 open to the internet and recommends enabling Just-In-Time VM Access.

---

## Interview Tip

"Defender for Cloud continuously monitors Azure resources and recommends security improvements."

---

## Quick Revision

- CSPM + CWPP.
- Secure Score.
- Threat detection.
- Security recommendations.
- Compliance monitoring.

---

## Important Interview Questions

1. What is Microsoft Defender for Cloud?
2. What is Secure Score?
3. What is CSPM?
4. What recommendations does Defender provide?
5. How does Defender improve security?

---

# Azure Key Vault

## Definition

- Azure Key Vault is a secure service for storing and managing sensitive information.
- It securely stores secrets, encryption keys, and digital certificates.

---

## Why is it used?

- Protect sensitive information.
- Centralize secret management.
- Secure application credentials.
- Manage encryption keys.
- Store SSL certificates.

---

## Key Features

- Secure secret storage.
- Hardware Security Module (HSM) support.
- RBAC integration.
- Managed identities.
- Automatic certificate renewal.
- Audit logging.

---

## Advantages

- Highly secure.
- Centralized management.
- Easy application integration.
- Supports key rotation.

---

## Disadvantages

- Requires proper access management.
- Incorrect permissions can expose secrets.

---

## Components

- Secrets
- Keys
- Certificates
- Access Policies / RBAC

---

## Workflow

```text
Application
      ↓
Authenticate
      ↓
Azure Key Vault
      ↓
Retrieve Secret/Key/Certificate
```

---

## Real-world Example

A web application retrieves its SQL database password from Azure Key Vault instead of storing it in the application code.

---

## Interview Tip

"Azure Key Vault securely stores secrets, encryption keys, and certificates instead of keeping them inside application code."

---

## Quick Revision

- Secure vault.
- Stores secrets.
- Stores keys.
- Stores certificates.
- Supports HSM.
- RBAC integration.

---

## Important Interview Questions

1. What is Azure Key Vault?
2. What does Azure Key Vault store?
3. Why should secrets not be stored in code?
4. What is HSM?
5. How does Azure Key Vault improve security?

---

# Azure Key Vault Secrets

## Definition

- Secrets are confidential values stored securely in Azure Key Vault.
- They include passwords, API keys, connection strings, and tokens.

---

## Why is it used?

- Protect passwords.
- Store API keys.
- Store connection strings.
- Secure application credentials.

---

## Key Features

- Encrypted storage.
- Versioning.
- Access control.
- Easy retrieval through APIs.
- Audit logging.

---

## Real-world Example

A web application stores its database password in Key Vault instead of inside configuration files.

---

## Interview Tip

"Secrets store sensitive text values like passwords and API keys."

---

## Quick Revision

- Passwords.
- API Keys.
- Tokens.
- Connection Strings.
- Versioning.

---

## Important Interview Questions

1. What is a Secret?
2. What types of data are stored as Secrets?
3. Why use Key Vault Secrets?
4. Can Secrets be versioned?
5. How are Secrets accessed securely?

---

# Azure Key Vault Keys

## Definition

- Keys are cryptographic keys used for encryption, decryption, signing, and verification.

---

## Why is it used?

- Encrypt data.
- Decrypt data.
- Digital signatures.
- Secure applications.

---

## Key Features

- RSA and EC keys.
- HSM protection.
- Key rotation.
- Key versioning.

---

## Real-world Example

A financial application encrypts customer data using an RSA key stored in Azure Key Vault.

---

## Interview Tip

"Keys are used for cryptographic operations rather than storing passwords."

---

## Quick Revision

- Encryption.
- Decryption.
- Signing.
- Verification.
- HSM support.

---

## Important Interview Questions

1. What is the difference between Secrets and Keys?
2. What operations use Keys?
3. What algorithms are supported?
4. Why use HSM?
5. Can Keys be rotated?

---

# Azure Key Vault Certificates

## Definition

- Certificates are digital certificates stored and managed in Azure Key Vault.
- They are commonly used for SSL/TLS encryption.

---

## Why is it used?

- Secure websites.
- SSL/TLS encryption.
- Certificate management.
- Automatic renewal.

---

## Key Features

- Certificate lifecycle management.
- Auto renewal.
- Integration with App Service.
- Secure storage.

---

## Real-world Example

An Azure App Service automatically retrieves its SSL certificate from Azure Key Vault.

---

## Interview Tip

"Certificates provide identity verification and encrypted communication."

---

## Quick Revision

- SSL/TLS.
- Secure websites.
- Auto renewal.
- Certificate lifecycle.

---

## Important Interview Questions

1. What are Certificates?
2. Why store certificates in Key Vault?
3. What is SSL?
4. Can certificates be renewed automatically?
5. Where are certificates commonly used?

---

# Azure Disk Encryption

## Definition

- Azure Disk Encryption encrypts Virtual Machine operating system and data disks.
- It protects stored data from unauthorized access.

---

## Why is it used?

- Protect VM disks.
- Meet compliance requirements.
- Secure sensitive data.
- Prevent offline data theft.

---

## Key Features

- Encrypts OS disks.
- Encrypts Data disks.
- Uses Azure Key Vault.
- Supports Windows and Linux.

---

## Advantages

- Strong security.
- Compliance support.
- Transparent to applications.

---

## Disadvantages

- Slight performance overhead.
- Requires Key Vault.

---

## Workflow

```text
Virtual Machine
      ↓
Azure Disk Encryption
      ↓
Encryption Key from Key Vault
      ↓
Encrypted Disk
```

---

## Real-world Example

A healthcare company encrypts all VM disks to protect patient information.

---

## Interview Tip

"Azure Disk Encryption protects VM disks using encryption keys stored in Azure Key Vault."

---

## Quick Revision

- Encrypts VM disks.
- Uses Key Vault.
- Supports Windows and Linux.
- Protects data at rest.

---

## Important Interview Questions

1. What is Azure Disk Encryption?
2. Which disks are encrypted?
3. Why is Key Vault required?
4. Does Disk Encryption affect applications?
5. When should Disk Encryption be enabled?

---

# Encryption at Rest

## Definition

- Encryption at Rest protects stored data using encryption while it is saved on disks or storage services.

---

## Why is it used?

- Protect stored data.
- Meet compliance.
- Prevent data theft.
- Secure backups.

---

## Key Features

- Automatic encryption.
- Uses AES-256 encryption.
- Microsoft-managed or customer-managed keys.

---

## Real-world Example

Azure Storage automatically encrypts uploaded files before storing them.

---

## Interview Tip

"Encryption at Rest protects stored data when it is not being accessed."

---

## Quick Revision

- Data stored on disk.
- AES-256.
- Automatic.
- Storage encryption.
- Managed keys.

---

## Important Interview Questions

1. What is Encryption at Rest?
2. Which Azure services use it?
3. What encryption algorithm is used?
4. What is a customer-managed key?
5. Why is Encryption at Rest important?

---

# Encryption in Transit

## Definition

- Encryption in Transit protects data while it moves between users, applications, and Azure services.

---

## Why is it used?

- Prevent network attacks.
- Secure communication.
- Protect sensitive information.

---

## Key Features

- HTTPS.
- TLS.
- VPN.
- ExpressRoute encryption.

---

## Real-world Example

Users access an Azure App Service using HTTPS, ensuring encrypted communication.

---

## Interview Tip

"Encryption in Transit protects data while it travels across networks."

---

## Quick Revision

- HTTPS.
- TLS.
- VPN.
- Secure communication.

---

## Important Interview Questions

1. What is Encryption in Transit?
2. Which protocol is commonly used?
3. Why is HTTPS important?
4. How is data protected during transmission?
5. Difference between At Rest and In Transit?

---

# Azure Policy

## Definition

- Azure Policy helps enforce organizational standards and compliance across Azure resources.
- It evaluates resources and ensures they follow defined rules.

---

## Why is it used?

- Enforce governance.
- Improve compliance.
- Standardize deployments.
- Prevent misconfigurations.

---

## Key Features

- Policy definitions.
- Policy assignments.
- Compliance reports.
- Built-in and custom policies.

---

## Real-world Example

A company creates a policy allowing Virtual Machines only in approved Azure regions.

---

## Interview Tip

"Azure Policy enforces organizational rules and prevents non-compliant resource deployments."

---

## Quick Revision

- Governance.
- Compliance.
- Built-in policies.
- Custom policies.
- Automatic evaluation.

---

## Important Interview Questions

1. What is Azure Policy?
2. What is the difference between RBAC and Policy?
3. Can Azure Policy block deployments?
4. What are Policy Definitions?
5. Why is Azure Policy important?

---

# Azure Blueprints (Basics)

## Definition

- Azure Blueprints allow organizations to deploy a repeatable environment that includes policies, RBAC assignments, ARM templates, and Resource Groups.
- **Note:** Azure Blueprints is being replaced by **Template Specs and Deployment Stacks** for many scenarios, but basic interview knowledge is still useful.

---

## Why is it used?

- Standardize environments.
- Accelerate deployments.
- Ensure governance.
- Simplify compliance.

---

## Key Features

- Policy assignments.
- RBAC assignments.
- ARM Templates.
- Resource Groups.

---

## Real-world Example

A financial organization creates a blueprint that automatically deploys secure development environments following company standards.

---

## Interview Tip

"Azure Blueprints package governance artifacts such as policies and RBAC assignments into reusable templates."

---

## Quick Revision

- Repeatable environments.
- Includes Policies.
- Includes RBAC.
- Includes ARM Templates.
- Governance tool.

---

## Important Interview Questions

1. What is Azure Blueprint?
2. What does a Blueprint contain?
3. How is Blueprint different from ARM Templates?
4. Why are Blueprints used?
5. Is Azure Blueprint still recommended for new deployments?

---

# Azure Resource Locks

## Definition

- Resource Locks prevent accidental deletion or modification of Azure resources.

---

## Why is it used?

- Protect production resources.
- Prevent accidental deletion.
- Improve governance.

---

## Types

| Lock Type | Description |
|-----------|-------------|
| CanNotDelete | Prevents deletion but allows modification |
| ReadOnly | Prevents modification and deletion |

---

## Real-world Example

A production SQL Database is protected using a **CanNotDelete** lock.

---

## Interview Tip

"Resource Locks provide an extra layer of protection against accidental changes."

---

## Quick Revision

- CanNotDelete.
- ReadOnly.
- Protect production resources.
- Applies to subscriptions, resource groups, or resources.

---

## Important Interview Questions

1. What are Resource Locks?
2. What is the difference between CanNotDelete and ReadOnly?
3. Where can Resource Locks be applied?
4. Why use Resource Locks?
5. Can an Owner remove a Resource Lock?

---

# Just-In-Time (JIT) VM Access

## Definition

- Just-In-Time (JIT) VM Access reduces exposure of management ports by opening them only for a limited time when required.
- It is a feature of Microsoft Defender for Cloud.

---

## Why is it used?

- Reduce attack surface.
- Protect RDP and SSH ports.
- Prevent brute-force attacks.
- Improve VM security.

---

## Key Features

- Temporary access.
- Time-limited permissions.
- Automatic NSG updates.
- Defender for Cloud integration.

---

## Workflow

```text
Request VM Access
        ↓
Approval
        ↓
Port Opens Temporarily
        ↓
Time Expires
        ↓
Port Closes Automatically
```

---

## Real-world Example

An administrator requests SSH access to a Linux VM for one hour. After one hour, port 22 is automatically closed.

---

## Interview Tip

"JIT VM Access minimizes exposure by opening management ports only when needed."

---

## Quick Revision

- Temporary RDP/SSH access.
- Reduces attack surface.
- Defender for Cloud feature.
- Automatic port closure.

---

## Important Interview Questions

1. What is JIT VM Access?
2. Why is JIT used?
3. Which ports are commonly protected?
4. Which Azure service provides JIT?
5. How does JIT improve security?

---

# Microsoft Sentinel (Basics)

## Definition

- Microsoft Sentinel is Microsoft's cloud-native Security Information and Event Management (SIEM) and Security Orchestration, Automation, and Response (SOAR) solution.
- It collects, analyzes, detects, investigates, and responds to security events across cloud and on-premises environments.

---

## Why is it used?

- Detect security threats.
- Collect security logs.
- Investigate incidents.
- Automate responses.
- Improve security monitoring.

---

## Key Features

- SIEM.
- SOAR.
- Threat intelligence.
- Incident management.
- Automated playbooks.
- AI-powered analytics.

---

## Advantages

- Centralized monitoring.
- Cloud-native.
- Automated response.
- Scalable.

---

## Disadvantages

- Requires log ingestion planning.
- Costs depend on data volume.

---

## Workflow

```text
Logs Collected
      ↓
Analytics Rules
      ↓
Threat Detection
      ↓
Incident Created
      ↓
Automated Response
```

---

## Real-world Example

Microsoft Sentinel detects multiple failed login attempts from different countries and automatically creates a security incident for investigation.

---

## Interview Tip

"Microsoft Sentinel is Azure's cloud-native SIEM and SOAR solution used for security monitoring, threat detection, and incident response."

---

## Quick Revision

- SIEM + SOAR.
- Collects logs.
- Detects threats.
- Creates incidents.
- Supports automated response.
- Integrates with Microsoft Defender.

---

## Important Interview Questions

1. What is Microsoft Sentinel?
2. What is the difference between SIEM and SOAR?
3. How does Sentinel detect threats?
4. What are Playbooks in Sentinel?
5. How does Sentinel integrate with Microsoft Defender?
