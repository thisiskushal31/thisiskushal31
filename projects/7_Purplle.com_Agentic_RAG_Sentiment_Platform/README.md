# RAG Sentiment Platform - Influencer Content Intelligence | Purplle.com

## Project Overview

**Company:** Purplle.com  
**Project Type:** Production Platform - AI/ML Infrastructure (Agentic RAG)  
**Status:** Live & Operational  
**Duration:** Dec 2024 - Feb 2025  
**Platform:** Sentiment intelligence for influencer marketing content  
**Deployment:** Production Environment (AI Pipeline & Vector Search)  
**Role:** DevOps / Platform Engineer (AI Infrastructure) — **managed infrastructure only**  
**Note:** I managed infrastructure only: Kubernetes, GPU workloads, Qdrant vector DB, and CI/CD for AI and RAG. Did not write application or RAG code. Core embedding logic and RAG application were developed by the engineering team.

## Executive Summary

Purplle commissions influencers to create branded video content (e.g., product placements, “add this lipstick” campaigns) and owns this content for internal use. The business faced a critical question: *Which content is working? What sentiment is right or wrong? What in the content performed well or poorly?* — and needed to surface the best content via a simple, search-like experience (e.g., “best content in the last 2 days” or “last 7 days”) to optimize campaign spend and decision-making.

An **agentic RAG-based sentiment intelligence platform** was built and operated in production. Video and engagement data are processed through a self-deployed LLM (ChatGPT) in a distributed Kubernetes architecture to generate embeddings, which are stored in Qdrant. Semantic search (cosine similarity, metadata filters, hash-based indexing) powers an agentic application that answers natural-language queries and delivers decision-ready results — links (e.g., Instagram), paid content flags, sentiment (right/wrong), and what worked or didn’t — so brand and marketing teams can act faster. The system is **orchestration- and vector-DB-centric** with **no persistent long-running LLM deployment**.

I managed **infrastructure only**: distributed architecture, GPU-based embedding pipeline (CUDA), production Qdrant cluster, and CI/CD for AI services and RAG components — ensuring high availability and faster time-to-result. I did not write application or RAG code; core embedding and RAG application logic were developed by the engineering team.

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
- Enable data-driven campaign optimization and faster decision-making for brand teams.

## Business Metrics

### Scale & Deployment
- **Deployment:** Kubernetes-based distributed architecture; GPU-enabled workloads for embedding services.
- **Vector DB:** Qdrant cluster for semantic search (cosine similarity, metadata filters, hash mapping).
- **Uptime:** High-availability design for AI pipeline and search services.
- **Architecture:** Agentic RAG — orchestration + vector DB; no persistent LLM deployment.

### Business Scale
- **Content scope:** Purplle-owned influencer video content (YouTube, Instagram, etc.) ingested, analyzed, and searchable.
- **Query patterns:** Natural-language queries over configurable time windows (e.g., last 2 days, 7 days) and filters.
- **Users:** Brand and marketing teams consuming decision-ready answers (links, sentiment, paid content flags).
- **Outcome:** Data-driven campaign optimization and reduced time-to-insight from a single search-like interface.

### Key Achievements

- ✅ **Agentic RAG platform** — End-to-end flow: video ingestion → LLM (self-deployed in K8s) → embeddings → Qdrant → semantic search → agentic answers for business queries.
- ✅ **GPU-based embedding pipeline** — CUDA-compatible nodes and scheduling for embedding generation at scale; Python-based embedding models and pipelines.
- ✅ **Qdrant operations** — Production vector DB cluster for cosine similarity, metadata filters, and hash-based indexing; maintained ingestion pipelines and search performance.
- ✅ **CI/CD for AI infra** — Pipelines for AI services, RAG components, vector DB updates, and safe rollouts of model and infrastructure changes.
- ✅ **High availability & faster results** — Infrastructure reliability and reduced time-to-insight for business; architecture-level debugging and fault tolerance improvements.
- ✅ **Security & ownership** — Self-deployed ChatGPT and Qdrant keep data and models under Purplle control; no reliance on external LLM APIs for core pipelines.
- ✅ **MCP & agentic orchestration** — Supported MCP-based agent workflows and RAG application for tool-aided LLM access and decision-ready output.
- ✅ **Production ready** — Platform live and operational for influencer content analysis and campaign optimization.

