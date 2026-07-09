# Storage & Networking Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

Why is storage required in Kubernetes?

**Answer**

Storage is required to persist application data beyond the lifecycle of a Pod.

By default, data stored inside a container is **ephemeral** and is lost when the Pod is deleted or recreated. Kubernetes storage enables applications to retain data across Pod restarts and rescheduling.

**Explanation**

Containers are designed to be temporary. Persistent storage allows stateful applications such as databases and file servers to maintain data independently of Pods.

**Used in Production**

- Databases
- File uploads
- Application logs
- Shared application data

**Common Mistake**

Many candidates assume container storage is permanent. It is deleted when the container or Pod is removed.

---

### Question 2

**Question**

What is a Volume in Kubernetes?

**Answer**

A Volume is a storage resource that is mounted into one or more containers within a Pod.

It allows containers to:

- Share data
- Persist data during the Pod's lifetime
- Store configuration files

**Explanation**

Unlike container filesystems, Volumes remain available even if individual containers inside the Pod restart.

**Used in Production**

- Shared files between containers
- Temporary storage
- Configurations
- Logs

**Common Mistake**

Thinking Volumes survive Pod deletion. Most volume types are removed when the Pod is deleted unless backed by persistent storage.

---

### Question 3

**Question**

What is a Persistent Volume (PV)?

**Answer**

A Persistent Volume (PV) is a cluster-wide storage resource managed by Kubernetes.

It represents actual storage provided by:

- Azure Disk
- AWS EBS
- NFS
- SAN
- Local storage

**Explanation**

A PV exists independently of Pods and can outlive the lifecycle of individual workloads.

**Used in Production**

Persistent storage for databases and stateful applications.

**Common Mistake**

Confusing a PV with a Pod Volume. A PV exists independently of any Pod.

---

### Question 4

**Question**

What is a Persistent Volume Claim (PVC)?

**Answer**

A Persistent Volume Claim (PVC) is a request for storage made by a Pod.

It specifies:

- Required storage size
- Access mode
- Storage Class

**Explanation**

Pods never consume Persistent Volumes directly. Instead, they request storage through PVCs, and Kubernetes binds an appropriate PV.

**Used in Production**

Database storage, persistent application data, shared file systems.

**Common Mistake**

Assuming Pods connect directly to Persistent Volumes.

---

### Question 5

**Question**

How do Persistent Volumes and Persistent Volume Claims work together?

**Answer**

The workflow is:

1. Administrator creates a PV (or uses dynamic provisioning).
2. Application creates a PVC.
3. Kubernetes binds the PVC to a matching PV.
4. Pod mounts the PVC.

**Explanation**

The PVC abstracts the underlying storage implementation, allowing applications to remain portable.

**Used in Production**

Nearly every stateful Kubernetes application.

---

### Question 6

**Question**

What is a StorageClass?

**Answer**

A StorageClass defines how Kubernetes dynamically provisions storage.

It specifies:

- Storage provisioner
- Performance tier
- Reclaim policy
- Volume parameters

**Explanation**

Instead of manually creating Persistent Volumes, Kubernetes automatically creates them when a PVC requests storage.

**Used in Production**

Dynamic storage provisioning in AKS, EKS, GKE, and OpenShift.

**Common Mistake**

Manually creating Persistent Volumes when dynamic provisioning is available.

---

### Question 7

**Question**

What is Pod Networking in Kubernetes?

**Answer**

Pod Networking allows Pods to communicate directly with each other.

Each Pod receives:

- A unique IP address
- Direct network connectivity
- No requirement for NAT between Pods

**Explanation**

Pods communicate using IP addresses regardless of the Worker Node on which they run.

**Used in Production**

Microservice communication.

**Common Mistake**

Thinking Pods on different nodes require port forwarding.

---

### Question 8

**Question**

What is Service Networking?

**Answer**

Service Networking provides stable access to Pods through Kubernetes Services.

Instead of communicating with changing Pod IPs, clients communicate with Service IPs or DNS names.

**Explanation**

Services automatically load balance traffic across healthy backend Pods.

**Used in Production**

Internal APIs, frontend-backend communication, service discovery.

---

### Question 9

**Question**

How does DNS work in Kubernetes?

**Answer**

Kubernetes uses CoreDNS to provide automatic DNS resolution.

Applications access Services using names such as:

```
http://backend-service
```

instead of Pod IP addresses.

**Explanation**

CoreDNS automatically creates DNS records for Services, enabling reliable service discovery.

**Used in Production**

Every Kubernetes cluster.

**Common Mistake**

Hardcoding Pod IP addresses instead of using Service names.

---

### Question 10

**Question**

