### 8.2 Microservices Dependency Management

To manage dependencies between services in a scalable and maintainable way, the Smarthome IoT system adopts **service mesh architecture** using **Istio** as the foundation for internal service-to-service communication.

Key benefits of using Istio include:

- **Decoupled service communication** via sidecar proxies, enabling services to focus solely on their business logic
- **Declarative dependency management**, where communication rules and routing policies are externally defined and centrally controlled
- **Centralized traffic control and policy enforcement**, including retries, circuit breaking, rate limiting, and access rules
- **Built-in observability and telemetry**, providing real-time insights into service health, request traces, and mesh topology

While synchronous communication is managed via Istio, the system also relies heavily on **asynchronous messaging through Kafka** to enable service decoupling at the data flow level. The details of this **event-driven integration model** are covered in **Section 8.3 – Event-Driven Strategy**.
