# Purplle Platform - Technical Architecture

## System Overview

Purplle.com is the main e-commerce platform infrastructure deployed on GCP (GKE) with a multi-tier architecture supporting 7 million total users with 150,000 daily active users (DAU) typically, scaling to 600,000 DAU during major sales events (4x) and 300,000 DAU during minor sales events (2x), with 300+ application instances and 125+ Microservices Distributed Workload. The platform uses Application Load Balancer (ALB) deployed separately from GKE, and GKE Ingress controller automatically manages Google Cloud Layer 7 HTTP(S) Load Balancer (GCLB) resources. The GCLB is added as backend in ALB pointing to the main platform. GKE Ingress handles SSL/TLS termination at the GCE L7 External Load Balancer and forwards traffic to Kubernetes Services with Container Native Load Balancing (direct to pods). Infrastructure is deployed across Production, Pre-Production, and Sandbox environments and is fully operational. Achieved ₹1 Crore in cost savings through infrastructure optimization and automation.

**Important Notes:**
- **ALB** is an **independent infrastructure component** deployed separately from GKE
- **GKE Ingress** automatically manages Google Cloud L7 External and L7 Internal Load Balancer resources
- **GCLB** is automatically provisioned by GKE Ingress controller and acts as traffic manager
- **Container Native Load Balancing** is configured to forward traffic directly to pods instead of node ports
- **Cloud SQL Proxy (Layer 7)** enables secure connection from different subnet in same VPC
- **125+ Microservices Distributed Workload** orchestrated on GKE across the platform

**Note:** Infrastructure deployment and management was handled by DevOps team. Application code was developed by the engineering team.

## Quick Architecture Overview

![Purplle Architecture](../../assets/purplle/purplle.png)

*4-Tier Architecture Diagram - See [architecture-diagram.mmd](architecture-diagram.mmd) for Mermaid diagram reference*

### Multi-Tier Architecture Summary

**Tier 1: DNS & Security Layer**
- Route53 (AWS) → WAF (Security filtering)
- Traffic Flow: Route53 → WAF

**Tier 2: Load Balancing Layer**
- ALB (separate infrastructure) → GCLB (provisioned by GKE Ingress)
- Traffic Flow: WAF → ALB → GCLB (provisioned by GKE Ingress)

**Tier 3: Application Layer**
- GCP Kubernetes Engine (Zone A and Zone B) → Kubernetes Ingress → Kubernetes Services → Kubernetes Deployments
- app-server IG (Zone A/B) → app-instance instances
- Management Instances (manage-01, manage-api, manage-util-01) in Zone A/B
- Cloud Functions (accessed via service account)
- Traffic Flow: Production LB → GKE/app-server IG OR Management LBs → Management Instances
- **125+ Microservices Distributed Workload** orchestrated on GKE

**Tier 4: Data Layer**
- MySQL Master-Slave (purplle_purplle2, warehouseDB) with replication
- Redis/Redis persistence/Memorystore (caching)
- Elasticsearch (search and analytics)
- MongoDB (document database)
- Aerospike (A/B testing)
- Cloud SQL Proxy (Layer 7) for secure connections
- GCP Cloud NAT for outgoing internet access
- Traffic Flow: Application → Redis/Elasticsearch/MongoDB/Aerospike → MySQL Master/Slaves

### Complete Data Flow

**Request Flow:**
1. User/Client (Mobile/Desktop) → Route53 (AWS DNS)
2. Route53 → Reblaze WAF (Security filtering)
3. WAF → Production LB (or Management LBs: Manage-001, manageapi-lb, reporting-manage-lb, manageutil)
4. Production LB → GCP Kubernetes Engine (Zone A/B) OR app-server IG (Zone A/B)
5. For Kubernetes: GCLB → Kubernetes Ingress → K8s Services → K8s Deployments
6. For Management: Management LBs → manage-01, manage-api, manage-util-01
7. Application → Redis/Redis persistence/Memorystore → MySQL (Master/Slave) OR Elasticsearch OR MongoDB OR Aerospike

