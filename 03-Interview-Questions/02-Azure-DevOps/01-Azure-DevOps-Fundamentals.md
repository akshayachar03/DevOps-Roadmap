# Azure DevOps Fundamentals Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What is Azure DevOps?

**Answer**

Azure DevOps is Microsoft's cloud-based DevOps platform that provides an end-to-end set of services for planning, developing, testing, deploying, and monitoring software applications. It enables collaboration between development and operations teams throughout the software development lifecycle (SDLC).

The major services include:

- Azure Boards
- Azure Repos
- Azure Pipelines
- Azure Test Plans
- Azure Artifacts

**Explanation**

Azure DevOps helps automate software delivery and improves collaboration among teams. It supports Agile, Scrum, CI/CD, version control, package management, and project tracking.

**Used in Production**

- CI/CD automation
- Source code management
- Agile project management
- Release automation
- Infrastructure deployment

**Common Mistake**

Many candidates confuse Azure DevOps with Azure Cloud. Azure DevOps is a DevOps platform and can deploy applications to Azure, AWS, GCP, Kubernetes, on-premises servers, or any other environment.

---

### Question 2

**Question**

What are the different services available in Azure DevOps?

**Answer**

Azure DevOps consists of five core services:

- Azure Boards
  - Work item tracking
  - Agile planning
  - Sprint management

- Azure Repos
  - Git repositories
  - TFVC repositories

- Azure Pipelines
  - Continuous Integration (CI)
  - Continuous Deployment (CD)

- Azure Test Plans
  - Manual testing
  - Exploratory testing

- Azure Artifacts
  - Package management
  - NuGet
  - npm
  - Maven
  - Python packages

**Explanation**

Each service focuses on a specific phase of the SDLC while integrating seamlessly with the others.

**Used in Production**

Development teams typically use all five services together to manage the complete application lifecycle.

---

### Question 3

**Question**

What is the difference between Azure and Azure DevOps?

**Answer**

| Azure | Azure DevOps |
|--------|--------------|
| Cloud platform | DevOps platform |
| Provides cloud infrastructure | Provides software development lifecycle tools |
| Hosts applications | Builds, tests, and deploys applications |
| Includes VMs, Storage, Networking | Includes Boards, Repos, Pipelines, Artifacts |

**Explanation**

Azure provides infrastructure and cloud services, while Azure DevOps manages software development and deployment processes.

**Production Example**

An application may be built using Azure DevOps Pipelines and deployed to Azure App Service.

**Common Mistake**

Many candidates incorrectly state that Azure DevOps can only deploy to Azure. It supports deployment to any cloud or on-premises environment.

---

### Question 4

**Question**

What is an Azure DevOps Organization?

**Answer**

An Azure DevOps Organization is the top-level container that manages all DevOps resources.

It contains:

- Projects
- Users
- Security
- Billing
- Repositories
- Pipelines

**Explanation**

Organizations provide isolation between different companies or business units.

**Production Example**

A company may create:

- Company-DevOps
- Company-Production
- Company-R&D

Each organization can have multiple projects.

**Common Mistake**

Candidates often confuse Organizations with Projects.

---

### Question 5

**Question**

What is an Azure DevOps Project?

**Answer**

A Project is a logical container inside an Azure DevOps Organization that groups resources for a particular application or team.

Each project can contain:

- Boards
- Repositories
- Pipelines
- Test Plans
- Artifacts

**Explanation**

Projects help isolate development activities for different applications or teams.

**Production Example**

Organization:

```
ABC Technologies
```

Projects:

- HR Portal
- Banking API
- Mobile App
- E-Commerce Website

Each project has its own repositories, pipelines, and work items.

---

### Question 6

**Question**

What is the difference between an Organization and a Project?

**Answer**

| Organization | Project |
|--------------|---------|
| Top-level container | Child container |
| Contains multiple projects | Contains application resources |
| Manages billing | Manages project resources |
| Manages users globally | Manages project permissions |

