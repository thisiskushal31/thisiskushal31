# PurplleAds - Technical Architecture

## System Overview

PurplleAds is a Kubernetes-based adtech platform deployed on GCP (GKE) with a multi-tier architecture supporting high-volume ad serving for 7 million monthly active users. The platform is deployed at `adtech.purplle.com`. The platform uses Application Load Balancer (ALB) deployed separately from GKE, and GKE Ingress controller automatically manages Google Cloud Layer 7 HTTP(S) Load Balancer (GCLB) resources. The GCLB is added as backend in ALB pointing to `adtech.purplle.com`. GKE Ingress handles SSL/TLS termination at the GCE L7 External Load Balancer and forwards traffic to Kubernetes Services with Container Native Load Balancing (direct to pods). Infrastructure is deployed across Production, Pre-Production, and Sandbox environments and is fully operational.

**Important Notes:**
- **ALB** is an **independent infrastructure component** deployed separately from GKE
- **GKE Ingress** automatically manages Google Cloud L7 External and L7 Internal Load Balancer resources
- **GCLB** is automatically provisioned by GKE Ingress controller and acts as traffic manager
- **Container Native Load Balancing** is configured to forward traffic directly to pods instead of node ports
- **CDN** is not deployed nor needed - service generating campaigns is in same region
- **Cloud SQL Proxy (Layer 7)** enables secure connection from different subnet in same VPC

## Quick Architecture Overview

![PurplleAds Architecture](../../assets/purplle/purplle.png)

*4-Tier Architecture Diagram - See [architecture-diagram.mmd](architecture-diagram.mmd) for Mermaid diagram reference*

### Multi-Tier Architecture Summary

**Tier 1: DNS & Security Layer**
- Route53 (AWS) → WAF (Security filtering)
- Traffic Flow: Route53 → WAF

**Tier 2: Load Balancing Layer**
- ALB (separate infrastructure) → GCLB (provisioned by GKE Ingress)
- Traffic Flow: WAF → ALB → GCLB (provisioned by GKE Ingress)

**Tier 3: Application Layer (GKE)**
- Kubernetes Ingress → Kubernetes Services → Kubernetes Deployments
- Cloud Functions (accessed via service account)
- Traffic Flow: ALB → GCLB → K8s Ingress → K8s Services → K8s Deployments

**Tier 4: Data Layer**
- Redis Cache → Cloud SQL Proxy (Layer 7) → Cloud SQL
- Traffic Flow: Application → Redis → Cloud SQL Proxy → Cloud SQL

### Complete Data Flow

**Request Flow:**
1. User/Client → Route53 (AWS DNS)
2. Route53 → WAF (Security filtering)
3. WAF → ALB (Application Load Balancer - separate infrastructure)
4. ALB → GCLB (Google Cloud Layer 7 HTTP(S) Load Balancer - provisioned by GKE Ingress)
5. GCLB → Kubernetes Ingress (within GKE cluster)
6. K8s Ingress → K8s Services → K8s Deployments
7. Application → Redis Cache → Cloud SQL Proxy (Layer 7) → Cloud SQL

**Response Flow:**
1. Cloud SQL/Redis → Application
2. Application → K8s Services → K8s Ingress
3. K8s Ingress → GCLB → ALB → WAF → Route53 → User/Client

### Key Architecture Notes

1. **ALB is NOT deployed by GKE** - It is a separate infrastructure component deployed independently
2. **GKE Ingress automatically manages GCLB** - GKE Ingress controller automatically manages Google Cloud L7 External and L7 Internal Load Balancer resources
3. **GCLB handles SSL/TLS termination** - Incoming L7 TLS connections terminate at the GCE L7 External Load Balancer
4. **Container Native Load Balancing** - Configured to forward traffic directly to pods instead of node ports
5. **GCLB is added as backend in ALB** - Points to `adtech.purplle.com` for traffic routing
6. **Cloud SQL Proxy (Layer 7)** - Enables secure connection from different subnet in same VPC
7. **CDN** - Not deployed nor needed - service generating campaigns is in same region
8. **Hybrid Cloud Architecture** - Route53 (AWS) + ALB/GCLB (GCP) + GKE (GCP)
9. **Clear Separation of Concerns** - Each tier has distinct responsibilities and deployment models

### Infrastructure Deployment Model

