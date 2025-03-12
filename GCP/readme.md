# Google Cloud Platform (GCP) IAM & GCS FAQ

## GCP IAM

### What is the difference between primitive roles, predefined roles, and custom roles in IAM?
- **Primitive roles**: Basic roles (Owner, Editor, Viewer) that apply across all resources in a project.
- **Predefined roles**: Google-managed roles tailored for specific services with granular permissions.
- **Custom roles**: User-defined roles with specific permissions to meet unique access requirements.

### What is resource hierarchy in GCP?
- GCP organizes resources in a hierarchy: **Organization > Folders > Projects > Resources**.
- This structure helps with access control, policy enforcement, and billing.

### What is the hierarchy of IAM policies?
- IAM policies follow the GCP resource hierarchy: **Organization > Folder > Project > Resource**.
- Policies applied at a higher level (e.g., organization) are inherited by lower levels (e.g., projects, resources).

### How do you audit and monitor access to resources in IAM?
- Use **Cloud Audit Logs** to track user actions.
- Use **Cloud Asset Inventory** for visibility into IAM policies.
- Use **Cloud Monitoring & Logging** to detect suspicious activity.

### What is the difference between a service account and a user account?
- **User account**: Represents an individual user with Google authentication.
- **Service account**: Represents an application or workload that needs to interact with GCP services.

### How does Google Cloud IAM integrate with other security and identity management tools?
- Integrates with **Cloud Identity**, **Google Workspace**, **Active Directory**, and **OAuth/OpenID**.
- Supports **IAM Conditions**, **VPC Service Controls**, and **Security Command Center**.

### How do you troubleshoot access issues in IAM?
- Check **IAM Policy Analyzer**.
- Use **Cloud Audit Logs** to track permission changes.
- Validate policies using **gcloud CLI** or **Cloud Console**.

### How do you enforce conditional access to GCP resources using IAM?
- Use **IAM Conditions** to apply access based on time, IP address, or resource attributes.

### Explain different basic roles in GCP IAM.
- **Owner**: Full control over resources, including billing.
- **Editor**: Modify resources but cannot manage IAM or billing.
- **Viewer**: Read-only access to resources.

---

## GCP GCS (Google Cloud Storage)

### What is GCS? What are the key features and benefits of GCS?
- GCS is an object storage service for scalable, durable, and secure storage.
- Features: **Automatic redundancy, lifecycle management, fine-grained access control, and integration with GCP services**.

### What are the storage classes available in GCS? Explain each class and its use cases.
- **Standard**: Frequently accessed data.
- **Nearline**: Infrequently accessed data (~30-day access).
- **Coldline**: Rarely accessed data (~90-day access).
- **Archive**: Long-term storage (~365-day access).

### How is data organized in GCS?
- Data is stored in **buckets**, and within buckets, data is structured as **objects**.

### How can you access GCS? What are the different methods available?
- **Google Cloud Console**
- **gcloud CLI**
- **Cloud Storage Client Libraries**
- **REST API**

### What is the difference between a bucket and an object in GCS?
- **Bucket**: Container for objects with storage class and location settings.
- **Object**: Data unit stored in a bucket.

### How do you control access to objects stored in GCS?
- **IAM policies** for granular access.
- **Bucket-level policies**.
- **Object ACLs (Access Control Lists)**.

### Explain the concept of object lifecycle management in GCS.
- Automates object retention and deletion based on age, storage class, or conditions.

### How can you transfer data to and from GCS?
- **gsutil rsync/cp** for command-line transfer.
- **Storage Transfer Service** for scheduled transfers.
- **Cloud Storage FUSE** for mounting buckets as file systems.

### What is the difference between regional and multi-regional storage in GCS?
- **Regional**: Stored in one region (low latency, good for compute workloads).
- **Multi-regional**: Stored across multiple regions for high availability.

### Can you use GCS for hosting static websites? How?
- Yes, by enabling **public access** and setting up an **index.html**.
- Use **Cloud CDN** to enhance performance.

### How does GCS ensure durability and availability of data?
- Uses automatic redundancy across multiple locations.
- Offers **99.999999999% (11 nines) durability**.

### How do you monitor and analyze storage usage in GCS?
- **Cloud Monitoring & Logging**
- **Storage Insights & Object Analytics**

### Explain the process of data encryption in GCS.
- **Google-managed encryption (default)**
- **Customer-managed encryption keys (CMEK)**
- **Customer-supplied encryption keys (CSEK)**

### What is the difference between Nearline, Coldline, and Archive storage classes in GCS?
- **Nearline**: Access once a month (~30 days retention required).
- **Coldline**: Access once a quarter (~90 days retention required).
- **Archive**: Access once a year (~365 days retention required).

### How can you configure data versioning and retention policies in GCS?
- **Enable object versioning** to retain deleted/overwritten objects.
- **Set lifecycle policies** to auto-delete or transition objects.

### Can you share data stored in GCS with other users or projects?
- Yes, using **IAM roles, signed URLs, and ACLs**.

### What are signed URLs in GCS, and how can they be used?
- **Temporary URLs** that grant time-limited access to objects.
- Useful for **secure file sharing** without IAM roles.

### How do you transfer large amounts of data to GCS efficiently?
- Use **Storage Transfer Service** for large-scale migration.
- Use **gsutil -m** for parallel uploads.

### Can you integrate GCS with other GCP services? Provide some examples.
- **BigQuery** for data analysis.
- **Cloud Functions** for event-driven automation.
- **Vertex AI** for ML model storage.

---
This document serves as a comprehensive FAQ guide for GCP IAM and GCS-related queries.