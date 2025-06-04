
## 1. Introduction and Goals

### 1.1 Requirements Overview

This document describes the architecture of  **Smarthome Iot**, our Microservices-based IoT System for **smart building management**. The system is designed to support the **registration, management, and monitoring** of up to **1 million IoT devices** deployed across **multiple buildings**.

These devices are installed in various physical locations and are hierarchically organized by **Room, Area, Floor, and Building**, allowing for structured oversight and precise **location tracking**.

The system supports three primary user roles:

- **Engineers**: Responsible for on-site device **installation and registration**, ensuring each device is correctly linked to its physical location.

- **Administrators**: Use the backend platform to **monitor** device statuses, detect building events, and trigger alerts when incidents occur.

- **End Users**: Can **monitor and control their personal in-house devices** — such as cameras, lights, and air conditioners—through user interfaces tailored for individual access and convenience.

The system adopts a microservices architecture to ensure scalability, real-time responsiveness, and modular service management, making it suitable for large-scale, flexible IoT deployments in smart buildings.

### 1.2 Quality Goals

|No.|Quality|Motivation|
|--|--|--|
|1| **Functional Suitability** | The system must provide essential functionality for the **registration, management, and monitoring** of up to **1 million IoT devices** across **multiple buildings, floors, areas, and rooms**. It must support core use cases for **Engineers, Administrators, and End Users**, enabling **installation, control, and monitoring of devices**. Detailed functional requirements will be defined and refined incrementally through Product Epics following an Agile development approach|
|2| **Security** |The system must ensure secure access control, data protection, and service isolation across all components and user roles. All communications must be protected using **TLS 1.3**, and access must be enforced via **OAuth2.0** and **role-based authorization** mechanisms. Sensitive data—such as device telemetry, user credentials, and event logs—must be encrypted both **in transit and at rest**. The architecture must adhere to **OWASP Top 10** guidelines to prevent common vulnerabilities. Where applicable, the system should support compliance with industry standards such as **GDPR** and **ISO/IEC 27001**. Security requirements will evolve through threat modeling, automated security testing, and Agile security reviews integrated into the delivery lifecycle.|
|3| **Usability** |The system must provide a clear, responsive, and intuitive user experience tailored to the needs of different roles: **Engineers**, **Administrators**, and **End Users**. Interfaces should support efficient workflows—such as device **registration**, **monitoring**, and **control—across** both **desktop** and **mobile** environments |
|4| **Reliability** |The system must provide **high availability, fault tolerance, and consistent performance** to support continuous operation of up to 1 million devices. Core functionalities—such as device registration, status monitoring, and event alerting—must remain reliable even under partial failures or degraded conditions. The system should recover gracefully from service disruptions through **redundancy, retry mechanisms**, and automated health checks. Reliability will be reinforced through resilience testing, monitoring, and incident response processes.</br>System availability must comply with the defined Service Level Agreements (SLAs).|
|5| **Extensibility** |The system must be designed to accommodate **new IoT device types** without requiring changes to the core architecture or existing services. Device definitions, data models, and behavior should be configurable or plugin-based, allowing the system to evolve as new device types are introduced. This ensures **long-term flexibility** and **minimizes** the need for code changes or service redeployment when onboarding future devices.|

### 1.3 Stakeholders

The following roles are key stakeholders who will read, contribute to, or rely on this architecture documentation:

| Role/Name |	Goal/Boundaries |
| -- |	-- |
| **Product Owners** |	Responsible for managing the product's business value and aligning development with business goals. They define and prioritize epics and features in the product backlog and ensure the product meets market and user needs. |
| **Software Architects** |	Define the technical vision and architecture of the system. They make strategic decisions about frameworks, patterns, and technologies to ensure the system is scalable, extensible, and maintainable. |
| **Developers** |	Implement the system based on architectural guidelines and functional requirements. They are responsible for coding, testing, and deploying microservices and integrations with IoT devices and external components. |
| **Operations Team** |	Ensure the system runs reliably and securely in production. They monitor infrastructure, respond to incidents, manage configuration, and maintain SLAs after the product goes live. |
