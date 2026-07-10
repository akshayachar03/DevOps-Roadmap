# Variables & Secrets & Workflow Expressions Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What are Variables in GitHub Actions?

**Answer**

Variables are values used to store configuration information that can be reused throughout a workflow.

Common types include:

- Repository Variables
- Environment Variables
- Workflow Variables

**Explanation**

Variables improve workflow readability and maintainability by avoiding hardcoded values.

**Where it is used in Production**

- Application names
- Environment names
- Image tags
- URLs
- Build configurations

**Common Mistake**

Candidates often store passwords or API keys in variables instead of Secrets.

---

### Question 2

**Question**

What is the difference between Variables and Secrets in GitHub Actions?

**Answer**

- **Variables** store non-sensitive configuration values.
- **Secrets** securely store sensitive information such as passwords, API keys, and access tokens.

**Explanation**

Secrets are encrypted and automatically masked in workflow logs, while variables are not encrypted.

**Where it is used in Production**

- Variables: Environment names, application versions.
- Secrets: Cloud credentials, SSH keys, GitHub tokens.

---

### Question 3

**Question**

What are Repository Variables?

**Answer**

Repository Variables are non-sensitive variables available to workflows within a specific GitHub repository.

**Explanation**

They provide centralized configuration values that can be reused across multiple workflows.

**Where it is used in Production**

- Project names
- Docker image names
- Build configurations
- Environment identifiers

---

### Question 4

**Question**

What are Environment Variables in GitHub Actions?

**Answer**

Environment Variables are values available during workflow execution.

They can be defined at:

- Workflow level
- Job level
- Step level

**Explanation**

Environment variables simplify configuration by allowing reusable values within a workflow.

**Where it is used in Production**

- Build environments
- Deployment paths
- Application configuration

---

### Question 5

**Question**

What are GitHub Secrets?

**Answer**

GitHub Secrets securely store sensitive information required by workflows.

Examples include:

- API Keys
- Cloud Credentials
- Personal Access Tokens
- SSH Keys

**Explanation**

Secrets are encrypted, protected, and automatically masked in logs during workflow execution.

**Where it is used in Production**

Every production deployment requiring authentication.

**Common Mistake**

Many candidates expose secrets using `echo`, unintentionally revealing sensitive data in logs.

---

### Question 6

**Question**

What are Environment Secrets?

**Answer**

Environment Secrets are secrets associated with a specific GitHub Environment, such as Development, Staging, or Production.

**Explanation**

They allow different credentials to be used for different deployment environments.

**Where it is used in Production**

- Development credentials
- Staging credentials
- Production credentials

---

### Question 7

**Question**

What are Contexts in GitHub Actions?

**Answer**

Contexts are objects that provide information about the workflow, repository, runner, jobs, and events.

Examples include:

- github
- env
- vars
- secrets
- runner
- matrix

**Explanation**

Contexts allow workflows to dynamically access runtime information.

**Where it is used in Production**

Conditional execution, deployments, and dynamic workflow configuration.

---

### Question 8

**Question**

What are Expressions in GitHub Actions?

**Answer**

Expressions evaluate dynamic values using the `${{ }}` syntax.

Example:

```yaml
${{ github.ref }}
```

**Explanation**

Expressions allow workflows to make decisions based on runtime information.

**Where it is used in Production**

- Branch-based deployments
- Conditional jobs
- Dynamic image tags

---

### Question 9

**Question**

What is Conditional Execution in GitHub Actions?

**Answer**

Conditional Execution controls whether a job or step executes based on a condition.

Example:

```yaml
if: github.ref == 'refs/heads/main'
```

**Explanation**

Conditions prevent unnecessary workflow execution and enforce deployment rules.

**Where it is used in Production**

Deploying only from the main branch.

---

### Question 10

**Question**

What is Matrix Strategy in GitHub Actions?

**Answer**

Matrix Strategy runs the same job across multiple configurations simultaneously.

Example:

