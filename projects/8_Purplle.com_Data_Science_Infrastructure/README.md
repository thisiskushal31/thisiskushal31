# Data Science Infrastructure | Purplle.com

## Project Overview

**Company:** Purplle.com  
**Project Type:** Production Platform - Data Science / ML Infrastructure (Infrastructure only)  
**Status:** Live & Operational  
**Duration:** Jun 2023 - Feb 2026  
**Platform:** One infrastructure, one outcome—this project powers the ₹700 Crore revenue marketing engine and what data engineering and storefront need (recommendations, outcomes). Infra maintained: CI/CD, servers, containerized applications (K8s), vector DB (Qdrant), network (Nginx, SSL, internal domain). Jupyter → Vertex AI; K8s → Vertex AI for inference; Cloud Function → K8s; multi-project GCP.  
**Deployment:** GCP (Kubernetes, Nginx ingress, SSL, internal domain; Jupyter VM, Vertex AI, Cloud Functions, Qdrant vector DB; data engineering, data science, and main Purplle app in separate projects)  
**Role:** DevOps / Infrastructure Engineer — managed infrastructure only; did not write application code  
**Note:** Managed the full infrastructure day-to-day: SSL/certifications, Nginx ingress, load balancers, internal domain exposure, Kubernetes cluster, vector DB (Qdrant), CI/CD, security (IAM, service accounts). Did not write a single piece of application/DS code—only CI/CD and infrastructure code to make the infrastructure run.

## Executive Summary