**Explanation**

Organizations manage the overall DevOps environment, while projects organize work for individual applications or teams.

**Common Mistake**

Candidates often think Projects can exist without an Organization.

---

### Question 7

**Question**

What are Users and Permissions in Azure DevOps?

**Answer**

Users are individuals who access Azure DevOps resources.

Permissions determine what users can:

- Read code
- Push code
- Create pipelines
- Approve releases
- Manage repositories
- Delete resources

Permissions are usually assigned through security groups.

**Explanation**

Role-based access control (RBAC) ensures users have only the permissions required for their responsibilities.

**Production Example**

- Developers can push code.
- QA can execute test plans.
- DevOps engineers manage pipelines.
- Administrators manage permissions.

**Common Mistake**

Granting Project Administrator permissions to every user violates the principle of least privilege.

---

### Question 8

**Question**

What is a Personal Access Token (PAT)?

**Answer**

A Personal Access Token (PAT) is an authentication token used instead of a password for accessing Azure DevOps resources programmatically.

It is commonly used for:

- Git authentication
- REST APIs
- Automation scripts
- CI/CD tools
- Third-party integrations

**Explanation**

PATs provide secure authentication without exposing account passwords.

**Production Example**

- Jenkins connecting to Azure DevOps
- Terraform accessing Azure Repos
- Git clone over HTTPS
- REST API automation

**Common Mistake**

Creating PATs with Full Access and long expiration periods instead of using the minimum required permissions and shorter lifetimes.

---

### Question 9

**Question**

Why should PATs be protected?

**Answer**

PATs provide direct access to Azure DevOps resources.

If exposed, an attacker may:

- Read repositories
- Modify code
- Delete pipelines
- Trigger deployments
- Access project data

**Explanation**

PATs should be treated like passwords.

Best practices include:

- Least privilege
- Short expiration
- Secure storage
- Regular rotation
- Never commit PATs to Git repositories

**Production Example**

PATs are often stored in Azure Key Vault or secure pipeline secret variables.

---

### Question 10

**Question**

How do Azure DevOps users authenticate?

**Answer**

Users can authenticate using:

- Microsoft Entra ID (Azure AD)
- Microsoft Account
- Personal Access Tokens (PAT)
- Service Principals (for automation)
- OAuth (for integrations)

**Explanation**

Interactive users typically sign in with Microsoft Entra ID, while automation uses PATs or service principals.

**Production Example**

- Developers log in with Entra ID.
- CI/CD tools use PATs or service principals.

---

### Question 11

**Question**

What are the benefits of using Azure DevOps?

**Answer**

Key benefits include:

- Integrated DevOps platform
- CI/CD automation
- Agile project management
- Git repository hosting
- Package management
- Secure access control
- Cross-platform support
- Integration with Azure, AWS, GCP, Kubernetes, GitHub, Jenkins, Terraform, and many other tools

**Explanation**

Azure DevOps reduces manual work, improves collaboration, accelerates software delivery, and increases deployment reliability.

**Production Example**

Organizations use Azure DevOps to automate build, test, approval, and deployment workflows.

---

## Scenario-Based Interview Questions

### Scenario 1

**Question**

A new developer joins your team but cannot access the project in Azure DevOps. What would you check?

**Answer**

Check:

1. User is added to the Azure DevOps Organization.
2. User is assigned access level.
3. User is added to the correct Project.
4. User belongs to the appropriate security group.
5. Required permissions are granted.
6. User signs in with the correct Microsoft account.

**Explanation**

Most access issues result from missing project membership or insufficient permissions rather than platform failures.

---

### Scenario 2

**Question**

A developer receives a "Permission Denied" error while pushing code to Azure Repos. How would you troubleshoot?

**Answer**

Verify:

- Repository permissions
- Branch permissions
- User group membership
- Git credentials
- PAT validity (if using HTTPS)
- Repository access rights