**Independent Infrastructure Components:**
- **ALB:** Deployed separately from GKE, managed as standalone infrastructure
- **GCLB:** Automatically managed by GKE Ingress controller, added as backend in ALB pointing to `adtech.purplle.com`
- **Route53:** AWS-managed DNS service
- **WAF:** Separate security layer
- **Cloud SQL:** GCP-managed database service
- **Cloud SQL Proxy:** Layer 7 (Application Layer) proxy for secure database connections from different subnet in same VPC
- **Redis:** Separate caching infrastructure

**GKE-Managed Components:**
- **Kubernetes Ingress:** Managed by GKE (Nginx ingress controller)
- **Kubernetes Deployments:** Managed by GKE (all application services like billing service, campaign service, etc.)
- **Kubernetes Services:** Managed by GKE (configured with service accounts for Cloud Functions access)
- **kubedns (Kubernetes DNS):** Managed by GKE for internal service discovery and DNS resolution
- **GKE Cluster:** Container orchestration platform

**Serverless Components:**
- **Cloud Functions:** Deployed separately, accessed by Kubernetes services
- **Authentication:** Service account credentials configured in Kubernetes services for secure Cloud Functions invocation

**Authentication & Authorization Components:**
- **Keycloak:** Identity Provider deployed separately, handles user authentication and identity verification
- **Sentinel Service:** RBAC service deployed on Kubernetes (not managed by this project), validates permissions after Keycloak authentication

## Architecture Pattern

PurplleAds follows a **Multi-Tier Architecture** pattern with clear separation of concerns across different layers:

### Tier 1: DNS & Security Layer
- **Route53 (AWS):** DNS service that resolves domain names and routes traffic to WAF
- **WAF (Web Application Firewall):** Standard application firewall rules, positioned after Route53
- **Purpose:** DNS resolution and first line of defense, filtering malicious traffic and enforcing security policies
- **Traffic Flow:** All external traffic flows through Route53 → WAF before reaching load balancers

### Tier 2: Load Balancing Layer
- **Route53 (AWS):** DNS service that resolves domain names and routes traffic to WAF
- **WAF (Web Application Firewall):** Security filtering with standard application firewall rules, positioned after Route53
- **Application Load Balancer (ALB):** HTTP/HTTPS traffic distribution (Layer 7 load balancing)
  - **Deployment Model:** Separate infrastructure component, deployed independently from GKE
  - **Note:** ALB is NOT deployed by GKE - it is managed as standalone infrastructure
  - **Backend Configuration:** GCLB (provisioned by GKE Ingress) is added as backend in ALB pointing to `adtech.purplle.com`
- **GCLB (Google Cloud Layer 7 HTTP(S) Load Balancer):** Automatically provisioned by GKE Ingress
  - **Purpose:** Acts as traffic manager for Kubernetes Services
  - **Features:** SSL termination, host/path routing, directs traffic to correct pods
  - **Deployment:** Automatically provisioned by GKE Ingress controller
  - **Note:** GCLB is provisioned by GKE Ingress, not a separate deployment
- **Purpose:** DNS resolution, security filtering, traffic distribution, SSL/TLS termination, high availability, and failover
- **Traffic Flow:** Route53 → WAF → ALB → GCLB (provisioned by GKE Ingress) → Kubernetes Services

### Tier 3: Application Layer
- **Kubernetes Ingress (GKE Ingress):** GKE Ingress controller that automatically provisions Google Cloud Layer 7 HTTP(S) Load Balancer (GCLB)
- **Kubernetes Deployments:** Containerized application services (auto-scales based on usage)
  - All application services (e.g., billing service, campaign service, etc.) are deployed as Kubernetes deployments
  - Services communicate through kubedns (Kubernetes DNS) for service discovery
- **Kubernetes Services:** Service discovery and internal load balancing
  - **Container Native Load Balancing:** Configured to forward traffic directly to pods instead of node ports
  - **Internal Networking:** kubedns handles DNS resolution and service discovery for inter-service communication
- **Authentication & Authorization:**
  - **Keycloak:** Identity Provider for user authentication and identity verification
  - **Sentinel Service:** RBAC service deployed on Kubernetes (not managed by this project) that validates permissions after Keycloak authentication
- **Cloud Functions:** Serverless functions accessed by Kubernetes services via service account authentication
- **Purpose:** Application logic, business processing, ad serving, campaign management, bidding system
- **Note:** CDN is not deployed nor needed - service generating campaigns is in same region
- **Traffic Flow:** Receives traffic from load balancers, processes requests through authentication/authorization, interacts with data layer and Cloud Functions

