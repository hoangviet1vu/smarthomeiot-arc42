### 8.1 Authentication and Authorization

The **Smarthome IoT** system adopts a **centralized authentication and authorization model** to ensure consistent and secure access control across all services.

All incoming **HTTP requests** are processed by the **Kong API Gateway**, which performs two critical checks before routing requests to backend microservices:

- **Authentication:**<br>
The gateway verifies the request's **JWT token** using **OIDC integration with AWS Cognito**, ensuring that the user is properly authenticated and the token is valid.

- **Authorization:**<br>
After verifying identity, the gateway calls the **User Service** to validate whether the user has the necessary access rights. Authorization is enforced via **dynamic policy rules** that evaluate user roles, resource ownership, and contextual access constraints.

![Authentication and Authorization](./Img/concepts/authz/authz/authz.png)

This approach enables **centralized user permission management**, allowing fine-grained control over access rules without burdening backend services. It also supports the **single-responsibility principle**, ensuring that microservices remain focused on their domain logic while deferring security checks to the edge and permission layer.
