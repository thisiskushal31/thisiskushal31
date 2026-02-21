# Nexus - POS Platform | Purplle.com

## Project Overview

**Company:** Purplle.com  
**Project Type:** Production Platform - In-House POS Solution  
**Status:** Live & Operational  
**Platform:** Nexus - Point of Sale (POS) System  
**Deployment:** Production Environment (POS Platform)  
**Environments:** DEV, SIT, UAT, PROD  
**Role:** DevOps Engineer (Infrastructure Deployment & Management) | Team Size: 5 people  
**Note:** Infrastructure deployment and management handled by DevOps team. Application code developed by engineering team.

## Executive Summary

Nexus is an in-house Point of Sale (POS) platform deployed in Production environment across multiple environments (DEV, SIT, UAT, PROD). The platform enables store teams to manage retail operations across 100+ stores, generating 40+ Crores in revenue and serving 500+ store employees daily. Successfully deployed high-availability Nexus (POS application) across purplle's retail stores, securing distributed infrastructure and maintaining 99%+ service availability using GCP services (GKE, GCR, Cloud SQL, Load Balancer, WAF, VPC, etc.). The platform follows a 4-tier architecture pattern with Kafka and Redis for messaging and caching, ensuring reliable and scalable retail operations across all environments.

**Note:** Infrastructure deployment and management was handled by DevOps team. Application code was developed by the engineering team.

## Business Objectives

**Primary Goal:** Build and deploy an in-house POS software that store teams can use to manage retail operations across 100+ stores, generating 40+ Crores in revenue and serving 500+ store employees daily.

**Business Requirements:**
- **Store Management:** Enable store teams to manage retail operations efficiently
- **Multi-Store Support:** Support operations across 100+ retail stores
- **User Scale:** Serve 500+ store employees daily
- **Revenue Generation:** Support 40+ Crores in revenue generation
- **High Availability:** 99%+ uptime across all retail locations
- **Scalability:** Support multiple retail stores with consistent performance
- **Reliability:** Robust infrastructure to handle retail operations
- **Security:** Secure transaction processing and data handling

**Business Drivers:**
- Replace third-party POS solutions with in-house solution
- Enable seamless retail operations across store locations
- Ensure high availability for critical POS operations
- Support retail store expansion and growth (100+ stores)
- Maintain secure and reliable transaction processing
- Provide self-service platform for store management

## Business Metrics

### Scale & Deployment
- **Deployment:** High-availability deployment in Production environment (POS Platform)
- **Environments:** DEV, SIT, UAT, PROD
- **Uptime:** 99%+ uptime maintained across all environments
- **Infrastructure:** GCP-based infrastructure (GKE, GCR, Cloud SQL, Load Balancer, WAF, VPC)
- **Architecture:** 4-tier architecture pattern (DNS & Security, Load Balancing, Application, Data layers)

### Business Scale
- **Store Coverage:** 100+ retail stores
- **Daily Active Users:** 500+ store employees using the platform daily
- **Revenue Generation:** 40+ Crores in revenue supported by the platform
- **Platform Purpose:** In-house POS software for store management and retail operations

### Key Achievements

- ✅ **In-House POS Solution** - Successfully deployed in-house POS software replacing third-party solutions
- ✅ **100+ Store Support** - Platform supports operations across 100+ retail stores
- ✅ **500+ Daily Users** - Serving 500+ store employees daily
- ✅ **40+ Crores Revenue** - Platform supports 40+ Crores in revenue generation
- ✅ **High-Availability Deployment** - Successfully deployed high-availability Nexus (POS application) across purplle's retail stores, securing distributed infrastructure and maintaining 99%+ service availability using GCP services (GKE, GCR, Cloud SQL, Load Balancer, WAF, VPC, etc.)
- ✅ **Multi-Environment Support** - Deployed across DEV, SIT, UAT, and PROD environments
- ✅ **Infrastructure Reliability** - GCP-based infrastructure ensuring consistent performance
- ✅ **Data Persistence & DR** - Engineered high-availability Data Persistence and Disaster Recovery (DR) solutions for MySQL, MongoDB, and Elasticsearch, utilizing automated backup triggers to ensure system resilience and data integrity
- ✅ **Security Implementation** - Hardened container security by implementing Kubernetes RBAC, Secure Boot, automated IAM role minimization using Python, and Trivy container scanning integrated with GitLab CI to detect and remediate vulnerable code, adhering to zero-trust architecture and DevSecOps principles. Strengthened microservices security by deploying Secrets Manager across Kubernetes (K8s) clusters and VMs, decoupling sensitive credentials from application source code. Implemented Single Sign-On (SSO) authentication & IP Whitelisting for multiple internal URLs, centralizing access control and improving security posture. Implemented defense-in-depth security controls to enforce traffic segmentation and access restrictions, ensuring secure and compliant deployments across environments
- ✅ **4-Tier Architecture** - Scalable architecture pattern with clear separation of concerns
- ✅ **Production Ready** - Fully operational and actively serving retail store operations