What are Network Policies in Kubernetes?

**Answer**

Network Policies define rules that control traffic between Pods.

They specify:

- Allowed ingress traffic
- Allowed egress traffic
- Namespace-based communication
- Label-based communication

**Explanation**

Without Network Policies, Pods can typically communicate freely with one another. Policies enable network-level security.

**Used in Production**

Securing communication between applications and databases.

**Common Mistake**

Assuming Network Policies work automatically. They require a compatible CNI plugin.

---

### Question 11

**Question**

What is the difference between a Volume, PV, and PVC?

**Answer**

| Volume | Persistent Volume (PV) | Persistent Volume Claim (PVC) |
|---------|-------------------------|-------------------------------|
| Pod-level storage | Cluster storage resource | Request for storage |
| Usually temporary | Persistent | Consumed by Pods |
| Created with Pod | Managed by Kubernetes | Created by application |

**Explanation**

Volumes are mounted into Pods, PVs provide storage, and PVCs request storage.

---

### Question 12

**Question**

When should you use a Persistent Volume instead of a regular Volume?

**Answer**

Use Persistent Volumes whenever application data must survive Pod deletion or recreation.

Examples:

- Databases
- CMS uploads
- User files
- Application state

Use regular Volumes for temporary data such as cache or shared files within a Pod.

**Explanation**

Persistent Volumes provide long-term storage independent of Pod lifecycle.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

Your MySQL Pod crashes and is recreated. After restart, all database data is missing. What is the most likely cause?

**Answer**

The Pod is using temporary storage instead of a Persistent Volume.

**Explanation**

Without a Persistent Volume and PVC, data stored inside the container is lost when the Pod is recreated.

---

### Scenario 2

**Question**

Your application cannot bind its Persistent Volume Claim. What should you investigate?

**Answer**

Check:

```bash
kubectl get pvc
kubectl describe pvc <pvc-name>
kubectl get pv
kubectl get storageclass
```

Verify:

- Available PV
- StorageClass
- Requested size
- Access mode

**Explanation**

Binding failures usually occur because no matching Persistent Volume exists or the StorageClass configuration is incorrect.

---

### Scenario 3

**Question**

Two application containers running inside the same Pod need to share log files. Which Kubernetes storage feature should you use?

**Answer**

A shared Volume mounted into both containers.

**Explanation**

Containers within the same Pod can share data using a common Volume.

---

### Scenario 4

**Question**

Your frontend application communicates with the backend using Pod IP addresses. After the backend Pod restarts, communication fails. How should this be fixed?

**Answer**

Use a Kubernetes Service instead of Pod IP addresses.

**Explanation**

Services provide stable IP addresses and DNS names regardless of Pod recreation.

---

### Scenario 5

**Question**

Applications in different namespaces should not communicate with each other unless explicitly allowed. Which Kubernetes feature should you implement?

**Answer**

Network Policies.

**Explanation**

Network Policies restrict ingress and egress traffic between Pods and namespaces.

---

### Scenario 6

**Question**

A developer creates a PVC, but no Persistent Volume exists. The cluster supports dynamic provisioning. What happens?

**Answer**

Kubernetes automatically provisions a new Persistent Volume using the appropriate StorageClass.

**Explanation**

Dynamic provisioning eliminates the need for administrators to manually create Persistent Volumes.

---

### Scenario 7

**Question**

Your application cannot resolve the hostname:

```
database-service
```

Which Kubernetes component should you investigate?

**Answer**

CoreDNS.

Useful commands:

```bash
kubectl get pods -n kube-system
kubectl logs -n kube-system <coredns-pod>
```

**Explanation**

CoreDNS provides DNS resolution for Kubernetes Services.

---

### Scenario 8

**Question**

A security audit reveals that every Pod in the cluster can communicate with every other Pod. How would you improve security?

**Answer**

Implement Network Policies to restrict Pod-to-Pod communication.

**Explanation**

By default, Kubernetes networking is generally permissive unless Network Policies are enforced.

---

### Scenario 9

**Question**

A production application requires high-performance SSD storage on Azure Kubernetes Service. Which Kubernetes feature allows developers to request this without manually creating disks?

**Answer**

A StorageClass configured for premium managed disks.

**Explanation**

The StorageClass dynamically provisions storage that meets the application's requirements.

---

### Scenario 10

**Question**

Your StatefulSet deployment is recreated after a node failure, but all application data remains intact. Which Kubernetes storage components made this possible?

**Answer**

- Persistent Volume (PV)
- Persistent Volume Claim (PVC)
- StorageClass (if dynamically provisioned)

**Explanation**

Persistent storage exists independently of Pods, allowing stateful workloads to recover without losing data.
