# Services, Labels & Selectors Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What is a Kubernetes Service, and why is it required?

**Answer**

A Kubernetes Service is an abstraction that provides a stable network endpoint for accessing one or more Pods.

It solves the problem of changing Pod IP addresses by exposing a fixed virtual IP (ClusterIP) and DNS name that clients can use consistently.

**Explanation**

Pods are ephemeral—they can be recreated at any time with new IP addresses. A Service continuously tracks Pods using labels and forwards traffic to healthy Pods.

**Used in Production**

- Exposing web applications
- Internal microservice communication
- Load balancing traffic across Pods

**Common Mistake**

Many candidates think a Service creates Pods. A Service only exposes and load-balances existing Pods.

---

### Question 2

**Question**

What are the different types of Kubernetes Services?

**Answer**

The four primary Service types are:

- **ClusterIP** – Internal communication within the cluster.
- **NodePort** – Exposes the application through a port on every Worker Node.
- **LoadBalancer** – Creates an external cloud load balancer.
- **ExternalName** – Maps a Service to an external DNS name.

**Explanation**

Each Service type is designed for different networking requirements depending on whether traffic originates inside or outside the cluster.

**Used in Production**

- ClusterIP → Internal APIs
- NodePort → Testing and on-premises environments
- LoadBalancer → Internet-facing applications
- ExternalName → External databases and third-party services

---

### Question 3

**Question**

What is a ClusterIP Service?

**Answer**

ClusterIP is the default Kubernetes Service type.

It exposes an application only inside the Kubernetes cluster using an internal virtual IP address.

**Explanation**

Pods within the cluster communicate using the Service's DNS name instead of Pod IP addresses.

**Used in Production**

Communication between:

- Frontend and Backend
- Backend and Database
- Internal microservices

**Common Mistake**

Thinking ClusterIP can be accessed from outside the cluster.

---

### Question 4

**Question**

What is a NodePort Service?

**Answer**

A NodePort Service exposes an application through a fixed port on every Worker Node.

External users can access the application using:

```
<Node-IP>:<NodePort>
```

**Explanation**

Kubernetes opens a port (typically between 30000–32767) on each node and forwards traffic to the corresponding Pods.

**Used in Production**

- Development
- Testing
- Small on-premises Kubernetes clusters

**Common Mistake**

Using NodePort directly for production internet-facing applications instead of a LoadBalancer or Ingress.

---

### Question 5

**Question**

What is a LoadBalancer Service?

**Answer**

A LoadBalancer Service exposes an application externally by provisioning a cloud load balancer.

**Explanation**

Cloud providers such as Azure, AWS, and GCP automatically create a load balancer that distributes traffic across healthy Pods.

**Used in Production**

Public-facing applications such as:

- Web applications
- APIs
- Customer portals

**Common Mistake**

Expecting LoadBalancer to work automatically on bare-metal Kubernetes clusters without additional software like MetalLB.

---

### Question 6

**Question**

What is an ExternalName Service?

**Answer**

An ExternalName Service maps a Kubernetes Service to an external DNS name.

Example:

```
database.company.com
```

**Explanation**

Instead of forwarding traffic to Pods, Kubernetes returns a DNS CNAME record pointing to the external resource.

**Used in Production**

Connecting applications to:

- External databases
- SaaS services
- Third-party APIs

**Common Mistake**

Assuming ExternalName routes traffic through Kubernetes Pods.

---

### Question 7

**Question**

What is Service Discovery in Kubernetes?

**Answer**

Service Discovery allows applications to communicate using Service names instead of IP addresses.

Example:

```
http://backend-service
```

instead of

```
10.244.2.15
```

**Explanation**

Kubernetes automatically creates DNS records for Services using CoreDNS.

Applications continue working even if Pod IP addresses change.

**Used in Production**

Microservice communication.

**Common Mistake**

Hardcoding Pod IP addresses in application configuration.

---

### Question 8

**Question**

What are Labels in Kubernetes?

**Answer**

Labels are key-value pairs attached to Kubernetes objects.

Example:

```yaml
labels:
  app: nginx
  environment: production
```

**Explanation**

Labels help organize, identify, and group Kubernetes resources.

**Used in Production**

- Service selection
- Deployments
- Monitoring
- Resource filtering

**Common Mistake**

Confusing Labels with Annotations.

---

### Question 9

**Question**

What are Selectors in Kubernetes?

**Answer**

Selectors identify Kubernetes objects based on Labels.

Example:

```yaml
selector:
  app: nginx
```

**Explanation**

Services use Selectors to determine which Pods should receive incoming traffic.

Deployments also use Selectors to manage Pods.

**Used in Production**

Connecting:

- Services to Pods
- ReplicaSets to Pods
- Deployments to ReplicaSets

**Common Mistake**

If Labels and Selectors do not match, the Service will have no backend Pods.

---

