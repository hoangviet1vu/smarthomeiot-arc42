## 4. Solution Strategy
The system is architected with a strong emphasis on **cloud-native principles**, **portability**, and **cost optimization**. It integrates tightly with **Tuya Cloud** for IoT device management, while extending core functionality through a modular microservices design. The following strategic technical decisions form the foundation of the overall solution:

- **Containerized Microservices on EKS (with EC2 nodes) :**
Core backend services are deployed on **Amazon EKS** using **EC2-based worker nodes**. This setup ensures Kubernetes-native scalability while maintaining cost efficiency. The use of standard Kubernetes components enables **future portability to on-premise environments or other cloud providers** (e.g., AKS, GKE) **without requiring code changes**.

- **MongoDB-compatible Storage :**
The system uses **MongoDB** as its primary data store for storing user information, building metadata, and device mappings. On AWS, **Amazon DocumentDB** is chosen for its **MongoDB API** compatibility, allowing smooth migration or hybrid deployment with native **MongoDB** solutions in other cloud environments.

- **Apache Kafka for Messaging :**
**Kafka** serves as the central event streaming platform, deployed within **EKS**. It enables reliable, decoupled, and scalable communication across microservices and acts as the backbone for data flow in the event-driven architecture.

- **InfluxDB for Time-Series Data :**
IoT device telemetry and historical event data are stored in **InfluxDB**, providing high-performance storage and efficient querying of time-series data.

- **Tuya Cloud Event Integration :**
When IoT device events are emitted from **Tuya Cloud**, they are captured and published to **Kafka**. A dedicated **Kafka Connect pipeline** processes and transforms these events into structured metrics, which are then ingested into **InfluxDB** for monitoring, analytics, and visualization.

- **Golang as Primary Programming Language :**
The backend services are primarily developed using **Go (Golang)**. Chosen for its **lightweight runtime**, **strong concurrency support**, and **native performance**, Go aligns well with microservices principles and simplifies deployment in containerized environments.

These strategic choices collectively ensure that the system is **cloud-agnostic, maintainable, and performance-optimized**, while enabling future extensibility and cross-cloud adoption.
