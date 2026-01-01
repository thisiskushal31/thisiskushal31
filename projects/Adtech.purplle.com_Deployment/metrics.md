# PurplleAds - Metrics & Impact

## Performance Metrics

### System Performance
- **Uptime:** Target 99.9%+ (Production environment)
- **Average Response Time:** [To be measured - target <100ms for ad serving]
- **Peak Throughput:** Supports 7M total users with 150K DAU typically (600K during major sales, 300K during minor sales)
  - Regular days: ~150K DAU typically
  - Major sales events: ~600K DAU (4x spike)
  - Minor sales events: ~300K DAU (2x spike)
  - Overall average: ~233K daily users
- **Error Rate:** Target <0.1% error rate
- **Scalability:** Infrastructure handles 4x traffic spikes during major sales events and 2x during minor sales events

### Infrastructure Metrics
- **Infrastructure Deployment:** Fully deployed and operational across all environments
- **Environment Coverage:** Production (Live), Pre-Production, Sandbox
- **Production Status:** Live and actively serving traffic
- **Resource Utilization:** [Monitored via Prometheus/Grafana]
- **Network Performance:** ALB and GCLB (provisioned by GKE Ingress) handling high-volume traffic
- **Kubernetes Cluster Health:** GKE clusters operational across environments

### Cost Savings Metrics
- **Third-Party Software Replacement:** Replaced ₹80 Lakh/year business management software
- **Annual Cost Savings:** ₹80 Lakh/year
- **Infrastructure Cost:** ₹5.7 Lakh/year (GKE infrastructure)
- **Net Annual Savings:** ₹74.3 Lakh/year (after infrastructure costs)
- **ROI:** Exceptional return on investment - infrastructure cost is only 7.1% of software savings
- **Cost Efficiency:** Infrastructure handles 7M total users and 133M+ clicks at minimal cost

### Infrastructure Cost Metrics
- **Monthly Infrastructure Cost:** ~₹48,000/month (~$570/month)
- **Annual Infrastructure Cost:** ~₹5.7 Lakh/year
- **Cost Per User (Monthly):** ~₹0.0069/user/month (0.69 paise)
- **Cost Per Click:** ~₹0.0043/click (0.43 paise)
- **Infrastructure Efficiency:** High - supports massive scale at minimal cost

## Business Impact Metrics

### User Metrics
- **Total Users:** 7,000,000 total users
- **Daily Active Users (Regular):** 150,000 DAU typically
- **Daily Active Users (Major Sales):** 600,000 DAU during major sales events (4x spike)
- **Daily Active Users (Minor Sales):** 300,000 DAU during minor sales events (2x spike)
- **Platform Scale:** High-volume ad serving infrastructure designed to handle 4x traffic spikes during major sales and 2x during minor sales

### Click Metrics
- **Total Annual Clicks:** ~13.33 Crore clicks/year (133.3 million clicks)
- **Monthly Clicks:** ~1.11 Crore clicks/month (11.1 million clicks)
- **Daily Clicks:** ~3.65 Lakh clicks/day (365,297 clicks/day)
- **Peak Daily Clicks:** Significantly higher during sales events and promotions
- **Transaction Volume:** Database handles millions of click transactions daily at this scale

### Financial Metrics

**Platform Revenue:**
- **Brand Advertising Revenue:** ₹400+ Crore
- **Total Marketing Cost Managed:** ₹180-₹210 Crore annually

**House Brand Performance (FY 2025 Estimates):**
- **Total House Brand Revenue:** ₹680-₹800 Crore
- **Total Marketing Spend:** ₹167-₹198 Crore
- **Average Marketing % of Revenue:** ~24%
- **Revenue Contribution:** 40% of Purplle's total operating revenue

### Key Performance Indicators (KPIs)
- **Total Users:** 7,000,000 total users
- **Daily Active Users (Regular):** 150,000 DAU typically
- **Daily Active Users (Major Sales):** 600,000 DAU during major sales events (4x spike)
- **Daily Active Users (Minor Sales):** 300,000 DAU during minor sales events (2x spike)
- **Daily Brand Revenue:** ~₹1.1 Crore/day (₹400 Cr ÷ 365)
- **Daily Marketing Cost:** ~₹0.49-0.58 Crore/day (₹180-210 Cr ÷ 365)
- **Infrastructure Deployment:** Fully deployed and operational across all environments
- **Traffic Spike Handling:** Successfully handles 4x traffic increase during major sales events and 2x during minor sales events

### Cost Metrics
- **Infrastructure Cost:** ₹5.7 Lakh/year (~₹48,000/month) - GCP/GKE costs tracked and monitored
- **Cost per User (Monthly):** ~₹0.0069/user/month (0.69 paise per user)
- **Cost per User (Annual):** ~₹0.081/user/year (8.1 paise per user)
- **Cost per Click:** ~₹0.0043/click (0.43 paise per click)
- **Cost Optimization:** Infrastructure efficiency through Kubernetes auto-scaling, handling 7M total users and 133M+ clicks at minimal cost
- **Cost Efficiency:** Infrastructure cost is only 7.1% of software savings (₹5.7 Lakh vs ₹80 Lakh saved)

