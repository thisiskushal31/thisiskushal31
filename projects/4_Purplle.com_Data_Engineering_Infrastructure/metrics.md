# Data Engineering Infrastructure - Metrics & Impact

## Business Impact Metrics

### Revenue backbone
- **₹700 Crore revenue backbone** — Data processing for **7 million users**: data collected **legally**, processed **anonymously**; used for business decisions (analytics) and to run **ML models**. Data treated as **PII** and handled in a very sensitive way.
- **Decision support** — Processed data helps business leaders (CEO-level, business leaders) take decisions—e.g. “This brand is doing great in this region or this age group”—so they can double down on insights and make more money using the same engine.

### Who uses the data
- Data is used by **business teams** (analytics, decision support) and by **other teams**: Data Science (models, analytics), Martech (campaigns), SCM (logistics, procurement, inventory), storefront (newer data, bulk operations), and legacy admin panel infrastructure, which powers the ₹700 Crore revenue management panel so business teams can run operations from the panel without technical intervention.

### Pipeline and consumers
- **Data flow:** MySQL → DE (cleanse, transform) → data warehousing (versioned); consumed by business teams (analytics, decision support), Data Science, Martech, SCM, storefront, and legacy admin panel.
- **Use cases:** Business decision support and analytics, models, campaigns (Martech), logistics and supply chain (SCM), bulk DB operations, campaign delivery and historical campaign data.
- **Outcome:** Infra for DE so the team could focus on data warehousing and processing; HA for K8s, Kafka, MySQL, DAG delivery to Composer.

### Ownership
- **Infra maintained:** GKE (DE services), ArgoCD, Helm, Terraform, GitLab CI, Jenkins; Kafka, MySQL, Pub/Sub; DAG sync (Git → GCS → Composer); Cloud Functions (networking, security); zero-trust.
- **DE team:** BigQuery, BigTable, ETL logic, DAG logic; application code on K8s.

## Scale & Deployment Metrics

### Scale & deployment (business context)
- **Triggers:** SCM, storefront, Martech, Data Science (or time-based) → DE API on K8s → event-driven (Cloud Function → Dataflow → ETL) or cron (Composer DAGs) → data warehousing.
- **Infra maintained:** K8s, CI/CD (ArgoCD, Helm, Terraform, GitLab CI, Jenkins), Kafka, MySQL, Pub/Sub, DAG sync to Composer, networking, zero-trust.
- **Consumers:** Business teams (analytics, decision support), Data Science (models, analytics), Martech (campaigns), SCM (logistics, inventory, procurement), storefront (newer data, bulk operations), legacy admin panel.

### What I managed (summary of facts)
- **K8s (GKE)** — Deployment and platform for DE services. **CI/CD** — ArgoCD, Helm, Terraform, GitLab CI, Jenkins; DAG sync pipeline. **Kafka, MySQL, Pub/Sub** — Infra-managed (Kafka, MySQL); Pub/Sub managed. **DAG delivery** — Git/GitLab → GCS → Composer. **Networking & security** — Zero-trust, connectivity for event-driven workflows. No ETL or DAG code—only infrastructure and CI/CD.

### Key Achievements (metrics view)
- ✅ **Infra for DE pipeline** — K8s, CI/CD, Kafka, MySQL, Pub/Sub, DAG sync; DE team could focus on data warehousing and processing.
- ✅ **HA for DE platform** — Managed Kafka, MySQL, deployment so DE did not operate infrastructure.
- ✅ **DAG delivery** — Pipeline to sync DAGs from repo to GCP Composer.
- ✅ **Event and cron paths** — Both supported by infra (event-driven and Composer DAGs).
- ✅ **Zero-trust and networking** — Connectivity and security for services.

## Operational Metrics

### Production status
- **Live and operational** — Infrastructure supported data engineering pipeline and data warehousing consumption by Data Science, Martech, SCM.
- **Ownership:** Infra—platform, CI/CD, Kafka, MySQL, Pub/Sub, DAG sync, networking, security; DE—data warehousing, ETL, DAG logic.
