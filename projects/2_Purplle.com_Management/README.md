# Purplle - E-Commerce Platform Infrastructure | Purplle.com

## Project Overview

**Company:** Purplle.com  
**Project Type:** Production Platform - Main E-Commerce Infrastructure  
**Status:** Live & Operational  
**Duration:** Jun 2023 - Feb 2026  
**Platform:** Purplle.com - Beauty & Personal Care E-Commerce Platform  
**Deployment:** Production infrastructure serving 1 crore+ users  
**Role:** DevOps Engineer | Team Size: 5 people

## Executive Summary

Purplle.com is the main e-commerce platform infrastructure supporting beauty and personal care retail operations, generating ₹700 Crore annually (as of January 1, 2026). The platform serves 7 million total users with 150,000 daily active users (DAU) typically, scaling to 600,000 DAU during major sales events (4x) and 300,000 DAU during minor sales events (2x). Infrastructure includes 300+ application instances, maintaining 99%+ uptime using GCP (GKE, GCR, Cloud SQL, Load Balancer, WAF, VPC) and AWS (Route53). The platform follows a 4-tier architecture pattern with comprehensive security, monitoring, and disaster recovery capabilities. Infrastructure is managed across Production, Pre-Production, and Sandbox environments and is fully operational. Achieved ₹1 Crore in cost savings through infrastructure optimization and automation.

**Note:** Infrastructure management and operations handled by DevOps team. Application code developed by engineering team.

## Business Objectives

**Primary Goal:** Manage and maintain robust, scalable infrastructure for the main e-commerce platform supporting:
- **User Scale:** Serve 7 million total users with 150,000 DAU typically, scaling to 600,000 DAU during major sales (4x) and 300,000 DAU during minor sales (2x)
- **High Availability:** 99%+ uptime for critical e-commerce operations
- **Scalability:** Support 300+ application instances, 200+ self-managed database instances, and 125+ Microservices Distributed Workload
- **Reliability:** Robust infrastructure for core e-commerce operations
- **Security:** Secure infrastructure with comprehensive security measures (zero-trust, DevSecOps)
- **Performance:** Optimized infrastructure for e-commerce transactions and user experience
- **Cost Optimization:** Achieve significant cost savings through automation and optimization

**Business Drivers:**
- Support core e-commerce business operations generating ₹700 Crore annually (as of January 1, 2026)
- Ensure high availability for critical services (product catalog, checkout, payments)
- Enable scalable infrastructure for business expansion
- Maintain secure and reliable platform operations
- Support high-volume traffic during sales events and promotions

## Business Metrics

### Scale & Infrastructure
- **Annual Revenue:** ₹700 Crore annually (as of January 1, 2026)
- **User Base:** 7 million total users, 150,000 DAU typically (600,000 DAU during major sales, 300,000 DAU during minor sales)
- **Microservices Distributed Workload:** 125+ microservices distributed workloads orchestrated on GKE
- **Database Instances:** 200+ self-managed database instances
- **Application Instances:** 300+ application instances
- **Infrastructure:** GCP-based infrastructure (GKE, GCR, Cloud SQL, Load Balancer, WAF, VPC) + AWS (Route53)
- **Database:** Primary MySQL database of 4TB size
- **Uptime:** 99%+ uptime maintained
- **Environments:** DEV, SIT, UAT, PROD (Production, Pre-Production, Sandbox)
- **Architecture:** 4-tier architecture pattern (DNS & Security, Load Balancing, Application, Data layers)
- **Status:** Fully managed and operational
- **Cost Savings:** ₹1 Crore achieved through infrastructure optimization and automation

### Key Achievements