**Response Flow:**
1. MySQL/Redis/Elasticsearch/MongoDB/Aerospike → Application
2. Application → K8s Services → K8s Ingress (for Kubernetes) OR Management Instances
3. K8s Ingress → GCLB → Production LB → WAF → Route53 → User/Client
4. Management Instances → Management LBs → Route53 → User/Client

**Outgoing Internet Access:**
- All components in Private Subnet → GCP Cloud NAT → Internet

### Key Architecture Notes

1. **ALB is NOT deployed by GKE** - It is a separate infrastructure component deployed independently
2. **GKE Ingress automatically manages GCLB** - GKE Ingress controller automatically manages Google Cloud L7 External and L7 Internal Load Balancer resources
3. **GCLB handles SSL/TLS termination** - Incoming L7 TLS connections terminate at the GCE L7 External Load Balancer
4. **Container Native Load Balancing** - Configured to forward traffic directly to pods instead of node ports
5. **GCLB is added as backend in ALB** - Points to main platform for traffic routing
6. **Cloud SQL Proxy (Layer 7)** - Enables secure connection from different subnet in same VPC
7. **Hybrid Cloud Architecture** - Route53 (AWS) + ALB/GCLB (GCP) + GKE (GCP)
8. **Clear Separation of Concerns** - Each tier has distinct responsibilities and deployment models
9. **125+ Microservices Distributed Workload** - Multiple application services orchestrated on GKE
10. **300+ Application Instances** - Infrastructure scale supporting 1 crore+ users

### Infrastructure Deployment Model

**Independent Infrastructure Components:**
- **ALB:** Deployed separately from GKE, managed as standalone infrastructure
- **GCLB:** Automatically managed by GKE Ingress controller, added as backend in ALB
- **Route53:** AWS-managed DNS service
- **WAF:** Separate security layer
- **Cloud SQL:** GCP-managed database service
- **Cloud SQL Proxy:** Layer 7 (Application Layer) proxy for secure database connections from different subnet in same VPC
- **Redis:** Separate caching infrastructure
- **Aerospike:** In-memory NoSQL database for A/B testing

**GKE-Managed Components:**
- **Kubernetes Ingress:** Managed by GKE (Nginx ingress controller)
- **Kubernetes Deployments:** Managed by GKE (125+ Microservices Distributed Workload)
- **Kubernetes Services:** Managed by GKE (configured with service accounts for Cloud Functions access)
- **kubedns (Kubernetes DNS):** Managed by GKE for internal service discovery and DNS resolution
- **GKE Cluster:** Container orchestration platform

**Serverless Components:**
- **Cloud Functions:** Deployed separately, accessed by Kubernetes services
- **Authentication:** Service account credentials configured in Kubernetes services for secure Cloud Functions invocation

## Architecture Pattern

Purplle.com follows a **Multi-Tier Architecture** pattern with clear separation of concerns across different layers:

### Tier 1: DNS & Security Layer
- **Route53 (AWS):** DNS service that resolves domain names and routes traffic to WAF
- **WAF (Web Application Firewall):** Security filtering and protection against web exploits
  - Standard application firewall rules
  - Filters malicious traffic and DDoS attacks
  - Enforces security policies
  - Positioned after Route53, before ALB

### Tier 2: Load Balancing Layer
- **Production Load Balancer (Production LB):** Main production traffic distribution
  - Receives traffic from Reblaze WAF
  - Routes to GCP Kubernetes Engine (Zone A and Zone B)
  - Routes to app-server instance groups (Zone A and Zone B)
- **Management Load Balancers:**
  - **Manage-001 LB:** Routes to manage-01 instances
  - **manageapi-lb:** Routes to manage-api instances
  - **reporting-manage-lb:** Routes to manage-api instances (reporting)
  - **manageutil LB:** Routes to manage-util-01 instances
