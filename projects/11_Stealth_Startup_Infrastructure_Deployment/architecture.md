# Stealth Startup Infrastructure Deployment & Software Compliance - Technical Architecture

## System Overview

Stealth Startup is an AI-powered CI/CD SaaS. Customers connect a **GitHub Organization** through a **GitHub App**. A Monk **control / orchestration layer** provisions runners, orchestrates workflows and AI agents, analyzes failures, manages caches, and runs security/compliance scanning. **Ephemeral GCP Compute Engine runners** execute GitHub CI jobs and return results and logs.

**Infra ownership (this project):** Cloud infrastructure, runner capacity, platform deployment automation, SOC 2–aligned security/compliance, caching, and observability. Product application logic and AI agent code are owned by engineering; this document describes how services and runners are configured in production.

## Current Architecture (Control Plane → Runners)

```
Customer GitHub Organization
          │
          │ GitHub App integration
          ▼
Stealth Startup Control / Orchestration Layer
          │
          ├── CI runner provisioning
          ├── Workflow and AI-agent orchestration
          ├── Build-log analysis and RCA
          ├── Docker and GitHub Actions caching
          └── Security / compliance scanning
          │
          ▼
Ephemeral GCP Compute Runners
          │
          ├── Execute GitHub CI jobs
          ├── Scale using on-demand VMs
          └── Send execution results and logs back
```

### Control / orchestration layer responsibilities

| Capability | Role |
|------------|------|
| CI runner provisioning | Allocate and tear down ephemeral runner capacity |
| Workflow & AI-agent orchestration | Coordinate CI workflows and multi-agent remediation |
| Build-log analysis & RCA | Detect failures, analyze logs, drive root-cause analysis |
| Docker & GitHub Actions caching | Speed up builds (alongside MicroCeph / K8s-native cache) |
| Security / compliance scanning | Scan before/alongside delivery; support SOC 2–aligned posture |

### Ephemeral runner plane

- Runs customer **GitHub CI jobs** on **on-demand Compute Engine VMs**  
- Scales with demand (runner capacity, not long-lived dedicated fleets)  
- Returns **execution results and logs** to the control layer  

## GCP Configuration

### Application plane — GKE / Kubernetes

- Runs **stateful and stateless** application components (control plane / product services)  
- Complements Cloud Run where used for selected managed workloads  
- Integrates with Kubernetes-native storage used in distributed CI caching  

### Data plane — ephemeral CI runners (Compute Engine)

| Attribute | Detail |
|-----------|--------|
| Model | Ephemeral, on-demand VMs |
| Region | Primarily **us-central1** |
| Machine family | Primarily AMD-based **C4D** |
| Common size | **32 vCPU / 128 GB** (frequent configuration) |
| Catalog | ~**30 VM types** across environments |

### Data, messaging, caching, and AI

| Service | Use |
|---------|-----|
| **PostgreSQL** | Persistent application data |
| **NATS JetStream** | Core distributed messaging for the runner plane: tracks and coordinates **runners**, **capacity**, and **authenticator** services. Communication path between **runners and platform / community services** across the distributed system |
| **Pub/Sub** | Ad hoc / event-style **triggers** — e.g. **add-ons trigger**, **log analysis trigger**, **debug trigger**, and other one-shot jobs that need to be fired without owning the runner control path |
| **MicroCeph** | Distributed **caching** for CI workloads (with Kubernetes-native storage); up to **80% faster** CI execution |
| **Vertex AI** | Hosts open-model AI workloads (current) |
| **GPU pipeline** | In development — self-host open models and perform inference internally |

**Messaging split (important):**
- **NATS JetStream** = ongoing runner/capacity/auth communication in the distributed system  
- **Pub/Sub** = ad hoc triggers (add-ons, log analysis, debug, …)  
- **MicroCeph** = caching (not messaging)

### Environments

| Environment | Purpose |
|-------------|---------|
| **Silicon** | Fully breakable sandbox / experimental |
| **Development** | Active development |
| **Staging** | Pre-production validation |
| **Production** | Customer-facing production |

## Platform Delivery, Caching, Compliance & Observability

These layers support how the control plane and runners are deployed and hardened:

### Infrastructure as Code & GitOps

