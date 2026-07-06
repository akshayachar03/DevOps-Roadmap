# Azure Identity and Access Management (IAM)

## Definition

- Azure Identity and Access Management (IAM) is a set of services that control **who can access Azure resources** and **what actions they can perform**.
- It uses identities, authentication, authorization, and Role-Based Access Control (RBAC) to secure Azure resources.
- Azure IAM is primarily built on **Microsoft Entra ID (formerly Azure Active Directory)**.

---

## Why is it used?

- Verify user identities.
- Control access to Azure resources.
- Implement least privilege access.
- Improve security and compliance.
- Support Single Sign-On (SSO).
- Enable secure access for users, groups, and applications.

---

## Key Features

- Microsoft Entra ID integration.
- Authentication and authorization.
- Role-Based Access Control (RBAC).
- Multi-Factor Authentication (MFA).
- Conditional Access policies.
- Managed Identities.
- Privileged Identity Management (PIM).
- Single Sign-On (SSO).

---

## Advantages

- Centralized identity management.
- Improved security.
- Fine-grained access control.
- Supports hybrid identity.
- Easy integration with Azure services.

---

## Disadvantages

- RBAC planning can become complex.
- Misconfigured permissions may expose resources.
- Advanced security features may require premium licensing.

---

## Components

### Identity

- User, Group, Service Principal, or Managed Identity.

### Authentication

- Verifies user identity.

### Authorization

- Determines permitted actions.

### RBAC

- Controls resource permissions.

### Microsoft Entra ID

- Identity provider for Azure.

---

## Workflow

```text
User
   ↓
Microsoft Entra ID
   ↓
Authentication
   ↓
Authorization (RBAC)
   ↓
Access Azure Resource
```

---

## Real-world Example

An Azure Administrator signs in using Microsoft Entra ID. Azure verifies the identity and RBAC determines whether the administrator can manage Virtual Machines.

---

## Interview Tip

"IAM ensures that the right person has the right level of access to the right Azure resources."

---

## Quick Revision

- IAM controls access to Azure resources.
- Uses Microsoft Entra ID.
- Authentication verifies identity.
- Authorization grants permissions.
- RBAC manages access.
- Supports MFA and Conditional Access.

---

## Important Interview Questions

1. What is Azure IAM?
2. What services are included in Azure IAM?
3. What is the difference between authentication and authorization?
4. How does IAM improve Azure security?
5. What is the relationship between IAM and RBAC?

---

# Authentication Services in Azure

## Definition

- Authentication is the process of verifying the identity of a user, application, or device before granting access.
- Azure authentication is primarily provided by Microsoft Entra ID.

---

## Why is it used?

- Verify user identity.
- Prevent unauthorized access.
- Enable secure application login.
- Support enterprise security.
- Protect cloud resources.

---

## Key Features

- Username and password authentication.
- Multi-Factor Authentication (MFA).
- Passwordless authentication.
- Single Sign-On (SSO).
- Conditional Access.
- OAuth and OpenID Connect support.

---

## Advantages

- Strong security.
- Easy user management.
- Centralized authentication.
- Supports cloud and hybrid environments.
- Reduces password-related risks.

---

## Disadvantages

- MFA may add extra login steps.
- Incorrect policies can block legitimate users.

---

## Types

### Username & Password

- Basic authentication method.

### Multi-Factor Authentication (MFA)

- Requires multiple verification methods.

### Single Sign-On (SSO)

- One login for multiple applications.

### Passwordless Authentication

- Uses biometrics, Windows Hello, or Microsoft Authenticator.

### Conditional Access

- Grants access based on policies like location, device, or risk.

---

## Workflow

```text
User
   ↓
Enter Credentials
   ↓
Microsoft Entra ID
   ↓
MFA (Optional)
   ↓
Authentication Successful
```

---

## Real-world Example

An employee signs in once using Microsoft Entra ID and accesses Microsoft 365, Azure Portal, and other enterprise applications without logging in again.

---

## Interview Tip

"Authentication answers the question 'Who are you?' before Azure grants access."

---

## Quick Revision

- Authentication verifies identity.
- Microsoft Entra ID handles authentication.
- MFA increases security.
- SSO provides one login.
- Conditional Access applies security policies.

---

## Important Interview Questions

1. What is authentication?
2. What is Microsoft Entra ID?
3. What is MFA?
4. What is Single Sign-On?
5. What is Conditional Access?

---

# Identity Access Management (IAM)

## Definition

- Identity Access Management (IAM) is the process of managing identities and controlling access to Azure resources.
- It ensures authenticated users receive only the permissions required for their work.

---

## Why is it used?

- Protect cloud resources.
- Reduce unauthorized access.
- Simplify user management.
- Enforce security policies.
- Support compliance.

---

## Key Features

- User and group management.
- Role assignments.
- Managed identities.
- RBAC integration.
- Conditional Access.
- Audit logs.

---

## Advantages

- Centralized management.
- Improved security.
- Easier administration.
- Supports automation.
- Better compliance.

---

## Disadvantages

- Requires proper planning.
- Poor permission design increases security risks.

---

## Components

### Users

- Individual identities.

### Groups

- Collection of users.