- **GCLB (Google Cloud Layer 7 HTTP(S) Load Balancer):** Traffic manager automatically managed by GKE Ingress
  - **Deployment:** Automatically managed by GKE Ingress controller
  - SSL/TLS termination at the GCE L7 External Load Balancer
  - Host/path routing
  - Directing traffic to correct pods via Container Native Load Balancing
  - Forwards incoming traffic to Kubernetes cluster nodes (or directly to pods with Container Native Load Balancing)

### Tier 3: Application Layer
- **Kubernetes Ingress (GKE Ingress):** GKE Ingress controller that automatically provisions Google Cloud Layer 7 HTTP(S) Load Balancer (GCLB)
- **Kubernetes Deployments:** Containerized application services (auto-scales based on usage)
  - **125+ Microservices Distributed Workload** orchestrated on GKE
  - Multiple application services deployed as Kubernetes deployments
  - Services communicate via kubedns for service discovery
- **Kubernetes Services:** Service discovery and internal load balancing
  - **Container Native Load Balancing:** Configured to forward traffic directly to pods instead of node ports
  - **Internal Networking:** kubedns handles DNS resolution and service discovery for inter-service communication
- **Cloud Functions:** Serverless functions accessed by Kubernetes services via service account authentication
- **Purpose:** Application logic, business processing, e-commerce operations, user management, product catalog, checkout, payments

### Tier 4: Data Layer
- **MySQL Databases (Master-Slave Replication):**
  - **MySQL Master - purplle_purplle2:** Primary database for main e-commerce operations
    - Connected to 3 MySQL Slaves for read replication
  - **MySQL Master - warehouseDB:** Primary database for warehouse operations
    - Connected to 1 MySQL Slave - warehouse for read replication
  - Point-in-time recovery (PITR) enabled
  - Automated daily backups
  - Multi-zone deployment for high availability
- **Redis Cache:**
  - **Redis:** In-memory caching layer
    - Reduces database load by 60-80%
    - Stores frequently accessed data (product catalog, user sessions, etc.)
    - Improves response times for read-heavy operations
  - **Redis persistence:** Persistent Redis cache for critical data
  - **Memorystore:** GCP managed caching service
- **Elasticsearch:** Search and analytics engine for product search and log analysis
- **MongoDB:** Document database for specific use cases
- **Aerospike:** In-memory NoSQL database used for A/B testing
  - High-performance key-value store for A/B testing experiments
  - Enables real-time feature flagging and experiment management
  - Supports high-throughput read/write operations for testing scenarios
- **Cloud SQL Proxy (Layer 7):** Secure database connection proxy
  - Enables secure connection from different subnet in same VPC
  - Layer 7 (Application Layer) proxy
  - Handles connection pooling and security
- **GCP Cloud NAT:** Network Address Translation for outgoing internet access from private subnet

## Data Flow

### E-Commerce Transaction Flow

1. User browses products → Request flows through all tiers
2. Application processes request → Redis (cache check) → Cloud SQL (if cache miss or write operation)
3. Transaction processed (product catalog, cart, checkout, payment)
4. Database handles e-commerce transactions with Redis reducing load by 60-80%
5. Background processing → Kubernetes Services → Cloud Functions (via service account) for async tasks

### Traffic Volume Handled:
- **Total Annual Clicks:** ~13.33 Crore clicks/year (133.3 million clicks)
- **Monthly Clicks:** ~1.11 Crore clicks/month (11.1 million clicks)
- **Daily Clicks:** ~3.65 Lakh clicks/day (365,297 clicks/day)
- **Peak Daily Clicks:** Significantly higher during sales events and promotions
- **Database Load:** Database handles millions of click transactions, campaign updates, and user preference queries daily

### Traffic Patterns

**Public Traffic:**
- External traffic from Mobile/Desktop users flows through Route53 → Reblaze WAF → Production LB → GCP Kubernetes Engine/app-server IG
- Management traffic flows through Route53 → Management LBs → manage-01, manage-api, manage-util-01
- Handles 7M total users with 150K DAU typically (600K during major sales, 300K during minor sales) with 300+ application instances