## Technical Stack

**Cloud & Infrastructure:** GCP (GKE), GCR, Cloud SQL, Load Balancer, WAF, VPC  
**Container Orchestration:** Kubernetes (GKE), K8s Ingress, Deployments, Services  
**Service Discovery:** kubedns (Kubernetes DNS) for internal cluster networking  
**Databases:** Cloud SQL (MySQL), Cloud SQL Proxy  
**Messaging & Caching:** Kafka (messaging), Redis (caching)  
**CI/CD:** Jenkins, GitLab CI (with Trivy security scanning)  
**Infrastructure as Code:** Terraform, Ansible  
**Monitoring:** Prometheus, Grafana, GCP Stackdriver  
**Security:** Zero Trust, WAF, Geo-blocking, Rate Limiting, Bot Protection, DPDP Compliance, Kubernetes RBAC, Secure Boot, Automated IAM role minimization (Python), Trivy container scanning, Secrets Manager, SSO, IP Whitelisting, Defense-in-Depth

## Architecture Overview

![Nexus Architecture](../../assets/purplle/purplle.png)

*4-Tier Architecture Diagram - See [Architecture Details](architecture.md) for complete technical documentation and [Mermaid Diagram](architecture-diagram.mmd) for diagram source*

## Service Architecture

**Application Services:**
- Single service deployed as Kubernetes deployment within the GKE cluster across DEV, SIT, UAT, and PROD environments
- **Auto-scaling:** Pods automatically scale based on demand and time of day:
  - **Night time:** 1 pod (low traffic)
  - **Peak time:** 6 pods (high traffic)
  - **Shop closing time:** 3 pods (moderate traffic)
  - **Average:** 3 pods
- Services communicate through Kubernetes service discovery and internal networking
- **Internal Networking:** kubedns (Kubernetes DNS) handles service discovery and DNS resolution for inter-service communication within the cluster
- Each service is containerized and managed through Kubernetes orchestration with Horizontal Pod Autoscaling (HPA)

**Traffic Patterns:**
- **Public Calls:** External traffic from store employees and retail locations accessing the Production POS Platform
  - Traffic flows through: Route53 → WAF → ALB → GCLB → Kubernetes Ingress → Services → Deployments
  - Public-facing API endpoints for store management operations
- **Private/Internal Calls:** Service-to-service communication within the cluster and from other internal systems
  - Internal service-to-service calls via kubedns (Kubernetes DNS)
  - Inter-service communication for microservices architecture
  - Internal API calls from other Purplle systems

**Messaging & Caching:**
- **Kafka:** Used for messaging and event streaming between services (both public and internal workflows)
- **Redis:** Used for caching to improve performance and reduce database load

## Documentation

For detailed information, see:
- **[Architecture Details](architecture.md)** - Complete technical architecture and infrastructure design
- **[Architecture Diagram](architecture-diagram.mmd)** - Mermaid diagram source for 4-tier architecture
- **[Metrics & Analysis](metrics.md)** - Detailed metrics, cost analysis, and performance data

---

**Note:** This is a production platform actively serving traffic through the Production POS Platform across DEV, SIT, UAT, and PROD environments. All metrics and infrastructure details are based on actual production deployment. Infrastructure deployment and management was handled by DevOps team; application code was developed by the engineering team.