### Service Principals

- Identity for applications.

### Managed Identities

- Azure-managed identities for Azure resources.

### Roles

- Define permissions.

---

## Workflow

```text
Create Identity
      ↓
Assign Role
      ↓
Authenticate
      ↓
Access Resource
```

---

## Real-world Example

A development team is added to a Developers group. The group receives Contributor access to the development Resource Group instead of assigning permissions individually.

---

## Interview Tip

"IAM manages identities while RBAC controls what those identities are allowed to do."

---

## Quick Revision

- IAM manages identities.
- Supports users and groups.
- Uses Microsoft Entra ID.
- Integrates with RBAC.
- Supports Managed Identities.

---

## Important Interview Questions

1. What is Identity Access Management?
2. What is a Managed Identity?
3. What is a Service Principal?
4. Why are groups preferred over individual users?
5. How does IAM improve security?

---

# Implementing Role-Based Access Control (RBAC)

## Definition

- Azure RBAC is an authorization system that controls who can perform actions on Azure resources.
- Permissions are assigned through roles instead of directly assigning permissions.

---

## Why is it used?

- Control access to Azure resources.
- Follow the principle of least privilege.
- Simplify permission management.
- Improve security.
- Reduce administrative effort.

---

## Key Features

- Built-in roles.
- Custom roles.
- Role assignments.
- Multiple assignment scopes.
- Azure AD integration.
- Inheritance of permissions.

---

## Advantages

- Fine-grained access control.
- Easy administration.
- Secure resource management.
- Supports custom permissions.
- Centralized authorization.

---

## Disadvantages

- Incorrect role assignments may cause security risks.
- Large environments require proper governance.

---

## Components

### Security Principal

- User
- Group
- Service Principal
- Managed Identity

### Role Definition

- Collection of allowed permissions.

### Scope

- Management Group
- Subscription
- Resource Group
- Resource

### Role Assignment

- Connects a security principal, role, and scope.

---

## Common Built-in Roles

| Role | Permissions |
|------|-------------|
| Owner | Full access including role assignments |
| Contributor | Create and manage resources but cannot assign roles |
| Reader | View resources only |
| User Access Administrator | Manage user access and RBAC assignments |

---

## Workflow

```text
User
   ↓
Assign Role
   ↓
Select Scope
   ↓
RBAC Evaluates Permissions
   ↓
Allow or Deny Access
```

---

## Real-world Example

A support engineer receives the Reader role on a Production Resource Group so they can monitor resources without modifying them.

---

## Interview Tip

"RBAC controls authorization by assigning roles to identities at different scopes."

---

## Quick Revision

- RBAC controls authorization.
- Uses built-in and custom roles.
- Assigns permissions by role.
- Supports inheritance.
- Scopes include Subscription, Resource Group, and Resource.

---

## Important Interview Questions

1. What is Azure RBAC?
2. What are the built-in RBAC roles?
3. What is the difference between Owner and Contributor?
4. What are RBAC scopes?
5. What is a Role Assignment?

---

# Best Practices for RBAC

## Definition

- RBAC best practices help organizations implement secure and manageable access control.
- Following these practices reduces security risks and simplifies administration.

---

## Why is it used?

- Improve security.
- Reduce excessive permissions.
- Simplify audits.
- Support compliance.
- Protect critical resources.

---

## Key Best Practices

### Follow Least Privilege

- Grant only the permissions required.

---

### Assign Roles to Groups

- Avoid assigning permissions directly to users.

---

### Use Built-in Roles

- Prefer built-in roles before creating custom roles.

---

### Use the Smallest Scope

- Assign permissions at the lowest possible scope.

---

### Separate Production and Development Access

- Different teams should have different permissions.

---

### Enable Multi-Factor Authentication

- Protect privileged accounts.

---

### Review Role Assignments Regularly

- Remove unused permissions.

---

### Use Privileged Identity Management (PIM)

- Provide just-in-time administrative access.

---

### Monitor Activity Logs

- Audit role assignments and access changes.

---

## Advantages

- Stronger security.
- Easier management.
- Better compliance.
- Reduced attack surface.
- Improved auditing.

---

## Disadvantages

- Requires continuous monitoring.
- Regular reviews consume administrative effort.

---

## Workflow

```text
Create Group
      ↓
Assign Least Privilege Role
      ↓
Enable MFA
      ↓
Review Permissions
      ↓
Audit Regularly
```

---

## Real-world Example

Instead of giving every developer Contributor access to an entire subscription, a company assigns the Contributor role only to the Development Resource Group and only through a Developers security group.

---

## Interview Tip

"The most important RBAC best practice is to always follow the Principle of Least Privilege."

---

## Quick Revision

- Apply least privilege.
- Assign roles to groups.
- Use built-in roles.
- Assign the smallest possible scope.
- Enable MFA.
- Review permissions regularly.
- Use PIM for administrators.
- Audit role assignments.

---

## Important Interview Questions

1. What is the Principle of Least Privilege?
2. Why should RBAC roles be assigned to groups instead of users?
3. Why should roles be assigned at the lowest possible scope?
4. What is Privileged Identity Management (PIM)?
5. What are the best practices for implementing Azure RBAC?