**Private/Internal Traffic:**
- Service-to-service communication within cluster via kubedns → Services
- Internal API calls between microservices
- Application layer to database layer communication (MySQL, Redis, Elasticsearch, MongoDB, Aerospike)

**Outgoing Internet:**
- All private subnet components access internet via GCP Cloud NAT

## Infrastructure Design

### Scalability Considerations

- **Auto-scaling:** 
  - **Horizontal Pod Autoscaling (HPA)** - Based on CPU, memory, and custom metrics
  - **Cluster Autoscaling** - Automatic cluster scaling based on demand
  - **Node Pool Autoscaling** - Node pool autoscaling based on demand
  - **Nginx Ingress** - Scales on network load
  - **Result:** Infrastructure scales horizontally without manual intervention
- **Load Balancing:**
  - Multiple layers of load balancing (ALB, GCLB, Kubernetes Services)
  - Container Native Load Balancing for direct pod access
- **Caching:**
  - Redis caching reduces database load by 60-80%
  - Improves response times for read-heavy operations

### Security Architecture

**Network Security:**
- WAF (Reblaze) for web application protection (major tasks done by Reblaze team)
- Zero-trust architecture
- Network isolation between tiers
- VPC for network segmentation
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

**Identity & Access Management:**
- Service account authentication for Cloud Functions
- **Kubernetes RBAC** for cluster access control
- **Automated IAM role minimization** using Python scripts, reducing misconfigurations
- **Secure Boot** enabled
- **Single Sign-On (SSO)** authentication implemented
- **IP Whitelisting** for multiple internal URLs
- OAuth keys management

**Data Security:**
- Cloud SQL Proxy for secure database connections
- Encrypted data at rest and in transit
- **Secrets Manager** deployed across Kubernetes & VMs, decoupling sensitive credentials from application source code
- DPDP compliance

**Security Scanning:**
- **Trivy container scanning** integrated with GitLab CI to detect and remediate vulnerable code
- Automated security checks
- Vulnerability scanning
- Adhering to zero-trust architecture and DevSecOps principles

**Defense-in-Depth:**
- Implemented defense-in-depth security controls to enforce traffic segmentation and access restrictions
- Ensuring secure and compliant deployments across environments

### Monitoring & Observability

**Monitoring Stack:**
- **Prometheus:** Metrics collection and storage
- **Grafana:** Visualization and alerting
- **GCP Stackdriver:** Cloud-native monitoring and logging
- **Unified Observability Stack:** Architectured unified observability stack with Prometheus and Grafana, enabling real-time monitoring and automated incident escalation

**Key Metrics:**
- Infrastructure health and performance
- Application performance and errors
- Resource utilization
- Cost tracking and optimization

**Alerting:**
- Unified alerting system with Grafana Alerts
- Automated escalation
- **MTTR Reduction:** Reduced Mean Time to Recovery (MTTR) from 30 to 7 minutes by architecting a unified observability stack with Prometheus and Grafana, enabling real-time monitoring and automated incident escalation

### Disaster Recovery

**Backup Strategy:**
- **Designed DR and backup plan** for databases and VMs
- **High-Availability Data Persistence and DR:** Engineered high-availability Data Persistence and Disaster Recovery (DR) solutions for MySQL, MongoDB, and Elasticsearch, utilizing automated backup triggers to ensure system resilience and data integrity
- **Automated Backups:** Using Python and Bash scripts with cron scheduling for:
  - MySQL databases
  - MongoDB databases
  - Elasticsearch clusters
  - Cloud SQL instances
- Automated daily backups for Cloud SQL
- Point-in-time recovery (PITR) enabled
- Backup retention policies
- Master/Slave database flag management on both VM-based and Cloud SQL instances
- **Result:** Improved data resilience, automated disaster recovery processes, ensuring system resilience and data integrity

**High Availability:**
- Multi-zone deployment
- 99%+ uptime maintained
- Automated failover capabilities
- Database replication with master/slave configuration

### Infrastructure Automation

**Infrastructure as Code:**
- Terraform for infrastructure provisioning
- Ansible for configuration management
- GitOps workflows for infrastructure changes
- Version-controlled infrastructure

