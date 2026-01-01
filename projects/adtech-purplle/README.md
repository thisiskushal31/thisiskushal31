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
- **Monthly Active Users:** 7 million users/month
- **Average Daily Active Users:** 146,000 users/day (regular days)
- **Peak Daily Active Users:** ~670,000 users/day (4.6x spike during sales events)
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

- ✅ **Live Production Platform** - Fully deployed at `adtech.purplle.com`, actively serving 7M+ users
- ✅ **Cost Optimization** - 93% reduction in software costs (₹80 Lakh → ₹5.7 Lakh infrastructure)
- ✅ **Scalability** - Handles 4.6x traffic spikes during sales events (146K → 670K daily users)
- ✅ **Revenue Support** - Platform supports ₹400+ Crore in brand advertising revenue
- ✅ **House Brand Support** - Critical platform for 5 major house brands (₹680-₹800 Cr revenue)

## Technical Stack

**Cloud & Infrastructure:** GCP (GKE), AWS (Route53), Kubernetes, ALB, GCLB  
**Container Orchestration:** Kubernetes (GKE), K8s Ingress, Deployments, Services  
**Service Discovery:** kubedns (Kubernetes DNS) for internal cluster networking  
**Databases:** Cloud SQL (MySQL/PostgreSQL), Redis, Cloud SQL Proxy  
**CI/CD:** Jenkins, GitLab CI  
**Infrastructure as Code:** Terraform, Ansible  
**Monitoring:** Prometheus, Grafana, GCP Stackdriver  
**Security:** Zero Trust, WAF, Geo-blocking, Rate Limiting, Bot Protection, DPDP Compliance  
**Authentication & Authorization:** Keycloak (Identity Provider), Sentinel Service (RBAC - Kubernetes deployment)

## Service Architecture

**Application Services:**
- All application services (e.g., billing service, campaign service, etc.) are deployed as Kubernetes deployments within the GKE cluster
- Services communicate through Kubernetes service discovery and internal networking
- **Internal Networking:** kubedns (Kubernetes DNS) handles service discovery and DNS resolution for inter-service communication within the cluster
- Each service is containerized and managed through Kubernetes orchestration

**Authentication & Authorization Flow:**
- **Keycloak:** Handles identity verification and authentication for all platform users
- **Sentinel Service:** RBAC (Role-Based Access Control) service deployed on Kubernetes
  - Operates after Keycloak verification completes
  - Manages role-based permissions and access control for platform services
  - Not managed by this project (separate service)
  - Validates user permissions before allowing access to application services

## Documentation

For detailed information, see:
- **[Architecture Details](architecture.md)** - Complete technical architecture and infrastructure design
- **[Metrics & Analysis](metrics.md)** - Detailed metrics, cost analysis, and business performance data

---

**Note:** This is a production platform actively serving traffic at `adtech.purplle.com`. All metrics and costs are based on actual production deployment.
