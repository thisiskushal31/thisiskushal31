# Legacy Admin Panels Infrastructure – Technical Architecture

## System Overview

The **Legacy Admin Panels Infrastructure** at Purplle.com supports the backend admin panels whose outcomes **business teams** use to deliver changes: front banner, newer campaigns, Martech campaigns, and logistic changes. Other teams (Storefront, Martech, SCM, Data Engineering, Data Science) own and maintain the application code; business teams use the panel to run operations. The **legacy monolith** is **PHP** (2011 to 2015). Code updates were largely paused around 2015; very few updates have been done since then till present. It is maintained **from the front-end side only**: the front-end manages the panel and calls the backend. Purplle has done **micro-service modernization**; the backend is supported by a **distributed architecture** — microservices on **Kubernetes**. The **legacy instance** calls the distributed architecture through an **internal load balancer**, managed by the DevOps team.

**Infrastructure focus (platform/DevOps ownership — infrastructure only):** CI/CD, network, monolith deployment, load balancer under high load, MySQL backing the legacy architecture, internal load balancer (legacy to distributed K8s). Application code is owned by Storefront, Martech, Supply Chain Management, Data Engineering, Data Science; this document describes the platform from an infrastructure perspective.

**What I managed (summary of facts):**
- **CI/CD** — Pipelines and deployment for the monolith and related infra.
- **Network** — Connectivity for admin panels and legacy-to-distributed path.
- **Monolith deployment** — Deploying and operating the legacy backend.
- **Load balancer** — Under high load; managed by DevOps.
- **MySQL** — Database backing the legacy architecture; connections managed by infra.
- **Internal load balancer** — Legacy instance to distributed (K8s) architecture; managed by DevOps.
- **Code** — Not owned by infra; owned by Storefront, Martech, SCM, Data Engineering, Data Science.

## High-Level Data Flow

1. **Business teams** — Use the admin panel (front-end) to request changes (banner, campaigns, Martech, logistics).
2. **Front-end** — Manages the panel; calls the **legacy backend** (PHP monolith).
3. **Legacy backend** — Serves the admin workflow; backed by **MySQL**; when needed, calls **distributed architecture** via **internal load balancer**.
4. **Internal load balancer** — Managed by DevOps; routes legacy to microservices on K8s.
5. **Distributed architecture** — Microservices on Kubernetes; code owned by Storefront, Martech, SCM, Data Engineering, Data Science.
6. **Infra** — CI/CD, network, monolith deployment, external load balancer (high load), MySQL, internal load balancer.

## Architecture Layers

### 1. Business and front-end (application)
- **Business teams** use the legacy panel outcomes to deliver changes (front banner, campaigns, Martech, logistics).
- **Front-end** manages the panel and calls the backend (legacy PHP monolith).
- **Ownership:** Application code—Storefront, Martech, SCM, Data Engineering, Data Science; panel outcomes used by business teams.

### 2. Legacy backend (PHP monolith) — infra deploys and operates
- **Monolith** — PHP (2011 to 2015); code updates largely paused around 2015, very few updates since then till present; maintained from front-end side.
- **Deployment** — CI/CD and monolith deployment managed by DevOps.
- **Ownership:** Infra—deployment and operations; application teams—code.

### 3. Load balancing — infra owned
- **External load balancer** — Serves traffic under high load; managed by DevOps.
- **Internal load balancer** — Legacy instance to distributed (K8s) architecture; managed by DevOps.
- **Ownership:** Platform/DevOps team.

### 4. MySQL — infra owned (backing legacy)
- **Database** — Backs the legacy architecture.
- **Connections** — Managed by infra.
- **Ownership:** Infra team.

### 5. Distributed architecture (K8s) — infra runs platform; teams own code
- **Microservices** on Kubernetes — Part of micro-service modernization.
- **Code** — Storefront, Martech, SCM, Data Engineering, Data Science.
- **Infra** — Platform, deployment, network; internal load balancer routes legacy to K8s.
- **Ownership:** Infra—platform and internal LB; teams—application code.

### 6. CI/CD and network — infra owned
- **CI/CD** — Pipelines and deployment for monolith and related infra.
- **Network** — Connectivity for admin panels, legacy, and legacy-to-distributed path.
- **Ownership:** Platform/DevOps team.

## Key Design Points

| Area | Responsibility |
|------|----------------|
| Monolith deployment, CI/CD, network | Infra team |
| External load balancer (high load) | Infra team |
| Internal load balancer (legacy to K8s) | Infra team |
| MySQL (legacy backing), connections | Infra team |
| Distributed K8s platform | Infra team (platform); teams (code) |
| Application code (legacy and microservices) | Storefront, Martech, SCM, Data Engineering, Data Science |

## Infrastructure Components

### Monolith deployment and CI/CD
- **Deployment** — Legacy PHP monolith deployed and operated by infra.
- **CI/CD** — Pipelines for monolith and related infrastructure.
- **High availability** — Load balancer and deployment managed for business continuity.

### Load balancers
- **External** — Serves traffic to the admin panels under high load; DevOps managed.
- **Internal** — Legacy instance to distributed K8s; DevOps managed.

### MySQL
- **Database** — Backs the legacy architecture.
- **Connections** — Managed by infra across the legacy stack.

### Distributed (K8s)
- **Platform** — Microservices on Kubernetes; infra runs the platform and internal LB.
- **Code** — Owned by Storefront, Martech, SCM, Data Engineering, Data Science.

### Network
- **Connectivity** — Admin panels, legacy backend, legacy to distributed path.
- **Ownership:** DevOps team.

## Documentation

- **[README](README.md)** — Project overview, business objectives, metrics, technical stack
- **[Architecture Diagram](architecture-diagram.mmd)** — Mermaid diagram for infra and flow
- **[Metrics](metrics.md)** — Scale, deployment, operational metrics