**Explanation**

Push failures are commonly caused by insufficient repository or branch permissions, expired credentials, or branch protection policies.

---

### Scenario 3

**Question**

A PAT used by Jenkins suddenly stops working. What could be the reasons?

**Answer**

Possible causes:

- PAT expired
- PAT revoked
- Required scopes removed
- User account disabled
- Incorrect PAT configured
- Secret updated incorrectly

**Explanation**

PAT expiration is a frequent cause of CI/CD authentication failures. Rotate tokens before they expire and update the consuming system.

---

### Scenario 4

**Question**

A developer accidentally shares a PAT in a Git repository. What should you do immediately?

**Answer**

1. Revoke the PAT immediately.
2. Generate a new PAT if required.
3. Remove the secret from the repository history.
4. Rotate any dependent credentials if necessary.
5. Audit recent Azure DevOps activity.
6. Inform the security team if organizational policy requires it.

**Explanation**

A leaked PAT can allow unauthorized access. Revoking it promptly minimizes risk.

---

### Scenario 5

**Question**

Your company has multiple applications. Would you create one Azure DevOps Project or multiple Projects?

**Answer**

Create separate projects for logically independent applications or teams.

Examples:

- HR Portal
- CRM
- Banking API
- Mobile Application

**Explanation**

Separate projects improve security isolation, permission management, and project organization while reducing operational complexity.

---

### Scenario 6

**Question**

A team member requests Project Administrator permissions because they cannot edit a pipeline. How would you handle this?

**Answer**

Do not immediately grant Project Administrator rights.

Instead:

- Identify the exact task.
- Grant only the required permission.
- Use an appropriate security group.
- Follow the principle of least privilege.

**Explanation**

Excessive permissions increase security risk and make governance more difficult.

---

### Scenario 7

**Question**

Your organization has hundreds of developers. How would you manage permissions efficiently?

**Answer**

Use security groups instead of assigning permissions individually.

Example groups:

- Developers
- QA
- DevOps
- Project Administrators
- Readers

Assign permissions to groups and add users to the relevant group.

**Explanation**

Group-based permission management simplifies administration and reduces configuration errors.

---

### Scenario 8

**Question**

A contractor requires temporary access to an Azure DevOps project for one month. What approach would you use?

**Answer**

- Add the contractor with the minimum required permissions.
- Assign only the necessary project access.
- Avoid Full Administrator rights.
- Set an end date for access and remove it after the engagement.

**Explanation**

Temporary users should follow the same least-privilege principles as permanent employees to reduce security risk.

---

### Scenario 9

**Question**

Two teams are working on completely different products. Should they use the same Azure DevOps Project?

**Answer**

Generally, no.

Use separate projects when products have different:

- Teams
- Security requirements
- Pipelines
- Repositories
- Release processes

**Explanation**

Separate projects provide better isolation, governance, and maintainability while reducing the chance of accidental access.

---

### Scenario 10

**Question**

A user reports they can view work items but cannot access the Git repository. What would you investigate?

**Answer**

Check:

- Repository permissions
- Project membership
- Security group assignments
- Repository-specific deny rules
- Inherited permissions
- Access level licensing, if applicable

**Explanation**

Azure DevOps permissions are resource-specific. Access to Boards does not automatically grant access to Repos.

---

### Scenario 11

**Question**

During a security audit, you discover several PATs with Full Access and no defined rotation process. What actions would you recommend?

**Answer**

- Inventory all existing PATs.
- Remove unused tokens.
- Reduce scopes to the minimum required.
- Shorten expiration periods.
- Store tokens securely.
- Establish a regular rotation policy.
- Prefer service principals or managed identities where supported for automation.

**Explanation**

Broad, long-lived PATs increase the impact of credential compromise. Implementing least privilege and credential lifecycle management strengthens the organization's security posture.