### Detailed Infrastructure Cost Breakdown

**GKE Infrastructure Deployment:**
- **Region:** Mumbai (asia-south1)
- **Configuration Mode:** GKE Standard

**Node Pool Specifications & Costs:**

| Node Pool | VM Type | Config | Pod Capacity (at 1000m-1500m request) | Monthly Cost (Est.) |
|-----------|---------|--------|----------------------------------------|---------------------|
| **Main Workload** | n2-standard-8 | 8 vCPU, 32GB RAM | ~5-6 High-Res Pods* | $340.60 (₹28,600) |
| **Ingress/LB** | n2-standard-4 | 4 vCPU, 16GB RAM | Dedicated Nginx Ingress | $170.30 (₹14,300) |

*Note: While a node pool supports up to 32/110 pods, the physical CPU limit of n2-8 (8000m) restricts pods with 1500m requests to ~5 per VM.

**Fixed & Networking Costs:**
- **Cluster Management Fee:** $73.00 (Standard Tier - 1 Zonal cluster)
- **GKE Free Tier Credit:** -$74.40 (Covers management fee for 1 cluster)
- **Load Balancer (ALB):** ~$25.00/month (Forwarding rules + basic data processing)
- **Persistent Storage (SSD):** ~$35.00 (200GB Balanced PD)

**Total Infrastructure Cost:**
- **Monthly:** ~$570.00 (approx. ₹48,000/month)
- **Annual:** ~₹5.7 Lakh/year

**Cost Breakdown Analysis:**

| Cost Category | Annual Cost | % of Software Savings |
|--------------|-------------|----------------------|
| Infrastructure (GKE) | ₹5.7 Lakh | ~7.1% |
| Software Savings | ₹80 Lakh | 100% (baseline) |
| **Net Savings** | **₹74.3 Lakh** | **~93%** |

### Business Model

**Revenue Streams:**
1. **Brand Advertising Fees:** Brands pay for ad placements
2. **Bidding System:** Revenue from competitive bidding for premium placements
3. **Daily Budget Management:** Revenue from brands managing daily advertising spend

**Cost Structure:**
1. **Infrastructure Costs:** Cloud infrastructure, load balancers, compute resources
2. **Platform Maintenance:** Ongoing development and maintenance
3. **Data Processing:** User preference data processing and targeting

### House Brand Financial Performance (FY 2025 Estimates)

**Total private label revenue is projected to hit ₹450–₹500 Crore, making up roughly 40% of Purplle's total operating revenue.**

| Brand | Estimated Revenue (FY25) | Est. Marketing Cost (FY25) | Marketing as % of Revenue | Strategy |
|-------|------------------------|---------------------------|--------------------------|----------|
| **Faces Canada** | ₹240 - ₹280 Cr | ₹65 - ₹75 Cr | ~27% | Premium / Offline |
| **Alps Goodness** | ₹180 - ₹210 Cr | ₹40 - ₹45 Cr | ~22% | Ingredients-led |
| **Good Vibes** | ₹150 - ₹170 Cr | ₹30 - ₹35 Cr | ~20% | Volume / Mass |
| **NY Bae** | ₹90 - ₹110 Cr | ₹22 - ₹28 Cr | ~25% | Digital / Tier 2-3 |
| **Carmesi** | ₹20 - ₹30 Cr | ₹10 - ₹15 Cr | ~45% | Premium Hygiene |
| **TOTAL** | **₹680 - ₹800 Cr** | **₹167 - ₹198 Cr** | **~24% Avg.** | |

**Key Insights:**
1. **House Brand Revenue Contribution:** ₹680-₹800 Crore represents ~40% of Purplle's total operating revenue
2. **Marketing Efficiency:** Average marketing spend is ~24% of revenue across house brands
3. **Brand Performance Variance:** Marketing % ranges from 20% (Good Vibes) to 45% (Carmesi)
4. **Scale:** Platform manages significant marketing spend (₹167-₹198 Cr) across 5 major house brands

## Operational Metrics

### Deployment Metrics
- **Deployment Frequency:** Regular deployments across Production, Pre-Production, and Sandbox environments
- **Deployment Success Rate:** High success rate with automated CI/CD pipelines (Jenkins, GitLab CI)
- **Infrastructure as Code:** Terraform and Ansible ensure consistent deployments across environments
- **Rollback Capability:** Automated rollback procedures in place for quick recovery if needed

