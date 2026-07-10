# AWS IAM Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What is AWS Identity and Access Management (IAM)?

**Answer**

AWS Identity and Access Management (IAM) is a service that enables you to securely manage authentication (who can sign in) and authorization (what they can access) for AWS resources.

IAM allows you to create and manage:

- Users
- Groups
- Roles
- Policies
- Permissions
- MFA

**Explanation**

IAM follows the principle of least privilege by granting users only the permissions they require. It is one of the first services configured in every AWS account.

**Where it is used in Production**

- Managing AWS administrators
- Granting application permissions
- CI/CD authentication
- Cross-service access

**Common Mistake**

Many candidates think IAM is only for users. It also manages roles, policies, and service permissions.

---

### Question 2

**Question**

What is an IAM User?

**Answer**

An IAM User is an identity created within an AWS account that represents a person or application requiring access to AWS resources.

An IAM User can have:

- Password
- Access Keys
- Policies
- MFA

**Explanation**

IAM Users are typically created for administrators or individuals who require long-term AWS access.

**Where it is used in Production**

AWS administrators, DevOps engineers, and automation accounts.

**Common Mistake**

Using the AWS Root User for daily operations instead of IAM Users.

---

### Question 3

**Question**

What is an IAM Group?

**Answer**

An IAM Group is a collection of IAM Users that share the same permissions.

Permissions are assigned to the group rather than individual users.

**Explanation**

Groups simplify permission management by allowing administrators to manage permissions centrally.

**Where it is used in Production**

Examples:

- Developers
- DevOps Team
- Database Team
- ReadOnly Users

**Common Mistake**

Trying to assign IAM Roles directly to IAM Groups. Roles can only be assumed by trusted identities.

---

### Question 4

**Question**

What is an IAM Role?

**Answer**

An IAM Role is an AWS identity with temporary credentials that can be assumed by users, AWS services, or external identities.

Roles do not have permanent credentials.

**Explanation**

Roles provide temporary security credentials and eliminate the need to store long-term access keys.

**Where it is used in Production**

- EC2 accessing S3
- Lambda accessing DynamoDB
- Cross-account access
- EKS Pods
- ECS Tasks

**Common Mistake**

Confusing IAM Users with IAM Roles.

---

### Question 5

**Question**

What is an IAM Policy?

**Answer**

An IAM Policy is a JSON document that defines permissions by specifying:

- Effect (Allow or Deny)
- Actions
- Resources
- Conditions

**Explanation**

Policies determine what actions identities can perform on AWS resources.

**Where it is used in Production**

Granting least-privilege access to AWS resources.

**Common Mistake**

Granting overly broad permissions such as `"Action": "*"` and `"Resource": "*"`.

---

### Question 6

**Question**

What are the different types of IAM Policies?

**Answer**

The primary policy types are:

- AWS Managed Policies
- Customer Managed Policies
- Inline Policies

**Explanation**

AWS Managed Policies are maintained by AWS, while Customer Managed Policies provide more granular control.

**Where it is used in Production**

Customer Managed Policies are commonly used because they offer flexibility and version control.

---

### Question 7

**Question**

What are Permission Boundaries in IAM?

**Answer**

Permission Boundaries define the maximum permissions an IAM User or Role can receive.

Even if a policy grants additional permissions, actions outside the boundary are denied.

**Explanation**

Permission Boundaries help organizations safely delegate IAM administration while preventing privilege escalation.

**Where it is used in Production**

Large enterprises with multiple AWS teams.

**Common Mistake**

Assuming Permission Boundaries grant permissions. They only limit the maximum permissions.

---

### Question 8

**Question**

What is Multi-Factor Authentication (MFA) in AWS?

**Answer**

MFA adds an additional authentication factor, such as a mobile authenticator app or hardware token, in addition to a password.

**Explanation**

Even if a password is compromised, an attacker cannot access the account without the second authentication factor.

**Where it is used in Production**

- Root User
- IAM Users
- Privileged administrators

**Common Mistake**

Enabling MFA only for the Root User and not for privileged IAM Users.

---

### Question 9

**Question**

Why should IAM Roles be preferred over Access Keys for AWS services?

**Answer**

IAM Roles provide temporary credentials that are automatically rotated and managed by AWS.

**Explanation**

Roles eliminate the need to store long-term access keys in applications or source code.

**Where it is used in Production**

- EC2
- Lambda
- ECS
- EKS
- CodeBuild

**Common Mistake**

Hardcoding AWS Access Keys inside application code.

---

### Question 10

**Question**

