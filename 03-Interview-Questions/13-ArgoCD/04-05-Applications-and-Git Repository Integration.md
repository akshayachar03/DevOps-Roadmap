# Applications & Git Repository Integration Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What is an Application in Argo CD?

**Answer**

An Application is the core custom resource in Argo CD that defines what application should be deployed, where it should be deployed, and from which Git repository the deployment manifests should be retrieved.

**Explanation**

The Application resource acts as the deployment blueprint. It specifies the source repository, target revision, destination cluster, destination namespace, synchronization policy, and other deployment settings. Argo CD continuously monitors this resource to keep the cluster synchronized with Git.

**Where it is used in Production**

- Kubernetes application deployments
- GitOps pipelines
- Multi-environment deployments

**Common Mistake**

Many candidates think an Application represents only a Kubernetes Deployment. In reality, it can manage an entire application consisting of Deployments, Services, ConfigMaps, Ingresses, and other Kubernetes resources.

---

### Question 2

**Question**

What are the main fields of an Argo CD Application resource?

**Answer**

The important fields are:

- Source Repository
- Target Revision
- Path
- Destination Cluster
- Destination Namespace
- Project
- Sync Policy

**Explanation**

These fields tell Argo CD where to retrieve the manifests from and where to deploy them.

**Where it is used in Production**

Every Argo CD application configuration.

---

### Question 3

**Question**

What is the Source Repository in an Argo CD Application?

**Answer**

The Source Repository is the Git repository that stores the Kubernetes manifests, Helm charts, or Kustomize configurations for the application.

**Explanation**

Argo CD continuously monitors this repository for changes and deploys updates whenever the desired state changes.

**Where it is used in Production**

GitHub, GitLab, Azure Repos, Bitbucket, and other Git providers.

**Common Mistake**

Some candidates think Docker images are pulled from the Source Repository. Docker images are pulled from container registries; the Git repository stores deployment manifests.

---

### Question 4

**Question**

What is the Destination Cluster in Argo CD?

**Answer**

The Destination Cluster is the Kubernetes cluster where the application will be deployed.

**Explanation**

Argo CD supports deploying applications to the local Kubernetes cluster or multiple remote Kubernetes clusters.

**Where it is used in Production**

Multi-cluster Kubernetes environments.

---

### Question 5

**Question**

What is the Destination Namespace?

**Answer**

The Destination Namespace specifies the Kubernetes namespace where the application's resources will be created.

**Explanation**

It helps organize workloads and isolate applications within a Kubernetes cluster.

**Where it is used in Production**

Development, testing, staging, and production namespaces.

**Common Mistake**

Many candidates confuse the namespace in Git with the Kubernetes namespace. The Destination Namespace refers to the Kubernetes namespace only.

---

### Question 6

**Question**

What is Project Association in Argo CD?

**Answer**

Project Association links an application to an Argo CD Project, which defines deployment permissions, accessible repositories, destination clusters, and namespaces.

**Explanation**

Projects provide logical isolation and access control for groups of applications.

**Where it is used in Production**

Large organizations with multiple teams and environments.

---

### Question 7

**Question**

How do you connect a Git repository to Argo CD?

**Answer**

A Git repository can be connected using:

- Argo CD Web UI
- Argo CD CLI
- Kubernetes Secret
- Repository credentials

**Explanation**

Once connected, Argo CD can access the repository and monitor it for changes.

**Where it is used in Production**

Every GitOps deployment begins by connecting a Git repository.

---

### Question 8

**Question**

What types of credentials can Argo CD use to access Git repositories?

**Answer**

Argo CD supports:

- Username and Password
- Personal Access Token (PAT)
- SSH Keys
- GitHub App authentication

**Explanation**

The authentication method depends on the Git provider and organizational security requirements.

**Where it is used in Production**

Private Git repositories.

**Common Mistake**

Candidates often think only SSH authentication is supported.

---

### Question 9

**Question**

What is the Target Revision in Argo CD?

**Answer**

Target Revision specifies which Git branch, tag, or commit Argo CD should deploy.

Examples include:

- main
- develop
- release
- v1.2.0
- Specific commit SHA

**Explanation**

It allows organizations to deploy different versions of applications from the same repository.

**Where it is used in Production**

Environment-specific deployments.

