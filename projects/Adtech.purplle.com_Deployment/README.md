# PurplleAds - AdTech Platform | Purplle.com

## Project Overview

**Company:** Purplle.com  
**Project Type:** Production Platform - In-House AdTech Solution  
**Status:** Live & Operational  
**Platform:** PurplleAds - Internal Brand Management & Advertising Platform  
**Deployment:** `adtech.purplle.com`  
**Role:** DevOps Engineer | Team Size: 5 people

## Executive Summary

PurplleAds is an in-house brand management platform that enables brands to advertise products on Purplle.com through search widgets and banners. The platform operates on a daily budget and bidding system, leveraging user preference data for optimized ad delivery. Successfully replaced ₹80 Lakh/year third-party business management software with in-house solution.

## Business Objectives

**Primary Goal:** Build an in-house internal-only brand management software that charges brands for displaying their products in Purplle.com search widgets or banners based on:
- **Daily Budget:** Brands set daily advertising budgets
- **Bidding System:** Brands bid for ad placements
- **User Preference Data:** Leverages existing user preference and behavioral data for targeted ad delivery

**Business Drivers:**
- Manage ₹180-₹210 Crore in annual marketing costs across house brands
- Generate ₹400+ Crore in brand advertising revenue
- Enable self-service platform for brands to manage their own campaigns
- Support 5 major house brands with projected FY25 revenue of ₹680-₹800 Crore

## Business Metrics

### Scale & Users
- **Total Users:** 7 million total users
- **Daily Active Users (Regular):** 150,000 DAU typically
- **Daily Active Users (Major Sales):** 600,000 DAU (4x spike during major sales events)
- **Daily Active Users (Minor Sales):** 300,000 DAU (2x spike during minor sales events)
- **Annual Clicks:** 133.3 million clicks/year (~365K clicks/day)

### Financial Performance

**Platform Revenue:**
- **Brand Advertising Revenue:** ₹400+ Crore
- **Total Marketing Cost Managed:** ₹180-₹210 Crore annually