## Technical Stack

**Cloud & Infrastructure:** Kubernetes (GKE or equivalent), GPU nodes (CUDA)  
**AI/ML:** Self-deployed ChatGPT (distributed architecture), Python-based embedding models  
**Vector DB:** Qdrant (cosine similarity, metadata filters, hash mapping)  
**Orchestration & agents:** MCP (Model Context Protocol), agentic workflows, RAG  
**CI/CD:** Jenkins / GitLab CI (or equivalent) for AI services and RAG components  
**Containers:** Docker, Kubernetes Deployments/Services  
**Monitoring:** Prometheus, Grafana (or equivalent) for infra and pipeline health  

## Architecture Overview

![RAG Sentiment Platform](../../assets/projects/7_Purplle.com_Agentic_RAG_Sentiment_Platform.png)

*Platform flow: Video → K8s/GPU → Embeddings → Qdrant → RAG/Agent → Answers. See [Architecture Details](architecture.md) for full technical design and [Architecture Diagram](architecture-diagram.mmd) for Mermaid source.*

## Service Architecture

**Pipeline services:**
- **Ingestion:** Video and engagement data from Purplle-owned influencer content (YouTube, Instagram, etc.) ingested into the platform.
- **Distributed processing:** Kubernetes-based services for scheduling, batching, and routing content to the embedding pipeline.
- **GPU / embedding layer:** CUDA-enabled nodes run the self-deployed LLM (ChatGPT) to generate embeddings; Python-based pipelines; no persistent LLM — invoked on demand for embedding and analysis.
- **Vector DB (Qdrant):** Embeddings and metadata stored with hash mapping and metadata filters; cosine similarity and semantic search over configurable time windows and filters.
- **RAG & agent layer:** MCP and agentic workflows orchestrate tool-aided LLM access; RAG application retrieves relevant vectors, compares new vs historical content and sentiment, and produces structured answers (links, sentiment, paid content flags).
- **User-facing output:** Brand and marketing teams query via natural language (e.g., “best content in last 2 days”); system returns decision-ready results for campaign optimization.

**Data flow:**
- **Request path:** User query → RAG/agent orchestration → semantic search (Qdrant) → retrieval + LLM (as needed) → structured answer (links, sentiment, decision support).
- **Ingestion path:** Video/content → distributed processing (K8s) → GPU/LLM → embeddings → Qdrant; continuous embedding updates and pipeline changes via CI/CD.

**Traffic & operations:**
- **Query patterns:** Semantic search over time windows (e.g., last 2 days, 7 days) and metadata filters; agentic workflows for complex or multi-step queries.
- **Pipeline operations:** CI/CD for AI services, RAG components, and vector DB updates; monitoring and alerting for pipeline health, GPU utilization, and Qdrant performance.
- **High availability:** Distributed architecture and fault tolerance; architecture-level ownership for root-cause analysis and recovery during incidents.

## Documentation

For detailed information, see:
- **[Architecture Details](architecture.md)** - Complete technical architecture, data flow, and infrastructure design
- **[Architecture Diagram](architecture-diagram.mmd)** - Mermaid diagram source for platform flow
- **[Metrics & Analysis](metrics.md)** - Detailed metrics, reliability, and business impact data

---

**Note:** This is a production platform supporting influencer content analysis and campaign optimization. I managed **infrastructure only** (Kubernetes, GPU workloads, Qdrant, CI/CD); I did not write application or RAG code. Core embedding and RAG application logic were developed by the engineering team. All metrics and design reflect actual production deployment.
