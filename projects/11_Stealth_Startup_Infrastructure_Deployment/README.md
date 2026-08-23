# Stealth Startup - Infrastructure Deployment & Software Compliance

## Project Overview

**Company:** Stealth Startup  
**Project Type:** Production Platform - AI-Powered CI/CD SaaS Infrastructure & Compliance  
**Status:** Live & Operational  
**Duration:** Mar 2026 - Present  
**Platform:** Stealth Startup - AI-powered CI/CD SaaS (GitHub-integrated control plane + ephemeral runners)  
**Deployment:** Google Cloud — GKE (application plane) + Compute Engine (ephemeral CI runners)  
**Role:** DevOps Engineer — own cloud infrastructure, platform engineering, deployment automation, security, and observability  

## Executive Summary

Stealth Startup is an AI-powered CI/CD SaaS. Customers connect their **GitHub Organization** via a **GitHub App**. the platform's **control / orchestration layer** provisions CI runners, orchestrates workflows and AI agents, analyzes build logs for RCA, manages Docker and GitHub Actions caching, and runs security/compliance scanning. **Ephemeral GCP Compute Engine runners** execute GitHub CI jobs on on-demand VMs, then return results and logs.

Application components (stateful and stateless) run on **GKE/Kubernetes**. Persistent data lives in **PostgreSQL**. Messaging is split by purpose: **NATS JetStream** is the distributed communication backbone for runners, capacity, and authenticator services (runner ↔ service / community service); **Pub/Sub** handles ad hoc triggers (add-ons, log analysis, debug, and similar one-shot jobs). **MicroCeph** provides distributed **caching** (up to **80% faster CI**). **Vertex AI** hosts open-model AI workloads today; a **GPU pipeline** is in progress to self-host open models and run inference internally. Environments progress from a fully breakable **Silicon** sandbox through **development**, **staging**, and **production**.

On the platform side: **everything is deployed with Infrastructure as Code**; **monitoring and alerting** are deployed as part of the platform; release operations include **fully automated inventory generation and cost auditing** (Slack-notified) for production readiness. Delivery uses **GitOps** with **semantic versioning** and **immutable images** for release lanes. **SOC 2–aligned** and **ISO/IEC 27001–aligned** controls (private networking, Zero Trust, least-privilege IAM, secure service-to-service) support enterprise SaaS. Observability uses **OpenTelemetry** and **Google Cloud Monitoring**. This is a **greenfield** startup platform — production is live and **gradually growing** as the product scales.

## Business Objectives

**Primary Goal:** Operate the production platform so Stealth Startup can run customer CI securely, scale runners on demand, remediate failures with AI, and stay compliance-ready:
- **Control plane + data plane:** Orchestration, runner capacity, databases, messaging, and AI remediation
- **Faster CI:** Caching and right-sized ephemeral runners (up to 80% faster CI execution)
- **Compliance:** SOC 2–aligned and ISO/IEC 27001–aligned infrastructure for enterprise SaaS readiness
- **Delivery:** Zero-touch Argo CD; reusable CI; semver RC → production tags; immutable service images (runners not versioned)
- **Ops automation:** Inventory generation and cost auditing with Slack notifications for production release readiness
- **Reliability:** Monitoring, alerting, and OpenTelemetry / Cloud Monitoring across the platform
- **Customer trust:** Sandboxed AI code examination; customer IP not retained after processing
- **Future:** BYOC — keep sensitive execution in the customer’s own cloud account

## Current Application Architecture

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

*Full detail: [architecture.md](architecture.md) · Diagram: [architecture-diagram.mmd](architecture-diagram.mmd)*

## GCP Configuration

| Area | Configuration |
|------|----------------|
| **GKE / Kubernetes** | Stateful and stateless application components (control / product services) |
| **Compute Engine** | Ephemeral, on-demand CI runners |
| **Runner machines** | Primarily AMD-based **C4D** in **us-central1**; frequently **32 vCPU / 128 GB** |
| **VM catalog** | ~**30 VM types** across environments |
| **PostgreSQL** | Persistent application data |
| **NATS JetStream** | Distributed communication for runners, capacity, and authenticator services (runner ↔ service / community service) |
| **Pub/Sub** | Ad hoc triggers — add-ons, log analysis, debug, and similar one-shot jobs |
| **MicroCeph** | Distributed **caching** for CI (up to 80% faster execution) |
| **Vertex AI** | Open-model AI workloads (current) |
| **GPU pipeline** | In development — self-host open models and run inference internally |
| **Environments** | **Silicon** (fully breakable) → **Development** → **Staging** → **Production** |

