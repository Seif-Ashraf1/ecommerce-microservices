<div align="center">

# 🛒 Enterprise E-Commerce Microservices

### Production-Grade E-Commerce Platform built with Spring Boot & Spring Cloud

Enterprise-grade E-Commerce Microservices built with **Java 21**, **Spring Boot**, **Spring Cloud**, **PostgreSQL**, **Kafka**, **Redis**, **Docker**, and **JWT**. Designed following **Clean Architecture**, **SOLID Principles**, **Domain-Driven Design (DDD)**, and **Enterprise Design Patterns**.

![Java](https://img.shields.io/badge/Java-21-orange)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5-green)
![Spring Cloud](https://img.shields.io/badge/Spring_Cloud-Latest-brightgreen)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-17-blue)
![Kafka](https://img.shields.io/badge/Apache_Kafka-Event_Driven-black)
![Redis](https://img.shields.io/badge/Redis-Cache-red)
![Docker](https://img.shields.io/badge/Docker-Enabled-2496ED)
![JWT](https://img.shields.io/badge/JWT-Secure_Authentication-purple)
![License](https://img.shields.io/badge/License-MIT-yellow)

</div>

---

# 📖 Overview

This project aims to simulate a **real-world enterprise e-commerce platform** using a **microservices architecture**.

Rather than building a simple CRUD application, the goal is to design and implement a scalable backend similar to systems used in production by large companies.

The project emphasizes:

- Clean Architecture
- SOLID Principles
- Domain-Driven Design (DDD)
- Event-Driven Architecture
- RESTful APIs
- Distributed Systems
- Enterprise Design Patterns
- Scalability & Maintainability

---

# 🛠 Tech Stack

| Category | Technology |
|-----------|------------|
| Language | Java 21 |
| Framework | Spring Boot |
| Microservices | Spring Cloud |
| Security | Spring Security + JWT |
| ORM | Spring Data JPA + Hibernate |
| Database | PostgreSQL |
| Cache | Redis |
| Messaging | Apache Kafka |
| API Communication | REST + OpenFeign |
| Service Discovery | Eureka |
| API Gateway | Spring Cloud Gateway |
| Configuration | Spring Cloud Config |
| Build Tool | Maven |
| Containerization | Docker & Docker Compose |
| Monitoring | Prometheus + Grafana *(planned)* |
| Tracing | Zipkin *(planned)* |

---

# 🏗 Architecture

> Architecture diagram coming soon.

The system follows a **Microservices Architecture** where each service owns its own database and communicates using both synchronous (REST/OpenFeign) and asynchronous (Kafka) communication.

---

# 📦 Planned Microservices

| Service | Purpose | Status |
|----------|---------|--------|
| Config Server | Centralized configuration | ⏳ Planned |
| Eureka Discovery Server | Service discovery | ⏳ Planned |
| API Gateway | Routing & API entry point | ⏳ Planned |
| Authentication Service | Authentication & JWT | ⏳ Planned |
| User Service | Customer profile management | ⏳ Planned |
| Admin Service | Administration & management operations | ⏳ Planned |
| Category Service | Product category management | ⏳ Planned |
| Product Service | Product catalog | ⏳ Planned |
| Inventory Service | Stock management | ⏳ Planned |
| Cart Service | Shopping cart | ⏳ Planned |
| Wishlist Service | Customer wishlist | ⏳ Planned |
| Coupon Service | Discounts & promotions | ⏳ Planned |
| Order Service | Order lifecycle | ⏳ Planned |
| Payment Service | Payment processing | ⏳ Planned |
| Shipping Service | Shipment & delivery | ⏳ Planned |
| Notification Service | Email/SMS/Push notifications | ⏳ Planned |
| Review Service | Ratings & reviews | ⏳ Planned |
| Search Service | Product search | ⏳ Planned |

---

# 🎯 Design Patterns

The project demonstrates several enterprise design patterns:

- Singleton
- Factory
- Strategy
- Facade
- Observer
- Bridge
- Chain of Responsibility
- Repository
- Builder
- Specification
- Adapter
- Template Method

---

# 🔄 Communication

The project combines both synchronous and asynchronous communication.

### Synchronous

- REST APIs
- OpenFeign

### Asynchronous

- Apache Kafka
- Domain Events
- Event-Driven Architecture

Examples of events:

- UserRegistered
- OrderCreated
- PaymentSucceeded
- PaymentFailed
- InventoryReserved
- InventoryReleased
- ShipmentCreated
- NotificationRequested

---

# 📁 Repository Structure

```text
ecommerce-microservices
│
├── architecture
├── database
├── diagrams
├── docker
├── docs
├── k8s
├── postman
├── scripts
├── services
│
├── .github
│   └── workflows
│
├── README.md
└── .gitignore
```

---

# 🚀 Getting Started

The project is currently under development.

Setup instructions will be added as the microservices are implemented.

---

# 🗺 Roadmap

# Project Roadmap

Enterprise E-Commerce Microservices Platform — build order and phase checklist.

Services and phases are ordered by dependency, not by feature grouping — e.g. `common-lib`,
Kafka, and Redis are introduced in Phase 2 infrastructure because services starting in Phase 3
already depend on them, not deferred to a later "production readiness" phase.

---

## ✅ Phase 1 — Project Planning

- [x] Create GitHub Repository
- [x] Initial Project Structure
- [x] Repository Documentation
- [x] Software Requirements Specification (SRS)
- [x] System Architecture
- [x] API Design
- [x] Database Design

---

## 🏗 Phase 2 — Infrastructure

- [ ] `common-lib` module (shared event DTOs, common exception shapes — **build before any service**)
- [ ] Eureka Discovery Server
- [ ] API Gateway (routing + JWT validation shell; full RBAC lands in Phase 3)
- [ ] Docker Compose skeleton, including infra containers even before code uses them:
  - [ ] PostgreSQL
  - [ ] Kafka (+ Zookeeper or KRaft)
  - [ ] RabbitMQ
  - [ ] Redis
  - [ ] Elasticsearch
  - [ ] MinIO
- [ ] Shared configuration profiles (`dev`, `staging`, `prod`)

---

## 🔐 Phase 3 — Authentication & Security

- [ ] Authentication Service (register, login, refresh, logout, password reset, email verification)
- [ ] JWT Authentication (RS256, short-lived access + revocable refresh tokens)
- [ ] Refresh Tokens (rotation on use, stored hashed)
- [ ] Role-Based Access Control (RBAC)
- [ ] Spring Security
- [ ] Minimal Notification Service (Kafka consumer + SMTP send only —
      enough to deliver verification/reset emails; full feature set completed in Phase 7)

---

## 👥 Phase 4 — User Management

- [ ] User Service

> **Note:** Admin Service is intentionally **not** in this phase — it aggregates Product, Order,
> Inventory, and Coupon data via Feign, none of which exist yet. See Phase 8.

---

## 🛍 Phase 5 — Product Catalog

- [ ] Category Service (build before Product — Product validates categories against it)
- [ ] Product Service (+ MinIO for images, Redis for catalog cache)
- [ ] Inventory Service
- [ ] Search Service (Elasticsearch, consumes Product events)

---

## 🛒 Phase 6 — Shopping Experience

- [ ] Coupon Service (no dependencies — can be built any time before checkout)
- [ ] Cart Service (depends on Product + Inventory)
- [ ] Wishlist Service (depends on Product + Cart)

---

## 📦 Phase 7 — Order Processing

- [ ] Order Service (Saga orchestrator — depends on Cart + Coupon)
- [ ] Payment Service
- [ ] Shipping Service
- [ ] Notification Service — completed here (full multi-channel dispatch, all event consumers wired)

---

## ⭐ Phase 8 — Customer Engagement & Aggregation

- [ ] Review Service (depends on Order Service for purchase verification)
- [ ] Admin / BFF Service (moved from Phase 4 — everything it aggregates now exists)

---

## 🚀 Phase 9 — Production Readiness

- [ ] Kafka hardening (partitioning, consumer group scale-out, DLQ policies)
- [ ] Redis hardening (cache eviction policy tuning, rate-limiter store)
- [ ] Prometheus
- [ ] Grafana
- [ ] Zipkin / OpenTelemetry
- [ ] Contract testing (Spring Cloud Contract or Pact) across all producer/consumer pairs
- [ ] CI/CD Pipeline
- [ ] Kubernetes Deployment (optional)

---

## Immediate next steps

Since Phase 1 is complete, build in this exact order:

1. Scaffold `common-lib` as its own Maven module.
2. Bring up the Docker Compose infra skeleton (Postgres, Kafka, RabbitMQ, Redis, Elasticsearch, MinIO).
3. Config Server → Eureka → API Gateway, in that order.
4. Auth Service, wired to Kafka from day one.
5. Minimal Notification Service, so Auth's email flows are testable end-to-end immediately.
# 💡 Future Improvements

- AI Product Recommendations
- Multi-Vendor Marketplace
- Elasticsearch Integration
- Kubernetes Deployment
- Multi-Tenant Architecture
- GraphQL API
- Mobile Application
- Recommendation Engine

---
# 🚀 What We Will Build Next

The project will be developed incrementally in the following order:

1. 📑 Software Requirements Specification (SRS)
2. 🏗 System Architecture
3. ⚙️ Spring Cloud Config Server
4. 🔍 Eureka Discovery Server
5. 🌐 API Gateway
6. 🔐 Authentication Service
7. 👥 User Service
8. 👨‍💼 Admin Service
9. 🗂 Category Service
10. 📦 Product Service
11. 📊 Inventory Service
12. 🛒 Cart Service
13. ❤️ Wishlist Service
14. 🎟 Coupon Service
15. 📑 Order Service
16. 💳 Payment Service
17. 🚚 Shipping Service
18. 📢 Notification Service
19. ⭐ Review Service
20. 🔎 Search Service
21. 📨 Kafka Event Integration
22. 📈 Monitoring & Observability
23. 🐳 Docker & Deployment
24. 🚀 CI/CD Pipeline


