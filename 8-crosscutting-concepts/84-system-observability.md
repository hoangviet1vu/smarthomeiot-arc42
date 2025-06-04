### 8.4 System observability

The Smarthome IoT system integrates a robust observability strategy to ensure that logs, traces, and metrics are collected, visualized, and acted upon consistently across all services and environments.

**Log Management – AWS CloudWatch**<br>

**AWS CloudWatch Logs** is used to manage application and infrastructure logs, especially for the **production environment**. Logs from microservices are centralized via Fluent Bit or CloudWatch agents, enabling:
- Real-time log aggregation for error diagnosis and operational insight
- Production incident investigation and root cause analysis
- Integration with CloudWatch Alarms for log-based alerting
- Long-term retention of structured log data for compliance and audit

**Distributed Tracing – AWS X-Ray via Istio**<br>
**AWS X-Ray** is integrated with Istio using the **OpenTelemetry protocol** to trace requests flowing across services. This allows visibility into:
- Cross-service request latency
- Trace IDs correlated with user requests or transaction flows
- Bottleneck identification across microservice chains
- Understanding of complex business workflows across the mesh

**System Metrics – Key Monitoring Targets**<br>
To ensure infrastructure and application health, a variety of **Kubernetes**, **database**, and **streaming platform** metrics are monitored using tools like CloudWatch, Prometheus, Grafana, and OpenSearch Dashboards.

**📊 Kubernetes Metrics (via CloudWatch Container Insights or  Prometheus)**

|Metric | Purpose
|--|--|
|CPU & Memory Usage per Pod/Node | Detect resource saturation and autoscaling triggers
|Pod Availability & Restarts | Identify unstable deployments or crash loops
|Request/Response Latency (Ingress/Service) | Measure API performance and detect timeouts
|Disk I/O and Network Traffic | Monitor service-level throughput and data movement
|HPA & Cluster Autoscaler Events | Track scaling activity and response to load
|Node Status & Conditions | Identify unhealthy or unreachable nodes


**🗄️ Database Metrics**<br>
Component | Key Metrics | Purpose
-- | -- | --
AWS DocumentDB (MongoDB) | CPU utilization, IOPS, memory, connections, query latency | Monitor performance and prevent overload
AWS OpenSearch | Indexing latency, search latency, heap memory, shard status | Ensure fast querying and prevent memory-related failures
Amazon MSK (Kafka) | Broker health, partition lag, consumer lag, topic throughput | Track delivery guarantees, detect slow consumers
InfluxDB (on EC2) | Write throughput, disk usage, query latency, series cardinality | Ensure time-series metrics are ingested and available reliably

Together, this observability stack provides full visibility into **system behavior, performance bottlenecks**, and **incident root cause analysis**, enabling proactive monitoring and fast operational response.