- Ubuntu
- Windows
- macOS

or

- Java 17
- Java 21

**Explanation**

Matrix builds reduce duplication and simplify cross-platform testing.

**Where it is used in Production**

Testing applications across multiple operating systems or runtime versions.

---

### Question 11

**Question**

Why are GitHub Secrets preferred over hardcoded credentials?

**Answer**

GitHub Secrets provide:

- Encryption
- Secure storage
- Automatic masking
- Centralized management
- Better security

**Explanation**

Hardcoding credentials exposes sensitive information and increases security risks.

**Where it is used in Production**

All enterprise CI/CD pipelines.

---

### Question 12

**Question**

How do Variables, Secrets, and Expressions work together in a workflow?

**Answer**

Variables provide reusable configuration values, Secrets securely store sensitive information, and Expressions dynamically access or evaluate these values during workflow execution.

**Explanation**

Together, they create flexible, secure, and maintainable workflows.

**Where it is used in Production**

Build, test, deployment, and infrastructure automation pipelines.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

Your deployment workflow needs an Azure Service Principal password. Should you store it as a Variable or a Secret?

**Answer**

I would store it as a **GitHub Secret**.

**Explanation**

Sensitive information should always be stored as Secrets because they are encrypted and masked in workflow logs.

---

### Scenario 2

**Question**

Your workflow should deploy only when code is pushed to the `main` branch. How would you implement this?

**Answer**

I would use conditional execution.

Example:

```yaml
if: github.ref == 'refs/heads/main'
```

**Explanation**

Conditional execution ensures deployments occur only from authorized branches.

---

### Scenario 3

**Question**

Your organization has Development, Staging, and Production environments with different cloud credentials. How would you manage them?

**Answer**

I would configure separate **Environment Secrets** for each environment.

**Explanation**

Environment-specific secrets improve security and simplify deployments.

---

### Scenario 4

**Question**

A workflow prints an API key in the logs during deployment. What mistake was likely made?

**Answer**

The workflow probably:

- Used a Variable instead of a Secret.
- Explicitly echoed the secret value.

**Explanation**

Sensitive credentials should never be printed in workflow logs.

---

### Scenario 5

**Question**

Your application must be tested on Ubuntu, Windows, and macOS. How would you configure the workflow?

**Answer**

I would use a **Matrix Strategy**.

**Explanation**

The matrix automatically creates parallel jobs for each operating system.

---

### Scenario 6

**Question**

A deployment succeeds in Development but fails in Production because the credentials are incorrect. How would you troubleshoot this?

**Answer**

I would verify:

- Environment Secrets
- Environment selection
- Secret names
- Workflow configuration
- Deployment logs

**Explanation**

Incorrect or missing environment-specific secrets are common causes of deployment failures.

---

### Scenario 7

**Question**

Your workflow needs to use the repository name dynamically. Which feature would you use?

**Answer**

I would use the **github context**.

Example:

```yaml
${{ github.repository }}
```

**Explanation**

Contexts provide runtime information without hardcoding values.

---

### Scenario 8

**Question**

Multiple workflows use the same Docker image name. How would you avoid repeating this value?

**Answer**

I would store it as a **Repository Variable**.

**Explanation**

Centralizing configuration values improves maintainability and reduces duplication.

---

### Scenario 9

**Question**

Your manager wants deployment jobs to run only when previous jobs succeed and the branch is `main`. How would you configure this?

**Answer**

I would use:

- Job dependencies (`needs`)
- Conditional execution (`if`)

**Explanation**

Combining dependencies with conditions ensures deployments occur only after successful validation and from approved branches.

---

### Scenario 10

**Question**

A company wants one workflow to test an application against multiple Node.js versions simultaneously. Which GitHub Actions feature would you recommend?

**Answer**

I would use a **Matrix Strategy**.

**Explanation**

A matrix automatically creates parallel jobs for each Node.js version, reducing workflow duplication while improving test coverage.