**CI/CD:**
- **Accelerated Infrastructure Delivery:** Accelerated infrastructure delivery speed by 40%+ by collaborating on CI/CD automation using Terraform, Jenkins, and GitOps, automating over 40% of provisioning tasks
- **GitLab CI** for automation (primary CI/CD tool, integrated with each service)
- **CI/CD Modernization:** Modernized CI/CD infrastructure by migrating from freestyle bash jobs to scripted pipeline jobs in Jenkins, integrated with Slack for real-time job failure alerts, improving monitoring and reducing incident response time
- Automated deployments using Infrastructure as Code
- 40%+ faster deployments through automation
- Scripted pipelines with Slack alerts
- **Trivy scanning** integrated with GitLab CI for security

**Automation Benefits:**
- 40%+ faster infrastructure delivery, automating over 40% of provisioning tasks
- Consistent infrastructure across environments
- Reduced manual errors
- Improved reliability
- **Cost Optimization:** Step scaling implemented for cost savings during night time
- **Elasticsearch Automation:** Engineered agentic AI-based automation for Elasticsearch cluster management using n8n, Terraform, Ansible, and Python, streamlining cluster provisioning and lifecycle management

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
- **Technology:** Reblaze WAF (major tasks done by Reblaze team)
- **Responsibilities:**
  - Filters malicious traffic and DDoS attacks
  - Enforces security policies
  - Applies standard application firewall rules
  - Positioned after Route53, before ALB
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

### 3. Application Load Balancer (ALB)
- **Purpose:** HTTP/HTTPS traffic distribution
- **Technology:** GCP Application Load Balancer
- **Deployment:** **Separate infrastructure component, deployed independently from GKE**
- **Note:** ALB is NOT deployed or managed by GKE - it is a standalone infrastructure component
- **Responsibilities:**
  - Layer 7 load balancing
  - HTTP/HTTPS routing to backend services (GCLB)
  - GCLB is added as backend in ALB

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
- **Integration:** Added as backend in ALB
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
- **Scale:** 125+ Microservices Distributed Workload orchestrated on GKE
- **Responsibilities:**
  - Application service hosting
  - Container orchestration
  - Auto-scaling and self-healing
  - Multiple microservices for e-commerce operations
  - **Step Scaling:** Implemented step scaling for cost savings during night time
  - **CI/CD:** GitLab CI integrated with each service, deployed using Infrastructure as Code (Terraform, Ansible)

### 7. Kubernetes Services
- **Purpose:** Service discovery and load balancing
- **Technology:** Kubernetes Service objects
- **Responsibilities:**
  - Internal service discovery
  - Load balancing within cluster
  - Service abstraction
  - **Container Native Load Balancing:** Configured to enable GCE load balancer to forward traffic directly to pods instead of node ports
- **Service Discovery:** kubedns (Kubernetes DNS) handles DNS resolution and service discovery for inter-service communication within the cluster
- **Application Services:** All application services are deployed as Kubernetes deployments and accessed via Kubernetes Services

### 8. Redis Cache
- **Purpose:** In-memory caching layer
- **Technology:** Redis
- **Responsibilities:**
  - Reduces database load by 60-80%
  - Stores frequently accessed data (product catalog, user sessions, etc.)
  - Improves response times for read-heavy operations
  - Session management

### 9. MySQL Databases
- **Purpose:** Primary databases for e-commerce data, user data, orders, and transactions
- **Technology:** MySQL with master-slave replication
- **Scale:** 4TB primary MySQL database
- **Database Instances:**
  - **MySQL Master - purplle_purplle2:** Primary database for main e-commerce operations
    - Connected to 3 MySQL Slaves for read replication
    - Stores product data, user data, orders, transactions
  - **MySQL Master - warehouseDB:** Primary database for warehouse operations
    - Connected to 1 MySQL Slave - warehouse for read replication
    - Stores warehouse and inventory data
