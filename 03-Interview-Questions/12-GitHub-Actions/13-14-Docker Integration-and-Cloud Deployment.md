# Docker Integration & Cloud Deployment Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

How do you build a Docker image using GitHub Actions?

**Answer**

A Docker image is built by adding a workflow step that executes the Docker build command after checking out the repository.

Example:

```yaml
- name: Build Docker Image
  run: docker build -t myapp:latest .
```

**Explanation**

The workflow uses the source code in the repository to create a Docker image. This image can then be tested locally on the runner or pushed to a container registry.

**Where it is used in Production**

- Containerized application builds
- CI/CD pipelines
- Microservices deployments

**Common Mistake**

Many candidates forget that the workflow must first check out the repository before the Docker build command can access the Dockerfile.

---

### Question 2

**Question**

Why do you need to log in to a Container Registry before pushing Docker images?

**Answer**

Authentication is required to verify that the workflow has permission to push images to the registry.

Examples of registries include:

- GitHub Container Registry (GHCR)
- Azure Container Registry (ACR)
- Docker Hub
- Amazon ECR

**Explanation**

Without authentication, Docker cannot upload images because registries reject anonymous push requests.

**Where it is used in Production**

Every CI/CD pipeline that publishes Docker images.

---

### Question 3

**Question**

How do you push a Docker image from GitHub Actions?

**Answer**

After successfully building the image and authenticating with the registry, the workflow executes the Docker push command.

Example:

```yaml
docker push myregistry.azurecr.io/myapp:latest
```

**Explanation**

The image is uploaded to the container registry where deployment platforms can retrieve it.

**Where it is used in Production**

- AKS deployments
- Kubernetes clusters
- Azure App Service for Containers

---

### Question 4

**Question**

Why is a Container Registry used in CI/CD pipelines?

**Answer**

A Container Registry stores versioned Docker images so deployment platforms can pull and run them.

**Explanation**

Instead of rebuilding an application on every server, deployments pull a tested image from the registry.

**Where it is used in Production**

- Azure Container Registry
- Docker Hub
- GitHub Container Registry
- Amazon ECR

---

### Question 5

**Question**

How does GitHub Actions authenticate with Azure?

**Answer**

GitHub Actions typically authenticates using an Azure Service Principal stored as GitHub Secrets.

**Explanation**

The workflow securely logs in to Azure using credentials without exposing passwords in the workflow file.

**Where it is used in Production**

All Azure deployment workflows.

**Common Mistake**

Candidates often hardcode Azure credentials instead of storing them as GitHub Secrets.

---

### Question 6

**Question**

Why are GitHub Secrets used for Azure authentication?

**Answer**

GitHub Secrets securely store sensitive credentials such as:

- Client ID
- Client Secret
- Tenant ID
- Subscription ID

**Explanation**

Secrets are encrypted and hidden from workflow logs, improving security.

**Where it is used in Production**

All production deployment pipelines.

---

### Question 7

**Question**

How do you deploy an application to Azure using GitHub Actions?

**Answer**

The workflow authenticates with Azure and executes deployment steps using Azure actions or Azure CLI commands.

**Explanation**

GitHub Actions automates deployment immediately after successful builds and tests.

**Where it is used in Production**

- Azure Web Apps
- Azure App Service
- Azure Virtual Machines
- Azure Kubernetes Service

---

### Question 8

**Question**

What is Azure App Service, and why is it commonly used with GitHub Actions?

**Answer**

Azure App Service is a managed platform for hosting web applications without managing infrastructure.

**Explanation**

GitHub Actions integrates directly with Azure App Service, enabling automated deployments after successful builds.

**Where it is used in Production**

- ASP.NET applications
- Node.js applications
- Java applications
- Python applications

---

### Question 9

**Question**

How does GitHub Actions deploy applications to Azure Kubernetes Service (AKS)?

**Answer**

The workflow authenticates with Azure, connects to the AKS cluster, and deploys Kubernetes manifests or Helm charts.

**Explanation**

The deployment updates Kubernetes resources using commands such as `kubectl apply`.

**Where it is used in Production**

Containerized microservices running on AKS.

---

### Question 10

**Question**

What is the typical CI/CD workflow for deploying Docker applications to Azure?

**Answer**

A common workflow is:

1. Checkout repository
2. Build Docker image
3. Run tests
4. Login to Azure
5. Login to Container Registry
6. Push Docker image
7. Deploy to Azure App Service or AKS

**Explanation**

This workflow ensures that only validated container images are deployed.

**Where it is used in Production**

Enterprise container deployment pipelines.

