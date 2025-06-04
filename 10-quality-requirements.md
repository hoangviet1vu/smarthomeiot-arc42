## 10. Quality Requirements
This section outlines the quality expectations for the Smarthome IoT system, covering both **development-time quality controls** and **non-functional runtime characteristics** to ensure long-term maintainability, performance, and compliance.

### 10.1 Quality Management in Development

To maintain a high standard of code quality, the following practices are enforced during development:

- **Unit Test Coverage**
  - Backend microservices: minimum **80% coverage**
  - Mobile and Web applications: minimum **60% coverage**
- **Static Code Analysis**
  - No **Critical** or **Major** issues are allowed in SonarQube results during active sprints
  - All code must pass quality gates before merging
- **Security Compliance**
  - No **High or Critical vulnerabilities** are allowed in production releases
  - Any new **Critical CVEs** discovered must be addressed in the next scheduled release cycle
- **Automated Testing**
  - Business logic is verified through **automated functional and integration tests** executed continuously during sprints

### 10.2 Non-Functional Requirements

| Aspect | Requirement Description |
| -- | -- |
| **Performance** | All API responses must complete within **3 seconds** under peak load, validated through performance testing |
| **Reliability** | The system must perform its functions **consistently and accurately**, with high transactional integrity |
| **Availability** | Uptime will comply with defined **SLA requirements**, documented separately |
| **Usability** | The system must offer a **user-friendly interface** across web and mobile platforms |
| **Security** | Compliance with **OWASP Top 10** is mandatory.<br>- **AWS WAF** is used to protect against common web attacks<br>- The platform complies with **GDPR** and aligns with **ISO/IEC 27001** standards|
| **Portability** | The system is designed with a **cloud-native strategy**, ensuring it can be deployed to **any major cloud provider or on-premises** without significant modification |
| **Observability**| The platform must provide comprehensive observability, including:<br>- **Application log tracing** (via AWS CloudWatch Logs)<br>- **Distributed request tracing** (via AWS X-Ray and OpenTelemetry)<br>- **Infrastructure and service-level metrics monitoring** (via CloudWatch, InfluxDB, and Grafana)<br>- Support for **alerting, visualization, and root cause analysis** to ensure operational transparency and traceability |
