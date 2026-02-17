# Data Science Infrastructure - Metrics & Impact

## Business Impact Metrics

### Revenue backbone
- **₹700 Crore revenue system** — This infrastructure was the **backbone** of the ₹700 Crore revenue system. Recommendations were passed to users (e.g. search lipstick → get lipstick, ad placement, other brands’ lipstick; not unrelated products). Other brands’ recommendations drove ad revenue for Purplle (see also [AdTech platform](https://github.com/thisiskushal31/thisiskushal31/tree/main/projects/6_Adtech.purplle.com_Deployment)).

### Cost saving (models for internal tasks)
- **50–60% cost saving** — Models were used for **internal tasks** such as **image tagging for Meta ads, Google Search ads**, and similar work that would otherwise require manual tagging. This **saved 50–60% of the cost** of doing those tasks manually.

## Scale & Deployment Metrics

### Two infrastructures
- **Infrastructure 1:** Distributed Kubernetes containerized services (mainly Python); Nginx ingress, SSL, load balancers, internal domain exposure; internal consumers (recommendation engine, data engineering, storefront).
- **Infrastructure 2:** Jupyter VM for training → model uploaded to Vertex AI (Vertex AI is the endpoint at the end); K8s hits Vertex AI for inference; Cloud Function hits K8s first. Triggers: Cloud Function, script on VM, or direct.
- **Multi-project:** Data engineering, data science, and main Purplle application in separate GCP projects; infra managed across them.

### Ownership
- **Infra team:** SSL, Nginx ingress, load balancers, internal domain, K8s cluster, CI/CD, IAM/service accounts, Jupyter VM, Vertex AI (infra side), Cloud Function (infra provisioning), multi-project infra. **No application code**—only CI/CD and infrastructure code.
- **DS team:** Application code, models, DAGs; use of VM, Vertex AI, K8s deployments.

## Operational Metrics

### Production status
- **Live and operational** — Infrastructure supported recommendation backbone and DS training/serving flow.
- **Internal services** — DS-deployed services on K8s consumed by recommendation engine, data engineering, storefront.