### Tier 4: Data Layer
- **Cloud SQL:** Primary database (MySQL/PostgreSQL) with Point-in-Time Recovery and daily backups
- **Redis Cache:** High-performance caching layer (reduces database load by 60-80%)
- **Purpose:** Persistent data storage, transaction processing, caching for performance optimization
- **Data Flow:** Application services query Redis first, then Cloud SQL for persistent data

### Data Flow Through Tiers

1. **External Request Flow:**
   - User/Client → Route53 (AWS DNS) → WAF (security filtering) → ALB → GCLB (provisioned by GKE Ingress) → K8s Ingress → K8s Services → K8s Deployments

2. **Application Processing:**
   - K8s Deployments → Redis Cache (check cache) → Cloud SQL (if cache miss or write operation)

3. **Response Flow:**
   - Cloud SQL/Redis → K8s Deployments → K8s Services → K8s Ingress → GCLB → ALB → WAF → Route53 → User/Client

### Architecture Benefits

- **Enhanced Security:** Multi-layer security with firewall, WAF, and network isolation
- **High Scalability:** Kubernetes auto-scaling (usage-based) and load balancing at multiple levels
- **Performance Optimization:** Redis caching reduces database load by 60-80%
- **Reliability:** Point-in-time recovery, daily backups, and multi-zone deployment
- **Maintainability:** Clear separation of concerns across tiers
- **Cost Efficiency:** Efficient resource utilization through caching and auto-scaling

## Components

### 1. Route53 (AWS)
- **Purpose:** DNS service for domain name resolution and traffic routing
- **Technology:** AWS Route53
- **Responsibilities:**
  - Domain name resolution
  - DNS routing to WAF
  - Health checks and failover
  - First point of entry for all external traffic

### 2. WAF (Web Application Firewall)
- **Purpose:** Security filtering and protection against web exploits
- **Technology:** Web Application Firewall with standard application firewall rules
- **Responsibilities:**
  - Filters malicious traffic and DDoS attacks
  - Enforces security policies
  - Applies standard application firewall rules
  - Positioned after Route53, before ALB

### 3. Application Load Balancer (ALB)
- **Purpose:** HTTP/HTTPS traffic distribution
- **Technology:** GCP Application Load Balancer
- **Deployment:** **Separate infrastructure component, deployed independently from GKE**
- **Note:** ALB is NOT deployed or managed by GKE - it is a standalone infrastructure component
- **Responsibilities:**
  - Layer 7 load balancing
  - HTTP/HTTPS routing to backend services (GCLB)
  - GCLB is added as backend in ALB pointing to `adtech.purplle.com`

### 4. GCLB (Google Cloud Layer 7 HTTP(S) Load Balancer)
- **Purpose:** Traffic manager automatically managed by GKE Ingress
- **Technology:** Google Cloud Layer 7 HTTP(S) Load Balancer (GCE L7 External Load Balancer)
- **Deployment:** Automatically managed by GKE Ingress controller
- **Responsibilities:**
  - SSL/TLS termination at the GCE L7 External Load Balancer
  - Host/path routing
  - Directing traffic to correct pods via Container Native Load Balancing
  - Exposing internal Kubernetes Services externally
  - Forwards incoming traffic to Kubernetes cluster nodes (or directly to pods with Container Native Load Balancing)
- **Integration:** Added as backend in ALB pointing to `adtech.purplle.com`
- **Note:** GKE Ingress automatically manages Google Cloud L7 External and L7 Internal Load Balancer resources. The incoming L7 TLS connections terminate at the GCE L7 External Load Balancer, which forwards traffic to the Kubernetes cluster nodes (or directly to pods with Container Native Load Balancing configured)

### 5. Kubernetes Ingress (GKE Ingress)
- **Purpose:** GKE Ingress controller that automatically provisions and manages Google Cloud Layer 7 HTTP(S) Load Balancer (GCLB)
- **Technology:** GKE Ingress Controller
- **Responsibilities:**
  - Automatically manages Google Cloud L7 External and L7 Internal Load Balancer resources
  - Automatically provisions GCLB which acts as traffic manager
  - Handles SSL/TLS termination at the GCE L7 External Load Balancer
  - HTTP/HTTPS routing within cluster
  - Path-based routing
  - Host-based routing
  - Forwards traffic to Kubernetes Services with Container Native Load Balancing (direct to pods)