---

### Question 10

**Question**

Can Argo CD deploy applications from different Git branches?

**Answer**

Yes.

Argo CD can deploy applications from different Git branches by specifying the required Target Revision.

**Explanation**

For example:

- Development → develop branch
- Testing → test branch
- Production → main branch

**Where it is used in Production**

Environment-based deployment strategies.

---

### Question 11

**Question**

Why is Git revision management important in Argo CD?

**Answer**

Git revisions provide version control, repeatable deployments, controlled releases, and easy rollback capabilities.

**Explanation**

Since every deployment corresponds to a Git revision, it is easy to reproduce or revert deployments.

**Where it is used in Production**

Release management and production deployments.

---

### Question 12

**Question**

How does Argo CD know when to deploy a new application version?

**Answer**

Argo CD continuously monitors the configured Git repository and target revision. When it detects a change, it compares the desired state with the cluster and synchronizes the application if required.

**Explanation**

This continuous monitoring is one of the key principles of GitOps.

**Where it is used in Production**

Automated Kubernetes deployments.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

Your development team updates Kubernetes manifests in the `develop` branch, but Argo CD does not deploy the changes. What would you check first?

**Answer**

I would verify whether the Application's Target Revision is configured to monitor the `develop` branch.

**Explanation**

If Argo CD is monitoring a different branch (such as `main`), it will ignore changes made to `develop`.

---

### Scenario 2

**Question**

An application is successfully synchronized but is deployed into the wrong Kubernetes namespace. What is the most likely cause?

**Answer**

The Destination Namespace configured in the Application resource is incorrect.

**Explanation**

Argo CD deploys resources into the namespace specified in the Application configuration.

---

### Scenario 3

**Question**

Argo CD displays "Repository connection failed" while adding a private Git repository. What would you check?

**Answer**

I would verify:

- Repository URL
- Authentication credentials
- Personal Access Token or SSH key
- Repository permissions
- Network connectivity

**Explanation**

Authentication failures are the most common reason private repositories cannot be accessed.

---

### Scenario 4

**Question**

Your organization manages separate development and production Kubernetes clusters. How can the same Git repository deploy to both environments?

**Answer**

Create separate Argo CD Applications with different Destination Clusters and Target Revisions if required.

**Explanation**

Each Application can deploy to a different Kubernetes cluster while using the same repository.

---

### Scenario 5

**Question**

A developer accidentally changes the production Git branch instead of the development branch. What happens if the Production Application monitors that branch?

**Answer**

Argo CD detects the change and deploys the updated manifests to the production cluster.

**Explanation**

Argo CD always follows the configured Target Revision.

---

### Scenario 6

**Question**

Your company wants different teams to deploy applications only to their assigned namespaces. Which Argo CD feature should you use?

**Answer**

Argo CD Projects.

**Explanation**

Projects can restrict accessible repositories, clusters, and namespaces for each team.

---

### Scenario 7

**Question**

A new application is created in Argo CD, but no Kubernetes resources are deployed. What would you verify first?

**Answer**

I would verify:

- Source Repository
- Repository credentials
- Target Revision
- Repository path
- Destination Cluster

**Explanation**

Incorrect source configuration is one of the most common deployment issues.

---

### Scenario 8

**Question**

During an interview, you are asked why Argo CD stores deployment manifests in Git instead of inside Kubernetes. How would you answer?

**Answer**

Git serves as the single source of truth, providing version control, change history, approvals, auditing, and rollback capabilities. Argo CD continuously synchronizes the cluster with the approved Git configuration.

**Explanation**

This approach improves reliability, security, and traceability.

---

### Scenario 9

**Question**

Your manager wants production deployments to always come from the `main` branch while testing deployments come from the `release` branch. Can Argo CD support this?

**Answer**

Yes.

Separate Applications can be configured with different Target Revisions for different environments.

**Explanation**

Branch-based deployment is a common GitOps practice.

---

### Scenario 10

**Question**

Your Git repository contains multiple applications in different folders. How does Argo CD know which application to deploy?

**Answer**

The Application resource specifies the repository **Path**, which tells Argo CD exactly where the Kubernetes manifests or Helm chart for that application are located.

**Explanation**

The repository path allows multiple applications to be managed from a single Git repository without conflict.
