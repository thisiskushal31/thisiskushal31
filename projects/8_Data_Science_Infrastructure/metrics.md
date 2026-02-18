# Data Science Infrastructure - Metrics & Impact

## Business Impact Metrics

### Revenue backbone
- **₹700 Crore revenue marketing engine** — Data engineering and storefront serve brand and marketing (requirements from them). Infrastructure supported their recommendations and outcomes. Backbone of the revenue marketing engine. **Vector DB (Qdrant)** and embeddings power recommendations (e.g. search lipstick → get lipstick, ad placement, other brands’ lipstick; not unrelated products). Other brands’ recommendations drove ad revenue for Purplle (see [AdTech platform](https://github.com/thisiskushal31/thisiskushal31/tree/main/projects/6_Adtech.purplle.com_Deployment)).

### Cost saving (models for internal tasks)
- **50–60% cost saving** — Models were used for **internal tasks** such as **image tagging for Meta ads, Google Search ads**, and similar work that would otherwise require manual tagging. This **saved 50–60% of the cost** of doing those tasks manually.

## Scale & Deployment Metrics

### Scale & deployment (business context)
- **Business:** Data engineering and storefront serve brands and marketing. Recommendations and outcomes for them. ₹700 Cr revenue backbone. 50–60% cost saving on manual tasks.
- **Infra maintained:** CI/CD, servers, containerized applications (K8s), **vector DB (Qdrant)**, network (Nginx ingress, SSL, load balancers, internal domain).
- **Flow:** Jupyter VM for training → model uploaded to Vertex AI; K8s hits Vertex AI for inference; Cloud Function → K8s. **Multi-project:** Data engineering, data science, main Purplle app in separate GCP projects.

### What I managed (summary of facts)
- **CI/CD** — Pipelines, deployment, infra code only. **Servers** — VMs (e.g. Jupyter), IAM, service accounts. **Containerized applications** — K8s cluster, rollouts, deployment pipeline. **Vector DB (Qdrant)** — Operated and maintained; DS team owns embedding pipeline. **Network** — Nginx ingress, SSL, load balancers, internal domain. **Vertex AI (infra side)** — Access, integration. **Cloud Function (infra side)** — Provisioning; Cloud Function → K8s. **Security** — IAM, service accounts. **Multi-project GCP** — Infra across data engineering, data science, main Purplle app. No application or DS code—only CI/CD and infrastructure code.

### Ownership
- **Infra team (what I managed):** CI/CD, servers, K8s cluster, Qdrant vector DB, network (Nginx ingress, SSL, load balancers, internal domain), IAM/service accounts, Jupyter VM, Vertex AI (infra side), Cloud Function (infra provisioning), multi-project infra. No application code—only CI/CD and infrastructure code.
- **DS team:** Application code, models, DAGs; use of VM, Vertex AI, K8s deployments.

## Operational Metrics

### Production status
- **Live and operational** — Infrastructure supported recommendation backbone and DS training/serving flow.
- **Internal services** — DS-deployed services on K8s consumed by recommendation engine, data engineering, storefront.
