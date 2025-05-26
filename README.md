# Astra-ride-bus-management-system



A distributed microservices-based bus booking platform designed for scalability, reliability, and modern development practices. This project demonstrates a polyglot architecture using Spring Boot, .NET, Node.js, multiple databases, and a robust set of infrastructure components.

---

## 🚦 System Overview

This platform allows users to view bus schedules, make bookings, complete payments, and receive notifications, all powered by independent yet connected services. The system leverages service discovery, centralized configuration, secure authentication, event-driven communication, and an API gateway for unified access.

---

## 🏗️ Architecture Diagram

```
+-------------------+       +------------------+      +----------------------+
|                   |       |                  |      |                      |
|   Keycloak Auth   +------>+  Spring Gateway  +----->+     Eureka Server    |
|                   |       |                  |      |                      |
+-------------------+       +--------+---------+      +----------------------+
                                         |
                                         v
  +-----------+    +-------------+   +-----------+   +---------+   +--------------+   +---------------+
  | Timetable |    | Booking     |   | Payment   |   | Seat    |   | Notification |   | Config Server |
  | Service   |    | Service     |   | Service   |   | Service |   | Service      |   |               |
  | (Spring   |    | (.NET +     |   | (Spring   |   | (Node + |   | (Node +      |   | (Spring Cloud)|
  |  Boot +   |    |  MySQL)     |   |  Boot +   |   | Firestore)| | MongoDB)     |   |               |
  |  MongoDB) |    |             |   |  Postgres)|   |         |   |              |   |               |
  +-----------+    +-------------+   +-----------+   +---------+   +--------------+   +---------------+
         \               |                |                |                |                |
          \              |                |                |                |                |
           +-------------+----------------+----------------+----------------+----------------+
                                         |
                                         v
                                   +------------+
                                   |   Kafka    |
                                   |  (Events)  |
                                   +------------+
```

---

## 🧩 Microservices Breakdown

| Service            | Tech Stack                   | Database     | Purpose                                              |
|--------------------|-----------------------------|--------------|------------------------------------------------------|
| Timetable Service  | Spring Boot                 | MongoDB      | Users can view today's busses and schedules.         |
| Booking Service    | .NET                        | MySQL        | Users can book seats on a selected bus.              |
| Payment Service    | Spring Boot                 | PostgreSQL   | Handles payments (Planned).                          |
| Notification       | Node.js                     | MongoDB      | Sends notifications to users (Planned).              |
| Seat Service       | Node.js                     | Firestore    | Manages seat assignments and availability (Planned). |
| Eureka Server      | Spring Cloud Netflix Eureka | N/A          | Service discovery and registry.                      |
| Config Server      | Spring Cloud Config         | N/A          | Centralized config management.                       |
| API Gateway        | Spring Cloud Gateway        | N/A          | Single entry point for all clients.                  |
| RabbitMq           | RabbitMq                    | N/A          | Asynchronous communication/event bus.                |
| Authentication     | Keycloak                    | N/A          | OAuth2/OpenID Connect authentication.                |

---

## 🛠️ Core Features

- **Service Discovery**: Eureka enables dynamic registration and discovery of all services.
- **Centralized Configuration**: Spring Cloud Config Server manages configuration across all environments.
- **API Gateway**: Single, secure entry point for all client requests, with routing and filtering.
- **Event-Driven**: Kafka enables robust, decoupled communication between services.
- **Polyglot Persistence**: Each service uses the database best suited for its needs (MongoDB, MySQL, PostgreSQL, Firestore).
- **Authentication**: Secured by Keycloak, supporting OAuth2 flows and role-based access.
- **Scalability**: Each service can be independently deployed and scaled.

---

## 📦 Repository Links

- **Booking Service (.NET + MySQL):**  
  [booking-service](https://github.com/Codersauruse/booking-service)

- **Timetable Service (Spring Boot + MongoDB):**  
  [timetable-service](https://github.com/Codersauruse/timetable-service)

- **Spring Config Server:**  
  [spring-config-server](https://github.com/Codersauruse/spring-config-server)

- *(Links for Payment, Notification, Seat, and Gateway services will be added as repositories are created.)*

---

## 🚧 Planned Services

- **Payment Service:**  
  - Built with Spring Boot & PostgreSQL.
  - Handles secure payment transactions and integrates with booking flow.

- **Notification Service:**  
  - Built with Node.js & MongoDB.
  - Sends confirmation emails, SMS, or push notifications to users.

- **Seat Service:**  
  - Built with Node.js & Firestore.
  - Manages real-time seat selection and availability.

- **Spring Cloud Gateway:**  
  - To be set up as the unified API gateway.

---

## 🔐 Security & Authentication

- **Keycloak** will manage user authentication and authorization.
- All sensitive endpoints will be protected via OAuth2/OpenID Connect.

---

## 📡 Communication

- **RabbitMq** is used for asynchronous, event-based communication between services (e.g., booking events triggering notifications or payments).

---

## 🌍 How It Works

1. **User Authentication:**  
   Users sign in via Keycloak and receive JWT tokens.

2. **Timetable Viewing:**  
   Users fetch available busses for today via the Timetable Service.

3. **Booking:**  
   Bookings are made through the Booking Service, which checks seat availability and reserves seats.

4. **Payment:**  
   Upon booking, a payment request is sent to the Payment Service (via Kafka).

5. **Notification:**  
   After a successful booking/payment, the Notification Service informs the user.

6. **Seat Management:**  
   Seat Service ensures real-time updates to seat status.

---

## 🧬 Tech Stack

- **Java (Spring Boot)**: Timetable, Payment, API Gateway, Config, Eureka
- **.NET**: Booking Service
- **Node.js**: Notification, Seat Services
- **MongoDB/MySQL/PostgreSQL/Firestore**: Polyglot persistence
- **Kafka**: Event bus
- **Keycloak**: Identity and access management

---

## 🚀 Getting Started

1. **Clone the repositories** for each microservice (links above).
2. **Set up infrastructure**:  
   - Start Eureka, Config Server, and Kafka.
   - Set up databases (MongoDB, MySQL, PostgreSQL, Firestore).
   - Deploy Keycloak and configure realms/clients.
3. **Configure services** to connect to the Eureka server, Config server, and databases.
4. **Run the API Gateway** and start exposing endpoints to clients.
5. **Deploy each microservice** independently.



## 📬 Contact

For questions or collaboration, connect via (https://github.com/Codersauruse).

---

*This project is under active development. Stay tuned for updates and more services!*
