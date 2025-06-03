
## 2. Architecture Constraints

### 2.1 Technical Constraints

- The system will be deployed on **AWS Cloud**, following a **microservices architecture** to ensure scalability, modularity, and ease of maintenance.

- **Tuya Cloud** will be integrated as the **primary IoT device management platform**, handling core capabilities such as device provisioning, connectivity, telemetry, and control. The system will **not replicate Tuya’s functionality**, but instead focus on building **additional services** to support device **location mapping within Buildings, Floors, Areas, and Rooms**.

- **Kubernetes** will serve as the **core container orchestration platform**, with **Amazon EKS (Elastic Kubernetes Service)** used as the runtime environment. This ensures consistent service deployment and scalability.

- The architecture will adopt **cloud-native** and **vendor-neutral patterns** to support future portability across Azure (AKS) and Google Cloud (GKE).

- **GitOps** will be used for **CI/CD**, enabling declarative, version-controlled infrastructure and deployment pipelines.

- Architectural decisions will follow a **cost-optimized strategy**, prioritizing managed services during early stages while maintaining flexibility for cloud-agnostic evolution.

### 2.2 Development Constraints
The project will follow the **Agile methodology**, promoting iterative and incremental development with close collaboration between **business** and **engineering teams**. A **release cycle of two versions per quarter** is planned to ensure **continuous delivery** of features and improvements.

To support Agile practices, a fully automated **CI/CD pipeline** based on the **GitOps** approach will be used to ensure consistent integration, testing, and deployment across environments.

To maintain high code quality and security standards, the following constraints are enforced:

- All backend services, mobile apps, and web UI applications must maintain unit test coverage above 80%.

- SonarQube analysis must report no critical or high-severity issues in the codebase.

- The system must have no critical security vulnerabilities, as identified by automated security scans integrated into the CI pipeline
