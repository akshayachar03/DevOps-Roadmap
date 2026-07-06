# Azure Storage Services

## Definition

- Azure Storage is a Microsoft-managed cloud storage service used to store structured and unstructured data.
- It provides highly available, scalable, secure, and durable storage for applications and services.
- Azure Storage can be accessed from anywhere over the internet or privately within Azure.

---

## Why is it used?

- Store application data.
- Store files, images, videos, and backups.
- Host static websites.
- Store virtual machine disks.
- Store logs and big data.
- Share files across multiple virtual machines.

---

## Key Features

- Highly available with built-in redundancy.
- Scalable to store petabytes of data.
- Durable with automatic data replication.
- Secure using encryption and access controls.
- Supports REST APIs, SMB, NFS, and HTTPS.
- Supports lifecycle management for cost optimization.

---

## Advantages

- Fully managed by Microsoft.
- Pay only for storage used.
- Supports multiple storage types.
- Highly secure and reliable.
- Global accessibility.
- Easy integration with Azure services.

---

## Disadvantages

- Storage costs increase with data growth.
- Different storage services require proper selection.
- Data retrieval from archive tier may take time.

---

## Components

### Storage Account

- The top-level Azure resource that contains storage services.

### Storage Types

- Blob Storage
- File Storage
- Queue Storage
- Table Storage
- Disk Storage

### Access Tiers

- Hot
- Cool
- Archive

---

## Workflow

```text
Create Storage Account
        ↓
Choose Storage Service
        ↓
Upload Data
        ↓
Configure Security
        ↓
Applications Access Storage
```

---

## Real-world Example

A company stores website images in Blob Storage, shares documents using Azure Files, stores VM disks in Managed Disks, and saves application logs in Table Storage.

---

## Interview Tip

"Azure Storage is a scalable and durable cloud storage platform that provides multiple storage services for different types of data."

---

## Quick Revision

- Azure Storage is fully managed.
- Data is stored inside a Storage Account.
- Multiple storage services are available.
- Supports redundancy and encryption.
- Access tiers reduce storage cost.
- Suitable for structured and unstructured data.

---

## Important Interview Questions

1. What is Azure Storage?
2. What is a Storage Account?
3. Why do we use Azure Storage?
4. What are Azure Storage access tiers?
5. How does Azure Storage ensure high availability?

---

# Types of Azure Storage Services

## Definition

- Azure provides different storage services based on the type of data being stored.
- Each storage service is optimized for a specific workload.

---

## Why is it used?

- Store different types of application data.
- Improve performance.
- Reduce storage costs.
- Support various workloads.
- Simplify application design.

---

## Types of Azure Storage

| Storage Service | Stores | Common Use Case |
|-----------------|--------|-----------------|
| Blob Storage | Unstructured data | Images, videos, backups |
| Azure Files | Shared files | File sharing between VMs |
| Queue Storage | Messages | Communication between applications |
| Table Storage | NoSQL structured data | Logs, metadata, user profiles |
| Azure Managed Disks | VM disks | Operating system and data disks |

---

## Key Features

### Blob Storage

- Stores unstructured data.
- Supports Hot, Cool, and Archive tiers.
- Accessible through HTTP/HTTPS.

### Azure Files

- Managed file shares.
- Supports SMB and NFS protocols.
- Can be mounted on Windows and Linux.

### Queue Storage

- Stores millions of messages.
- Supports asynchronous communication.
- Improves application reliability.

### Table Storage

- NoSQL key-value storage.
- Stores semi-structured data.
- Fast and cost-effective.

### Azure Managed Disks

- Storage for Azure Virtual Machines.
- Managed automatically by Azure.
- Supports SSD and HDD options.

---

## Advantages

- Multiple storage options.
- High scalability.
- Secure.
- Cost-effective.
- Easy Azure integration.

---

## Disadvantages

- Each storage service serves a specific purpose.
- Choosing the wrong storage type can affect performance.

