## 9. Architecture Decisions

This section outlines key architectural decisions made in the Smarthome IoT system, focusing on core platform and technology choices. The documented topics include **container orchestration** strategy,  **API gateway** deployment and **database selection**.

### 9.1 EKS for container orchestration

Although the Smarthome IoT system is primarily deployed on AWS, the architectural vision follows **cloud-native principles**, aiming for **portability across multiple cloud providers and on-premise environments**. To balance **cloud-agnostic flexibility** with **operational efficiency**, the team selected **Amazon EKS** as the container orchestration platform.

EKS provides a **fully managed Kubernetes environment**, enabling the system to benefit from standardized tooling, ecosystem compatibility, and scalability—while offloading control plane management to AWS. This approach aligns with both **cloud-native best practices** and the need to reduce operational burden without locking the system into a single proprietary deployment model.

### 9.2 Kong API Gateway inside EKS instead of using AWS API Gateway

The Smarthome IoT system uses a **centralized authentication and authorization mechanism** based on dynamic policy rules, as described in Section 8.1. To support this across microservices deployed in EKS, the team evaluated two API gateway options: **Kong API Gateway** and **AWS API Gateway**.

**Considered Options**<br>
- **Option 1: Kong API Gateway**
  - Deployed **inside the Kubernetes cluster** using the Kubernetes Gateway API model
  - Fully **cloud-native** and portable across environments
  - Leverages the **Kong OIDC plugin** to integrate with **AWS Cognito** for **authentication**
  - Supports development of **custom Kong plugins (in Lua)** to connect with the **User Service** for enforcing **authorization policies** based on dynamic rules

- **Option 2: AWS API Gateway**
  - Fully managed AWS service, deployed **outside the Kubernetes cluster** as a **Private REST API**
  - Requires **integration with Lambda authorizers** to enforce custom policies, making **dynamic authorization logic harder to implement**
  - Less aligned with **cloud-native and on-prem portability goals**

**Decision**<br>
**Kong API Gateway** was selected for its **Kubernetes-native integration, extensibility**, and **alignment with the system’s cloud-native and multi-cloud vision**. Deploying Kong within EKS allows tighter integration with internal services, more flexible control over routing and security, and consistent behavior across all environments.

### 9.3 MongoDB vs Aurora PostgreSQL

The Smarthome IoT system is designed to manage **millions of IoT devices** deployed across buildings, with each device containing metadata and telemetry that may **evolve over time**. As the system grows, the underlying database must support **schema flexibility, horizontal scalability**, and **high write throughput**.

**Amazon Aurora (PostgreSQL-compatible)** is a powerful managed relational database that supports JSON data types and offers strong **cloud-native capabilities** through its PostgreSQL foundation. However, relational databases like Aurora introduce limitations when handling:

- **Flexible or evolving schemas**
- **High-volume write operations**
- **Large-scale document-based datasets**

In contrast, **MongoDB** (document-based NoSQL) is designed to handle such use cases more naturally. Its schema-less model supports frequent data shape changes, and it can scale horizontally to accommodate high write rates and growing data volumes.

**Decision**<br>
To meet the demands of the Smarthome IoT platform—particularly around **flexibility, scalability**, and **performance under large-scale workloads—MongoDB** was selected as the preferred data model. For AWS deployments, the system uses **Amazon DocumentDB**, a managed MongoDB-compatible service, to reduce operational overhead while maintaining compatibility with cloud infrastructure