---

### Question 11

**Question**

Why should Docker images be tagged before pushing them to a registry?

**Answer**

Tags uniquely identify image versions, making deployments reproducible and simplifying rollbacks.

Examples:

- `v1.0`
- `v2.1`
- `latest`
- Git commit SHA

**Explanation**

Versioned images allow teams to deploy or roll back to specific application versions.

**Where it is used in Production**

Every container-based deployment pipeline.

---

### Question 12

**Question**

What are the benefits of integrating GitHub Actions with Azure?

**Answer**

Benefits include:

- Automated deployments
- Faster releases
- Consistent deployments
- Secure authentication
- Reduced manual effort

**Explanation**

GitHub Actions provides end-to-end CI/CD automation for Azure-hosted applications.

**Where it is used in Production**

Cloud-native DevOps environments using Microsoft Azure.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

Your workflow builds a Docker image successfully but fails to push it to Azure Container Registry with an authentication error. What would you check?

**Answer**

I would verify:

- Azure login
- Registry credentials
- GitHub Secrets
- Registry permissions
- Docker login step

**Explanation**

Authentication failures are usually caused by incorrect credentials or missing registry login.

---

### Scenario 2

**Question**

Your deployment to Azure App Service fails even though the application builds successfully. How would you troubleshoot it?

**Answer**

I would verify:

- Azure authentication
- App Service name
- Resource group
- Deployment logs
- Publish profile or Service Principal permissions

**Explanation**

Most deployment failures are caused by incorrect Azure configuration rather than build issues.

---

### Scenario 3

**Question**

Your AKS deployment completes successfully, but the application is still running the old version. What would you investigate?

**Answer**

I would verify:

- Image tag
- Image pull policy
- Deployment rollout status
- Updated Kubernetes manifest
- Successful image push

**Explanation**

AKS often continues using an old image if the image tag was not updated or the image was not pulled again.

---

### Scenario 4

**Question**

A workflow pushes Docker images with the `latest` tag only. Your team wants the ability to roll back to previous versions. What would you recommend?

**Answer**

I would tag images using version numbers or Git commit SHAs in addition to `latest`.

**Explanation**

Unique tags make deployments traceable and enable reliable rollbacks.

---

### Scenario 5

**Question**

Your workflow fails during the Docker build step because it cannot find the Dockerfile. What is the likely cause?

**Answer**

The repository was not checked out, or the Dockerfile path is incorrect.

**Explanation**

Docker can build an image only if it can locate the Dockerfile in the specified build context.

---

### Scenario 6

**Question**

Your security team does not allow Azure credentials to be stored directly in workflow files. How would you address this?

**Answer**

I would store all Azure credentials as GitHub Secrets or use OpenID Connect (OIDC) federation where supported.

**Explanation**

Secrets and OIDC provide secure authentication without exposing credentials in source code.

---

### Scenario 7

**Question**

Your GitHub Actions workflow successfully pushes the Docker image, but the deployment job cannot pull it from the registry. What would you check?

**Answer**

I would verify:

- Registry permissions
- Image name and tag
- Registry authentication
- AKS or App Service pull permissions

**Explanation**

Deployment services require permission to access private container registries.

---

### Scenario 8

**Question**

Your team wants every successful merge into the `main` branch to automatically build a Docker image and deploy it to Azure App Service. How would you design the workflow?

**Answer**

I would configure the workflow to:

1. Trigger on pushes to `main`
2. Checkout the repository
3. Build the Docker image
4. Run tests
5. Authenticate with Azure
6. Push the image to Azure Container Registry
7. Deploy the latest image to Azure App Service

**Explanation**

This provides a fully automated CI/CD pipeline with minimal manual intervention.

---

### Scenario 9

**Question**

A deployment to AKS fails because Kubernetes cannot pull the Docker image. What are the most common causes?

**Answer**

I would check:

- Incorrect image name
- Wrong image tag
- Missing registry authentication
- Image was never pushed
- AKS lacks permission to access the registry

**Explanation**

Image pull failures are usually related to registry access or incorrect image references.

---

### Scenario 10

**Question**

Your manager asks you to improve deployment reliability for containerized applications using GitHub Actions. What best practices would you recommend?

**Answer**

I would recommend:

- Version Docker images with unique tags
- Store credentials in GitHub Secrets or use OIDC
- Run automated tests before deployment
- Push images to a trusted container registry
- Deploy only after successful builds
- Monitor deployment status and enable rollback procedures

**Explanation**

These practices reduce deployment failures, improve traceability, and make production releases safer and more reliable.
