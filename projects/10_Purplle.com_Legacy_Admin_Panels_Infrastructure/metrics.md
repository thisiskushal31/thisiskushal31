# Legacy Admin Panels Infrastructure - Metrics & Impact

## Business Impact Metrics

### Revenue backbone
- **Backbone of the ₹700 Crore revenue management panel** — **Business teams use the legacy panel outcomes** to run business operations seamlessly without the intervention of technical teams. Other teams own the code; business teams go to the panel, click a few buttons, and it happens (front banner, campaigns, Martech, logistics).

### Platform and who uses the outcomes
- **Use case:** Business teams use the panel outcomes to deliver changes: front banner, newer campaigns, Martech campaigns, logistic changes. Other teams (Storefront, Martech, SCM, Data Engineering, Data Science) own and maintain the application code.
- **Flow:** Business teams → front-end (panel) → legacy backend (PHP monolith) → internal load balancer → distributed K8s when needed. MySQL backs legacy.
- **Outcome:** Infra for legacy admin panels so business teams can reliably use the panel to push changes; hybrid legacy + distributed architecture supported via internal load balancer.

### Ownership
- **Infra maintained:** CI/CD, network, monolith deployment, load balancer (high load), MySQL, internal load balancer (legacy → distributed K8s).
- **Code:** Storefront, Martech, SCM, Data Engineering, Data Science own and maintain application code.

## Scale & Deployment Metrics

### Scale & deployment (business context)
- **Legacy:** PHP monolith (2011 to 2015); code updates largely paused around 2015, very few updates since then till present; maintained from front-end side; front-end calls backend.
- **Distributed:** Micro-service modernization; microservices on K8s; legacy calls via internal load balancer.
- **Infra maintained:** CI/CD, network, monolith deployment, external load balancer (high load), MySQL, internal load balancer.

### What I managed (summary of facts)
- **CI/CD** — Pipelines and deployment for monolith and related infra. **Network** — Connectivity for admin panels and legacy-to-distributed path. **Monolith deployment** — Deploying and operating legacy backend. **Load balancer** — Under high load; managed by DevOps. **MySQL** — Backing legacy architecture; connections managed by infra. **Internal load balancer** — Legacy → distributed K8s; managed by DevOps. No application code—only infrastructure and operations.

### Key Achievements (metrics view)
- ✅ **Infra for legacy admin panels** — CI/CD, network, monolith deployment, load balancer, MySQL, internal load balancer.
- ✅ **Load balancer under high load** — Managed by DevOps for availability.
- ✅ **Legacy–distributed path** — Internal load balancer between legacy and K8s; managed by DevOps.
- ✅ **MySQL and connections** — Database and connections for legacy architecture managed by infra.
- ✅ **Hybrid legacy + distributed** — Infra supports both legacy and micro-service modernization.

## Operational Metrics

### Production status
- **Live and operational** — Infrastructure supports legacy backend admin panels and business team delivery of banner, campaigns, Martech, and logistic changes.
- **Ownership:** Infra—CI/CD, network, monolith deployment, load balancer, MySQL, internal load balancer; teams—application code (Storefront, Martech, SCM, Data Engineering, Data Science).