**House Brand Performance (FY 2025 Estimates):**
- **Total House Brand Revenue:** ₹680-₹800 Crore (40% of Purplle's operating revenue)
- **Total Marketing Spend:** ₹167-₹198 Crore
- **Average Marketing % of Revenue:** ~24%

**House Brand Breakdown:**

| Brand | Revenue (FY25) | Marketing Cost (FY25) | Marketing % |
|-------|----------------|----------------------|-------------|
| Faces Canada | ₹240-₹280 Cr | ₹65-₹75 Cr | ~27% |
| Alps Goodness | ₹180-₹210 Cr | ₹40-₹45 Cr | ~22% |
| Good Vibes | ₹150-₹170 Cr | ₹30-₹35 Cr | ~20% |
| NY Bae | ₹90-₹110 Cr | ₹22-₹28 Cr | ~25% |
| Carmesi | ₹20-₹30 Cr | ₹10-₹15 Cr | ~45% |

### Cost Savings & ROI

- **Software Replacement:** Replaced ₹80 Lakh/year third-party business management software
- **Infrastructure Cost:** ₹5.7 Lakh/year (GKE - Mumbai region)
- **Net Annual Savings:** ₹74.3 Lakh/year (93% cost reduction)
- **ROI:** Infrastructure cost is only 7.1% of software savings
- **Cost Efficiency:** 
  - ₹0.0069/user/month (0.69 paise per user)
  - ₹0.0043/click (0.43 paise per click)

### Business Model

**Revenue Streams:**
1. Brand Advertising Fees - Brands pay for ad placements
2. Bidding System - Revenue from competitive bidding for premium placements
3. Daily Budget Management - Revenue from brands managing daily advertising spend

**Key Insights:**
- House Brand Revenue Contribution: ₹680-₹800 Crore represents ~40% of Purplle's total operating revenue
- Marketing Efficiency: Average marketing spend is ~24% of revenue across house brands
- Platform manages significant marketing spend (₹167-₹198 Cr) across 5 major house brands

### Key Achievements

- ✅ **Live Production Platform** - Fully deployed at `adtech.purplle.com`, actively serving 7M total users
- ✅ **100+ Kubernetes Deployments** - Managed 100+ high-availability Kubernetes deployments on Google Kubernetes Engine (GKE), ensuring optimal performance, scalability, and reliability in production
- ✅ **Cost Optimization** - 93% reduction in software costs (₹80 Lakh → ₹5.7 Lakh infrastructure). Optimized resource utilization and cost-efficiency by rightsizing GCP/AWS instances and implementing autoscaling policies, achieving a 30% reduction in cloud spend through usage audits and resource cleanup
- ✅ **Scalability** - Handles 4x traffic spikes during major sales events (150K → 600K DAU) and 2x during minor sales (150K → 300K DAU)
- ✅ **Revenue Support** - Platform supports ₹400+ Crore in brand advertising revenue
- ✅ **House Brand Support** - Critical platform for 5 major house brands (₹680-₹800 Cr revenue)
- ✅ **CI/CD Modernization** - Accelerated infrastructure delivery speed by 40%+ by collaborating on CI/CD automation using Terraform, Jenkins, and GitOps, automating over 40% of provisioning tasks. Modernized CI/CD infrastructure by migrating from freestyle bash jobs to scripted pipeline jobs in Jenkins, integrated with Slack for real-time job failure alerts, improving monitoring and reducing incident response time
- ✅ **Monitoring & Observability** - Reduced Mean Time to Recovery (MTTR) from 30 to 7 minutes by architecting a unified observability stack with Prometheus and Grafana, enabling real-time monitoring and automated incident escalation
- ✅ **Infrastructure Automation** - 40%+ faster deployments through Terraform and CI/CD automation
- ✅ **Data Persistence & DR** - Engineered high-availability Data Persistence and Disaster Recovery (DR) solutions for MySQL, MongoDB, and Elasticsearch, utilizing automated backup triggers to ensure system resilience and data integrity
- ✅ **Elasticsearch Automation** - Engineered agentic AI-based automation for Elasticsearch cluster management using n8n, Terraform, Ansible, and Python, streamlining cluster provisioning and lifecycle management
- ✅ **Security Implementation** - Hardened container security by implementing Kubernetes RBAC, Secure Boot, automated IAM role minimization using Python, and Trivy container scanning integrated with GitLab CI to detect and remediate vulnerable code, adhering to zero-trust architecture and DevSecOps principles. Strengthened microservices security by deploying Secrets Manager across Kubernetes (K8s) clusters and VMs, decoupling sensitive credentials from application source code. Implemented Single Sign-On (SSO) authentication & IP Whitelisting for multiple internal URLs, centralizing access control and improving security posture. Implemented defense-in-depth security controls to enforce traffic segmentation and access restrictions, ensuring secure and compliant deployments across environments
- ✅ **4-Tier Architecture** - Scalable architecture pattern with multi-layer security
- ✅ **Multi-Cloud Infrastructure** - Hybrid cloud architecture (AWS Route53 + GCP GKE)

## Technical Stack

**Cloud & Infrastructure:** GCP (GKE), AWS (Route53), Kubernetes, ALB, GCLB  
**Container Orchestration:** Kubernetes (GKE), K8s Ingress, Deployments, Services  
**Service Discovery:** kubedns (Kubernetes DNS) for internal cluster networking  
**Databases:** Cloud SQL (MySQL/PostgreSQL), Redis, Cloud SQL Proxy  
**CI/CD:** Jenkins (scripted pipeline jobs with Slack integration), GitLab CI (with automated testing and Trivy security scanning), GitOps workflows  
**Infrastructure as Code:** Terraform (reusable modules), Ansible, GitOps workflows  
**Monitoring:** Prometheus, Grafana, GCP Stackdriver (unified observability stack)  
**Security:** Zero Trust, WAF, Geo-blocking, Rate Limiting, Bot Protection, DPDP Compliance, Kubernetes RBAC, Secure Boot, Automated IAM role minimization (Python), Trivy container scanning (GitLab CI), GCP Secrets Manager, SSO, IP Whitelisting, Defense-in-Depth  
**Authentication & Authorization:** Keycloak (Identity Provider)

## Architecture Overview

![PurplleAds Architecture](../../assets/purplle/purplle.png)

*4-Tier Architecture Diagram - See [Architecture Details](architecture.md) for complete technical documentation and [Mermaid Diagram](architecture-diagram.mmd) for diagram source*

## Infrastructure Automation & Deployment

**Infrastructure as Code:**
- Standardized on Terraform for Infrastructure as Code and integrated into GitOps workflows
- Created reusable, parameterized Terraform modules for:
  - GKE clusters with multi-environment support
  - Cloud SQL instances (MySQL/PostgreSQL) with automated backups
  - VPCs and network configurations
  - Load balancers (ALB, GCLB) with WAF integration
  - Kubernetes deployments and services
- Built Python scripts to automate IAM role management, reducing misconfigurations
- Integrated into GitLab CI and Jenkins pipelines with automated testing
- **Result:** 40%+ faster deployments with consistent infrastructure, automating over 40% of provisioning tasks

**CI/CD Automation:**
- GitLab CI pipelines for automated infrastructure provisioning and application deployments
- Jenkins pipelines integrated with Terraform for infrastructure automation
- Modernized CI/CD infrastructure by migrating from freestyle bash jobs to scripted pipeline jobs in Jenkins
- Integrated Slack for real-time job failure alerts, improving monitoring and reducing incident response time
- Automated testing and validation in CI/CD workflows
- GitOps approach for consistent infrastructure management
- Automated security scanning (Trivy) integrated into GitLab CI deployment pipelines
- **Result:** Accelerated infrastructure delivery speed by 40%+, automating over 40% of provisioning tasks

**Multi-Environment Deployment:**
- Parameterized Terraform modules enabling consistent deployment across environments
- Environment-specific configurations while maintaining infrastructure consistency
- Automated environment provisioning and management
- **Result:** Consistent infrastructure across Production, Pre-Production, and Sandbox environments

## Service Architecture

**Application Services:**
- All application services (e.g., billing service, campaign service, etc.) are deployed as Kubernetes deployments within the GKE cluster
- Services communicate through Kubernetes service discovery and internal networking
- **Internal Networking:** kubedns (Kubernetes DNS) handles service discovery and DNS resolution for inter-service communication within the cluster
- Each service is containerized and managed through Kubernetes orchestration
- Managed 100+ high-availability Kubernetes deployments on GKE, ensuring optimal performance, scalability, and reliability in production

**Authentication & Authorization Flow:**
- **Keycloak:** Handles identity verification and authentication for all platform users
- **Sentinel Service:** RBAC (Role-Based Access Control) service deployed on Kubernetes
  - Operates after Keycloak verification completes
  - Manages role-based permissions and access control for platform services
  - Not managed by this project (separate service)
  - Validates user permissions before allowing access to application services
- Automated service account management for secure inter-service communication

**Security Automation:**
- Hardened container security by implementing Kubernetes RBAC, Secure Boot, automated IAM role minimization using Python, and Trivy container scanning integrated with GitLab CI to detect and remediate vulnerable code, adhering to zero-trust architecture and DevSecOps principles
- Strengthened microservices security by deploying Secrets Manager across Kubernetes (K8s) clusters and VMs, decoupling sensitive credentials from application source code
- Implemented Single Sign-On (SSO) authentication & IP Whitelisting for multiple internal URLs, centralizing access control and improving security posture
- Implemented defense-in-depth security controls to enforce traffic segmentation and access restrictions, ensuring secure and compliant deployments across environments
- Zero-trust security principles with automated network logging and public IP cleanup
- WAF rules configured for geo-blocking, rate limiting, and bot protection

## Documentation

For detailed information, see:
- **[Architecture Details](architecture.md)** - Complete technical architecture and infrastructure design
- **[Architecture Diagram](architecture-diagram.mmd)** - Mermaid diagram source for 4-tier architecture
- **[Metrics & Analysis](metrics.md)** - Detailed metrics, cost analysis, and business performance data

---

**Note:** This is a production platform actively serving traffic at `adtech.purplle.com`. All metrics and costs are based on actual production deployment.
