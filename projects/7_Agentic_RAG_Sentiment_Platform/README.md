# Agentic RAG-Based Sentiment Intelligence Platform | Purplle.com

## Project Overview

**Company:** Purplle.com  
**Project Type:** Production Platform – AI/ML Infrastructure (Agentic RAG)  
**Status:** Live & Operational  
**Platform:** Sentiment intelligence for influencer marketing content  
**Role:** DevOps / Platform Engineer (AI Infrastructure)  
**Note:** Infrastructure, GPU workloads, vector DB, and CI/CD owned by platform team. Core embedding logic and RAG application developed by engineering team.

## Executive Summary

Purplle commissions influencers to create branded video content (e.g., product placements, “add this lipstick” campaigns). Purplle owns this content and uses it for internal AI-driven analysis. The business needed to answer: *Which content is working? What sentiment is right or wrong? What in the content performed well or poorly?* — and to surface the best content via a simple, search-like experience (e.g., “best content in the last 2 days” or “last 7 days”).

An **agentic RAG-based sentiment intelligence platform** was built: video and engagement data are processed through a self-deployed LLM (ChatGPT) in a distributed Kubernetes architecture to generate embeddings, which are stored in Qdrant. Semantic search (cosine similarity, metadata filters, hash-based indexing) powers an agentic application that answers natural-language queries and delivers decision-ready results (e.g., Instagram links, paid content, sentiment labels). **No persistent long-running LLM deployment** — the system is orchestration- and vector-DB-centric.

Infrastructure responsibilities included: designing and operating the distributed architecture, deploying and maintaining GPU-based embedding services (CUDA), running the Qdrant vector DB cluster, CI/CD for AI services and RAG components, and ensuring high availability and faster time-to-result for the business.

## Business Objectives

**Primary Goal:** Enable brand and marketing teams to discover the best influencer content, understand sentiment (right/wrong), and see what worked or didn’t in content — via a simple, search-like interface — to optimize campaigns and decision-making.

**Business Requirements:**
- **Content ownership:** Purplle-paid influencer videos (YouTube, Instagram, etc.) are owned and used for internal AI analysis.
- **Semantic search:** Find best content by time window (e.g., last 2 days, 7 days) and by criteria (sentiment, performance).
- **Decision support:** Surface links (e.g., Instagram), paid vs organic, and sentiment (right/wrong) for each piece of content.
- **Reliability & speed:** High-availability infrastructure and faster results for business users.
- **Scalability:** Support growing volume of video and embedding data.

**Business Drivers:**
- Optimize influencer campaign spend by understanding which content and sentiment perform best.
- Replace manual or ad-hoc analysis with a single, searchable AI-powered view.
- Keep data and models under Purplle control (self-deployed LLM, private pipelines).

## Business Metrics

### Scale & Deployment
- **Deployment:** Kubernetes-based distributed architecture; GPU-enabled workloads for embedding services.
- **Vector DB:** Qdrant cluster for semantic search (cosine similarity, metadata filters, hash mapping).
- **Uptime:** High-availability design for AI pipeline and search services.
- **Architecture:** Agentic RAG — orchestration + vector DB; no persistent LLM deployment.

### Key Achievements

- ✅ **Agentic RAG platform** — End-to-end flow: video ingestion → LLM (self-deployed in K8s) → embeddings → Qdrant → semantic search → agentic answers for business queries.
- ✅ **GPU-based embedding pipeline** — CUDA-compatible nodes and scheduling for embedding generation at scale.
- ✅ **Qdrant operations** — Production vector DB for cosine similarity, metadata filters, and hash-based indexing.
- ✅ **CI/CD for AI infra** — Pipelines for AI services, RAG components, vector DB updates, and safe rollouts.
- ✅ **High availability & faster results** — Infrastructure reliability and reduced time-to-insight for business.
- ✅ **Architecture-level ownership** — Root-cause analysis, debugging across infra and application boundaries, improved fault tolerance and recovery.

## Technical Stack

**Cloud & Infrastructure:** Kubernetes (GKE or equivalent), GPU nodes (CUDA)  
**AI/ML:** Self-deployed ChatGPT (distributed architecture), Python-based embedding models  
**Vector DB:** Qdrant (cosine similarity, metadata filters, hash mapping)  
**Orchestration & agents:** MCP (Model Context Protocol), agentic workflows, RAG  
**CI/CD:** Jenkins / GitLab CI (or equivalent) for AI services and RAG components  
**Containers:** Docker, Kubernetes Deployments/Services  
**Monitoring:** Prometheus, Grafana (or equivalent) for infra and pipeline health  

## System Flow (Infrastructure View)

1. **Video & engagement data** ingestion into the platform.
2. **Distributed processing** services in Kubernetes.
3. **GPU-based embedding generation** (CUDA) from video/content via self-deployed LLM.
4. **Vector storage** in Qdrant with metadata and hash-based indexing.
5. **Cosine similarity** and semantic search over the vector DB.
6. **MCP / agentic orchestration** for tool-aided LLM access and RAG workflows.
7. **RAG-based comparison** of new vs historical content and sentiment.
8. **User queries** (e.g., “best content in last 2 days”) → **answers** with links, sentiment (right/wrong), and decision support.
9. **Continuous embedding updates** and pipeline maintenance via CI/CD.

## Architecture Overview

*See [Architecture Details](architecture.md) for full technical design and [Architecture Diagram](architecture-diagram.mmd) for Mermaid source.*

## Documentation

- **[Architecture Details](architecture.md)** — Technical architecture, data flow, and infrastructure design.
- **[Architecture Diagram](architecture-diagram.mmd)** — Mermaid diagram source.
- **[Metrics & Impact](metrics.md)** — Performance, reliability, and business impact metrics.

---

**Note:** This platform supports production use for influencer content analysis and campaign optimization. Infrastructure and platform engineering (Kubernetes, GPU workloads, Qdrant, CI/CD) were owned by the platform/DevOps team; core embedding and RAG application logic were developed by the engineering team.