## AI Failure-Remediation Flow

1. A CI job runs on an ephemeral runner.  
2. Stealth Startup detects a failure and captures logs.  
3. The GitHub App supplies authorized repository context.  
4. Code is temporarily examined inside a **sandbox**.  
5. Multiple AI agents perform root-cause analysis and propose a fix.  
6. A pull request is raised.  
7. Security and quality checks run against it.  
8. The customer’s code owner reviews and decides whether to merge.  

**IP posture:** Customer IP is **not** intended to be retained after sandbox processing.

## Planned BYOC Architecture

```
Stealth Startup–managed infrastructure
└── Control plane, controller, and orchestration “brain”
                    │
                    ▼
Customer AWS / GCP environment
└── Data plane — CI execution, code, and sensitive workloads
```

- **Cloud-neutral direction:** replace GCP-specific Pub/Sub with **Kafka** where needed  
- **Centrally managed controller** stays with Stealth Startup  
- **Execution / data plane** runs in each customer’s own cloud account  
- Sensitive code and workloads stay inside the customer environment  

## Platform Operations: IaC, Monitoring, Release Automation

Public-safe summary of how the platform is operated (no internal system names or proprietary configs):

| Capability | What it means |
|------------|----------------|
| **Full IaC** | Cloud foundation and capacity are defined as code; operators pick config via a Jenkins script → PR to the infra repo’s **main** → **[Atlantis](https://www.runatlantis.io/)** plans/applies so everyone sees IAM and infra changes in one place |
| **GitOps delivery (Argo CD)** | Developers push the right **branch** / **tag**; **Argo CD** deploys. No manual cluster changes for normal releases |
| **Monitoring & alerting** | Observability and alerting are **deployed as infrastructure** (OpenTelemetry + Google Cloud Monitoring, plus platform alert paths) |
| **Inventory automation** | Automated **live cloud inventory** for release / ops visibility |
| **Cost auditing** | Automated **cost / billing audit** for production-oriented release readiness |
| **Slack notifications** | Inventory and cost audit outputs delivered automatically to Slack when triggered |

### Branches, CI, semantic versioning & immutable images

**Branches**
- **`dev`** — day-to-day coding. Commits drive **dev-only** images (testing). Dev is not a production version lane.
- **`main`** — release lane selection and tagging. Code quality CI has already run on the PR before merge; on **main**, owners create **version tags**.

**CI (reusable workflows)**
- Shared / reusable CI builds and publishes **immutable images** from the configured branch or tag.
- PR CI validates code quality before merge; promotion on **main** is driven by **tags**, not ad-hoc deploys.

**Version strategy (services — not runners)**
- **Dev:** separate **dev image** for testing only — **never `:latest`**. Tag format:
  - `YYYY.MM.DD.dev-sha-<shortsha>`
  - Example: `2026.08.23.dev-sha-a1b2c3d`
- **Staging / production path:** version name is chosen for what will go to production — **`MAJOR.MINOR.PATCH`**.
- On **main**, create an **RC tag** first: `MAJOR.MINOR.PATCH-rc.N` (e.g. rc.1 … rc.4, or whichever RC is selected).
- That RC promotes to the **production tag**: `MAJOR.MINOR.PATCH` (same major/minor/patch, without the RC suffix).
- **Runners are not versioned** — only service/application images follow this scheme.

**Argo CD behavior**
- Developers only need the right **branch** and **tag**; Argo CD reconciles the rest.
- **Dev:** image/tag in GitOps **updates automatically**.
- **Staging & production:** the **version tag is updated in the Argo CD / GitOps config** for that environment (manual pin of the chosen version).

### Infrastructure change path (Atlantis)

```
Operator runs Jenkins script (select infra config)
        ↓
PR opened to infra repo main
        ↓
Atlantis (https://www.runatlantis.io/) plans the PR
        ↓
Single-pane view: IAM, resources, and other IaC diffs
        ↓
Apply when approved
```

## Compliance Posture

| Framework | Role in this project |
|-----------|----------------------|
| **SOC 2** | Infrastructure and security controls aligned for enterprise SaaS (private networking, Zero Trust, least-privilege IAM, secure service-to-service, compliance scanning) |
| **ISO/IEC 27001** | Information security management alignment (correct standard for infosec — **not** “ISO 12001”) |

Controls are treated as **platform architecture**, not documentation-only.

## Key Achievements (LinkedIn / Resume)

- ✅ **Platform ownership** — Cloud infrastructure, platform engineering, deployment automation, security, and observability for an AI-powered CI/CD SaaS  
- ✅ **Full IaC + GitOps** — Terraform + **[Atlantis](https://www.runatlantis.io/)** for infra PRs; Argo CD deploys from branch/tag; monitoring and alerting deployed as platform infra  
- ✅ **Release ops automation** — Automated inventory generation and cost auditing with Slack notifications for production release readiness  
- ✅ **Up to 80% faster CI** — Distributed caching with MicroCeph and Kubernetes-native storage  
- ✅ **Production GCP platform** — Greenfield deployment of Kubernetes, Cloud Run, PostgreSQL, **NATS JetStream**, **Pub/Sub**, **MicroCeph**, Terraform, Helm, ArgoCD, and GitOps for a growing CI/CD SaaS  
- ✅ **SOC 2– and ISO/IEC 27001–aligned compliance** — Private networking, Zero Trust, least-privilege IAM, secure service-to-service communication  
- ✅ **Semver + immutable images** — `dev` tags `YYYY.MM.DD.dev-sha-<shortsha>` (never `:latest`); `main` RC `X.Y.Z-rc.N` → production `X.Y.Z`; reusable CI; **runners not versioned**  
- ✅ **End-to-end observability** — OpenTelemetry and Google Cloud Monitoring across cloud services, Kubernetes, and VMs  

## Technical Stack

**Integration:** GitHub App, GitHub Actions / customer CI jobs  
**Control plane:** Runner provisioning, workflow & AI-agent orchestration, build-log RCA, Docker/GHA caching, security/compliance scanning  
**Runners:** Ephemeral Compute Engine VMs (C4D / ~30 VM types, us-central1) — **not versioned**  
**Application plane:** GKE (stateful + stateless), Cloud Run (selected services)  
**Data:** PostgreSQL  
**Messaging:** NATS JetStream (runners / capacity / authenticator; runner ↔ service); Pub/Sub (ad hoc triggers: add-ons, log analysis, debug, …)  
**AI:** Vertex AI (current); GPU self-host pipeline (in progress)  
**IaC:** Terraform; Jenkins-assisted config selection → PR; **[Atlantis](https://www.runatlantis.io/)** plan/apply  
**Delivery:** Reusable CI; Helm; **Argo CD** GitOps (`dev` auto-pin; staging/prod tag update in GitOps)  
**Release:** Semantic versioning — `dev` → `YYYY.MM.DD.dev-sha-<shortsha>` (no `:latest`); RC `X.Y.Z-rc.N` → production `X.Y.Z`; immutable service images  
**Ops automation:** Inventory generation, cost/billing audit, Slack delivery  
**Caching:** MicroCeph (+ Kubernetes-native storage); Docker/GHA caches in control layer  
**Observability & alerting:** OpenTelemetry, Google Cloud Monitoring, deployed monitoring/alerting stack  
**Security & compliance:** SOC 2–aligned and ISO/IEC 27001–aligned controls; Zero Trust; private networking; least-privilege IAM; secure S2S; compliance scanning  

## Related Documentation

- **[Architecture Details](architecture.md)** — Layers, runners, AI flow, BYOC, compliance, ops automation  
- **[Metrics & Analysis](metrics.md)** — Scale, runner capacity, CI performance, compliance  
- **[Architecture Diagram](architecture-diagram.mmd)** — Mermaid source  

## Project Status

**Status:** Live & Operational (Mar 2026 – Present)  
**Ownership:** DevOps / platform engineering for production infrastructure, runner capacity, delivery, security, and observability  

**Note:** Application architecture reflects current product configuration from internal architecture discussions. Achievements and operational scale align with LinkedIn and resume experience. Proprietary internals from working repos are intentionally omitted.
