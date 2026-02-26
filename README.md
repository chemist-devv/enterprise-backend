# Project Name

> A scalable application built using Clean Architecture principles.

## 🏗 Architecture Overview

This project follows a **Clean Architecture** (or Hexagonal Architecture) approach, separating concerns into distinct layers to ensure maintainability, testability, and independence from frameworks.

### Layer Breakdown

| Layer | Directory | Responsibility |
| :--- | :--- | :--- |
| **Domain** | `/src/domain` | **Layer 1:** Pure Business Logic. Entities, Repository Interfaces, Value Objects. No external dependencies. |
| **Application** | `/src/application` | **Layer 2:** Use Cases & Orchestration. DTOs, Application Services. Coordinates the flow of data. |
| **Infrastructure** | `/src/infrastructure` | **Layer 3:** Tech-specific implementations. Database logic, External APIs, Security implementations. |
| **Presentation** | `/src/presentation` | **Layer 4:** Interface adapters. Controllers, Routes, Middlewares. How the world interacts with the system. |

## 📁 Project Structure

```text
/project-root
├── /config             # Port numbers, API keys, env loading
├── /tests              # Unit, Integration, E2E
├── /scripts            # Database migration triggers, seeders
└── /src
    ├── /domain         # (Layer 1) Pure Business Logic
    │   ├── /entities
    │   ├── /repositories (Interfaces only)
    │   └── /value-objects
    ├── /application    # (Layer 2) Use Cases & Orchestration
    │   ├── /use-cases
    │   ├── /dtos
    │   └── /services
    ├── /infrastructure # (Layer 3) Tech-specific implementations
    │   ├── /database   # Mongoose/TypeORM/Prisma logic
    │   ├── /gateways   # Implementation of external APIs (Stripe, etc.)
    │   └── /security   # JWT implementation, Bcrypt
    ├── /presentation   # (Layer 4) How the world interacts with you
    │   ├── /http       # Controllers, Routes
    │   ├── /grpc       # If you use gRPC
    │   └── /middlewares
    └── main.ts         # The "Composition Root" (Starts the server)