- ✅ **Production Infrastructure** - Successfully managed and operational, serving 7M total users with 150K DAU typically (600K during major sales, 300K during minor sales)
- ✅ **125+ Microservices Distributed Workload** - Managed 125+ high-availability microservices distributed workloads on GKE, including Hypertest (QA tool), ensuring optimal performance, scalability, and reliability in production
- ✅ **300+ Application Instances** - Managed 300+ application instances across infrastructure
- ✅ **High Availability** - 99%+ uptime maintained across all environments
- ✅ **Scalable Architecture** - Infrastructure supports business growth and traffic spikes
- ✅ **CI/CD Modernization** - Accelerated infrastructure delivery speed by 40%+ by collaborating on CI/CD automation using Terraform, Jenkins, and GitOps, automating over 40% of provisioning tasks. Modernized CI/CD infrastructure by migrating from freestyle bash jobs to scripted pipeline jobs in Jenkins, integrated with Slack for real-time job failure alerts, improving monitoring and reducing incident response time
- ✅ **Monitoring & Observability** - Reduced Mean Time to Recovery (MTTR) from 30 to 7 minutes by architecting a unified observability stack with Prometheus and Grafana, enabling real-time monitoring and automated incident escalation
- ✅ **Cost Optimization** - Optimized resource utilization and cost-efficiency by rightsizing GCP/AWS instances and implementing autoscaling policies, achieving a 30% reduction in cloud spend through usage audits and resource cleanup. Total ₹1 Crore cost savings through infrastructure optimization, step scaling, and automation
- ✅ **Security Implementation** - Hardened container security by implementing Kubernetes RBAC, Secure Boot, automated IAM role minimization using Python, and Trivy container scanning integrated with GitLab CI to detect and remediate vulnerable code, adhering to zero-trust architecture and DevSecOps principles. Strengthened microservices security by deploying Secrets Manager across Kubernetes (K8s) clusters and VMs, decoupling sensitive credentials from application source code. Implemented Single Sign-On (SSO) authentication & IP Whitelisting for multiple internal URLs, centralizing access control and improving security posture. Implemented defense-in-depth security controls to enforce traffic segmentation and access restrictions, ensuring secure and compliant deployments across environments
- ✅ **Infrastructure Automation** - 40%+ faster deployments through reusable Terraform modules, GitOps workflows, and CI/CD automation
- ✅ **Multi-Environment Deployment** - Consistent infrastructure across DEV, SIT, UAT, PROD using parameterized Terraform modules
- ✅ **Database Management** - Zero-lag MySQL schema alterations on 4TB database using gh-ost
- ✅ **Disaster Recovery & Data Persistence** - Engineered high-availability Data Persistence and Disaster Recovery (DR) solutions for MySQL, MongoDB, and Elasticsearch, utilizing automated backup triggers to ensure system resilience and data integrity. Comprehensive DR and backup plans for databases and VMs
- ✅ **Elasticsearch Automation** - Engineered agentic AI-based automation for Elasticsearch cluster management using n8n, Terraform, Ansible, and Python, streamlining cluster provisioning and lifecycle management

## Technical Stack

**Cloud & Infrastructure:** GCP (GKE), AWS (Route53), Kubernetes, ALB, GCLB, Cloud Functions  
**Container Orchestration:** Kubernetes (GKE), K8s Ingress, Deployments, Services  
**Service Discovery:** kubedns (Kubernetes DNS) for internal cluster networking  
**Databases:** Cloud SQL (MySQL), Redis, Cloud SQL Proxy, MySQL (4TB primary database), Aerospike (A/B testing)  
**Database Migration:** gh-ost for zero-lag MySQL schema alterations  
**CI/CD:** GitLab CI, Jenkins (scripted pipeline jobs with Slack integration), Infrastructure as Code (Terraform, Ansible), GitOps workflows  
**Infrastructure as Code:** Terraform, Ansible  
**Monitoring:** Prometheus, Grafana, GCP Stackdriver (unified observability stack)  
**Security:** Zero Trust, WAF (Reblaze), Geo-blocking, Rate Limiting, Bot Protection, DPDP Compliance, Kubernetes RBAC, Secure Boot, Secrets Manager, SSO, IP Whitelisting, Trivy scanning  
**Automation:** Python (IAM role minimization, Elasticsearch automation), Bash, n8n (agentic AI-based automation for Elasticsearch cluster management)  
**Workflow Orchestration:** DAGs (Airflow) for whole Purplle app  
**Legacy Systems:** PHP application (Management Platform - Legacy) for SCM

## Architecture Overview

![Purplle Architecture](../../assets/purplle/purplle.png)

*4-Tier Architecture Diagram - See [Architecture Details](architecture.md) for complete technical documentation and [Mermaid Diagram](architecture-diagram.mmd) for diagram source*

## Service Architecture

**Application Services:**
- Multiple application services deployed as Kubernetes deployments within the GKE cluster across Production, Pre-Production, and Sandbox environments
- **125+ Microservices Distributed Workload** orchestrated on GKE
- Services communicate through Kubernetes service discovery and internal networking
- **Internal Networking:** kubedns (Kubernetes DNS) handles service discovery and DNS resolution for inter-service communication within the cluster
- Each service is containerized and managed through Kubernetes orchestration
- Auto-scaling configured based on demand and traffic patterns
- **Step Scaling:** Implemented step scaling for cost savings during night time
- **CI/CD:** GitLab CI integrated with each service, deployed using Infrastructure as Code (Terraform, Ansible)

**Infrastructure Scale:**
- **300+ Application Instances:** Managed across GCP and AWS infrastructure
- **Multi-Environment:** Deployed across DEV, SIT, UAT, PROD (Production, Pre-Production, Sandbox) with consistent infrastructure
- **High Availability:** Multi-zone deployment for fault tolerance
- **Auto-scaling:** Horizontal Pod Autoscaling (HPA) and cluster autoscaling

## Documentation

For detailed information, see:
- **[Architecture Details](architecture.md)** - Complete technical architecture and infrastructure design
- **[Architecture Diagram](architecture-diagram.mmd)** - Mermaid diagram source for 4-tier architecture
- **[Metrics & Analysis](metrics.md)** - Detailed metrics, cost analysis, and performance data

---

**Note:** This is a production platform actively serving 7 million total users with 150,000 DAU typically (600,000 DAU during major sales, 300,000 DAU during minor sales) with 300+ application instances, 200+ self-managed database instances, and 125+ Microservices Distributed Workload. All metrics and infrastructure details are based on actual production operations. Infrastructure management and operations was handled by DevOps team; application code was developed by the engineering team.
