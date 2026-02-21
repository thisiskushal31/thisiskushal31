# Data Engineering Infrastructure – Technical Architecture

## System Overview

The **Data Engineering Infrastructure** at Purplle.com supports the pipeline from primary databases (MySQL) to data warehousing (BigQuery, BigTable). Data is cleansed, transformed, and loaded (ETL) by the Data Engineering team; the result is versioned and consumed by business teams, Data Science, Martech, and Supply Chain Management for analytics, decision support, models, campaigns, and operations.

**Infrastructure focus (platform/DevOps ownership — infrastructure only):** Kubernetes (GKE) for DE services, CI/CD (ArgoCD, Helm, Terraform, GitLab CI, Jenkins), Kafka, MySQL, Pub/Sub, DAG sync (Git → GCS → GCP Composer/Airflow), Cloud Functions (event-driven), and networking/zero-trust. Data Engineering team owned BigQuery, BigTable, ETL logic, and DAG logic; this document describes the platform from an infrastructure perspective.

**What I managed (summary of facts):**
- **K8s (GKE)** — Deployment and platform for DE services (Java, Go, Scala, Python).
- **CI/CD** — ArgoCD, Helm, Terraform; GitLab CI (CI), Jenkins (CD); DAG sync pipeline (Git/GitLab → GCS → Composer).
- **Kafka** — Managed by infra.
- **MySQL** — Primary DB (source); managed by infra.
- **Pub/Sub** — Managed service.
- **Cloud Functions** — Event-driven; DE owned logic; infra owned networking and security.
- **Networking & zero-trust** — Connectivity between services.
- **BigQuery, BigTable, ETL, DAGs** — DE team; infra did not write this code.

## High-Level Data Flow

1. **Triggers** — SCM, storefront, Martech, or Data Science change; or time-based schedule.
2. **DE API (K8s)** — Data Engineering API and services deployed on GKE; entry point for the data engineering solution.
3. **Event path** — Cloud Function → Dataflow → ETL (DE-designed) → data warehousing (BigQuery, BigTable).
4. **Cron path** — GCP Composer (Airflow) DAGs run on schedule; DAGs synced from Git/GitLab to GCS via GitLab CI, then appear in Composer.
5. **Data warehousing** — Versioned data in BigQuery/BigTable; owned by DE team.
6. **Consumers** — Business teams (analytics, decision support), Data Science (models, analytics), Martech (campaigns, historical campaign data), SCM (logistics, bulk DB updates), storefront (newer data to users), legacy admin panel (revenue management operations).

## Architecture Layers

### 1. Triggers & entry (infra supports)
- **Entry point:** DE API deployed on Kubernetes; triggered by other Purplle services (storefront, SCM, Martech, Data Science) or by time.
- **Ownership:** DE team owns API and service logic; infra owns K8s, deployment, networking.

### 2. Kubernetes (GKE) — infra owned
- **DE services** — Java, Go, Scala, Python services; deployed via ArgoCD, Helm, Terraform.
- **CI/CD** — GitLab CI (CI), Jenkins (CD); infra and deployment code only.
- **Ownership:** Infra—cluster, deployment pipeline, rollouts; DE—application code on cluster.

### 3. Messaging & primary DB — infra owned (where stated)
- **Kafka** — Managed by infra; DE team uses it, does not operate it.
- **MySQL** — Primary database (source of data); managed by infra.
- **Pub/Sub** — Managed service for messaging.
- **Ownership:** Infra—Kafka, MySQL, Pub/Sub operations.

### 4. Event-driven path — split ownership
- **Cloud Function** — Triggers Dataflow; DE may own function logic; infra owns provisioning, networking, zero-trust.
- **Dataflow** — ETL jobs; DE-owned design and logic.
- **Flow:** Cloud Function → Dataflow → ETL → data warehousing.
- **Ownership:** Infra—connectivity, security; DE—ETL and Dataflow logic.

### 5. Cron path — DAG sync infra owned
- **GCP Composer (Airflow)** — DAGs stored in GCS; Composer reads from bucket.
- **DAG sync** — GitLab CI pipeline: DAGs in Git/GitLab repo → build → GCS bucket → visible in Composer/Airflow.
- **Ownership:** Infra—pipeline that gets DAGs from repo to Composer; DE—DAG logic and content.

### 6. Data warehousing — DE owned
- **BigQuery, BigTable** — Managed by DE team (tables, schema, usage).
- **Ownership:** DE team.

### 7. Networking & security — infra owned
- **Zero-trust** — Connectivity and security for Cloud Functions, event-driven workflows, and service-to-service.
- **Keyless authentication** — Service accounts managed via GCP IAM; minimum permissions required with custom roles; used to control flow and access.
- **Ownership:** Platform/DevOps team.

## Key Design Points

| Area | Responsibility |
|------|----------------|
| GKE, K8s deployment, ArgoCD, Helm, Terraform | Infra team |
| GitLab CI, Jenkins (CI/CD) | Infra team |
| DAG sync (Git/GitLab → GCS → Composer) | Infra team |
| Kafka, MySQL, Pub/Sub | Infra team (Kafka, MySQL); Pub/Sub managed service |
| Cloud Function (networking, security, provisioning) | Infra team |
| Dataflow, ETL logic, BigQuery, BigTable, DAG logic | DE team |
| DE application code on K8s | DE team |

## Infrastructure Components

### Kubernetes (GKE)
- **Cluster:** DE services (Java, Go, Scala, Python) run on GKE.
- **Deployment:** ArgoCD, Helm, Terraform for infra and app deployment.
- **High availability:** Platform and deployment managed so DE team can rely on the cluster.

### CI/CD
- **ArgoCD, Helm, Terraform** — Infra and application deployment to GKE.
- **GitLab CI** — CI (e.g. DAG sync: repo → GCS → Composer).
- **Jenkins** — CD for deployment pipelines.
- **DAG sync:** Git/GitLab → GCS bucket → GCP Composer so DAGs appear in Airflow.

### Kafka, MySQL, Pub/Sub
- **Kafka** — Infra-managed; DE team uses for messaging.
- **MySQL** — Primary database; infra-managed; source for ETL.
- **Pub/Sub** — Managed service for event-driven messaging.

### GCP Composer (Airflow)
- **DAGs** — Stored in GCS; Composer reads from bucket.
- **Sync** — Infra pipeline ensures DAGs in repo reach the bucket and thus Composer.

### Cloud Functions & event-driven
- **Cloud Function** — Can trigger Dataflow (event-driven); infra owns networking and zero-trust.
- **Dataflow** — DE-owned ETL; infra does not write ETL code.

### Monitoring & operations
- **Observability:** Infra maintains platform health so DE can focus on data warehousing and processing.
- **Ownership:** Infra ensures HA for K8s, Kafka, MySQL, DAG delivery.

## Documentation

- **[README](README.md)** — Project overview, business objectives, metrics, technical stack
- **[Architecture Diagram](architecture-diagram.mmd)** — Mermaid diagram for infra and data flow
- **[Metrics](metrics.md)** — Scale, deployment, operational metrics