### Incident Metrics
- **Uptime Target:** 99.9%+ (Production environment)
- **MTTR (Mean Time to Recovery):** Rapid recovery enabled through automated monitoring (Prometheus/Grafana) and alerting
- **MTBF (Mean Time Between Failures):** High reliability with multi-zone deployment and disaster recovery capabilities
- **Incident Response:** Comprehensive monitoring and alerting setup with Grafana alerts and GCP Stackdriver logging
- **Disaster Recovery:** Point-in-Time Recovery (PITR) and daily backups ensure quick recovery from incidents

## User/Client Impact

### Platform Adoption
- **Production Status:** Fully live and operational, actively serving 7M total users
- **Platform Usage:** Successfully replacing ₹80 Lakh/year third-party business management software
- **Brand Adoption:** Platform supports 5 major house brands (Faces Canada, Alps Goodness, Good Vibes, NY Bae, Carmesi)
- **Traffic Handling:** Successfully handles regular traffic (150K DAU typically) and sales event spikes (600K DAU during major sales - 4x increase, 300K DAU during minor sales - 2x increase)

### Client Metrics
- **Brand Revenue Support:** ₹400+ Crore in brand advertising revenue
- **Marketing Cost Management:** ₹180-₹210 Crore annually managed through platform
- **House Brand Revenue:** ₹680-₹800 Crore (FY25 projected) supported by platform
- **Cost Savings:** Brands benefit from reduced operational overhead through self-service platform

## Before & After Comparison

### Before Implementation
- **Software Cost:** ₹80 Lakh/year for third-party business management software
- **Dependency:** Dependent on external software vendor
- **Scalability:** Limited by third-party platform constraints
- **Control:** Limited control over infrastructure and customization
- **Cost per User:** Higher operational costs due to software licensing

### After Implementation
- **Software Cost:** ₹0 (in-house solution)
- **Infrastructure Cost:** ₹5.7 Lakh/year (only 7.1% of previous software cost)
- **Net Savings:** ₹74.3 Lakh/year (93% cost reduction)
- **Independence:** Fully independent, self-managed platform
- **Scalability:** Built to handle 7M total users with 4x traffic spikes during major sales and 2x during minor sales
- **Control:** Full control over infrastructure, customization, and feature development
- **Cost per User:** ₹0.0069/user/month (extremely cost-efficient)

### Improvement
- **Cost Reduction:** 93% reduction in software costs (₹80 Lakh → ₹5.7 Lakh infrastructure cost)
- **ROI:** Exceptional ROI - infrastructure cost is only 7.1% of software savings
- **Scalability:** Platform handles 7M total users with 4x traffic spikes during major sales events and 2x during minor sales events
- **Operational Efficiency:** Self-service platform reduces manual campaign management overhead
- **Performance:** 99.9%+ uptime target with sub-100ms latency for ad serving
- **Strategic Value:** Platform supports 40% of Purplle's total operating revenue through house brands

## Team & Collaboration

- **Role:** DevOps Engineer
- **Team Size:** 5 people
- **Collaboration:** Worked closely with product & engineering teams throughout the project lifecycle
  - Collaborated with product team on requirements and feature delivery
  - Worked with engineering team on infrastructure design and implementation
  - Cross-functional collaboration for deployment, monitoring, and operations

## Lessons Learned

### Project Context
- **Team Size:** 5 people
- **Role:** DevOps Engineer
- **Collaboration:** Worked closely with product & engineering teams throughout the project lifecycle

### What Went Well
- **Successful Infrastructure Deployment:** Complete infrastructure stack deployed across Production, Pre-Production, and Sandbox environments
- **Cost Optimization:** Achieved significant cost savings by replacing ₹80 Lakh/year third-party software with in-house solution
- **Scalability:** Built platform capable of handling 4x traffic spikes during major sales events (150K to 600K DAU) and 2x during minor sales (150K to 300K DAU)
- **Cross-Functional Collaboration:** Effective collaboration between DevOps, Product, and Engineering teams
- **Production Readiness:** Successfully deployed live platform serving 7M total users
- **Security Implementation:** Comprehensive security measures including zero-trust, WAF, geo-blocking, and DPDP compliance

### What Could Be Improved
- **Monitoring Enhancements:** Further optimization of monitoring and alerting systems
- **Documentation:** Continuous improvement of operational runbooks and documentation
- **Automation:** Additional automation opportunities for deployment and scaling processes

### Key Takeaways
- **Infrastructure as Code:** IaC (Terraform, Ansible) enabled consistent deployments across environments
- **Kubernetes at Scale:** GKE with auto-scaling effectively handles variable traffic loads
- **Cost Efficiency:** In-house solutions can provide significant cost savings while maintaining functionality
- **Security First:** Zero-trust architecture and comprehensive security measures are critical for production platforms
- **Team Collaboration:** Close collaboration with product and engineering teams is essential for successful platform delivery
- **Compliance:** Understanding and implementing regulatory requirements (DPDP) from the start is crucial

