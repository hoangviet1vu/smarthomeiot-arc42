### 6.1 Building Construction

When an Administrator creates a new Area within a building, the system performs the following steps:
- The Administrator searches and selects the target Building via the Building Service API.
- The Administrator queries the User Service to select the User Group responsible for the new Area.
- The Area creation request is submitted to the Building Service.
- The Building Service persists the Area into MongoDB (DocumentDB).
- A CDC event is published to the Building CDC Kafka Stream.
- The Elasticsearch Collector consumes the event and indexes the Area into OpenSearch, enabling geo-based and full-text search capabilities.

![Create Area](../Img/Usecases/building-construction/admin-create-areas/Building%20Construction%20%20Add%20an%20area%20and%20assign%20to%20user%20group.png)

Upon successful Area creation, a notification is generated and delivered to users in the assigned User Group:

- The Notification Collector consumes the Area Created event, transforms it into a notification message, and sends it to the Notification Stream.
- The Notification Service consumes the event, queries the User Service to retrieve the recipients, and stores the composed notification in the Notification MongoDB Collection.
- A CDC event is triggered on notification insertion and published to the Notification CDC Stream

![Compose Notification](../Img/Usecases/building-construction/newarea.notification/Building%20Construction%20%20New%20Area%20Notification.png)

- The Push Notification Service consumes events from the Notification CDC Stream and delivers push notifications to users via Firebase.

![Push Notification](../Img/Usecases/building-construction/push.notification/Building%20Construction%20%20Push%20Notification.png)

- The Email Delivery Service processes the same stream and sends corresponding emails through the integrated email provider.

![Email Delivery](../Img/Usecases/building-construction/email/Building%20Construction%20%20Email.png)

