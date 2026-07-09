# Terraform Azure Infrastructure Provisioning and Terraform in CI/CD Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What resources are typically created first when provisioning Azure infrastructure using Terraform?

**Answer**

The Resource Group is usually created first, followed by networking resources (Virtual Network, Subnet, Network Security Group), Storage Account (if required), and finally Virtual Machines.

Typical deployment order:

```
Resource Group
      ↓
Virtual Network
      ↓
Subnet
      ↓
Network Security Group
      ↓
Storage Account (Optional)
      ↓
Virtual Machine
```

**Explanation**

Most Azure resources require a Resource Group. A Virtual Machine also depends on networking resources such as a Virtual Network and Subnet. Terraform automatically determines this order based on resource references.

**Used in Production**

- Azure infrastructure deployments
- Landing zones
- Enterprise environment provisioning

**Common Mistake**

Creating resources in the wrong order or manually managing dependencies instead of using Terraform references.

---

### Question 2

**Question**

Why is a Resource Group required in Azure Terraform deployments?

**Answer**

A Resource Group is a logical container that holds Azure resources such as Virtual Machines, Storage Accounts, Virtual Networks, and Network Security Groups.

Example:

```hcl
resource "azurerm_resource_group" "rg" {
  name     = "prod-rg"
  location = "East US"
}
```

**Explanation**

Almost every Azure resource must belong to a Resource Group. Deleting the Resource Group removes all contained resources.

**Used in Production**

- Environment separation
- Cost management
- Resource organization
- RBAC assignment

**Common Mistake**

Creating unrelated resources in the same Resource Group.

---

### Question 3

**Question**

How do you create a Virtual Network and Subnet using Terraform?

**Answer**

A Virtual Network is created first, followed by one or more Subnets.

Example:

```hcl
resource "azurerm_virtual_network" "vnet" {
  name                = "prod-vnet"
  address_space       = ["10.0.0.0/16"]
}

resource "azurerm_subnet" "subnet" {
  name                 = "web-subnet"
  virtual_network_name = azurerm_virtual_network.vnet.name
}
```

**Explanation**

The Subnet references the Virtual Network, so Terraform automatically creates the VNet before the Subnet.

**Used in Production**

Every Azure deployment requiring private networking.

---

### Question 4

**Question**

What is the purpose of a Network Security Group (NSG)?

**Answer**

A Network Security Group controls inbound and outbound network traffic using security rules.

Example rules:

- Allow SSH (22)
- Allow HTTP (80)
- Allow HTTPS (443)
- Deny unnecessary traffic

**Explanation**

NSGs function like firewalls for Azure resources and help secure Virtual Machines and Subnets.

**Used in Production**

- Restricting public access
- Securing application servers
- Database protection

**Common Mistake**

Allowing all inbound traffic (`0.0.0.0/0`) unnecessarily.

---

### Question 5

**Question**

How does Terraform create a Virtual Machine?

**Answer**

Terraform uses the `azurerm_linux_virtual_machine` or `azurerm_windows_virtual_machine` resource.

A VM typically requires:

- Resource Group
- Virtual Network
- Subnet
- Network Interface
- Operating System Image

**Explanation**

Terraform provisions the VM after all dependent networking resources are available.

**Used in Production**

Deploying Linux and Windows servers for applications, databases, and CI/CD tools.

---

### Question 6

**Question**

Why are Storage Accounts commonly created with Terraform?

**Answer**

Storage Accounts are used to store:

- Application data
- Files
- Backups
- Diagnostics
- Terraform Remote State

**Explanation**

Storage Accounts are foundational Azure services and are frequently provisioned alongside compute and networking resources.

**Used in Production**

- Blob Storage
- Remote Terraform State
- VM boot diagnostics

---

### Question 7

**Question**

How does Terraform determine the order of Azure resource creation?

**Answer**

Terraform analyzes resource references and builds a dependency graph.

Example:

```hcl
subnet_id = azurerm_subnet.web.id
```

Terraform understands that the Subnet must exist before the Virtual Machine.

**Explanation**

Explicit references eliminate the need to manually specify deployment order in most cases.

**Used in Production**

All Terraform deployments.

**Common Mistake**

Using hardcoded resource names instead of resource references.

---

### Question 8

**Question**

How is Terraform integrated into Azure DevOps Pipelines?

**Answer**

A typical Azure DevOps pipeline executes:

1. Terraform Init
2. Terraform Validate
3. Terraform Plan
4. Manual Approval (Optional)
5. Terraform Apply

**Explanation**

Azure DevOps automates infrastructure deployments while enabling approvals and version control.

**Used in Production**

- Infrastructure deployment
- Environment provisioning
- Infrastructure updates

---

### Question 9

**Question**

How is Terraform integrated into Jenkins Pipelines?

**Answer**

Jenkins executes Terraform commands within a Pipeline or Freestyle Job.

Typical stages:

```
Checkout

↓

Terraform Init

↓

Terraform Validate

↓

Terraform Plan

↓

Approval

↓

Terraform Apply
```

**Explanation**

Jenkins automates Terraform deployments and integrates with Git, Docker, and cloud providers.

