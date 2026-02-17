# Data Science Infrastructure – Technical Architecture

## System Overview

The **infrastructure/DevOps team** managed the **full infrastructure** for data science and recommendation platforms. The DS team owns application code and models; the infra team owned everything below—**no application or data science code** written by infra. Infra team wrote **CI/CD and infrastructure code** only, to make the infrastructure run.

**Two main infrastructures:**

1. **Distributed Kubernetes-based (containerized)** — Python services deployed as containerized workloads; Nginx ingress, SSL, load balancers, internal domain exposure so internal teams (recommendation engine, data engineering, storefront) can hit these services.
2. **Jupyter VM (training) and Vertex AI (model destination and inference endpoint)** — Jupyter on VM for training (IAM/service accounts managed by infra); model uploaded to Vertex AI (Vertex AI is the end of the pipeline; it only gets hit). K8s services hit Vertex AI for inference; Vertex AI only returns output. Cloud Function hits K8s first; triggers: Cloud Function, script on VM, or direct.

**Multi-project:** Data engineering in one GCP project, data science in another, main Purplle application in another. Infra managed across these projects.

## High-Level Flow

### Infrastructure 1: Kubernetes containerized services (internal services)
1. **Nginx ingress** — SSL/certifications, load balancers; entry point for traffic (managed by infra).
2. **Kubernetes cluster** — DS team deploys mainly **Python code as containerized services**; infra team owned cluster, deployment pipeline, and rollouts.
3. **Recommendation pipeline:** **DS team** manages the **embedding pipeline**; **infra team** manages the **Qdrant vector DB**. **Embeddings are used to power recommendations** (e.g. semantic similarity). Output is consumed by storefront and data engineering.
4. **Internal domain exposure** — Services exposed on internal domain so **other teams can hit them** (e.g. recommendation engine, data engineering, storefront). Data science workloads run behind these internal services.
5. **Consumers:** Internal systems—storefront (public-facing) or data engineering (internal)—request output (e.g. hit DB, get data, run transformation in VM or K8s script, get recommendation/result).

### Infrastructure 2: Jupyter VM (training) and Vertex AI (model destination; K8s hits it for inference)
1. **Jupyter VM** — Data science team uses for data fetch and **training**; **IAM, service accounts** managed by DevOps/infra team. Model is stored (e.g. in storage) then **uploaded to Vertex AI**. Vertex AI is the **end** of the training pipeline—it holds the model; it does not sit in the middle.
2. **Vertex AI** — Receives the uploaded model. **Only K8s hits Vertex AI** (for inference). Vertex AI only returns the inference output; it does not call anything else.
3. **K8s hits Vertex AI** — The **service deployed on Kubernetes** (Python recommendation/DS services) **hits Vertex AI** for inference when it needs model output. User-facing output can come from K8s (which may call Vertex AI), from Jupyter VM (e.g. script output), or via Cloud Function.
4. **Cloud Function hits K8s first** — In event-driven flow, **Cloud Function** triggers and **hits K8s first**; K8s then gets data (and may call Vertex AI). Cloud Function does not call Vertex AI directly.
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
- **Cloud Function** — In event-driven flow, **Cloud Function hits K8s first**; K8s then gets data (and may call Vertex AI). Cloud Function can also trigger VM/jobs. Cloud Function does not call Vertex AI directly.
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
- **[Architecture Diagram](architecture-diagram.mmd)** — Mermaid diagram for two infrastructures and flow
- **[Metrics](metrics.md)** — Business and operational metrics