### Question 10

**Question**

What are Annotations in Kubernetes?

**Answer**

Annotations are key-value pairs used to store metadata that is not used for selecting objects.

Example:

```yaml
annotations:
  owner: DevOps-Team
  backup: daily
```

**Explanation**

Unlike Labels, Annotations are intended for tools, automation, documentation, and integrations.

**Used in Production**

- Ingress configuration
- Monitoring integrations
- CI/CD metadata
- Backup policies

**Common Mistake**

Using Annotations instead of Labels for object selection.

---

### Question 11

**Question**

What is the difference between Labels and Annotations?

**Answer**

| Labels | Annotations |
|---------|-------------|
| Used for object selection | Not used for selection |
| Small identifying metadata | Large descriptive metadata |
| Used by Services and Deployments | Used by tools and automation |
| Supports filtering | Does not support filtering |

**Explanation**

Labels identify resources, while Annotations provide additional information.

**Used in Production**

Both are commonly used together.

---

### Question 12

**Question**

How do Services use Labels and Selectors?

**Answer**

A Service selects Pods whose Labels match its Selector.

Example:

Pod:

```yaml
labels:
  app: frontend
```

Service:

```yaml
selector:
  app: frontend
```

The Service automatically routes traffic to all matching Pods.

**Explanation**

This dynamic association ensures Services continue functioning even when Pods are recreated.

**Used in Production**

Every Kubernetes Deployment that exposes Pods through a Service.

**Common Mistake**

If the labels don't match exactly, the Service will not forward traffic to any Pods.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

A Service has been created successfully, but no application traffic reaches the Pods. What would you check first?

**Answer**

Verify that the Service Selector matches the Pod Labels.

Commands:

```bash
kubectl get svc
kubectl describe svc <service-name>
kubectl get pods --show-labels
```

**Explanation**

The most common reason is a mismatch between Labels and Selectors, resulting in zero backend endpoints.

---

### Scenario 2

**Question**

Your frontend application needs to communicate with a backend API inside the cluster. Which Service type should you choose?

**Answer**

**ClusterIP**

**Explanation**

ClusterIP provides secure internal communication without exposing the backend externally.

---

### Scenario 3

**Question**

A company wants to expose its web application to internet users on Azure Kubernetes Service (AKS). Which Service type should you use?

**Answer**

**LoadBalancer**

**Explanation**

LoadBalancer provisions an Azure Load Balancer that distributes traffic to backend Pods.

---

### Scenario 4

**Question**

Your application works correctly inside the cluster but cannot be accessed from outside. Which Service types could solve this?

**Answer**

Use:

- NodePort
- LoadBalancer
- Ingress (commonly used with ClusterIP Services)

**Explanation**

ClusterIP only supports internal communication.

---

### Scenario 5

**Question**

Your Service shows no Endpoints when you run:

```bash
kubectl get endpoints
```

What is the most likely cause?

**Answer**

The Service Selector does not match the Pod Labels.

**Explanation**

Without matching Labels, Kubernetes cannot associate Pods with the Service.

---

### Scenario 6

**Question**

Your application needs to connect to an external corporate database using a Kubernetes Service. Which Service type would you choose?

**Answer**

**ExternalName**

**Explanation**

ExternalName maps the Service to an external DNS name without requiring Kubernetes-managed Pods.

---

### Scenario 7

**Question**

You accidentally changed a Pod Label from:

```yaml
app: frontend
```

to

```yaml
app: web
```

What happens?

**Answer**

The Service using the selector:

```yaml
app: frontend
```

will stop routing traffic to that Pod.

**Explanation**

Services only forward traffic to Pods with matching Labels.

---

### Scenario 8

**Question**

A developer hardcoded Pod IP addresses in the application configuration. Why is this a bad practice?

**Answer**

Pod IP addresses change whenever Pods are recreated.

Applications should communicate using Kubernetes Service names.

**Explanation**

Service Discovery provides stable DNS names regardless of Pod lifecycle events.

---

### Scenario 9

**Question**

Your monitoring team wants to store deployment ownership information for each application without affecting Service selection. Should you use Labels or Annotations?

**Answer**

Use **Annotations**.

**Explanation**

Ownership information is metadata and should not be used for resource selection.

---

### Scenario 10

**Question**

A LoadBalancer Service is created successfully in a cloud environment, but traffic still does not reach the application Pods. What components would you investigate?

**Answer**

Check:

- Service configuration
- Pod Labels
- Service Selectors
- Service Endpoints
- Pod readiness
- Network Policies
- Application listening port

Useful commands:

```bash
kubectl describe svc <service-name>
kubectl get endpoints
kubectl get pods --show-labels
kubectl describe pod <pod-name>
```

**Explanation**

A cloud load balancer can only forward traffic to healthy Service endpoints. Missing endpoints or unhealthy Pods are common production causes.