**One infrastructure, one outcome.** This project (Data Science Infrastructure) is **one project** on that infrastructure—just like the [main e-commerce platform](https://github.com/thisiskushal31/thisiskushal31/tree/main/projects/2_Purplle.com_Management). The outcome is the same: recommendations, what data engineering and storefront need, ₹700 Crore revenue marketing engine.

**What infra did (maintaining):**
- **CI/CD** — Pipelines, deployment, infra code only.
- **Servers** — VMs (e.g. Jupyter), compute.
- **Containerized applications** — Kubernetes cluster, rollouts, deployment pipeline; DS team deploys application code, infra maintains the platform.
- **Vector DB (Qdrant)** — Infra-managed. DS team owns embedding pipeline; embeddings power recommendations.
- **Network** — Ingress (Nginx), SSL, load balancers, internal domain so teams (recommendation engine, data engineering, storefront) can reach services.

**Flow (for reference):** Jupyter VM → model to Vertex AI; K8s hits Vertex AI for inference; Cloud Function → K8s; triggers: Cloud Function, script on VM, or direct. Multi-project GCP. **Ownership:** Infra only—no application or DS code; CI/CD and infrastructure code so the infrastructure runs.

### What I managed (summary of facts)

- **CI/CD** — Pipelines, deployment, infra and CI/CD code only (no application code).
- **Servers** — VMs (e.g. Jupyter for training); compute; IAM, service accounts.
- **Containerized applications** — Kubernetes cluster, rollouts, deployment pipeline; DS team deploys application code, I maintained the platform.
- **Vector DB (Qdrant)** — Operated and maintained Qdrant; DS team owns embedding pipeline; embeddings power recommendations.
- **Network** — Nginx ingress, SSL/certifications, load balancers, internal domain exposure so recommendation engine, data engineering, and storefront can reach services.
- **Vertex AI (infra side)** — Access, integration, and infra support for model upload (from Jupyter) and inference (K8s calls Vertex AI).
- **Cloud Function (infra side)** — Provisioning and wiring; event-driven flow Cloud Function → K8s.
- **Security** — IAM, service accounts, access; no application or DS code written by me—only CI/CD and infrastructure code.
- **Multi-project GCP** — Data engineering, data science, and main Purplle app in separate projects; I managed infrastructure across them.

## Business Impact

### One infrastructure, one outcome — ₹700 Crore revenue marketing engine
- This project is one project on that infrastructure (like the [main e-commerce platform](https://github.com/thisiskushal31/thisiskushal31/tree/main/projects/2_Purplle.com_Management)). 
- Outcome: recommendations and what data engineering and storefront need. Data engineering and storefront serve brand and marketing teams (requirements from them). That’s the **₹700 Crore revenue marketing engine**. It **spits out recommendations** and **generates outcomes** and supports everything **data engineering** and **storefront** need. The **DS team manages the embedding pipeline**; the **infra team manages the Qdrant vector DB**. **Embeddings power recommendations** to users (e.g. search for lipstick → get relevant lipstick, ad placement, other brands’ lipstick; not unrelated products). Other brands’ recommendations drove ad revenue for Purplle (see [AdTech platform](https://github.com/thisiskushal31/thisiskushal31/tree/main/projects/6_Purplle.com_Adtech_Deployment)).

### Models for internal tasks — 50–60% cost saving
- Models were used for **internal tasks** such as **image tagging for Meta ads, Google Search ads**, and similar work that would otherwise require manual tagging. This **saved 50–60% of the cost** of doing those tasks manually.

## Business Objectives

**Primary Goal:** Maintain infrastructure so the outcome (recommendations, what data engineering and storefront need) is delivered. Infra maintained: CI/CD, servers, containerized applications (K8s), vector DB (Qdrant), network. No application or DS code written by infra.

**Business Requirements:**
- **Infra maintains:** CI/CD, servers, containerized applications (K8s), vector DB (Qdrant), network (Nginx ingress, SSL, load balancers, internal domain). Data engineering and storefront get requirements from brands and marketing and get recommendations and outcomes.
- **Flow:** Jupyter VM for training → model to Vertex AI; K8s hits Vertex AI for inference; Cloud Function → K8s; script on VM or direct for triggers.
- **Multi-project:** Data engineering, data science, and main Purplle app in separate GCP projects; infra managed across them.
- **CI/CD and security:** Infra team owned CI/CD and security; no application code written by infra.

**Business Drivers:**
- Recommendation and DS outputs power revenue and ads; infra must be reliable and secure.
- Clear split: DS team owns code and models; infra team owns infrastructure, CI/CD, and operations.

## Business Metrics

### Scale & Deployment
- **Infra maintained:** CI/CD, servers, containerized applications (K8s), vector DB (Qdrant), network (Nginx ingress, SSL, load balancers, internal domain). Flow: Jupyter → Vertex AI, K8s → Vertex AI for inference, Cloud Function → K8s.
- **Multi-project:** Data engineering, data science, main Purplle application in separate GCP projects.
- **Ownership:** Infra team—CI/CD, servers, K8s cluster, **Qdrant vector DB**, network (ingress, SSL, load balancers, internal domain), IAM/service accounts, VM, Vertex AI (infra side); DS team—application code, models, embedding pipeline.

### Key Achievements

- ✅ **₹700 Crore revenue backbone** — Infrastructure supported recommendations and outcomes for data engineering and storefront (they serve brand and marketing). Backbone of the revenue marketing engine.
- ✅ **50–60% cost saving** — Models for internal tasks (e.g. image tagging for Meta/Google ads) reduced manual cost.
- ✅ **Vector DB (Qdrant) and network** — Maintained vector DB and network so embeddings power recommendations consumed by storefront and data engineering.
- ✅ **Multi-project, production ready** — Infra managed across data engineering, data science, and main Purplle projects; reliable so DS and other teams could rely on services.
- ✅ **CI/CD and security** — Owned CI/CD and security; no application code written by infra.

## Technical Stack (Infrastructure side)

**Cloud:** GCP, multi-project (data engineering, data science, main app)  
**Kubernetes:** Nginx ingress, SSL/certifications, load balancers, internal domain exposure; Python containerized services (DS team code)  
**Vector DB:** **Qdrant** (infra-managed); DS team manages **embedding pipeline**; **embeddings power recommendations** consumed by storefront and data engineering  
**Training:** Jupyter VM (model trained, then uploaded to Vertex AI); IAM, service accounts (infra managed)  
**Serving:** K8s hits Vertex AI for inference; Vertex AI only returns output  
**Event-driven:** Cloud Function → K8s; script on VM or direct for training/job triggers  
**CI/CD & security:** Git, pipelines, infra and CI/CD code only; security and access managed by infra team  

## Architecture Overview

![Data Science Infrastructure](../../assets/projects/8_Purplle.com_Data_Science_Infrastructure.png)

*Infrastructure for the ₹700 Cr revenue marketing engine. Data engineering and storefront serve brands and marketing. Recommendations and outcomes for them. Maintained CI/CD, servers, containerized applications (K8s), vector DB (Qdrant), network. See [Architecture Details](architecture.md) and [Architecture Diagram](architecture-diagram.mmd).*

**Infrastructure ownership (platform/DevOps team):**
- **Infra only:** SSL, Nginx ingress, load balancers, internal domain, Kubernetes cluster, CI/CD, IAM/service accounts, Jupyter VM and Vertex AI (infra side). No application or DS code written by infra.
- **DS team:** Application code, models, DAGs; use of VM, Vertex AI, K8s deployments.

## Documentation

- **[Architecture Details](architecture.md)** — What I managed (CI/CD, servers, K8s, vector DB (Qdrant), network, Vertex AI infra, Cloud Function); flow (Jupyter → Vertex AI; K8s hits Vertex AI; Cloud Function → K8s); multi-project, triggers
- **[Architecture Diagram](architecture-diagram.mmd)** — Mermaid diagram for infra flow
- **[Metrics & Analysis](metrics.md)** — Business impact (₹700 Cr backbone, 50–60% cost save), scale, deployment

---

**Note:** Maintained infrastructure for the ₹700 Cr revenue marketing engine. Data engineering and storefront serve brands and marketing. Recommendations and outcomes for them. CI/CD, servers, containerized applications (K8s), **Qdrant vector DB**, network (SSL, ingress, load balancers, internal domain), Jupyter VM and Vertex AI (infra side), across multiple GCP projects. No application or data science code—only CI/CD and infrastructure code.