What is the Principle of Least Privilege in IAM?

**Answer**

The Principle of Least Privilege means granting only the permissions required to perform a task and nothing more.

**Explanation**

Limiting permissions reduces the attack surface and minimizes the impact of compromised credentials.

**Where it is used in Production**

All enterprise AWS environments.

---

### Question 11

**Question**

Why should the AWS Root User not be used for daily operations?

**Answer**

The Root User has unrestricted access to all AWS resources.

Instead, create IAM Users with limited permissions and enable MFA on the Root User.

**Explanation**

Using the Root User increases security risks because it bypasses many permission restrictions.

**Where it is used in Production**

AWS account administration.

**Common Mistake**

Creating infrastructure using the Root User.

---

### Question 12

**Question**

What is the difference between an IAM User and an IAM Role?

**Answer**

| IAM User | IAM Role |
|----------|----------|
| Permanent identity | Temporary identity |
| Long-term credentials | Temporary credentials |
| Used by people and applications | Assumed by users, services, or applications |
| Password and Access Keys | No permanent credentials |

**Explanation**

IAM Users represent identities, while IAM Roles provide temporary access without permanent credentials.

**Where it is used in Production**

IAM Users for administrators, IAM Roles for AWS services and applications.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

Your EC2 instance needs to upload files to an S3 bucket. How would you provide secure access?

**Answer**

Attach an IAM Role with the required S3 permissions to the EC2 instance.

**Explanation**

IAM Roles provide temporary credentials, eliminating the need to store AWS Access Keys on the server.

---

### Scenario 2

**Question**

A developer has committed AWS Access Keys to a GitHub repository. What actions would you take?

**Answer**

- Immediately deactivate or delete the exposed keys.
- Create new credentials if required.
- Investigate CloudTrail logs for unauthorized activity.
- Replace access keys with an IAM Role whenever possible.

**Explanation**

Exposed credentials can be exploited quickly. Rotating credentials and using IAM Roles reduces this risk.

---

### Scenario 3

**Question**

A new DevOps engineer joins your team and needs the same permissions as other DevOps engineers. What is the best approach?

**Answer**

Create an IAM User and add it to the existing DevOps IAM Group.

**Explanation**

Managing permissions through groups simplifies administration and ensures consistency.

---

### Scenario 4

**Question**

An interviewer asks whether Lambda functions should use IAM Users or IAM Roles. What is your answer?

**Answer**

Lambda functions should use IAM Roles.

**Explanation**

IAM Roles provide temporary credentials that AWS automatically manages, making them more secure than long-term access keys.

---

### Scenario 5

**Question**

A junior administrator accidentally grants `AdministratorAccess` to every developer. What should be done?

**Answer**

Replace the broad permissions with least-privilege IAM Policies that allow only the actions required for each role.

**Explanation**

Following the Principle of Least Privilege reduces security risks and limits accidental changes.

---

### Scenario 6

**Question**

Your organization wants every administrator to use an additional authentication method during login. Which IAM feature would you enable?

**Answer**

Enable Multi-Factor Authentication (MFA) for all privileged IAM Users.

**Explanation**

MFA significantly improves account security by requiring a second authentication factor.

---

### Scenario 7

**Question**

Your security team wants to ensure junior administrators cannot create highly privileged IAM Roles. Which IAM feature would you use?

**Answer**

Use Permission Boundaries.

**Explanation**

Permission Boundaries define the maximum permissions that IAM Users or Roles can receive, preventing privilege escalation.

---

### Scenario 8

**Question**

An application running on EC2 fails to access S3 because of an `AccessDenied` error. What would you check first?

**Answer**

Verify that the EC2 instance has the correct IAM Role attached and that the IAM Policy grants the required S3 permissions.

**Explanation**

Most `AccessDenied` errors result from missing or incorrect IAM permissions.

---

### Scenario 9

**Question**

Your company has separate Development, QA, and Production teams. How would you organize IAM permissions?

**Answer**

Create separate IAM Groups for each team and assign environment-specific IAM Policies based on job responsibilities.

**Explanation**

Using groups simplifies permission management and supports the Principle of Least Privilege.

---

### Scenario 10

**Question**

During a security audit, you discover several applications using long-term AWS Access Keys stored in configuration files. What is your recommendation?

**Answer**

Replace long-term access keys with IAM Roles wherever possible, remove hardcoded credentials, rotate existing keys, and enforce least-privilege IAM Policies.

**Explanation**

IAM Roles provide temporary credentials managed by AWS, reducing the risk of credential exposure and improving overall security.
