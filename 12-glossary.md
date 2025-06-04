## 12. Glossary

Term | Definition
| -- | --|
IoT (Internet of Things) | A network of physical devices embedded with sensors, software, and connectivity that enable them to collect and exchange data.
EKS (Elastic Kubernetes Service) | AWS-managed Kubernetes service used to orchestrate containerized microservices in the Smarthome IoT system.
Kubernetes Gateway API | A standard for managing ingress and routing traffic within Kubernetes clusters. Used by Kong in this architecture.
Kong API Gateway | An open-source API gateway deployed inside EKS to manage routing, rate-limiting, authentication, and authorization of API traffic.
AWS API Gateway | A fully managed AWS service for exposing REST and WebSocket APIs, considered as an alternative to Kong.
OIDC (OpenID Connect) | An identity layer built on OAuth 2.0 used to integrate authentication via AWS Cognito.
AWS Cognito | AWS-managed identity service used for authenticating users via OIDC in the system.
User Permission Service | Internal microservice responsible for evaluating dynamic policies and ownership rules for authorization.
DocumentDB | AWS-managed MongoDB-compatible database used to store device metadata and structured documents.
Aurora PostgreSQL | A fully managed SQL database offered by AWS; evaluated as a candidate during architectural planning.
Kafka (MSK) | Apache Kafka, deployed via Amazon MSK, serves as the event streaming platform for asynchronous microservice communication.
InfluxDB | A high-performance time-series database used to store IoT metrics and telemetry data.
OpenSearch | AWS-managed search and analytics engine used for indexing and querying geo-based building data.
Argo CD | A GitOps continuous deployment tool used to synchronize application state in Kubernetes with the configuration stored in Git.
GitOps | A deployment methodology where Git is used as the single source of truth for both infrastructure and application configurations.
CloudFormation | AWS-native Infrastructure-as-Code (IaC) tool used to provision cloud resources in the Infrastructure Installation flow.
SonarQube | Static code analysis tool used to enforce code quality standards and detect security issues.
OWASP Top 10 | A list of the 10 most critical web application security risks, used as a baseline for securing the Smarthome IoT system.
OpenTelemetry | A vendor-neutral standard used for collecting distributed traces and metrics in the system, integrated with AWS X-Ray.
Service Mesh (Istio) | A dedicated infrastructure layer within Kubernetes for controlling and securing service-to-service communication.
CDC (Change Data Capture) | A pattern where changes in a database are published as events (e.g., to Kafka), used for real-time stream processing.
Dynamic Policy Rules | A flexible, runtime-based authorization mechanism used to determine access based on user role, resource ownership, and context.
SLAs (Service-Level Agreements) | Commitments about system availability, response time, or reliability, defined per environment.
