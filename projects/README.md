# Purplle.com Infrastructure Projects | Portfolio

## Overview

This directory contains comprehensive documentation for infrastructure projects implemented at **Purplle.com** (Mumbai, India) during my tenure as **SDE1 - DevOps Engineer** (Jun 2023 - Present). These projects demonstrate expertise in cloud infrastructure, Kubernetes, Infrastructure as Code, security, monitoring, and multi-cloud deployments across production platforms serving millions of users.

## Projects

### 🚀 Production Platform Deployments

#### [Adtech.purplle.com Deployment](./Adtech.purplle.com_Deployment/)
**In-House AdTech Platform** - Brand management and advertising platform  
- **Scale:** 7M+ monthly active users, ₹400+ Crore brand advertising revenue
- **Infrastructure:** 100+ Kubernetes deployments, GKE, multi-cloud (AWS + GCP)
- **Achievements:** 93% cost reduction (₹80 Lakh → ₹5.7 Lakh), 4.6x traffic spike handling
- **Key Technologies:** Kubernetes, Terraform, GitLab CI, Keycloak, Sentinel Service
- [View Details →](./Adtech.purplle.com_Deployment/)

#### [Nexus.purplle.com Deployment](./Nexus.purplle.com_Deployment/)
**In-House POS Platform** - Point of Sale system for retail stores  
- **Scale:** 100+ retail stores, 500+ daily employees, 40+ Crores revenue
- **Infrastructure:** High-availability deployment across DEV, SIT, UAT, PROD
- **Achievements:** 99%+ uptime, auto-scaling (1-6 pods), multi-environment support
- **Key Technologies:** Kubernetes, Kafka, Redis, Terraform, Jenkins
- [View Details →](./Nexus.purplle.com_Deployment/)

#### [Purplle.com Management](./Purplle.com_Management/)
**Main E-Commerce Platform** - Core e-commerce infrastructure  
- **Scale:** 7M users (10M peak), 300+ compute instances, 125+ Kubernetes deployments
- **Infrastructure:** 4TB MySQL database, multi-zone deployment, hybrid cloud
- **Achievements:** ₹1 Crore cost savings, 99%+ uptime, zero-lag MySQL migrations (gh-ost)
- **Key Technologies:** Kubernetes, MySQL, Elasticsearch, MongoDB, Redis, Cloud Functions
- [View Details →](./Purplle.com_Management/)

### 🔧 Infrastructure Automation & DevOps

#### [Purplle.com IAC Deployment](./Purplle.com_IAC_Deployment/)
**Infrastructure as Code Initiative** - Terraform-based infrastructure automation  
- **Scale:** 125+ Kubernetes deployments, 300+ compute instances automated
- **Infrastructure:** Multi-environment (DEV, SIT, UAT, PROD), multi-cloud support
- **Achievements:** 40%+ faster deployments, 40%+ provisioning tasks automated
- **Key Technologies:** Terraform, Ansible, Jenkins, GitLab CI, GitOps, Python
- [View Details →](./Purplle.com_IAC_Deployment/)

### 🔒 Security & Compliance

#### [Purplle.com Security Improvement](./Purplle.com_SecurityImprovement/)
**Security Hardening Initiative** - Comprehensive security improvements  
- **Scale:** 125+ Kubernetes deployments, 300+ compute instances secured
- **Infrastructure:** Zero-trust architecture, defense-in-depth, multi-layer security
- **Achievements:** Hardened container security, automated IAM minimization, SSO, IP Whitelisting
- **Key Technologies:** Kubernetes RBAC, Secure Boot, Trivy, Secrets Manager, SSO
- **Compliance:** DPDP, ISO 27001/27018/27017/27002 alignment, NIST, CIS, OWASP
- [View Details →](./Purplle.com_SecurityImprovement/)

### 📊 Monitoring & Observability

#### [PurplleInfra Monitoring Improvement](./PurplleInfra_Monitoring_Improvement/)
**Unified Observability Stack** - Prometheus and Grafana implementation  
- **Scale:** 125+ Kubernetes deployments, 300+ compute instances monitored
- **Infrastructure:** Unified observability stack, real-time monitoring, automated escalation
- **Achievements:** 76% MTTR reduction (30 to 7 minutes), real-time alerting
- **Key Technologies:** Prometheus, Grafana, GCP Stackdriver, Jenkins, Slack
- [View Details →](./PurplleInfra_Monitoring_Improvement/)

## Project Statistics