- **Responsibilities:**
  - Stores product data, user data, orders, transactions, warehouse data
  - Point-in-time recovery (PITR) enabled
  - Automated daily backups
  - Multi-zone deployment for high availability
  - Master-slave replication for read scaling
- **Schema Migration:** Zero-lag MySQL schema alterations using [gh-ost](https://github.com/github/gh-ost)
  - **Tool:** GitHub's gh-ost (triggerless online schema migration for MySQL)
  - **Command Pattern:**
    ```bash
    gh-ost --user="<user>" --password="<password>" --host=<host_ip> --database="<db_ip>" --table="<table_to_alter>" --verbose --alter="<alter_query>" --critical-load=Threads_running=1000 --chunk-size=1000 --max-lag-millis=1500 --allow-on-master --switch-to-rbr --exact-rowcount --concurrent-rowcount --default-retries=120 --panic-flag-file=/tmp/ghost_<table_to_alter>.panic.flag --postpone-cut-over-flag-file=/tmp/ghost_<table_to_alter>.postpone.flag --execute --initially-drop-ghost-table --replica-server-id=10000 >> output_ghost_<table_to_alter>.log
    ```
  - **Features:** Zero-lag migrations, pausability, dynamic control, auditing
  - **Master/Slave Flag Management:** Flag management on both VM-based and Cloud SQL instances after migration

### 10. Cloud SQL Proxy
- **Purpose:** Secure database connection proxy
- **Technology:** Cloud SQL Proxy (Layer 7)
- **Responsibilities:**
  - Enables secure connection from different subnet in same VPC
  - Layer 7 (Application Layer) proxy
  - Handles connection pooling and security
  - Provides secure access to Cloud SQL instances

### 11. Cloud Functions
- **Purpose:** Serverless functions for async processing
- **Technology:** GCP Cloud Functions
- **Responsibilities:**
  - Background processing tasks
  - Async operations
  - Event-driven processing
- **Authentication:** Service account credentials configured in Kubernetes services for secure Cloud Functions invocation

## Infrastructure Scale

### Compute Resources
- **300+ Application Instances:** Managed across GCP and AWS infrastructure
- **125+ Microservices Distributed Workload:** Orchestrated on GKE
- **Multi-Environment:** DEV, SIT, UAT, PROD (Production, Pre-Production, Sandbox)
- **Consistent Infrastructure:** Parameterized Terraform modules enable consistent deployment across all environments
- **Multi-Zone Deployment:** High availability across zones

### Business Scale
- **Annual Revenue:** ₹700 Crore annually (as of January 1, 2026)
- **Revenue Generation:** Platform supporting significant annual revenue through e-commerce operations
- **Business Impact:** Infrastructure supporting substantial business operations and growth

### User Scale
- **7 Million Total Users:** Platform serves 7 million total users
- **150,000 DAU (Regular):** Typically serves 150,000 daily active users
- **600,000 DAU (Major Sales):** Scales to 600,000 DAU during major sales events (4x spike)
- **300,000 DAU (Minor Sales):** Scales to 300,000 DAU during minor sales events (2x spike)
- **Traffic Handling:** Successfully handles traffic spikes during sales events
- **Global Reach:** E-commerce platform accessible worldwide

## Cost Optimization

### Cost Reduction Achievements
- **₹1 Crore Cost Savings:** Achieved through infrastructure optimization and automation
- **30% Cloud Cost Reduction:** Through rightsizing GCP/AWS instances, autoscaling policies, and resource cleanup
- **40-50% Cost Savings:** Achieved through cloud infrastructure rightsizing and cleaning up unused resources
- **Efficient Resource Utilization:** Auto-scaling and caching reduce infrastructure costs
- **Step Scaling:** Implemented step scaling for cost savings during night time

### Cost Management
- Infrastructure costs tracked and monitored
- Rightsizing of application instances
- Automated resource cleanup
- Autoscaling policies for cost efficiency
- Step scaling policies for night-time cost optimization

---

**Note:** Infrastructure deployment and management was handled by DevOps team. Application code was developed by the engineering team.
