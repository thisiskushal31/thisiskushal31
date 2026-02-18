# Data Science Infrastructure – Technical Architecture

## System Overview

**One infrastructure, one outcome.** This project (Data Science Infrastructure) is one project on that infrastructure—just like the [main e-commerce platform](https://github.com/thisiskushal31/thisiskushal31/tree/main/projects/2_Purplle.com_Management). The outcome is the same: recommendations and what data engineering and storefront need. They serve brand and marketing (requirements from them). That’s the ₹700 Crore revenue marketing engine. The DS team owns application code and models; the infra team owned everything below—**no application or data science code** written by infra. Infra team wrote **CI/CD and infrastructure code** only.

**What I managed (summary of facts):**
- **CI/CD** — Pipelines, deployment, infra and CI/CD code only (no application code).
- **Servers** — VMs (e.g. Jupyter), compute; IAM, service accounts.
- **Containerized applications** — Kubernetes cluster, rollouts, deployment pipeline; DS team deploys application code, I maintained the platform.
- **Vector DB (Qdrant)** — Operated and maintained Qdrant; DS team owns embedding pipeline; embeddings power recommendations.
- **Network** — Nginx ingress, SSL, load balancers, internal domain so recommendation engine, data engineering, and storefront can reach services.
- **Vertex AI (infra side)** — Access, integration; model upload from Jupyter, inference from K8s.
- **Cloud Function (infra side)** — Provisioning, wiring; event-driven Cloud Function → K8s.
- **Security** — IAM, service accounts, access.
- **Multi-project GCP** — Data engineering, data science, main Purplle app in separate projects; I managed infrastructure across them.

**Multi-project:** Data engineering in one GCP project, data science in another, main Purplle application in another. Infra managed across these projects.

## High-Level Flow

### Infra-maintained components (CI/CD, servers, containerized apps, vector DB, network)
1. **Nginx ingress** — SSL/certifications, load balancers; entry point for traffic (managed by infra).
2. **Kubernetes cluster** — DS team deploys mainly **Python code as containerized services**; infra team owned cluster, deployment pipeline, and rollouts.
3. **Vector DB (Qdrant)** — **Infra team** manages the **Qdrant vector DB**; **DS team** manages the **embedding pipeline**. **Embeddings power recommendations** (e.g. semantic similarity). Output is consumed by storefront and data engineering.
4. **Internal domain (network)** — Services exposed on internal domain so **data engineering and storefront** get the outcomes they need (recommendations, transformed data).
5. **Consumers:** Data engineering and storefront serve brand and marketing teams. They request recommendations and outcomes; recommendation engine and internal systems hit these services.

### Flow (training, inference, event-driven)
1. **Jupyter VM** — Data science team uses for data fetch and **training**; **IAM, service accounts** managed by DevOps/infra team. Model is stored (e.g. in storage) then **uploaded to Vertex AI**. Vertex AI is the **end** of the training pipeline—it holds the model; it does not sit in the middle.
2. **Vertex AI** — Receives the uploaded model. **Only K8s hits Vertex AI** (for inference). Vertex AI only returns the inference output; it does not call anything else.
3. **K8s hits Vertex AI** — The **service deployed on Kubernetes** (Python recommendation/DS services) **hits Vertex AI** for inference when it needs model output. User-facing output can come from K8s (which may call Vertex AI), from Jupyter VM (e.g. script output), or via Cloud Function.
4. **Cloud Function → K8s** — In event-driven flow, **Cloud Function → K8s**; K8s then gets data (and may call Vertex AI). Cloud Function does not call Vertex AI directly.
5. **Triggering training/jobs:** **Cloud Function** (event-driven), **script on the training VM**, or **direct** (IAM, service account).

## Architecture Layers (Infrastructure)

### 1. Ingress & access (infra owned)
- **Nginx ingress** — SSL/certifications, load balancers; routing into Kubernetes cluster.
- **Internal domain** — Expose services so internal teams (recommendation engine, data engineering, storefront) can hit DS services.
- **Ownership:** Platform/DevOps team.

### 2. Kubernetes cluster (infra owned; DS team deploys code)
- **Distributed containerized architecture** — Mainly Python services deployed as containers.
- **Deployment pipeline** — Infra team owned CI/CD and deployment; DS team owned application code.
- **Ownership:** Infra—cluster, ingress, CI/CD; DS team—application code running on cluster.

### 3. Jupyter VM (infra owned)
- **VM for Jupyter** — Data fetch, training; IAM and service accounts managed by infra team.
- **Flow** — Training complete → model uploaded to Vertex AI.
- **Ownership:** Infra—VM, IAM, service accounts; DS team—notebooks, training code, models.

### 4. Vertex AI (infra owned for access and integration)
- **Model destination and inference endpoint** — Models uploaded from Jupyter/VM to Vertex AI. **Only K8s calls Vertex AI** for inference; Vertex AI only returns output (it does not call anything). Vertex AI is at the end of the flow, not in the middle.
- **Ownership:** Infra—access, integration with pipeline; DS team—models and model code.

### 5. Event-driven and triggers (infra owned where it’s infra)
- **Cloud Function** — In event-driven flow, **Cloud Function → K8s**; K8s then gets data (and may call Vertex AI). Cloud Function can also trigger VM/jobs. Cloud Function does not call Vertex AI directly.
- **Direct** — IAM, service account to start job; or scripts on VM.
- **Ownership:** Infra—provisioning, security, wiring; DS team—event producers and consumers (application logic).

### 6. Multi-project
- **Data engineering** — Deployed in one GCP project.
- **Data science** — Deployed in another GCP project.
- **Main Purplle application** — Deployed in another GCP project.
- **Ownership:** Infra team managed infrastructure across these projects.

### 7. CI/CD & security (infra only)
- **CI/CD:** Infra team owned pipelines; wrote CI/CD and infrastructure code only; no application code.
- **Security:** SSL, IAM, service accounts, access; managed by platform team.
- **Ownership:** Platform/DevOps team.

## Key Design Points

| Area | Responsibility |
|------|----------------|
| SSL, Nginx ingress, load balancers, internal domain | Infra team |
| Kubernetes cluster, deployment pipeline | Infra team |
| Jupyter VM, IAM, service accounts | Infra team |
| Vertex AI (infra, access, integration) | Infra team |
| Cloud Function / triggers (infra side) | Infra team |
| Multi-project infrastructure | Infra team |
| CI/CD, security | Infra team (infra/CI/CD code only) |
| Qdrant vector DB | Infra team |
| Embedding pipeline (application side) | DS team |
| Application code, DS code, models, DAGs | DS team |

## Documentation

- **[README](README.md)** — Project overview, business impact (₹700 Cr backbone, 50–60% cost save), AdTech link
- **[Architecture Diagram](architecture-diagram.mmd)** — Mermaid diagram for infra flow
- **[Metrics](metrics.md)** — Business and operational metrics