### Overall Infrastructure Scale
- **Total Kubernetes Deployments:** 125+ deployments managed
- **Total Compute Instances:** 300+ instances across infrastructure
- **Production Platforms:** 3 major platforms (purplle.com, nexus.purplle.com, adtech.purplle.com)
- **Environments:** 4 environments (DEV, SIT, UAT, PROD)
- **User Base:** 7M+ users (10M at peak)
- **Database Size:** 4TB MySQL primary database

### Key Achievements Across Projects
- ✅ **40%+ Faster Deployments** - Infrastructure automation and CI/CD modernization
- ✅ **76% MTTR Reduction** - Monitoring improvements (30 to 7 minutes)
- ✅ **₹1 Crore Cost Savings** - Infrastructure optimization and automation
- ✅ **99%+ Uptime** - High availability across all production platforms
- ✅ **100% Infrastructure Automation** - Terraform-based IAC deployment
- ✅ **Comprehensive Security** - Zero-trust architecture, defense-in-depth
- ✅ **Multi-Cloud Architecture** - AWS + GCP hybrid cloud deployment

## Technology Stack

### Cloud & Infrastructure
- **Cloud Platforms:** GCP (GKE, Cloud SQL, VPC, Load Balancer), AWS (Route53)
- **Container Orchestration:** Kubernetes (GKE), 125+ deployments
- **Infrastructure as Code:** Terraform, Ansible
- **CI/CD:** Jenkins, GitLab CI, GitOps workflows

### Databases & Storage
- **Relational:** MySQL (4TB primary database), Cloud SQL
- **NoSQL:** MongoDB, Elasticsearch
- **Caching:** Redis, Memorystore
- **Messaging:** Kafka

### Security & Compliance
- **Container Security:** Kubernetes RBAC, Secure Boot, Trivy scanning
- **Access Control:** SSO, IP Whitelisting, automated IAM minimization
- **Secrets Management:** GCP Secrets Manager
- **Compliance:** DPDP, ISO 27001/27018/27017/27002, NIST, CIS, OWASP

### Monitoring & Observability
- **Metrics:** Prometheus
- **Visualization:** Grafana
- **Cloud Monitoring:** GCP Stackdriver
- **Alerting:** Slack integration, automated escalation

## Project Documentation Structure

Each project follows a consistent documentation structure:

- **README.md** - Project overview, business objectives, key achievements, technical stack
- **architecture.md** - Complete technical architecture, implementation details, design decisions
- **metrics.md** - Quantifiable metrics, performance data, before/after comparisons
- **architecture-diagram.mmd** - Mermaid diagram source for architecture visualization

## Quick Navigation

| Project | Type | Key Metric | Status |
|---------|------|------------|--------|
| [Adtech.purplle.com](./Adtech.purplle.com_Deployment/) | AdTech Platform | ₹400+ Cr revenue | ✅ Live |
| [Nexus.purplle.com](./Nexus.purplle.com_Deployment/) | POS Platform | 100+ stores | ✅ Live |
| [Purplle.com Management](./Purplle.com_Management/) | E-Commerce Platform | 7M users | ✅ Live |
| [IAC Deployment](./Purplle.com_IAC_Deployment/) | Infrastructure Automation | 40%+ faster | ✅ Implemented |
| [Security Improvement](./Purplle.com_SecurityImprovement/) | Security Hardening | 125+ deployments | ✅ Implemented |
| [Monitoring Improvement](./PurplleInfra_Monitoring_Improvement/) | Observability | 76% MTTR reduction | ✅ Implemented |

## Role & Responsibilities

**Position:** SDE1 - DevOps Engineer  
**Company:** Purplle.com, Mumbai, India  
**Duration:** Jun 2023 - Present  
**Team Size:** 5 people

**Key Responsibilities:**
- Infrastructure deployment and management across all production platforms
- Infrastructure as Code (Terraform, Ansible) implementation and automation
- Kubernetes cluster management and 125+ deployment orchestration
- CI/CD pipeline modernization and automation
- Security hardening and compliance implementation
- Monitoring and observability stack implementation
- Multi-cloud and multi-environment infrastructure management

## Contact & Usage

This portfolio is designed for:
- **Technical Interviews** - Demonstrate infrastructure expertise and impact
- **Client Showcases** - Share relevant projects for specific opportunities
- **Employer Reviews** - Showcase technical capabilities and achievements
- **Technical Discussions** - Reference during architecture and design discussions

---

**Note:** All projects documented here are based on actual production deployments and implementations at Purplle.com. Infrastructure deployment and management was handled by DevOps team; application code was developed by engineering teams. All metrics and achievements are based on actual production data.
