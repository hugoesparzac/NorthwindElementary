<h1 align="center">Northwind Elementary System</h1>

<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

---

![.NET 10](https://img.shields.io/badge/.NET_10-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white)
![Angular 21](https://img.shields.io/badge/Angular_21-DD0031?style=for-the-badge&logo=angular&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![Vitest](https://img.shields.io/badge/Vitest-FCC72B?style=for-the-badge&logo=vitest&logoColor=1E1E20)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

---

</div>

Northwind Elementary is a modern school management system designed to manage students, staff, academic structures, grading, and report cards.

This project serves as a reference implementation of a **Modular Monolith** using **Vertical Slice Architecture (VSA)** and the **REPR Pattern** (Request-EndPoint-Response) with a modern full-stack architecture powered by .NET 10, Angular 21, PostgreSQL, and Docker.

---

## 🚧 Project Status

Northwind Elementary is currently under active development.

The project is being built as a long-term reference implementation focused on:
- modular monolith architecture
- Vertical Slice Architecture
- modern Angular patterns
- enterprise backend practices
- clean developer experience

---

# ✨ Technical Highlights

- Modular Monolith architecture
- Vertical Slice Architecture
- Dedicated schema per module
- Minimal APIs with REPR Pattern
- Angular Signals + Zoneless
- Dockerized development environment
- OpenAPI + Scalar integration
- Feature-oriented frontend architecture

---

# 🏗️ Architectural Vision

The system is designed to avoid the classic "Big Ball of Mud" anti-pattern by enforcing high cohesion, low coupling, and clear module boundaries.

## Core Architectural Principles

- **Modular Monolith**
  
  Business capabilities are divided into isolated modules:
  
  - Identity
  - People
  - Academic
  - Assessment

  Each module owns:
  
  - its business rules
  - its application layer
  - its persistence logic
  - its dedicated database schema

- **Vertical Slice Architecture (VSA)**

  Instead of organizing code by technical layers, the application is organized by features. Each slice encapsulates everything required for a use case:

  - Endpoint
  - Request
  - Validation
  - Business logic
  - Persistence

- **REPR Pattern**

  The backend leverages .NET 10 Minimal APIs following the Request-EndPoint-Response pattern to create lean, feature-oriented endpoints.

- **Mono-repo Strategy**

  Backend and frontend coexist in the same repository, enabling:

  - atomic commits
  - simpler CI/CD orchestration
  - unified versioning
  - easier onboarding

---

# 🚀 Tech Stack

## Backend (.NET 10)

- **Framework:** ASP.NET Core 10 (LTS)
- **Language:** C# 14
- **Database:** PostgreSQL 17 with EF Core 10
- **Architecture:** Modular Monolith + Vertical Slice Architecture
- **Patterns:** REPR Pattern, MediatR, FluentValidation
- **Documentation:** OpenAPI + Scalar
- **Testing:** xUnit

## Frontend (Angular 21)

- **Framework:** Angular 21
- **Language:** TypeScript
- **Rendering Model:** Zoneless by default
- **State Management:** Angular Signals
- **Architecture:** Standalone Components
- **Styling:** Tailwind CSS + SCSS
- **Modern Features:** Deferrable Views (`@defer`) and Signal-based Forms
- **Testing:** Vitest

## DevOps & Infrastructure

- Docker & Docker Compose
- Multi-stage Docker builds
- Nginx for frontend hosting
- PostgreSQL containerized development environment

---

# 📁 Project Structure

```text
src/
 ├── Northwind.Api/             # ASP.NET Core Aggregator Host
 ├── Northwind.Client/          # Angular 21 Application
 │    └── app/features/         # Frontend Vertical Slices
 │
 └── Modules/
      ├── Identity/
      │    ├── Northwind.Modules.Identity/
      │    └── Northwind.Modules.Identity.Contracts/
      │
      ├── People/
      │    ├── Northwind.Modules.People/
      │    └── Northwind.Modules.People.Contracts/
      │
      ├── Academic/
      │    ├── Northwind.Modules.Academic/
      │    └── Northwind.Modules.Academic.Contracts/
      │
      └── Assessment/
           ├── Northwind.Modules.Assessment/
           └── Northwind.Modules.Assessment.Contracts/

tests/
 └── Backend and frontend tests mirrored by module
```

## 🛠️ Getting Started

The project supports two development workflows:

1. Fully containerized setup using Docker
2. Hybrid local development workflow (recommended for active development)

### 🐳 Option 1 — Full Docker Experience

This option requires only Docker installed on your machine.

Perfect for:

- recruiters
- reviewers
- quick demos
- contributors
- onboarding

#### Prerequisites

- Docker (Desktop or Engine)
- Docker Compose

#### Run Everything

```bash
git clone https://github.com/hugoesparzac/NorthwindElementary.git
```

```bash
cd NorthwindElementary
```

```bash
docker compose up --build
```

This will automatically start:

- PostgreSQL 17
- ASP.NET Core API
- Angular frontend served with Nginx

#### Application URLs

| Service         | URL                                                                |
| --------------- | ------------------------------------------------------------------ |
| Frontend        | [http://localhost:4200](http://localhost:4200)                     |
| Backend API     | [http://localhost:8080](http://localhost:8080)                     |
| Scalar API Docs | [http://localhost:8080/scalar/v1](http://localhost:8080/scalar/v1) |

### 💻 Option 2 — Hybrid Local Development (Recommended)

This workflow provides the best developer experience with:

- Angular Hot Reload
- dotnet watch
- faster rebuilds
- easier debugging

#### Prerequisites

- .NET 10 SDK
- Node.js 22+
- Angular CLI 21
- Docker

#### 1. Clone the Repository

```bash
git clone https://github.com/hugoesparzac/NorthwindElementary.git
```

```bash
cd NorthwindElementary
```

#### 2. Start PostgreSQL

The development database configuration is already included in appsettings.Development.json.

Start only the PostgreSQL container:

```bash
docker compose up database
```

#### 3. Run the Backend

```bash
cd src/Northwind.Api
```

```bash
dotnet restore
```

```bash
dotnet watch
```

#### 4. Run the Frontend

Open another terminal:

```bash
cd src/Northwind.Client
```

```bash
npm install
```

```bash
ng serve
```

#### Application URLs

| Service         | URL                                   |
| ----------------| ------------------------------------- |
| Frontend        | http://localhost:4200                |
| Backend API     | http://localhost:5000                |
| Scalar API Docs | http://localhost:5000/scalar/v1      |

## 🔧 Environment Configuration

> [!NOTE]
> No manual environment configuration is required for local development.
> The repository already includes a preconfigured `appsettings.Development.json` file intended exclusively for development and onboarding purposes.

> [!WARNING]
> **Development Credentials Only:** The `docker-compose.yml` includes default credentials for development purposes only. **Never use these in production.** Always replace them with strong, unique passwords when deploying to production environments.

## 📝 API Documentation

Interactive documentation is available via Scalar when the API is running in development mode:

- **Scalar UI:** `https://localhost:PORT/scalar/v1`
- **OpenAPI Spec:** `https://localhost:PORT/openapi/v1.json`

## 🤝 Contributing

Contributions are welcome! Please review our [CONTRIBUTING.md](CONTRIBUTING.md) file for more details on how to report bugs, propose features, or submit Pull Requests.

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