---

## Workflow

```text
Application
     ↓
Choose Storage Type
     ↓
Store Data
     ↓
Retrieve Data When Needed
```

---

## Real-world Example

An e-commerce application:

- Product images → Blob Storage
- Shared invoices → Azure Files
- Order processing → Queue Storage
- Customer details → Table Storage
- Web server OS → Managed Disks

---

## Interview Tip

"Azure provides different storage services because different workloads require different storage solutions."

---

## Quick Revision

- Blob → Unstructured data.
- Files → Shared file storage.
- Queue → Messaging service.
- Table → NoSQL data.
- Managed Disk → VM storage.

---

## Important Interview Questions

1. What are the different Azure Storage services?
2. What is Blob Storage used for?
3. When should Azure Files be used?
4. What is Queue Storage?
5. What is the difference between Blob Storage and Azure Files?

---

# Azure Blob Storage

## Definition

- Azure Blob Storage is an object storage service for storing large amounts of unstructured data.
- It is commonly used for images, videos, backups, logs, and documents.

---

## Why is it used?

- Store files of any size.
- Host static website content.
- Store backups.
- Store multimedia files.
- Store application logs.

---

## Key Features

- Supports Hot, Cool, and Archive tiers.
- Highly scalable.
- Secure access using SAS and RBAC.
- Supports versioning.
- Lifecycle management.

---

## Advantages

- Low-cost storage.
- Highly durable.
- Easy internet access.
- Supports massive data.

---

## Disadvantages

- Not suitable for shared file access.
- Archive retrieval is slow.

---

## Components

### Storage Account

- Contains Blob Storage.

### Container

- Similar to a folder.

### Blob

- Individual file stored inside a container.

### Blob Types

- Block Blob
- Append Blob
- Page Blob

---

## Workflow

```text
Storage Account
      ↓
Container
      ↓
Blob (Image, Video, File)
```

---

## Real-world Example

A streaming company stores movie files in Blob Storage for users to access online.

---

## Interview Tip

"Blob Storage is Azure's object storage service for unstructured data like images, videos, and backups."

---

## Quick Revision

- Object storage.
- Stores unstructured data.
- Uses Containers.
- Supports access tiers.
- Highly scalable.

---

## Important Interview Questions

1. What is Blob Storage?
2. What are Blob access tiers?
3. What are Blob types?
4. What is a Blob Container?
5. When should Blob Storage be used?

---

# Azure Files

## Definition

- Azure Files is a managed cloud file-sharing service.
- It provides shared file storage using SMB and NFS protocols.

---

## Why is it used?

- Share files between virtual machines.
- Replace on-premises file servers.
- Store shared application files.
- Lift-and-shift legacy applications.

---

## Key Features

- SMB and NFS support.
- Managed file shares.
- High availability.
- Azure Backup integration.
- Azure File Sync support.

---

## Advantages

- Easy file sharing.
- No file server maintenance.
- Secure access.
- Cross-platform support.

---

## Disadvantages

- More expensive than Blob Storage for large object storage.
- Not designed for object storage.

---

## Workflow

```text
Storage Account
      ↓
File Share
      ↓
Windows/Linux VM
```

---

## Real-world Example

Multiple application servers share configuration files using Azure Files.

---

## Interview Tip

"Azure Files provides managed network file shares that can be accessed from multiple machines simultaneously."

---

## Quick Revision

- Managed file sharing.
- Supports SMB and NFS.
- Shared by multiple VMs.
- Azure File Sync available.
- Suitable for lift-and-shift applications.

---

## Important Interview Questions

1. What is Azure Files?
2. Which protocols does Azure Files support?
3. What is Azure File Sync?
4. When should Azure Files be used?
5. How is Azure Files different from Blob Storage?

---

# Azure Queue Storage

## Definition

- Azure Queue Storage is a messaging service that stores messages between applications.
- It enables asynchronous communication between different components.