- **Terraform** — provision GCP network, GKE, runners-related infra, IAM foundations  
- **Jenkins-assisted infra config** — operator selects the right stack/config; opens a PR to the infra repo **main**  
- **[Atlantis](https://www.runatlantis.io/)** — plans/applies that PR so reviewers get a single view of IAM, resources, and other IaC diffs before apply  
- **Helm + Argo CD** — GitOps application delivery  
- **Developer contract:** push the correct **branch** / **tag**; Argo CD deploys — no manual cluster surgery for normal releases  
  - **Dev:** GitOps image/tag **auto-updates**  
  - **Staging & production:** version **tag is updated in Argo CD / GitOps config** for that environment  

### Release model (semantic versioning + reusable CI)

| Item | Rule |
|------|------|
| **dev branch** | Coding + commits; builds a **separate dev image** — tag `YYYY.MM.DD.dev-sha-<shortsha>` (**never `:latest`**) |
| **main branch** | Release tagging after PR CI has already validated code quality |
| **Reusable CI** | Shared workflows build/publish **immutable** service images from branch or tag |
| **RC tags** | On main: `MAJOR.MINOR.PATCH-rc.N` (rc.1, rc.2, …) for staging-bound candidates |
| **Production tag** | Same `MAJOR.MINOR.PATCH` (RC stripped) — the version name used toward production |
| **Runners** | **Not versioned** |

```
dev branch → image tag YYYY.MM.DD.dev-sha-<shortsha> (test only; never :latest)
        ↓
merge / promote to main (PR CI already ran for code quality)
        ↓
tag RC: X.Y.Z-rc.N  →  staging path / candidate
        ↓
tag release: X.Y.Z   →  production version
        ↓
Argo CD syncs (dev auto-pin; staging/prod pin updated in GitOps)
```

### CI performance (caching)

- **MicroCeph** — primary distributed **cache** layer for CI (with Kubernetes-native storage); up to **80% faster** CI execution for customer workloads  
- **Docker and GitHub Actions caching** — additional caches managed in the control / orchestration layer  

### SOC 2– and ISO/IEC 27001–aligned software compliance

| Control | Focus |
|---------|--------|
| Private networking | Limit exposure of production and runner-related paths |
| Zero Trust | Explicit identity and access; minimize implicit trust |
| Least-privilege IAM | Scoped human and workload permissions |
| Secure service-to-service | Authenticated/authorized communication across services |
| Compliance scanning | Integrated in the control layer for enterprise readiness |
| **SOC 2** | Trust-services–oriented SaaS control alignment |
| **ISO/IEC 27001** | Information security management system (ISMS) alignment — **not** ISO 12001 |

### Platform operations (IaC, monitoring, release automation)

| Capability | Public-safe description |
|------------|-------------------------|
| Full IaC | Terraform; Jenkins script selects config → PR to infra **main** |
| Atlantis | [runatlantis.io](https://www.runatlantis.io/) — plan/apply with single-pane IAM/infra diffs |
| GitOps | Argo CD: push branch/tag; cluster reconciles |
| Dev pins | Auto-update in GitOps |
| Staging / prod pins | Version tag updated in Argo CD / GitOps config |
| Monitoring & alerting | Deployed with the platform |
| Inventory + cost audit | Automated; Slack when triggered |
| Semver | Dev = `YYYY.MM.DD.dev-sha-<shortsha>` (no `:latest`); main RC `X.Y.Z-rc.N` → prod `X.Y.Z`; **runners not versioned** |
| Reusable CI | Shared CI builds immutable service images |

### Observability

- **OpenTelemetry** — traces/metrics across services  
- **Google Cloud Monitoring** — cloud services, Kubernetes, and VMs (including runner hosts)  

## AI Failure-Remediation Flow

```
CI job on ephemeral runner fails
        ↓
Stealth Startup captures logs
        ↓
GitHub App supplies authorized repo context
        ↓
Code examined temporarily in sandbox
        ↓
Multiple AI agents → RCA + proposed fix
        ↓
Pull request raised
        ↓
Security & quality checks
        ↓
Customer code owner reviews → merge decision
```

**IP / trust:** Customer IP is **not** intended to be retained after sandbox processing.

## Planned BYOC Architecture

Hybrid design for enterprises that must keep sensitive code and CI execution in their own account:

```
Stealth Startup–managed infrastructure
└── Control plane, controller, and orchestration “brain”
                    │
                    ▼
Customer AWS / GCP environment
└── Data plane — CI execution, code, and sensitive workloads
```

| Principle | Intent |
|-----------|--------|
| Central controller | platform-managed orchestration “brain” |
| Customer data plane | Runners, code, sensitive workloads stay in customer cloud |
| Cloud-neutral messaging | Replace GCP-specific Pub/Sub with **Kafka** where required |
| Compliance | Sensitive IP remains inside the customer environment |

## Design Decisions

1. **Separate control plane from runner capacity** — Orchestration and AI live in platform-managed services; heavy CI work runs on ephemeral VMs.  
2. **Ephemeral runners** — On-demand C4D (and ~30 VM types) for elasticity and clean teardown.  
3. **GitHub App as the customer edge** — Authorized repo context without broad standing access beyond the integration model.  
4. **Sandbox for AI remediation** — Temporary code examination; no intended long-term retention of customer IP.  
5. **Compliance by architecture** — SOC 2–aligned networking/IAM plus control-layer security scanning.  
6. **BYOC as the enterprise path** — Keep control plane centralized; move execution/data plane to the customer cloud.

## Operational Scale (LinkedIn / Resume)

- **Greenfield** startup platform — production live and **gradually growing**  
- Up to **80%** faster CI via distributed caching  
- Runner capacity designed for growth (~**30** VM types; frequent **32 vCPU / 128 GB** C4D in us-central1)  

## Related Documentation

- [README](README.md) — Overview and achievements  
- [Metrics](metrics.md) — Runner, platform, and compliance metrics  
- [Diagram](architecture-diagram.mmd) — Mermaid architecture source  