- **Reference:** [GKE Ingress Documentation](https://cloud.google.com/kubernetes-engine/docs/concepts/ingress)

### 6. Kubernetes Deployments
- **Purpose:** Containerized application services
- **Technology:** Kubernetes (GKE)
- **Responsibilities:**
  - Application service hosting
  - Container orchestration
  - Auto-scaling and self-healing

### 7. Kubernetes Services
- **Purpose:** Service discovery and load balancing
- **Technology:** Kubernetes Service objects
- **Responsibilities:**
  - Internal service discovery
  - Load balancing within cluster
  - Service abstraction
  - **Container Native Load Balancing:** Configured to enable GCE load balancer to forward traffic directly to pods instead of node ports
- **Service Discovery:** kubedns (Kubernetes DNS) handles DNS resolution and service discovery for inter-service communication within the cluster
- **Application Services:** All application services (e.g., billing service, campaign service, etc.) are deployed as Kubernetes deployments and accessed via Kubernetes Services


### 9. Cloud SQL Database
- **Purpose:** Primary database for campaign data, user preferences, and transactions
- **Technology:** Cloud SQL (MySQL/PostgreSQL)
- **Responsibilities:**
  - Persistent data storage
  - Transaction processing (handles 30 Rs/click rate)
  - Campaign and bidding data management
  - User preference data storage
- **Features:**
  - Point-in-time recovery (PITR) enabled
  - Daily automated backups
  - High availability configuration

### 10. Cloud SQL Proxy
- **Purpose:** Secure connection to Cloud SQL from different subnet in same VPC
- **Technology:** Cloud SQL Proxy (Layer 7 - Application Layer)
- **OSI Layer:** Layer 7 (Application Layer)
- **Deployment:** Deployed in Kubernetes cluster
- **Responsibilities:**
  - Provides secure connection to Cloud SQL database
  - Enables connection from different subnet within same VPC
  - Handles authentication and encryption
  - Manages connection pooling
- **Network Architecture:** Connects Kubernetes pods in one subnet to Cloud SQL in different subnet within same VPC

### 11. Redis Cache
- **Purpose:** High-performance caching layer to reduce database load
- **Technology:** Redis
- **Responsibilities:**
  - Cache frequently accessed ad data
  - Cache user preference data
  - Cache campaign configurations
  - Reduce database query load by 60-80%

### 12. Cloud Functions
- **Purpose:** Serverless functions for event-driven processing and background tasks
- **Technology:** GCP Cloud Functions
- **Deployment:** Deployed separately, accessed by Kubernetes services
- **Authentication:** Accessed via service account used in Kubernetes services
- **Responsibilities:**
  - Event-driven processing
  - Background task execution
  - Asynchronous operations
  - Integration with other GCP services
- **Access Pattern:** Kubernetes services authenticate to Cloud Functions using service account credentials

### 13. Keycloak
- **Purpose:** Identity Provider for authentication and identity verification
- **Technology:** Keycloak (Identity and Access Management)
- **Deployment:** Deployed separately from this project
- **Responsibilities:**
  - User authentication and identity verification
  - Single Sign-On (SSO) capabilities
  - Token issuance for authenticated users
  - Identity management for platform users
- **Integration:** All platform users authenticate through Keycloak before accessing application services

### 14. Sentinel Service
- **Purpose:** Role-Based Access Control (RBAC) service for authorization
- **Technology:** RBAC service deployed on Kubernetes
- **Deployment:** Kubernetes deployment (not managed by this project)
- **Responsibilities:**
  - Role-based permission management
  - Access control validation after Keycloak authentication
  - Authorization checks for platform services
  - Permission validation before allowing access to application services
- **Authentication Flow:** Operates after Keycloak verification completes, validates user permissions before allowing access to application services

## Data Flow

### Request Flow (Inbound)

1. **DNS Resolution:**
   - User/Client sends request → Route53 (AWS DNS service)
   - Route53 resolves domain name to WAF endpoint

2. **Security Layer:**
   - Route53 → WAF (Web Application Firewall applies standard firewall rules)
   - WAF filters malicious traffic, DDoS attacks, and enforces security policies

3. **Application Load Balancing:**
   - WAF → ALB (Application Load Balancer for HTTP/HTTPS traffic)
   - ALB has GCLB added as backend pointing to `adtech.purplle.com`

4. **GKE Ingress & GCLB:**
   - ALB → GCLB (Google Cloud Layer 7 HTTP(S) Load Balancer)
   - GCLB is automatically provisioned by GKE Ingress controller
   - GCLB acts as traffic manager, handles SSL termination, host/path routing
   - GCLB directs traffic to correct pods

5. **Application Routing:**
   - GCLB → Kubernetes Ingress (GKE Ingress controller)
   - Ingress automatically provisions GCLB and routes based on host, path, and routing rules
   - Ingress scales automatically based on network load

5. **Service Discovery:**
   - K8s Ingress → Kubernetes Services (internal load balancing)
   - kubedns (Kubernetes DNS) resolves service names for inter-service communication
   - Services route to appropriate pods based on service selectors

6. **Authentication & Authorization:**
   - Request → Keycloak (identity verification and authentication)
   - Keycloak → Sentinel Service (RBAC - validates user permissions)
   - Sentinel Service validates permissions before allowing access to application services

7. **Application Processing:**
   - K8s Services → Kubernetes Deployments (application pods)
   - Application processes request, executes business logic
   - Deployments auto-scale based on CPU, memory, and custom metrics
   - Application services (e.g., billing service, campaign service) communicate via kubedns

8. **Data Access:**
   - Application → Redis Cache (check for cached data)
   - If cache hit: Return data from Redis
   - If cache miss: Application → Cloud SQL Proxy (Layer 7) → Cloud SQL (query database)
   - Cloud SQL Proxy provides secure connection from different subnet in same VPC
   - Cache updated after database query

9. **Cloud Functions Integration:**
   - Kubernetes Services → Cloud Functions (authenticated via service account)
   - Cloud Functions execute event-driven tasks and background processing
   - Service account credentials used for secure authentication between K8s services and Cloud Functions

### Response Flow (Outbound)

1. **Data Retrieval:**
   - Cloud SQL/Redis → Application (K8s Deployments)

2. **Response Processing:**
   - Application processes data, generates response
   - Application → K8s Services → K8s Ingress

3. **Load Balancing:**
   - K8s Ingress → GCLB (Google Cloud Layer 7 HTTP(S) Load Balancer)
   - GCLB → ALB (Application Load Balancer)

4. **Security & Delivery:**
   - ALB → WAF (Web Application Firewall)
   - WAF → Route53 (AWS DNS)
   - Route53 → User/Client


### Click Transaction Flow

1. User clicks ad → Request flows through all tiers
2. Application records click → Redis (cache update) → Cloud SQL (persistent storage)
3. Transaction processed at ~3.65 Lakh clicks/day capacity
4. Database handles millions of transactions with Redis reducing load by 60-80%
5. Background processing → Kubernetes Services → Cloud Functions (via service account) for async tasks

## Infrastructure Design

### Network Architecture
- **VPC Structure:** Multi-VPC setup for Production, Pre-Production, and Sandbox
- **Subnets:** Segregated subnets for different tiers and services
  - **Cloud SQL Proxy:** Enables secure connection from Kubernetes pods in one subnet to Cloud SQL in different subnet within same VPC
- **Internal Service Discovery:** 
  - **kubedns (Kubernetes DNS):** Handles DNS resolution and service discovery for inter-service communication within the Kubernetes cluster
  - All application services communicate via kubedns for service discovery
- **Load Balancing:** 
  - **ALB:** Separate infrastructure component for application traffic (HTTP/HTTPS) - NOT deployed by GKE
  - **GCLB:** Automatically provisioned by GKE Ingress, added as backend in ALB pointing to `adtech.purplle.com`
  - **K8s Ingress:** Managed by GKE, automatically provisions GCLB for traffic management
- **CDN:** Not deployed nor needed - service generating campaigns is in same region
- **Deployment Model:** ALB is deployed independently from GKE, GCLB is automatically provisioned by GKE Ingress

### Compute Resources
- **Kubernetes Clusters:** GKE Standard clusters across three environments
  - Production cluster (Mumbai - asia-south1)
  - Pre-Production cluster
  - Sandbox cluster
- **Node Pools:** 
  - **Main Workload Pool:** n2-standard-8 (8 vCPU, 32GB RAM) - ~5-6 high-res pods per VM
  - **Ingress/LB Pool:** n2-standard-4 (4 vCPU, 16GB RAM) - Dedicated Nginx Ingress
- **Auto-scaling:** 
  - Horizontal Pod Autoscaling (HPA) - usage-based scaling
  - Cluster Autoscaling
  - Node pool autoscaling based on demand
  - Nginx Ingress scales on network load

### Storage & Databases
- **Primary Database:** 
  - Cloud SQL (MySQL/PostgreSQL) for persistent data storage
  - Handles campaign data, user preferences, bidding data, and transaction records
  - **Point-in-Time Recovery (PITR):** Enabled for data recovery to any point in time
  - **Daily Backup:** Automated daily backups for disaster recovery
  - **Transaction Capacity:** Designed to handle high-volume click transactions
  - **Click Volume Handled:**
    - **Total Annual Clicks:** ~13.33 Crore clicks/year (133.3 million clicks)
    - **Monthly Clicks:** ~1.11 Crore clicks/month (11.1 million clicks)
    - **Daily Clicks:** ~3.65 Lakh clicks/day (365,297 clicks/day)
    - **Peak Daily Clicks:** Significantly higher during sales events and promotions
  - **Database Load:** Database handles millions of click transactions, campaign updates, and user preference queries daily
- **Caching Layer:** 
  - Redis deployed for high-performance caching
  - Reduces database load by caching:
    - Frequently accessed ad data
    - User preference data
    - Campaign configurations
    - Bidding data
  - Significantly improves response times and reduces database query load
- **Object Storage:** GCS for static assets, logs, and backup storage
- **Backup Strategy:** 
  - Daily automated backups via Cloud SQL
  - Point-in-time recovery capability
  - Backup retention policy configured

### Environment Status
- **Production:** Fully deployed and live, actively serving production traffic
- **Pre-Production:** Deployed for testing and staging
- **Sandbox:** Deployed for development and experimentation

### Production Status
- **Live & Operational:** Platform is actively being used in production
- **Software Replacement:** Successfully replaced ₹80 Lakh/year business management software
- **Active Usage:** Currently serving as alternative to expensive third-party solution

## Security Architecture

### Zero Trust Security
- **Zero Trust Architecture:** Implemented zero-trust security model with defense-in-depth approach
- **Defense-in-Depth:** Multiple layers of security controls at network, application, and data levels
- **Least Privilege Access:** Minimal required permissions for services and users
- **Continuous Verification:** Ongoing security monitoring and verification

### Network Security
- **DNS & Entry Point:** Route53 (AWS DNS) is the entry point for all external traffic
- **Web Application Firewall (WAF):** 
  - Traffic flows Route53 → WAF (Web Application Firewall) with standard application firewall rules
  - WAF filters malicious traffic before it reaches ALB
  - WAF provides protection against common web exploits and attacks
  - Content filtering mechanisms in place
- **Firewall Rules:** 
  - Strict firewall rules allowing only ports 80/443 access via WAF
  - Rest of traffic restricted to internal network only
  - Network segmentation via VPC
- **Geo-blocking:** Geo-blocking implemented to restrict access outside India
- **Rate Limiting:** Rate limiting configured to prevent abuse and ensure fair resource usage
- **Bot Protection:** Bot detection and blocking mechanisms to prevent automated attacks and bot calls

### Identity & Access Management
- **IAM:** Identity and Access Management with role-based policies
- **Keycloak:** Identity Provider for user authentication and identity verification
  - Handles all platform user authentication
  - Issues authentication tokens for verified users
  - Single Sign-On (SSO) capabilities
- **Sentinel Service:** RBAC (Role-Based Access Control) service for authorization
  - Deployed on Kubernetes (not managed by this project)
  - Validates user permissions after Keycloak authentication
  - Manages role-based access control for platform services
  - Validates permissions before allowing access to application services
- **Kubernetes RBAC:** Role-Based Access Control for cluster access
- **Service Account Authentication:** Service account authentication for Cloud Functions access from Kubernetes services
- **Service Accounts:** Service accounts configured in Kubernetes services for secure Cloud Functions invocation
- **Authentication Flow:** Keycloak (authentication) → Sentinel Service (authorization/RBAC) → Application Services

### Data Protection & Compliance
- **DPDP Law Compliance:** Compliant with India's Digital Personal Data Protection Act, 2023
  - Data protection and privacy measures aligned with DPDP requirements
  - User data handling in accordance with Indian data protection regulations
  - Privacy-first approach to data collection and processing
- **Secrets Management:** GCP Secrets Manager used for all secrets management
  - API keys and tokens
  - Database credentials
  - Application configuration secrets
  - All sensitive data and credentials
- **SSL/TLS Certificates:** Self-managed SSL certificates
  - Self-managed certificates obtained, provisioned, and renewed independently
  - Used to secure communication between clients and load balancers
  - Supported certificate types: Domain Validation (DV), Organization Validation (OV), Extended Validation (EV)
  - Used with Global external Application Load Balancer and Regional external Application Load Balancer
- **Encryption:** 
  - Encryption in transit: TLS/SSL for all external traffic (ports 80/443)
  - Encryption at rest: Cloud SQL and storage encryption enabled

### Security Best Practices
- **Network Segmentation:** VPC-based network isolation
- **Regular Security Audits:** Ongoing security monitoring and assessment
- **Incident Response:** Prepared incident response procedures
- **Security Monitoring:** Continuous monitoring of security events and anomalies

## Monitoring & Observability

- **Unified Observability Stack:** Architectured unified observability stack with Prometheus and Grafana, enabling real-time monitoring and automated incident escalation

- **Metrics Collection:** 
  - Prometheus deployed in Kubernetes cluster for metrics collection
  - Scrapes metrics from K8s pods, services, and infrastructure components
  - Collects application metrics, infrastructure metrics, and business metrics
- **Visualization:** 
  - Grafana connected to Prometheus as datasource
  - Custom dashboards for real-time monitoring of:
    - Application performance metrics
    - Infrastructure health (CPU, memory, network)
    - Ad serving metrics and click-through rates
    - Database performance metrics
- **Alerting:** 
  - Grafana alerts configured for critical thresholds
  - Alert notifications for:
    - High error rates
    - Resource exhaustion
    - Database connection issues
    - Service downtime
    - Performance degradation
  - **MTTR Reduction:** Reduced Mean Time to Recovery (MTTR) from 30 to 7 minutes by architecting a unified observability stack with Prometheus and Grafana, enabling real-time monitoring and automated incident escalation
- **Logging:** 
  - GCP Stackdriver (Cloud Logging) for centralized log aggregation
  - Application logs, access logs, and system logs collected
  - Log-based monitoring and analysis
  - Integration with GCP monitoring stack

## Infrastructure Automation

### Infrastructure as Code

- **Terraform Modules:**
  - Reusable, parameterized Terraform modules for common GCP patterns
  - Modules for GKE clusters, Cloud SQL instances, VPCs, load balancers (ALB, GCLB) with WAF integration
  - Kubernetes deployments and services defined as code
  - Environment-specific configurations while maintaining infrastructure consistency
  - **Result:** 40%+ faster deployments with consistent infrastructure

- **Ansible Integration:**
  - Configuration management for system-level settings
  - Automated application configuration and deployment
  - Integration with Terraform for complete infrastructure automation

- **GitOps Workflows:**
  - Infrastructure changes managed through version-controlled Git repositories
  - Automated testing and validation of infrastructure changes
  - Consistent infrastructure management across environments

### CI/CD Automation

- **Accelerated Infrastructure Delivery:** Accelerated infrastructure delivery speed by 40%+ by collaborating on CI/CD automation using Terraform, Jenkins, and GitOps, automating over 40% of provisioning tasks

- **GitLab CI Integration:**
  - Automated infrastructure provisioning through GitLab CI pipelines
  - Integrated Trivy security scanning into GitLab CI deployment pipelines
  - Automated testing and validation of infrastructure changes
  - Application deployment automation

- **Jenkins Integration:**
  - Jenkins pipelines integrated with Terraform for infrastructure automation
  - **CI/CD Modernization:** Modernized CI/CD infrastructure by migrating from freestyle bash jobs to scripted pipeline jobs in Jenkins, integrated with Slack for real-time job failure alerts, improving monitoring and reducing incident response time
  - Automated deployment workflows
  - Integration with monitoring and alerting systems

- **Automated Security:**
  - Trivy scanning integrated into CI/CD pipelines to catch vulnerabilities early
  - Automated IAM role minimization to enforce least privilege access
  - GCP Secrets Manager integration for secure credential management
  - Automated network logging and public IP cleanup

### Service Orchestration

- **Kubernetes Deployment Management:**
  - Managed 100+ high-availability Kubernetes deployments on Google Kubernetes Engine (GKE), ensuring optimal performance, scalability, and reliability in production
  - Automated deployment of application services (billing, campaign services) as Kubernetes deployments
  - kubedns (Kubernetes DNS) for internal service discovery
  - Automated service account management for secure inter-service communication

- **Elasticsearch Automation:**
  - **Agentic AI-Based Automation:** Engineered agentic AI-based automation for Elasticsearch cluster management using n8n, Terraform, Ansible, and Python, streamlining cluster provisioning and lifecycle management

- **Automated Backups:**
  - Cloud SQL automated daily backups with Point-in-Time Recovery (PITR)
  - Automated backup scheduling and retention policies
  - **Result:** Improved data resilience with automated disaster recovery processes

## Disaster Recovery

- **High-Availability Data Persistence and DR:** Engineered high-availability Data Persistence and Disaster Recovery (DR) solutions for MySQL, MongoDB, and Elasticsearch, utilizing automated backup triggers to ensure system resilience and data integrity

- **Backup Strategy:** 
  - Cloud SQL point-in-time recovery (PITR) enabled
  - Daily automated backups stored in GCS
  - Backup retention policy configured for compliance
  - Cloud SQL automated daily backups with Point-in-Time Recovery (PITR)
  - Automated backup triggers for MySQL, MongoDB, and Elasticsearch
- **DR Plan:** 
  - **Point-in-Time Recovery:** Configured in different subnet/zone for geographic redundancy
  - **Infrastructure as Code (IaC):** Complete infrastructure defined in Terraform/Ansible with reusable modules
  - **DR Environment:** Ready-to-deploy infrastructure code for rapid recovery
  - **Backup Restoration:** Automated restore procedures from daily backups
  - **Multi-Zone Deployment:** Production infrastructure spans multiple availability zones
  - **Failover Capability:** Can quickly spin up infrastructure in different zone using IaC
- **RTO/RPO:** 
  - **Recovery Time Objective (RTO):** [Target: < 1 hour with IaC deployment]
  - **Recovery Point Objective (RPO):** [Target: < 15 minutes with PITR, < 24 hours with daily backups]

## Scalability Considerations

- **Horizontal Scaling:** 
  - **Kubernetes Usage-Based Scaling:** 
    - Horizontal Pod Autoscaler (HPA) configured based on CPU, memory, and custom metrics
    - Pods automatically scale up/down based on actual usage and demand
    - Supports traffic spikes during peak hours and sales events (4.6x traffic increase during sales events)
  - **Nginx Ingress Scaling:** 
    - Nginx ingress controller scales automatically based on network load
    - Handles increased traffic volume during high-demand periods
    - Load distribution across multiple ingress pods
  - **Database Scaling:** 
    - Cloud SQL read replicas for read-heavy workloads
    - Connection pooling to handle concurrent requests
  - **Infrastructure Automation:** 
    - Parameterized Terraform modules enable easy environment replication
    - Automated scaling through infrastructure as code
    - Consistent scaling patterns across environments
- **Vertical Scaling:** 
  - Cloud SQL instance sizing can be adjusted based on workload
  - Kubernetes node pool scaling for compute resources
  - Redis cluster scaling for cache capacity
  - Automated scaling policies managed through Terraform
- **Performance Optimization:** 
  - **Caching Strategy:** 
    - Redis caching layer reduces database load by 60-80%
    - Frequently accessed data cached (campaigns, user preferences, ad configurations)
    - Cache invalidation strategies for data consistency
  - **Database Optimization:** 
    - Indexed queries for fast data retrieval
    - Connection pooling to manage database connections efficiently
    - Query optimization for high transaction volume (~3.65 Lakh clicks/day, ~1.11 Crore clicks/month)
  - **Load Balancing:** 
    - ALB distributes traffic across multiple backend instances
    - GCLB (provisioned by GKE Ingress) handles traffic routing
    - Kubernetes service load balancing for internal traffic
  - **CDN:** Not deployed nor needed - service generating campaigns is in same region - service generating campaigns is in same region
  - **Network Optimization:** 
    - WAF positioned before ALB for security without performance impact
    - Optimized routing through internal network for backend services
  - **Application-Level Optimization:** 
    - Efficient ad serving algorithms
    - Batch processing for non-critical operations
    - Async processing for background tasks
  - **Monitoring-Driven Optimization:** 
    - Prometheus metrics identify performance bottlenecks
    - Grafana dashboards enable proactive optimization
    - Continuous performance tuning based on real-time metrics