---

## Why is it used?

- Decouple applications.
- Improve scalability.
- Process background jobs.
- Improve application reliability.

---

## Key Features

- Stores millions of messages.
- Supports REST API.
- Highly available.
- Reliable message delivery.

---

## Advantages

- Simple messaging.
- Low cost.
- Highly scalable.
- Improves application performance.

---

## Disadvantages

- Only text-based messages.
- Limited message size.

---

## Workflow

```text
Application A
      ↓
Queue Storage
      ↓
Application B
```

---

## Real-world Example

An online shopping application stores order messages in Queue Storage for background order processing.

---

## Interview Tip

"Queue Storage enables asynchronous communication between applications."

---

## Quick Revision

- Message queue.
- Supports asynchronous processing.
- Reliable messaging.
- Scalable.
- Used in distributed applications.

---

## Important Interview Questions

1. What is Queue Storage?
2. Why do we use Queue Storage?
3. How does Queue Storage improve scalability?
4. What type of data does Queue Storage store?
5. Give a real-world example of Queue Storage.

---

# Azure Table Storage

## Definition

- Azure Table Storage is a NoSQL key-value storage service.
- It stores large amounts of structured or semi-structured data.

---

## Why is it used?

- Store metadata.
- Store logs.
- Store user profiles.
- Store IoT data.

---

## Key Features

- NoSQL storage.
- Fast lookup using Partition Key and Row Key.
- Highly scalable.
- Low-cost storage.

---

## Advantages

- Fast performance.
- Highly scalable.
- Cost-effective.
- Simple schema.

---

## Disadvantages

- Limited querying compared to relational databases.
- No joins or complex relationships.

---

## Components

### Partition Key

- Groups related data.

### Row Key

- Unique identifier within a partition.

---

## Workflow

```text
Application
      ↓
Table
      ↓
Partition Key
      ↓
Row Key
```

---

## Real-world Example

An IoT application stores millions of sensor readings in Table Storage.

---

## Interview Tip

"Table Storage is a NoSQL service optimized for storing large amounts of structured data."

---

## Quick Revision

- NoSQL storage.
- Uses Partition Key.
- Uses Row Key.
- Highly scalable.
- Low cost.

---

## Important Interview Questions

1. What is Azure Table Storage?
2. What is a Partition Key?
3. What is a Row Key?
4. When should Table Storage be used?
5. How is Table Storage different from SQL Database?

---

# Azure Storage Use Cases

## Definition

- Different Azure Storage services are designed for different business requirements and workloads.

---

## Common Use Cases

| Requirement | Recommended Storage |
|-------------|---------------------|
| Images, Videos, Backups | Blob Storage |
| Shared File Server | Azure Files |
| Virtual Machine OS Disk | Managed Disks |
| Background Processing | Queue Storage |
| Application Logs | Table Storage |
| Static Website Hosting | Blob Storage |
| Disaster Recovery Backups | Blob Storage |
| Shared Application Files | Azure Files |
| Metadata Storage | Table Storage |
| Large Object Storage | Blob Storage |

---

## Real-world Architecture

```text
Users
   ↓
Web Application
   ├── Blob Storage (Images)
   ├── Azure Files (Documents)
   ├── Queue Storage (Orders)
   ├── Table Storage (Logs)
   └── Managed Disks (VM OS)
```

---

## Interview Tip

"Choosing the correct Azure Storage service depends on the type of data and application requirement."

---

## Quick Revision

- Blob → Images, videos, backups.
- Files → Shared file server.
- Queue → Messaging.
- Table → NoSQL data.
- Managed Disk → Azure VM storage.

---

## Important Interview Questions

1. Which Azure Storage service would you use for images?
2. Which service is best for shared file storage?
3. Which service is used for asynchronous messaging?
4. Which storage is used by Azure Virtual Machines?
5. How do you choose the right Azure Storage service?