**Used in Production**

CI/CD pipelines for Infrastructure as Code.

---

### Question 10

**Question**

What is the purpose of the Terraform Plan stage in CI/CD?

**Answer**

The Plan stage previews infrastructure changes without modifying resources.

Command:

```bash
terraform plan
```

**Explanation**

It identifies resources to be created, updated, or destroyed before execution.

**Used in Production**

Almost every enterprise CI/CD pipeline.

**Common Mistake**

Skipping the Plan stage and applying changes directly.

---

### Question 11

**Question**

What is the purpose of the Terraform Apply stage?

**Answer**

The Apply stage executes the changes generated by the Terraform Plan.

Command:

```bash
terraform apply
```

**Explanation**

Terraform compares the desired configuration with the current state and makes the required changes.

**Used in Production**

Automated infrastructure deployments after approval.

**Common Mistake**

Applying changes without reviewing the execution plan.

---

### Question 12

**Question**

Why is Terraform widely used in CI/CD pipelines?

**Answer**

Terraform enables automated, repeatable, and version-controlled infrastructure deployments.

Benefits include:

- Infrastructure as Code
- Consistency
- Reduced manual errors
- Faster deployments
- Easy rollback using version control

**Explanation**

Integrating Terraform into CI/CD ensures infrastructure changes follow the same review and deployment processes as application code.

**Used in Production**

Azure DevOps, Jenkins, GitHub Actions, GitLab CI/CD, and similar platforms.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

Your team needs to provision identical Azure infrastructure for Development, Testing, and Production. How would you use Terraform?

**Answer**

Create reusable Terraform modules and use different variable files (`.tfvars`) for each environment while keeping the same infrastructure code.

**Explanation**

This approach promotes consistency, reduces duplication, and simplifies maintenance.

---

### Scenario 2

**Question**

A Virtual Machine deployment fails because the subnet cannot be found. What would you check first?

**Answer**

Verify that the Subnet resource exists and that the VM references it correctly using the subnet ID.

**Explanation**

Terraform relies on resource references to determine dependencies. Incorrect or missing references commonly cause deployment failures.

---

### Scenario 3

**Question**

Your Terraform deployment created a Virtual Machine, but it is inaccessible from the internet. What is the most likely issue?

**Answer**

Check the Network Security Group rules, Public IP association, and Network Interface configuration.

**Explanation**

Even if the VM is running, incorrect NSG rules or missing public networking configuration can block access.

---

### Scenario 4

**Question**

Your organization requires every infrastructure deployment to be reviewed before execution. How would you implement this in Azure DevOps?

**Answer**

Configure the pipeline to run `terraform plan`, publish the plan for review, require manual approval, and then execute `terraform apply`.

**Explanation**

This reduces the risk of accidental infrastructure changes and aligns with enterprise change management practices.

---

### Scenario 5

**Question**

A Jenkins pipeline successfully runs `terraform init`, but `terraform apply` fails because the Azure provider cannot authenticate. What would you investigate?

**Answer**

Verify Azure service principal credentials, environment variables, stored Jenkins credentials, and provider configuration.

**Explanation**

Authentication issues are commonly caused by expired secrets, incorrect credentials, or misconfigured service connections.

---

### Scenario 6

**Question**

A developer manually deletes an Azure Storage Account that Terraform previously created. What should you do before the next deployment?

**Answer**

Run `terraform plan` to detect the drift and then execute `terraform apply` to recreate the missing resource if appropriate.

**Explanation**

Terraform compares the desired configuration with the actual infrastructure and identifies missing resources.

---

### Scenario 7

**Question**

Your team accidentally executes `terraform apply` directly in Production without reviewing the changes. How can this be prevented?

**Answer**

Implement a mandatory Plan stage followed by manual approval before the Apply stage in the CI/CD pipeline.

**Explanation**

This introduces governance and reduces the risk of unintended production changes.

---

### Scenario 8

**Question**

Your company provisions the same Virtual Network configuration across multiple projects. What is the recommended Terraform approach?

**Answer**

Create a reusable Virtual Network module and reference it from each project.

**Explanation**

Reusable modules ensure consistency, simplify updates, and reduce code duplication.

---

### Scenario 9

**Question**

A Terraform deployment reports that it will destroy several production resources unexpectedly. What should you do?

**Answer**

Stop the deployment immediately, review the `terraform plan` output, verify the state file, inspect recent configuration changes, and only apply after confirming the planned actions.

**Explanation**

Unexpected resource destruction often results from configuration changes, incorrect state, or modified resource identifiers.

---

### Scenario 10

**Question**

Your Infrastructure as Code pipeline needs to deploy Azure resources automatically after code is merged into the main branch. What would a typical workflow look like?

**Answer**

A standard workflow is:

1. Developer pushes code to Git.
2. CI/CD pipeline is triggered.
3. Run `terraform fmt`.
4. Run `terraform validate`.
5. Run `terraform plan`.
6. Perform manual approval (Production).
7. Run `terraform apply`.
8. Verify deployment and publish logs.

**Explanation**

This workflow provides automated, consistent, and auditable infrastructure deployments while minimizing deployment risks.
