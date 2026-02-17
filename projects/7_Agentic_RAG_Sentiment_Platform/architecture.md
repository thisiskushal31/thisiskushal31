# Agentic RAG Sentiment Platform – Technical Architecture

## System Overview

The platform is an **agentic RAG-based sentiment intelligence system** for Purplle’s influencer marketing content. Purplle commissions and owns branded video content (e.g., YouTube, Instagram). The business problem is to understand which content works, what sentiment is right or wrong, and what in the content performed well or poorly — and to expose this via a simple, search-like interface (e.g., “best content in the last 2 days or 7 days”).

The system does **not** run a persistent, long-lived LLM deployment. It is **orchestration- and vector-DB-centric**: video and engagement data are processed through a **self-deployed ChatGPT** in a **distributed Kubernetes** setup to produce embeddings; embeddings are stored in **Qdrant**; **cosine similarity**, **metadata filters**, and **hash-based indexing** power semantic search; and **MCP-based agentic** workflows plus a **RAG** application answer user queries and return decision-ready results (links, sentiment, paid content flags).

**Infrastructure focus (platform/DevOps ownership — infrastructure only):** Kubernetes-based distributed architecture, GPU-enabled workloads (CUDA) for embedding services, Qdrant cluster operations, CI/CD for AI and RAG components, high availability, and faster time-to-result. Application and RAG logic were developed by the engineering team; this document describes the platform from an infrastructure perspective.

## High-Level Data Flow

1. **Ingestion** — Video and engagement data are ingested into the platform.
2. **Processing** — Distributed processing services (Kubernetes) prepare and route content.
3. **Embedding** — GPU workers run the self-deployed LLM (ChatGPT) to generate embeddings (Python-based pipelines).
4. **Storage** — Embeddings and metadata are written to Qdrant (vector DB) with hash mapping and metadata filters.
5. **Search** — Cosine similarity and semantic search over Qdrant support configurable time windows and filters.
6. **Orchestration** — MCP and agentic workflows orchestrate tool-aided LLM access and RAG retrieval.
7. **RAG application** — Compares new vs historical content and sentiment; generates answers.
8. **User** — Natural-language queries (e.g., “best content in last 2 days”) return links (e.g., Instagram), sentiment (right/wrong), and decision support.
9. **Updates** — Continuous embedding updates and pipeline changes are delivered via CI/CD.

## Architecture Layers

### 1. Ingestion Layer
- **Input:** Video and engagement data from Purplle-owned influencer content (YouTube, Instagram, etc.).
- **Ownership:** Purplle-owned, copyrighted data used for internal AI training and analysis.
- **Infrastructure:** Data pipelines and storage feeding into the distributed processing layer.

### 2. Compute & AI Layer (Kubernetes)
- **Distributed processing:** Kubernetes-based services for scheduling, batching, and routing.
- **GPU workloads:** CUDA-compatible nodes for embedding generation; GPU scheduling and resource management.
- **Self-deployed LLM:** ChatGPT deployed in a distributed architecture (no persistent always-on LLM; invoked as needed for embedding and analysis).
- **Python:** Embedding models and pipelines implemented in Python.
- **Infrastructure responsibilities:** Node configuration, GPU scheduling, scaling, and reliability of the embedding pipeline.

### 3. Vector DB Layer (Qdrant)
- **Role:** Store and query embeddings; support semantic search and metadata filtering.
- **Mechanisms:** Cosine similarity, metadata filters, hash-based indexing.
- **Operations:** Cluster maintenance, ingestion pipelines, index tuning, and availability.
- **No persistent LLM:** Primary state is in the vector DB and orchestration; LLM is used for embedding and agent steps, not as a long-running service.

### 4. RAG & Agent Layer
- **Semantic search:** Queries over Qdrant with time windows (e.g., last 2 days, 7 days) and filters.
- **MCP (Model Context Protocol):** Enables tool-based LLM access and agentic workflows.
- **RAG application:** Retrieves relevant vectors and context; compares new vs old content; produces structured answers.
- **Output:** Links (e.g., Instagram), paid content indicators, sentiment (right/wrong), and decision support for brand and marketing teams.

### 5. User & Business Impact
- **Users:** Brand and marketing teams.
- **Interface:** Search-like natural-language queries.
- **Outcomes:** Faster, decision-ready insights; high-availability infrastructure for reliable access and faster results.

## Key Design Decisions

| Decision | Rationale |
|----------|-----------|
| No persistent LLM | Cost and complexity; orchestration + vector DB sufficient for RAG and agentic use cases. |
| Self-deployed ChatGPT in K8s | Control, data privacy, and alignment with Purplle’s infrastructure. |
| Qdrant for vector store | Semantic search, cosine similarity, metadata filters, and hash-based indexing. |
| GPU nodes (CUDA) | Efficient embedding generation at scale. |
| MCP & agentic design | Tool-aided LLM access and flexible RAG workflows. |
| CI/CD for AI/RAG | Safe rollouts of model and pipeline updates. |

## Infrastructure Components

### Kubernetes
- **Clusters:** Distributed architecture for processing, GPU workers, and LLM invocation.
- **GPU node pools:** CUDA-compatible nodes; scheduling and resource limits for embedding workloads.
- **Services:** Processing services, embedding pipelines, and RAG/agent components as K8s workloads.
- **High availability:** Multi-replica, health checks, and failover for critical services.

### Vector DB (Qdrant)
- **Cluster:** Production Qdrant deployment for vector storage and search.
- **Indexing:** Hash mapping and metadata filters for efficient retrieval.
- **Search:** Cosine similarity and semantic search over configurable time windows and filters.
- **Operations:** Backup, scaling, and monitoring of ingestion and query performance.

### CI/CD
- **Pipelines:** Build, test, and deploy AI services, RAG components, and vector DB schema/ingestion updates.
- **Safe rollouts:** Staged deployments and rollback for model and infra changes.
- **Automation:** Reduced manual steps and faster delivery of embedding and pipeline updates.

### Monitoring & Reliability
- **Observability:** Metrics and logging for pipeline health, GPU utilization, Qdrant performance, and RAG latency.
- **Incident response:** Architecture-level debugging across infra and application; improved fault tolerance and recovery time.
- **Business impact:** High availability and faster results for campaign optimization and decision-making.

## Security & Data

- **Data ownership:** Purplle-owned influencer content; processed and stored within Purplle-controlled infrastructure.
- **Self-deployed LLM:** No reliance on external LLM APIs for core embedding and analysis; data stays in-house.
- **Access control:** Platform and application access aligned with internal security and compliance requirements.

## Scalability

- **Horizontal scaling:** Kubernetes scaling for processing and GPU workers; Qdrant scaling for vectors and query load.
- **Embedding throughput:** GPU capacity and batching tuned for ingestion and update frequency.
- **Search performance:** Qdrant indexing and metadata filters optimized for time-window and semantic queries.

## Summary

The agentic RAG sentiment platform uses **Kubernetes** for distributed processing and **GPU workloads** for embeddings, a **self-deployed ChatGPT** for embedding and analysis (no persistent LLM), **Qdrant** for semantic search (cosine similarity, metadata, hash mapping), and **MCP/agentic RAG** for natural-language queries and decision support. Infrastructure ownership covers distributed architecture, GPU deployment, vector DB operations, CI/CD, and high availability to deliver reliable, faster results for Purplle’s influencer content and campaign optimization.
