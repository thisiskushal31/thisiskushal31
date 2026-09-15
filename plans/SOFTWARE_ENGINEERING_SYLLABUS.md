# Software Engineering Syllabus

**Filename:** `SOFTWARE_ENGINEERING_SYLLABUS.md`  
**Canonical path (git-backed backup):** `thisiskushal31/plans/SOFTWARE_ENGINEERING_SYLLABUS.md`  
**Pass this file to the agent** when filling Deep-Dive notes.

**Not published into Deep-Dive repos or DocHub.** Lives in the private `thisiskushal31` repo under `plans/` so it survives a machine loss when that repo is pushed. Do not copy it into a public Deep-Dive root.

Give this file to an agent when filling notes. Add more rulebook sections below as you need them. **When merging Archive sources into public Deep-Dive notes:** Part A **rule 10**.

Public surface of each Deep-Dive: **one root `README.md`** plus topic files under job folders. Planning, write-order, stub status, and goals live **only here**.

---

# Part A — Rules (every session)

You are helping **one person** learn and write **one craft: software engineering**. The notes are split into git repos only so they stay manageable and so [DocHub](https://thisiskushal31.github.io/dochub/) can host them. In your head they are **one syllabus**.

Site config (the same 11 names): `dochub/src/config/repositories.ts`. `dochub/` is the reader site, not a 12th notes repo.

## Rules

1. **One ecosystem, eleven standalone paths.** The repo `README.md` is the public intro (what the room covers + links into folders). Named things live under the *job* folder (`CiCd/`, `Systems/`, `Web-Backend/`, `Utility/`). Do not add a `Tools/` dump or a `From-Zero/` folder. Full *slice* depth still has one home (packets = Networks; Nmap *install* = Tooling `Security/Reconnaissance/Nmap`).
2. **One home for the deep slice.** Do not write two Nmap books. Tooling `Security/Reconnaissance/Nmap` = install and first lab. Networks `Security/8` = what the scan looks like on the wire. Security-Deep-Dive = the *program*.
3. **Kind of work vs named thing.** New engine, framework, strategy, format, or research → new folder under the *existing job* (including legacy: SOAP, COBOL, CVS). Not a 12th repo. **Do not create a `Tools/` folder anywhere.** Named CLIs/libraries/scanners live in **Tooling-and-Frameworks** under a job domain. Engines of a craft stay in that home (`Systems/Kafka`, `Relational/DuckDB`). Git/Make live in `Utility/`. DevOps `Automation/` is config management (Ansible), not n8n. If even that is unclear, ask.
4. **Do not add a 12th DocHub repo** unless the kind of work does not fit the 11.
5. **Do not rewrite** blog, portfolio, Archive unless asked.
6. **Do not commit** unless asked.
7. **Title folders and files; keep real command names.** Job folders and topic files use Title Case (`Local-Dev/`, `1_LRU_Cache.md`). Do not leave all-lowercase kebab dumps unless the name **is** the command (`psql`, `mysql`, `mongosh`, `ping`, `curl`, `kubectl`, `k9s`, `bq`). Product courses (Docker, Kubernetes, GKE) still get Title Case. Keep `complx` as `complx` when that is the chosen spelling.
8. **Do not put planning files back on a Deep-Dive repo root.** Write-order, planned lists, stub status, and goals live **only in this syllabus**. Do not recreate root trackers (`TIMELESS.md`, `THIN_TOPICS.md`, `TOPICS_TO_COVER.md`, `PLAN_*.md`, `CONTENT_WRITE_ORDER.md`, `0_Start_Here.md`, `PLANNED_*.md`, `COVERAGE_MATRIX.md`). Folder-level `README.md` files stay (they introduce that folder’s notes).
9. **Timeless and full-spectrum coverage (guardrail).** Deep-Dive notes must cover the **whole craft surface**, not only the fashionable slice of the moment.
   - **Languages (model):** like `DevOps-Handbook/Languages/Python/` — cover the language thoroughly; when behavior depends on a version, **say so** (e.g. feature from 3.10+, legacy 2.7 still seen in brownfield). Reader should know what works where.
   - **Spectrum:** include **very legacy** (e.g. COBOL/mainframe promote, CVS/SVN, FTP/copy, classic VMs), **mainstream non-cloud-native** (VM fleets, MIGs/ASGs, static sites + CDN), **modern** (containers, GitOps, progressive delivery), and **current assisted/AI-era** delivery (assistants on the same gated loop — policy, small batches, revert). Do not skip COBOL-era or VM-era paths because they are unfashionable; fintech and enterprises still run them.
   - **Durable vs named:** write **durable jobs** (build, artifact, promote, verify, rollback) first; treat vendor/CLI names as examples that can change. Prefer “this mechanism family” over “only this year’s product.”
   - **No year-as-identity framing** in prose (“the 2026 way”). Version/generation gates are fine (“OIDC federation”, “`match` since Python 3.10”).
   - **CiCd pointer:** deployment-target spectrum lives in [CiCd/19](../../Deep-Dives/DevOps-Handbook/CiCd/19_Delivery_Spectrum_Legacy_Through_Modern.md), [17 static/CDN](../../Deep-Dives/DevOps-Handbook/CiCd/17_Static_Sites_And_CDN_Deploy.md), [18 VM/MIG](../../Deep-Dives/DevOps-Handbook/CiCd/18_VM_MIG_And_Host_Based_Deploy.md), classical Jenkins/host/Compose/Swarm ([20](../../Deep-Dives/DevOps-Handbook/CiCd/20_Classical_Jenkins_Host_And_Web_Deploy.md)–[21](../../Deep-Dives/DevOps-Handbook/CiCd/21_Compose_And_Swarm_Delivery.md)), MLOps/AI systems ([22](../../Deep-Dives/DevOps-Handbook/CiCd/22_MLOps_And_AI_System_Delivery.md)), and the [classical stack map](../../Deep-Dives/DevOps-Handbook/CiCd/23_Classical_DevOps_Stack_Map.md). Methodologies posture: [9](../../Deep-Dives/DevOps-Handbook/Methodologies/9_Maintenance_And_Legacy.md) + [20](../../Deep-Dives/DevOps-Handbook/Methodologies/20_Delivery_Reality_Full_Spectrum.md); amplifiers [19](../../Deep-Dives/DevOps-Handbook/Methodologies/19_Durable_Mindsets_And_Evolving_Toolsets.md).
   - **CiCd / Methodologies staircases:** readers climb [Methodologies README](../../Deep-Dives/DevOps-Handbook/Methodologies/README.md) (mindset floors 0–6, including legacy/full spectrum) then [CiCd README](../../Deep-Dives/DevOps-Handbook/CiCd/README.md) (delivery floors 1–6). Arrange and cross-link as a **staircase**, not a fragment dump or calendar of eras. Mindset companion for spectrum: [Methodologies/20](../../Deep-Dives/DevOps-Handbook/Methodologies/20_Delivery_Reality_Full_Spectrum.md).
   - When filling **any** Deep-Dive folder, ask: *Did I leave out legacy, boring-mainstream, classical host/Jenkins/Compose, assisted-modern, or MLOps/distributed AI delivery that a working engineer still hits?* If yes, add a chapter or an explicit related-repo door — do not leave a blind spot.
10. **Filling public Deep-Dive notes from Archive sources (every repo).** There is **not** one handbook source — there are **many** under `Archive/` (e.g. `DevOps-Handbook-Source/`, `Networks-Deep-Dive-Source/`, clones and link dumps inside them, and any future `*-Source` / scrape trees). Agents use those dumps to **write** public notes under `Deep-Dives/<repo>/`. **Readers never open Archive or this syllabus.** Edit this rule when a domain needs a permanent exception.

    **When you copy / merge from a source into the public handbook, do not:**
    - Paste wholesale or leave the public page reading like someone else’s tutorial dump — rewrite in handbook voice; keep depth (do not summarize away meaning), but **own** the prose.
    - Invent facts not supported by the source (or another trusted official reference you are actually using).
    - Put **“source: …”**, “from repo X”, “according to the docs…”, clone paths, scrape paths, `*_LINKS.md`, or any **Archive / `*-Source` path** in public `.md`.
    - Add mid-body “go read this URL” redirects; optional **Further reading / References** only at chapter/README **end**, preferably **official** project/docs hubs (not Medium/TutorialsPoint/random blogs unless that home’s Source README explicitly allows a listed URL style — still never link Archive).
    - Leak meta about how the book was built, scrape reports, or clone maps into the public tree.
    - Publish a public “how we author” / process section — author rules live here (and in Archive Source READMEs for that home), not in DocHub pages.

    **Public page must stand alone:** Deep-Dive is standalone for readers (same idea as Networks and other multi-source Archive homes). Do not add “source: …” or redirects to Archive / clones. Source folders are temporary staging and may be deleted after extraction.

    **Learning shape (each chapter and the track)**
    | Stage | Reader gets |
    |-------|-------------|
    | **1. Basic concepts** | What it is, why it exists, mental model, minimum to reason |
    | **2. Advanced concepts** | Edge cases, internals, gotchas, version/platform nuance, staff depth |
    | **3. Use cases / applications** | Where it shows up; whole-engineering angles (app, systems, security, ops, SE) |
    | **4. Staff checklist** (when enforceable) | Review criteria as plain `-` bullets — **not** `- [ ]` |

    - Do not jump to advanced without basics; do not end on theory alone; do not dump use cases before the concept is clear.
    - Folder READMEs / progression tables should match that arc. **Tool folders:** default is a short primer (what/when → loop → first use → pitfalls → official further reading). When the user asks for **depth** on a named tool (model: Languages tracks; e.g. `CiCd/Argo_CD/` chapters 01–N), write a **standalone multi-chapter track** — the handbook teaches the product; official URLs only at chapter **References**, not as “go read upstream instead.”

    **Craft voice**
    - **Text first**, then code/YAML only when it illustrates a rule — no decorative paste.
    - Whole craft framing (not one-slogan / fashion-only); prefer current narrative with brownfield called out where it still matters (rule 9).
    - Images optional: store under the public repo’s assets path, relative links, **credit** beside the figure; no stock filler.

    **Order of work**
    1. Use the right Archive Source for that home (LINKS / MAPPING / clones).  
    2. Merge into the mapped public file(s).  
    3. Pre-check: standalone voice? basic→advanced→use cases (or primer equivalent)? no Archive leaks? further reading OK?

If two folders start answering the same *what/why*, convert the extra one to a one-line pointer on that repo’s README. Do not add an `Entry-Points/` folder.

## Where the syllabus lives

All 11 clones: `Deep-Dives/`

| # | Repo | This home writes | Top folders |
|---|------|------------------|-------------|
| 1 | [Deep-Dives/DevOps-Handbook](../../Deep-Dives/DevOps-Handbook/) | How software is **delivered** | `Methodologies/` `CiCd/` `IAC/` `Automation/` `Cloud/` `Cloud-Native/` `Servers/` `Observability/` `Security/` `Operating-Systems/` `Languages/` |
| 2 | [Deep-Dives/Containerization-Deep-Dive](../../Deep-Dives/Containerization-Deep-Dive/) | What **containers and clusters** are | `Containerization-Basic/` `Runtimes/` `Orchestration/` `Managed-Services/` `Networking-Advanced/` `Security-Advanced/` `Local-Dev/` `GitOps-Packaging/` `Serverless-Containers/` |
| 3 | [Deep-Dives/Networks-Deep-Dive](../../Deep-Dives/Networks-Deep-Dive/) | How **bits move** | `Foundations/` `Transport/` `Routing-Switching/` `Services/` `Security/` `Cloud-Native/` `Observability/` `Advanced/` `Labs/` `Service-Mesh/` |
| 4 | [Deep-Dives/Databases-Deep-Dive](../../Deep-Dives/Databases-Deep-Dive/) | **Data at rest** | `Concepts/` `Relational/` `Document/` `Key-Value/` `Wide-Column/` `Graph/` `Cache/` `Time-Series/` `Search-Engine/` `Vector/` `Blob-Object/` `NoSQL/` `Cloud-Managed/` `Data-Platform/` |
| 5 | [Deep-Dives/System-Design-Concepts](../../Deep-Dives/System-Design-Concepts/) | How to **design a product system** | `Fundamentals/` `Caching/` `Messaging/` `Databases/` `Storage/` `Availability/` `Consistency/` `Performance/` `Observability/` `Patterns/` `Security/` `Security-Tradeoffs/` `Failure-Modes/` `Primer-Gaps/` `Cases/` |
| 6 | [Deep-Dives/Datastructures-and-Algorithms](../../Deep-Dives/Datastructures-and-Algorithms/) | **Algorithms and structures** | `Foundation/` `DataStructures/` `Algorithms/` `Leetcode/` `GeekforGeeks/` `SystemDesignBridge/` |
| 7 | [Deep-Dives/Commands-and-Cheatsheets](../../Deep-Dives/Commands-and-Cheatsheets/) | Commands you forget | `Languages/` `DevOps-And-Cloud-Essentials/` `Databases/` `Web-Dev-Essentials/` `Machine-Learning/` |
| 8 | [Deep-Dives/Data-Engineering-Deep-Dive](../../Deep-Dives/Data-Engineering-Deep-Dive/) | How a **fact** becomes a trustworthy table | `Foundations/` `Capture/` `Movement/` `Transformation/` `Storage/` `Orchestration/` `Serving/` `Governance/` `Platform-Ops/` `Systems/` `Use-Cases/` `Instances/` |
| 9 | [Deep-Dives/Data-Science-AI-Deep-Dive](../../Deep-Dives/Data-Science-AI-Deep-Dive/) | How a **question** becomes a prediction or an answer | `Foundations/` `Representation/` `Learning/` `Adaptation/` `Retrieval-And-Grounding/` `Control-And-Agency/` `Evaluation/` `Safety-And-Adversaries/` `Inference-And-Serving/` `Applied/` `Instances/` |
| 10 | [Deep-Dives/Tooling-and-Frameworks-Deep-Dive](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/) | **Named software** | `Web-Backend/` `Web-Frontend/` `Utility/` `Network-Utilities/` `Containers/` `Security/` `Diagramming/` `Database-Clients/` `Schema-Migration/` `Data-Quality/` `Automation/` `Data-ML/` `Mobile/` `Desktop/` `Specs-Standards/` `Quality-And-Testing/` `Runtime-And-Edge/` `Developer-Workflow/` `Cloud-Platform/` |
| 11 | [Deep-Dives/Security-Deep-Dive](../../Deep-Dives/Security-Deep-Dive/) | Cybersecurity **program** | `Foundations/` `Threats/` `Identity/` `AppSec/` `Cloud-Security/` `Defensive-Ops/` `Offensive/` `GRC/` `Cryptography/` `Labs/` |

## Same topic, different slice

| Slice | Write it in | Others |
|-------|-------------|--------|
| What Docker / K8s *are* | Containerization | DevOps README related table |
| How a pipeline *ships* a container | DevOps `CiCd/` | Not a Jenkins book in Containerization |
| Kafka the engine | Data Engineering `Systems/Kafka/` | System Design = when a design needs a log |
| Spark | Data Engineering `Systems/Spark/` | Not Tooling, not DS-AI |
| Postgres internals | Databases `Relational/` | System Design = SQL vs NoSQL *selection* |
| TLS on the wire | Networks `Security/` | System Design = design-time trade-off |
| REST vs GraphQL vs gRPC as a *choice* | System Design `Fundamentals/11_API_Styles.md` | Tooling `Specs-Standards/` = the stack when you pick it |
| Learning / retrieval | Data Science & AI | DE = feature *table* only; Tooling `Data-ML/` = library hello-world |
| AppSec as a program | Security-Deep-Dive | Networks = packets; DevOps Security = pipeline gates; scanners → Tooling `Security/` |
| Nmap / Wireshark *install* | Tooling `Security/` | Networks = on the wire; Security-Deep-Dive = program |

## Not in this syllabus

Leave alone unless asked: `blog`, `portfolio-website`, `dochub`, `Archive`, `research`, and other app/work folders. Product / sales / GTM do not get a DocHub repo.

## When you add notes

1. Find the **home** in the table above. Write there.
2. New named CLI/library → Tooling under a *job* domain. New *engine* → that home. **Never a `Tools/` folder.**
3. Tick status in **this file** (the matching repo section below).
4. After push: in `dochub/`, `npm run update-repos`.
5. New *kind of work* that truly does not fit → new repo + a row here and in `dochub/src/config/repositories.ts`.

## Current focus — deadline 30 September 2026

**One person, one syllabus, one calendar.** Everything below overrides the generic “Tooling first / Security prose last” fill advice **until this deadline**. After 30 Sep, revert to the long-term order in Part B.

### Must finish by 30 Sep (deep-tech skills)

“Finish” = notes you would **defend** on the chosen folders below — not every stub in that repo.

**Identity first:** you are a **DevOps engineer first** — strengthen that home before network security. Languages / OS are already written; the delivery spine is still scaffold.

| Priority | Skill you named | Home (write here) | Finish these first |
|----------|-----------------|-------------------|--------------------|
| 1 | **DevOps** | [DevOps-Handbook](../../Deep-Dives/DevOps-Handbook/) | Delivery spine **concepts** (not every tool folder): `Methodologies/0` → `CiCd/1–7` → `Security/1–5` (esp. gate chain) → `IAC/1–3` → `Observability/1–3`. Do not start a new Languages course. Vendor tool READMEs (Jenkins, Prometheus, nginx, …) after concepts. |
| 2 | **Network security** | [Networks-Deep-Dive](../../Deep-Dives/Networks-Deep-Dive/) `Security/` | After DevOps spine: TLS, threat-on-the-wire, common attacks/defenses. Tooling `Security/` = install/lab only when you need a scanner. |
| 3 | **System design** | [System-Design-Concepts](../../Deep-Dives/System-Design-Concepts/) | After DevOps + Networks: `Fundamentals/` (short → defendable) + the cases you will actually interview/design with. `Security-Tradeoffs/` when it touches the design. |
| 4 | **Database** | [Databases-Deep-Dive](../../Deep-Dives/Databases-Deep-Dive/) | `Concepts/` + the engines you operate (e.g. PostgreSQL, Redis). Other engines stay stub until after the deadline. |

Containers stay **support** for DevOps (already largely written). Do not open Containerization gap stubs unless a deadline topic needs one pointer.

### Side lane (AI — do not steal deadline days)

Keep moving, lightly:

| Lane | Home | Allowed under deadline |
|------|------|------------------------|
| AI / learning | [Data-Science-AI-Deep-Dive](../../Deep-Dives/Data-Science-AI-Deep-Dive/) | `Foundations/` + one of `Representation/` or `Retrieval-And-Grounding/` |
| Library hello | Tooling `Data-ML/` | Only when you need a named library (PyTorch, Jupyter, …) |

### Still in the house — after 30 Sep (or when the job appears)

Do **not** abandon these; they stay in this file. Just not the Sept sprint.

| Room | When |
|------|------|
| [Data-Engineering-Deep-Dive](../../Deep-Dives/Data-Engineering-Deep-Dive/) | After deadline, or the week you build a real pipeline |
| Rest of DS-AI | After Foundations / retrieval side-lane |
| [Tooling-and-Frameworks-Deep-Dive](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/) | **Whenever a new tool/framework appears** → add folder under the job domain, fill what/when + hello-world |
| [Security-Deep-Dive](../../Deep-Dives/Security-Deep-Dive/) | Full **program** prose last (AppSec, GRC, SOC). Network *wire* security after DevOps is Networks, not this tree. |
| [System-Design-Concepts](../../Deep-Dives/System-Design-Concepts/) | After DevOps + Networks in the Sept table (priority 3) |
| Containerization remaining stubs | Local-Dev / Serverless / GitOps when you need them |
| DSA / Cheatsheets | Reference; tick when you practice |

### New tool or framework (anytime)

1. Does it fit an existing job domain in Tooling (or an engine home)? → **new folder there**.  
2. Never a `Tools/` dump or a 12th repo unless the *kind of work* is new.  
3. Timeless About on GitHub if it is a new public repo; otherwise just notes.  
4. Tick the matching section in **this file**.

### Session rule for agents (until 30 Sep 2026)

Default write target = **DevOps-Handbook delivery spine** (priority 1). Next = **Networks `Security/`** (priority 2). Do not jump to System Design, Databases, DE, full Security program, or random Tooling unless the user asks — and if they ask without tying it to this order, **ask** whether to spend a Sept day on it or park it post-deadline.

---

# Part B — Reader atlas (was SOFTWARE-ENGINEERING-ATLAS.md)

# Software engineering atlas

**Agents:** start at Part A of this file (one ecosystem, homes, rules). Stub places: Part C. This section is the **reader** map.

**This is the front door.** Software engineering is the whole craft — not one job title. These repos are rooms in one house. You do not need every room at full depth. Some you will go deep; some you only need to know exist.

**How to use**

1. Find yourself in [By role](#by-role) or your question in [By question](#by-question).  
2. Open that repo’s `README.md` (or DevOps `Methodologies/0_SE_Learning_DevOps_Start_Here.md`).  
3. When a topic is only **survey**, read the pointer and stop. When it is **deep**, follow that repo’s `1.md (this file)` or write order.  
4. When you learn named software with no job in that home, **add a folder** under a Tooling domain (`Security/`, `Diagramming/`, `Automation/`, …). Do not invent a `Tools/` dump or a 12th repo.

Living content plan (phases, gaps, checklists): [ENGINEERING-KNOWLEDGE-ECOSYSTEM-REPORT.md](./1.md#part-d--ecosystem-report)  
Public reader: [DocHub](https://thisiskushal31.github.io/dochub/)

**Depth keys:** **Deep** = notes you would defend. **Survey** = enough to talk and know where to go next.

---

## The 11 rooms

| If you want to understand… | Open | Depth today |
|----------------------------|------|-------------|
| How software is **delivered** (CI/CD, IaC, OS, cloud, languages as tools) | [DevOps-Handbook](../../Deep-Dives/DevOps-Handbook/README.md) | Deep (spine) |
| How **containers and clusters** work | [Containerization-Deep-Dive](../../Deep-Dives/Containerization-Deep-Dive/README.md) | Deep core |
| How **bits move** (L1–L7, DNS, TLS) | [Networks-Deep-Dive](../../Deep-Dives/Networks-Deep-Dive/README.md) | Deep |
| How **data at rest** is stored (SQL, docs, queues, vectors…) | [Databases-Deep-Dive](../../Deep-Dives/Databases-Deep-Dive/README.md) | Deep some engines, survey others |
| How to **design a product system** (HLD/LLD, scale, failure) | [System-Design-Concepts](../../Deep-Dives/System-Design-Concepts/README.md) | Breadth; many files thin |
| **Algorithms and structures** | [Datastructures-and-Algorithms](../../Deep-Dives/Datastructures-and-Algorithms/README.md) | Deep notes + problems |
| Commands you forget | [Commands-and-Cheatsheets](../../Deep-Dives/Commands-and-Cheatsheets/README.md) | Survey / reference |
| How a **fact** becomes a trustworthy table | [Data-Engineering-Deep-Dive](../../Deep-Dives/Data-Engineering-Deep-Dive/README.md) | Scaffold (layers + systems) |
| How a **question** becomes a prediction or an answer | [Data-Science-AI-Deep-Dive](../../Deep-Dives/Data-Science-AI-Deep-Dive/README.md) | Scaffold (layers) |
| **Application frameworks + named software** with no other home | [Tooling-and-Frameworks-Deep-Dive](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/README.md) | Scaffold (backend/frontend door + Security/Diagramming/…) |
| **Cybersecurity as a program** | [Security-Deep-Dive](../../Deep-Dives/Security-Deep-Dive/README.md) | From-zero + tools + program (stubs) — prose last |

DevOps Handbook already points here: [Where to go deeper](../../Deep-Dives/DevOps-Handbook/README.md#where-to-go-deeper).

---

## By role

| I am / I want to be | Start | Then | Leave for later |
|---------------------|--------|------|-----------------|
| **Backend engineer** who wants DevOps | [DevOps Methodologies start](../../Deep-Dives/DevOps-Handbook/Methodologies/0_SE_Learning_DevOps_Start_Here.md) | CiCd, IAC, a bit of Observability | Full K8s internals (Containerization) only if you operate clusters |
| **Backend engineer** who wants to write services | [Tooling → Web-Backend](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/Web-Backend/README.md) | [System Design fundamentals](../../Deep-Dives/System-Design-Concepts/Fundamentals/README.md) + [Databases](../../Deep-Dives/Databases-Deep-Dive/README.md) | DE/DS-AI until you own data/ML |
| **Frontend engineer** | [Tooling → Web-Frontend](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/Web-Frontend/README.md) | DevOps CiCd (how the app ships) | Kernel, Spark |
| **Platform / DevOps / SRE** | DevOps Handbook (home) | Containerization, Networks, Observability | App framework internals: survey in Tooling |
| **Architect** | [System Design](../../Deep-Dives/System-Design-Concepts/README.md) | Databases (selection) + Networks (when the wire matters) | One engine deep only as needed |
| **Data engineer** | [Data Engineering](../../Deep-Dives/Data-Engineering-Deep-Dive/README.md) | [Systems/Spark or Kafka](../../Deep-Dives/Data-Engineering-Deep-Dive/Systems/README.md) after the *job* (transform / movement) | Training models → DS-AI |
| **ML / AI engineer** | [Data Science & AI](../../Deep-Dives/Data-Science-AI-Deep-Dive/README.md) | Retrieval + eval; DE if you need a feature table | Pretraining from scratch (survey unless that becomes a goal) |
| **Security-curious** | Networks `Security/` + DevOps `Security/` (survey) | System Design `Security-Tradeoffs/` | [Security-Deep-Dive](../../Deep-Dives/Security-Deep-Dive/README.md) when the other rooms have substance |
| **Interview / DSA** | [DSA](../../Deep-Dives/Datastructures-and-Algorithms/README.md) | System Design cases | Not a substitute for building |
| **“I just want to know it exists”** | This atlas + the repo README | Stop | Adding a stub folder when you touch it is enough |

---

## By question

| Question | Repo | Notes |
|----------|------|--------|
| How does a **DevOps / CI/CD flow** work? | DevOps-Handbook `CiCd/`, `Methodologies/` | Spine for delivery |
| How do I **design** a feed, chat, or payments system? | System-Design-Concepts | Architecture, not a framework tutorial |
| How does **TCP / DNS / TLS** actually work? | Networks-Deep-Dive | Wire depth |
| What is **Docker / Kubernetes**? | Containerization-Deep-Dive | DevOps only needs enough to ship |
| Why **Postgres vs Redis vs a vector store**? | Databases-Deep-Dive (10 types) | Engine folders = deep; type README = survey |
| How does **Spark / Kafka** fit? | DE: learn **Transformation / Movement** first, then `Systems/Spark` or `Systems/Kafka` | Named engines are not layers |
| How do I write **Spring / FastAPI / React**? | Tooling (this repo’s application door) | Language syntax → DevOps `Languages/` |
| How does **hardware / OS / process** work? | DevOps `Operating-Systems/Fundamentals/` then Linux | No separate hardware repo yet — survey here, add a room later if you go deep |
| **HLD vs LLD**? | System Design `Fundamentals/12_HLD_and_LLD.md` | Low-level *design*, not CPU microarch |
| How do **facts** get into a warehouse? | Data-Engineering-Deep-Dive | Path of a fact |
| How does **retrieval / an LLM app** work? | Data-Science-AI-Deep-Dive | Path of a question; one room among many |
| I forgot a **command** | Commands-and-Cheatsheets | Reference, not a course |

---

## Two axes (so the house does not rot)

Same idea in every catalog repo:

| Axis | Meaning | Example |
|------|---------|---------|
| **Job / layer** | Survives tools | Movement, Transformation, Representation, Web-Backend |
| **Named thing** | One folder, like DevOps `Languages/Python` | `Systems/Kafka`, `Web-Backend/FastAPI`, `Languages/Go` |

When a new framework appears: add a folder under the job. Do not add an 12th “Spark-era” repo.

---

## One ecosystem, one home

The 11 DocHub repos are **one syllabus**, split so git and DocHub stay manageable. They are not competing courses.

**Rule:** A topic is written in **one** place. Every other repo that needs it uses a one-line pointer on its `README.md` (directory / related-repos table). Do not add an `Entry-Points/` folder.

| Slice of the same topic | Who *writes* it | Who only *points* |
|-------------------------|-----------------|-------------------|
| What Docker/K8s *are* | Containerization-Deep-Dive | DevOps README (Containers row) |
| How a pipeline *ships* a container | DevOps `CiCd/` | Containerization (ops of the cluster, not Jenkins) |
| REST vs GraphQL vs gRPC as a *design choice* | System Design `Fundamentals/11_API_Styles.md` | Tooling Specs folders = how that stack looks when you pick it |
| Kafka as a log / engine | Data-Engineering `Systems/Kafka/` | System Design `Messaging/` = when a design needs a log |
| Postgres internals | Databases `Relational/PostgreSQL/` | System Design `Databases/` = SQL vs NoSQL *selection* |
| TLS on the wire | Networks `Security/` | System Design `Security/6_SSL_and_TLS.md` |
| Spark jobs | Data-Engineering `Systems/Spark/` | Not Tooling, not DS-AI |
| Learning / retrieval *jobs* | Data-Science-AI-Deep-Dive | DE only for the feature *table*; Tooling `Data-ML/` only for a library hello-world |
| AppSec as a *program* | Security-Deep-Dive (last) | Networks = packets; DevOps Security = pipeline gates; SD = design-time trade-offs |

If two folders start explaining the same “what/why,” one of them is wrong. Convert the extra one to a pointer.

---

## What “do not fake a room” meant

It did **not** mean “never learn compilers, IoT, or games.” It meant: **do not add a 12th DocHub repo** (a fake extra house) for a topic that already has a home, or for a topic you only need as a short note inside an existing home.

Examples:

| Temptation | Why it would be a fake extra repo | What to do instead |
|------------|-----------------------------------|-------------------|
| “Compiler-Deep-Dive” because compilers exist in the industry | Language *syntax* already lives in DevOps `Languages/`. A compiler course is a new *job* only if you actually take it. | One survey file under OS fundamentals or Languages, **pointing** at official texts. New DocHub id only if that job becomes real. |
| “IoT-Deep-Dive” | IoT is Networks + constrained devices + maybe containers. Not a new ecosystem member. | Pointers from Networks / Containerization. Tooling domain later if you *build* firmware UIs. |
| “Games-Deep-Dive” | Same: it is application code + rendering. | `Tooling/` domain if you build games. Until then, no folder required. |
| “Vue-Deep-Dive” as its own GitHub repo | Vue is a named frontend tool. Web-Frontend already owns that job. | `Tooling/Web-Frontend/Vue/` when you learn Vue. |
| Copying Kafka into System Design *and* DE *and* DevOps as full writeups | Three homes for one engine. | DE writes the engine. SD writes “when a design uses a log.” DevOps writes “how we run it in CI/prod” as an entry, not a second Kafka book. |

**Fake room** = a new DocHub repository (or a duplicate chapter) that pretends to be a separate world. **Real coverage** = one owner in the 11, and references everywhere else.

Product / GTM / sales are not software-engineering notes. They stay out of DocHub (ecosystem report §2). That is not a fake room; it is a different craft.

---

## Adding as you learn

1. Tick a box in that repo’s `1.md (this file)` (or create the file if missing).  
2. If it is a **new named tool** in a job you already have: new folder under `Systems/` or Tooling domain.  
3. If it is a **new job** (e.g. you actually study compilers): new repo + a row in this atlas and in DocHub `repositories.ts`.  
4. Push → `dochub` `npm run update-repos` → readers see it.

---

## Suggested order to *fill notes* (not a career ladder)

**Until 30 September 2026:** follow [Current focus — deadline 30 September 2026](#current-focus--deadline-30-september-2026) in Part A (**DevOps delivery spine → Networks Security → system design → database**; AI side-lane; DE / full Security program / new Tooling after or when needed).

**After that deadline** (long-term house order):

You already have deep rooms: DevOps, Containers, Networks, Databases, System Design, DSA. Empty rooms to grow:

1. **Tooling** — so backend/frontend have a door (application code); also every new named framework as it appears.  
2. **DE + DS-AI** — already scaffolded; fill when you work those jobs.  
3. **Security-Deep-Dive** — last, on top of the rest (program prose; wire security already in Networks).

Survey is allowed. Deep is for rooms you will operate or teach.

---

## Landscape check (2026) — are any *jobs* missing?

Named tools will always be incomplete (add a folder when you touch them). The test is: **does every job have a door?**

### Has a door (do not add a 12th repo)

| Job | Door | Honest status |
|-----|------|----------------|
| Deliver / CI/CD / IaC / OS / SRE | DevOps-Handbook | Deep; artifacts, flags, supply chain still listed in Part E DevOps completeness plan |
| Containers / K8s | Containerization | Deep core; containerd, GitOps, Serverless-Containers TBD |
| Networks | Networks-Deep-Dive | Deep; mesh/labs thin |
| Data at rest (10 types) | Databases | Types mapped; most engines stubs |
| Product architecture | System Design | Skeleton complete; primers/cases many TBD |
| Algorithms | DSA | Solid |
| Application code (backend/frontend) | Tooling Web-* | Scaffold + first frameworks |
| Specs (REST, GraphQL, gRPC, OAuth, OTel) | Tooling Specs + SD `11-api-styles` | Survey stubs |
| Testing as a discipline | Tooling `Quality-And-Testing/` | Survey door (was missing) |
| Edge / WASM / functions | Tooling `Runtime-And-Edge/` + Containerization serverless | Survey |
| How engineers work in 2026 (inner loop, AI pair) | Tooling `Developer-Workflow/` | Survey |
| Desktop | Tooling `Desktop/` | Survey |
| Mobile | Tooling `Mobile/` | Survey |
| Accessibility / i18n | Tooling `Web-Frontend/5_Accessibility_And_I18n.md` | Survey |
| Path of a fact | Data Engineering | Scaffold |
| Path of a question / ML / LLM apps | Data Science & AI | Scaffold |
| Identity / AppSec / SOC | Pieces in Networks, DevOps Security, SD; **program** in Security-Deep-Dive | Capstone empty — last on purpose |
| Search, payments, video, notifications | System Design cases + Databases search | On the map; stubs |
| Realtime / WebSockets | SD `Fundamentals/14` + Slack case | Thin |
| Privacy / PII | DE `Governance/` | Scaffold |
| Cost / FinOps | DE Governance + SD cost-vs-performance | Thin, has a home |
| Feature flags | DevOps plan | Planned, not written |
| Web3 | DevOps `Languages/` Solidity family | Niche, has a home |

### Not a 12th DocHub repo (cover in an existing home, or a short pointer)

These are real topics. They do **not** get their own ecosystem member. Write them once where they belong; link from the rest.

| Topic | Single home (when you write it) |
|-------|----------------------------------|
| CPU / OS / process model | DevOps `Operating-Systems/Fundamentals/` (already) |
| Compilers as a field | Short survey under Languages or OS — **or** a new DocHub repo only if that becomes a real track |
| Embedded / IoT | Networks + Containerization; Tooling only if you ship device software |
| Games / graphics | Tooling domain if you build; otherwise skip |
| Quantum, AR/VR platforms | One pointer file in System Design or Tooling if you ever need literacy |
| Vue, Django, Flutter, Playwright, … | Folder under the **existing** Tooling domain (Web-Frontend, Web-Backend, Quality-And-Testing, Mobile) |
| Product / sales / GTM | Outside DocHub |

### Thin on purpose (mapped, not filled)

You are not missing the topic. You are missing **prose**. Highest-leverage fills for landscape literacy:

1. One real backend + one real frontend framework note in Tooling.  
2. System Design `Primer-Gaps/` + thin observability.  
3. DevOps plan: artifact registries, supply chain, feature flags.  
4. Databases `Vector/Pgvector` if retrieval matters to you.  
5. Security-Deep-Dive last.

You will never list every SKU. If a new *job* appears, add a domain or a repo and a row in this file.

---

# Part C — Stub index (was STUB-INDEX.md)

# Stub index — places, not prose

**Give this whole file to the agent.** One syllabus, eleven homes under `Deep-Dives/`. A stub is a **place** so you can fill later. Each home is also a **standalone path** (know-nothing → advanced). Full *slice* depth still has one home.

Counts below are file-level (September 2026). A file with `*(Content TBD)*` or “stub created” is a stub. Security used to have no tree — it now has stub folders; **prose still last**.

---

## How to use

1. Find the home.  
2. Open that home’s Part E section. Tick when a file has no TBD.  
3. New named CLI/library → Tooling under a *job* domain. New *engine* → that home (`Systems/`, `Relational/`). **Never a `Tools/` folder.**  
4. New *kind of work* that does not fit → ask before adding a 12th repo.

---

## The 11 homes

| Home | Plan | Places (honest) | Stub-ish files |
|------|------|-----------------|----------------|
| [DevOps-Handbook](../../Deep-Dives/DevOps-Handbook/) | Part E | Languages + OS written. Delivery spine (CiCd, IAC, Security, Observability, Methodologies) is scaffold. | ~98 |
| [Containerization-Deep-Dive](../../Deep-Dives/Containerization-Deep-Dive/) | Part E | Docker, Podman, K8s, OpenShift, Swarm, GKE/EKS/AKS written. Later sections stub. | ~29 |
| [Networks-Deep-Dive](../../Deep-Dives/Networks-Deep-Dive/) | Part E | Core layers written. Mesh / extra labs stub. | ~17 |
| [Databases-Deep-Dive](../../Deep-Dives/Databases-Deep-Dive/) | Part E | Six engines written. Other engines stub. **Qdrant added.** | ~113 (was 108) |
| [System-Design-Concepts](../../Deep-Dives/System-Design-Concepts/) | Part E | Fundamentals exist (many thin). primer-gaps and later cases stub. | ~38 |
| [Datastructures-and-Algorithms](../../Deep-Dives/Datastructures-and-Algorithms/) | Part E | Theory + Leetcode written. SystemDesignBridge stub. | ~9 |
| [Commands-and-Cheatsheets](../../Deep-Dives/Commands-and-Cheatsheets/) | Part E | Reference. Do not turn into a course. | 0 |
| [Data-Engineering-Deep-Dive](../../Deep-Dives/Data-Engineering-Deep-Dive/) | Part E | Map complete (layers + Systems + Use-Cases). Almost all stub. | ~140 |
| [Data-Science-AI-Deep-Dive](../../Deep-Dives/Data-Science-AI-Deep-Dive/) | Part E | Layers named. Topic files stub. | ~42 |
| [Tooling-and-Frameworks-Deep-Dive](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/) | Part E | Application door. **Express added.** FastAPI/Spring/React still stub. | ~47 (was 42) |
| [Security-Deep-Dive](../../Deep-Dives/Security-Deep-Dive/) | Part E | Program tree. Named software → Tooling `Security/`. Prose last. | whole tree |

DevOps named delivery products live under CiCd/IAC/Observability. Named CLIs/libraries → Tooling job domains. **No `Tools/` folder in any home.** README is the intro — no `From-Zero/` folder.

Site: `dochub/` — not a 12th notes repo.

---

## Added this session (places only)

| Place | Home | Why here |
|-------|------|----------|
| [Vector/Qdrant/](../../Deep-Dives/Databases-Deep-Dive/Vector/Qdrant/README.md) | Databases | Production vector **engine**. Retrieval job → DS-AI. |
| [Relational/DuckDB/](../../Deep-Dives/Databases-Deep-Dive/Relational/DuckDB/README.md) | Databases | In-process OLAP SQL. DE `Systems/DuckDB` is a GitHub pointer only. |
| [Web-Backend/Express/](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/Web-Backend/Express/README.md) | Tooling | Node HTTP **framework**. Syntax → DevOps `Languages/JavaScript`. |
| [Foundations/ … Labs/](../../Deep-Dives/Security-Deep-Dive/README.md) | Security | Program tree |
| [Security/](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/Security/README.md) | Tooling | Lab software (Nmap, Burp, Wireshark, …) — program stays in Security-Deep-Dive |
| [Threats/](../../Deep-Dives/Security-Deep-Dive/Threats/README.md) | Security | Security+ domain 2 |
| [Specs-Standards/SOAP](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/Specs-Standards/SOAP/README.md) | Tooling | Legacy XML services |
| [Specs-Standards/MCP](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/Specs-Standards/MCP/README.md) | Tooling | Agent tool protocol (2024–) |
| [Control-And-Agency/4_MCP…](../../Deep-Dives/Data-Science-AI-Deep-Dive/Control-And-Agency/4_MCP_And_Tool_Protocols.md) | DS-AI | MCP as a *job*, not the spec |
| [Fundamentals/0-requirements…](../../Deep-Dives/System-Design-Concepts/Fundamentals/0_Requirements_and_Constraints.md) | System Design | SWEBOK requirements door |
| [Methodologies/9_Maintenance…](../../Deep-Dives/DevOps-Handbook/Methodologies/9_Maintenance_And_Legacy.md) | DevOps | SWEBOK maintenance / CVS / mainframes |
| [README.md](../../Deep-Dives/DevOps-Handbook/README.md) | DevOps | Beginner door at repo root |
| [README.md](../../Deep-Dives/Commands-and-Cheatsheets/README.md) | Cheatsheets | How to use a reference |

---

## Still no place (ask before creating)

Do not invent these unless you say so:

| Topic | Likely home if you want a place |
|-------|----------------------------------|
| Feature-flag *tools* (OpenFeature, LaunchDarkly) | DevOps `CiCd/` (Unleash folder exists) |
| Harbor / Artifactory as a *folder* | DevOps `CiCd/` (concept file already: `4_Artifacts_And_Registries.md`) |
| Vertex AI SKU | Tooling `Data-ML/` — job stays in DS-AI |
| Flutter | Tooling `Mobile/` when you build |

---

## One-home reminders

| Write here | Not here |
|------------|----------|
| Qdrant engine → Databases `Vector/Qdrant/` | DS-AI, Tooling Data-ML |
| Express → Tooling Web-Backend | DevOps Languages (syntax only) |
| Kafka / Spark → DE `Systems/` | Tooling, DS-AI |
| TLS → Networks Security | Security Cryptography (pitfalls + pointer) |
| OAuth stack → Tooling Specs | Security Identity (program + pointer) |
| AppSec program → Security AppSec | DevOps Security (gates only) |
| Nmap *install + first lab scan* → Tooling `Security/Reconnaissance/Nmap` | Networks `Security/8` = on the wire; Security-Deep-Dive = program |
| Wireshark *install + first capture* → Tooling `Security/Defensive/Wireshark` | Networks `Observability/3` = filters / protocols |

---

## Coverage check (web, September 2026)

Checked against IEEE **SWEBOK v4** (18 knowledge areas), CompTIA **Security+ SY0-701**, common Nmap/Wireshark beginner labs, and 2026 DE/AI writing (Iceberg, MCP, agents).

| Source topic | Already had a home? | What we did |
|--------------|---------------------|-------------|
| Requirements, architecture, design | System Design | Added `Fundamentals/0_Requirements_and_Constraints.md` |
| Construction / frameworks | Tooling | Already |
| Testing | Tooling `Quality-And-Testing/` | Survey door exists |
| Operations, SCM, process, quality, economics (FinOps) | DevOps | Added maintenance/legacy; FinOps stub already |
| Computing / OS / languages (incl. COBOL, Fortran, Perl, PHP) | DevOps OS + Languages (47 languages) | Already — legacy is strong |
| Math | DSA + DS-AI Foundations | Already |
| Software security as a *program* | Security | Program tree; named software → Tooling `Security/` |
| Nmap / Wireshark from zero | Networks had *depth* | Install lives in Tooling `Security/`; Networks stays the wire book |
| Iceberg / Delta / Hudi / Kafka / Spark | DE `Systems/` | Already stubbed |
| MCP / agents | DS-AI Control; Tooling Developer-Workflow | Added Specs/MCP + Control topic 4 |
| SOAP / WSDL (1990s–) | Missing | Tooling Specs/SOAP |
| New tool / paper / format next year | — | Add a folder under the existing home |

You will never list every SKU. A new thing gets a folder when you touch it — or when we agree it is a hole, like Qdrant and MCP.

---

# Part D — Ecosystem report (was ENGINEERING-KNOWLEDGE-ECOSYSTEM-REPORT.md)

# Engineering Knowledge Ecosystem — Map & Content Plan

**Last updated:** September 11, 2026 (reader atlas added)  
**Scope:** DocHub, 11 linked GitHub repositories, local clones under `Personal_Project`, blog/portfolio overlap  
**Purpose:** Living map of what exists, what you will cover, and in what order — culminating in **cybersecurity** after broad engineering depth

**Front door for any reader (backend, DevOps, architect, survey):** [SOFTWARE-ENGINEERING-ATLAS.md](./1.md#part-b--reader-atlas-was-software-engineering-atlasmd) — software engineering as the whole craft; each repo is a room; depth vs survey is allowed. This report stays the *content plan* (phases, gaps, checklists).


---

## 1. Your learning philosophy

You are building a **personal engineering knowledge base** — not a single course, but a set of deep-dive repos you return to month by month, tick off as you go, and share publicly via DocHub and blog.

**Core belief (your plan):** Cybersecurity is a **capstone domain**. Strong practitioners usually stand on:

1. **Systems & platforms** — OS, languages, containers, cloud, CI/CD  
2. **Data & logic** — DSA, databases, data pipelines, ML/AI  
3. **Networks & design** — how bits move, how systems scale  
4. **Tooling literacy** — frameworks, SDKs, platforms across the stack  
5. **Security synthesis** — AppSec, IAM, cloud posture, forensics, offensive/defensive ops  

You can read security *along the way* (OWASP, threat modeling, DevOps `Security/`), but **Security-Deep-Dive** is the last major repo to fill — after the foundation repos have substance.

**Progress tracking today:** GFM task lists (`- [ ]` / `- [x]`) in markdown; commit checked boxes to git for public progress. DocHub renders tasks read-only (no browser persistence yet).

---

## 2. Expertise profile, gaps & entrepreneur north star

Edit the block below as you grow. **Levels:** `none` → `exposure` → `working` → `strong` → `expert` → `target` (where you want to end up).

**North star:** Cybersecurity tech entrepreneur *(or general tech entrepreneur)* — technical depth + ability to **ship**, **sell**, and **lead**.

```yaml
# ═══════════════════════════════════════════════════════════════════
# EXPERTISE_PROFILE — Kushal Gupta (edit this block over time)
# Last reviewed: 2026-08
# ═══════════════════════════════════════════════════════════════════

north_star:
  primary: "Cybersecurity tech entrepreneur"
  alternate: "General tech entrepreneur"
  means: "Deep technical credibility + product/business execution — not IC forever"

# What you want EXPERT-LEVEL depth in (your stated deep dives)
depth_targets:
  - devops                    # home base — already closest to expert
  - security                  # capstone — build last, on top of everything
  - application_code          # full stack — read/write production apps confidently
  - architecture              # system design — trade-offs, scale, failure modes

# What you are actively building toward (broader than depth targets)
building_toward:
  - full_stack_engineering    # frontend + backend + APIs + data layer
  - solution_architecture     # end-to-end designs, not just infra boxes

# ─── WHAT I CAN DO TODAY (concrete — add/remove bullets) ───────────
can_do_today:
  devops_platform:
    - "Design & run CI/CD (GitHub Actions, Jenkins-style patterns, GitOps)"
    - "Kubernetes & container ops (deploy, debug, networking basics, Helm)"
    - "IaC — Terraform / HCL, infra modules, environment promotion"
    - "Cloud-native on GCP (GKE, Cloud Run, IAM, networking, cost awareness)"
    - "Observability — metrics/logs/traces, Prometheus/Grafana-style stacks"
    - "Linux ops, shell automation, Nginx/apache reverse proxy patterns"
    - "Secrets, pipeline hygiene, shift-left security in delivery (intro level)"
  data_platform:               # from Purplle delivery — platform more than science
    - "Data engineering infra — pipelines, orchestration, warehouse touchpoints"
    - "ML/DS platform infra — GPU/scheduling, RAG platform ops (not model research)"
    - "Unified monitoring & IaC at org scale (Purplle-scale narratives)"
  security:                    # early — not cyber specialist yet
    - "DevSecOps in pipeline, compliance-aligned controls (project narrative)"
    - "Blog series on AI + shift-left security (conceptual + practical ops angle)"
  application_code:            # gap vs full stack goal
    - "Automation scripts, config, infra glue (Python/Shell/HCL)"
    - "Read & patch application configs; not primary product feature owner yet"
  architecture:
    - "Infra & platform architecture for distributed systems"
    - "System design study in progress (repo + cases — not interview-only)"
  business_entrepreneur:       # thinnest layer today
    - "Technical storytelling — blog, portfolio, public repos (DocHub)"
    - "Stakeholder-facing infra delivery in enterprise/e-commerce context"

# ─── CURRENT LEVELS (honest snapshot) ──────────────────────────────
levels:
  # Core depth targets
  devops:                 strong        # current professional identity
  security:               exposure      # ops-aware; not pentest/GRC/AppSec depth yet
  application_code:       working       # scripts/glue strong; product full stack weak
  architecture:           working       # infra arch strong; product/system arch growing

  # Supporting engineering (feeds cyber + entrepreneur path)
  containers_orchestration: strong
  cloud_gcp:                strong
  networking:               working     # Networks-Deep-Dive in progress
  databases:                working     # ops + modeling; not DBA expert
  data_engineering:         working     # platform delivery > pipeline authoring depth
  data_science_ai:          exposure    # infra + RAG ops > ML math/research
  dsa:                      working
  system_design:            working
  tooling_frameworks:       exposure    # repo shell; catalog not built
  languages_product:        exposure    # Python/Go/Shell for ops > app frameworks

  # Business & entrepreneur stack
  product_management:       exposure    # technical PM instincts; no formal PM craft
  go_to_market_sales:       none        # pricing, discovery, closing — not started
  marketing_brand:          working     # blog, portfolio, public learning brand
  finance_unit_economics:   exposure    # cloud cost yes; P&L, fundraising no
  legal_compliance_biz:     exposure    # eng-side compliance; not contracts/entity ops
  people_leadership:        working     # team delivery; not hiring org design at scale
  fundraising_investors:    none
  customer_discovery:       exposure

# ─── GAPS (what you're lacking vs north star) ─────────────────────
# DevOps → strong ✓  |  Security expert ✗  |  Full-stack app ✗  |  Product arch ✗  |  Biz ✗

gaps:
  technical_critical:        # blocks "cybersecurity entrepreneur" credibility
    - "Application security depth — OWASP, secure SDLC, code review as practitioner"
    - "Offensive/defensive ops — labs, IR, forensics, SIEM (Security-Deep-Dive empty)"
    - "Production full stack — ship a real web/mobile product you wrote end-to-end"
    - "Product architecture — APIs, domain modeling, frontend state, not just infra diagrams"
    - "Cryptography & identity beyond TLS/nginx — OIDC/SAML threat models, key management"
    - "Network security synthesis — Networks repo helps; Security repo not started"

  technical_important:       # general tech entrepreneur / full-stack architect
    - "Framework fluency catalog — Tooling repo empty; pick 5 stacks and go deep"
    - "DSA → system design bridge — tagged problems + written trade-off docs"
    - "ML/AI beyond infra — evaluation, modeling choices (DS-AI repo shell)"
    - "DE beyond platform — authoring pipelines, data contracts, quality/lineage"

  business_entrepreneur_critical:
    - "Customer discovery — talk to buyers, not just build in public"
    - "Problem/solution fit — narrow wedge (e.g. DevSecOps consulting vs broad 'cyber')"
    - "Pricing & packaging — hourly vs product vs retainer; what you sell first"
    - "Basic finance — runway, revenue model, when to quit IC for venture"

  business_entrepreneur_important:
    - "Sales pipeline — outbound, demos, proposals (even for freelance/consulting)"
    - "Legal basics — contracts, liability, company structure, IP"
    - "Hiring/delegation — when north star needs a team, not solo repos"
    - "Pitch narrative — 5-min story linking Purplle outcomes → cyber/security offer"

# ─── SUGGESTED FOCUS ORDER (aligns with Section 6 phases) ─────────
next_12_months:
  - "DevOps first — fill handbook delivery spine (CiCd / Security gates / IAC / Observability); strong → expert"
  - "Then Networks Security/ — wire security you can defend"
  - "Application code: one shipped full-stack project (backend + frontend + auth + deploy)"
  - "Architecture: 2 written system designs with failure modes + security angle"
  - "Security program (Security-Deep-Dive): Phase 4 last; Phase 1 parallel only if needed"
  - "Entrepreneur: pick ONE wedge + 10 customer conversations before more repos"

# ─── REPO MAP (where gaps get closed) ─────────────────────────────
gap_to_repo:
  devops_expert:              DevOps-Handbook, Containerization-Deep-Dive
  application_code_fullstack: Tooling-and-Frameworks-Deep-Dive + ship a side project
  architecture:               System-Design-Concepts
  security_expert:              Security-Deep-Dive (last), Networks-Deep-Dive/Security
  data_depth:                   Data-Engineering-Deep-Dive, Data-Science-AI-Deep-Dive
  entrepreneur:                 outside repos — customers, offers, finance (no markdown repo)
```

**How to use this block**

1. Update `can_do_today` when you finish a project or role milestone.  
2. Bump `levels` when you'd trust yourself to lead that work for 6 months.  
3. Re-read `gaps` quarterly — if a gap has a repo, link a checklist there.  
4. `business_entrepreneur_*` gaps **won't close from DocHub alone** — schedule real market contact.

---

## 3. How DocHub links repositories

DocHub does **not** read markdown from `Personal_Project/` at runtime in production. Flow:

```
src/config/repositories.ts   ← single source of truth (11 repos)
        ↓
scripts/clone-repos.js       ← clones from GitHub (HTTPS), copies .md → public/repository/{id}/
        ↓
public/repository/{id}/      ← static markdown + tree.json (GitHub Pages)
        ↓
DocHub UI                    ← FileTree + DocumentView
```

| Step | Command / location |
|------|-------------------|
| Local working copy | Clone under `Personal_Project/` with `git@ghub-p:thisiskushal31/{Repo}.git` |
| Refresh DocHub cache | `cd dochub && npm run update-repos` (or `clone-repos`) after pushing to GitHub |
| Live site | [thisiskushal31.github.io/dochub](https://thisiskushal31.github.io/dochub/) |

**Rule:** Edit locally → push to GitHub → update DocHub cache → deploy.

---

## 4. All repositories in DocHub (11)

| DocHub `id` | Display name | GitHub repo | Local clone | Cached `.md` | Content state |
|-------------|--------------|-------------|-------------|--------------|---------------|
| `devops` | DevOps Handbook | `DevOps-Handbook` | `DevOps-Handbook/` | ~1,046 | **Mature** — primary platform/delivery hub |
| `dsa` | Data Structures & Algorithms | `Datastructures-and-Algorithms` | `Datastructures-and-Algorithms/` | ~70 | **Solid** — notes & solutions |
| `Databases` | Databases Deep Dive | `Databases-Deep-Dive` | `Databases-Deep-Dive/` | ~101 | **Solid** — engines, models, object storage |
| `networks` | Networks Deep Dive | `Networks-Deep-Dive` | `Networks-Deep-Dive/` | ~65 | **Solid** — L1–L7 + cloud-native + network security |
| `system-design` | System Design Concepts | `System-Design-Concepts` | `System-Design-Concepts/` | ~170+ | **Solid breadth** — Part E industry coverage matrix tracks industry gaps |
| `container` | Containerization Deep Dive | `Containerization-Deep-Dive` | `Containerization-Deep-Dive/` | ~64 | **Solid** — Docker, K8s, managed platforms |
| `cheatsheets` | Commands and Cheatsheets | `Commands-and-Cheatsheets` | `Commands-and-Cheatsheets/` | ~85 | **Solid** — quick reference |
| `data-engineering` | Data Engineering Deep Dive | `Data-Engineering-Deep-Dive` | `Data-Engineering-Deep-Dive/` | 1 | **Shell** — README only |
| `data-science-ai` | Data Science & AI Deep Dive | `Data-Science-AI-Deep-Dive` | `Data-Science-AI-Deep-Dive/` | 1 | **Shell** — README only |
| `tooling-frameworks` | Tooling & Frameworks Deep Dive | `Tooling-and-Frameworks-Deep-Dive` | `Tooling-and-Frameworks-Deep-Dive/` | 1 | **Shell** — README only |
| `Security` | Security Deep Dive | `Security-Deep-Dive` | `Security-Deep-Dive/` | 1 | **Shell** — README only (push initial commit to GitHub for CI clone) |

**Hub role:** `DevOps-Handbook` is the **delivery & platform spine**. Other repos are **domain deep dives**. `Tooling-and-Frameworks-Deep-Dive` is a **cross-cutting catalog** (frameworks, libraries, SDKs, platforms) — not a duplicate of DevOps `Languages/`.

---

## 5. Local folder map

```
Personal_Project/
├── dochub/                              ← Reader app + public/repository cache
│
├── DevOps-Handbook/                     ← Platform, CI/CD, IaC, cloud-native, OS, languages (devops)
├── Datastructures-and-Algorithms/       ← DSA (dsa)
├── Databases-Deep-Dive/                 ← DB engines, models, object storage (databases)
├── Networks-Deep-Dive/                  ← Networking + network-layer security (networks)
├── System-Design-Concepts/              ← Architecture & scale (system-design)
├── Containerization-Deep-Dive/          ← Containers & orchestration (container)
├── Commands-and-Cheatsheets/          ← Commands reference (cheatsheets)
│
├── Data-Engineering-Deep-Dive/          ← Pipelines, warehousing, orchestration (data-engineering)
├── Data-Science-AI-Deep-Dive/           ← Stats, ML, DL, applied AI (data-science-ai)
├── Tooling-and-Frameworks-Deep-Dive/    ← Frameworks, SDKs, platforms catalog (tooling-frameworks)
├── Security-Deep-Dive/                  ← Cybersecurity capstone (security)
│
├── blog/                                ← Narrative series, case studies
└── portfolio-website/                   ← Projects & experience
```

---

## 6. Domain boundaries (avoid duplication)

| Topic | Primary home | Secondary / pointer only |
|-------|--------------|---------------------------|
| CI/CD, IaC, observability, OS fundamentals | `DevOps-Handbook` | Cheatsheets for commands |
| Network protocols, routing, packet-level | `Networks-Deep-Dive` | DevOps Cloud-Native networking pointers |
| Network-layer attacks, firewalls, VPN, NIDS | `Networks-Deep-Dive/Security/` | Security-Deep-Dive links here for L3–L7 network angle |
| DevOps security (secrets, pipeline, supply chain) | `DevOps-Handbook/Security/` | Security-Deep-Dive for full AppSec/GRC depth |
| SQL, engines, vector DBs | `Databases-Deep-Dive` | DE for pipeline into warehouses; DS-AI for Vector/RAG |
| Spring, React, PyTorch, Terraform as *products* | `Tooling-and-Frameworks-Deep-Dive` | DevOps for *how you use them in delivery* |
| Leetcode / DSA patterns | `Datastructures-and-Algorithms` | System Design for scale trade-offs |
| Production ML, RAG, evaluation | `Data-Science-AI-Deep-Dive` | Blog LLM series; DE for feature pipelines |
| Batch/stream pipelines, data quality | `Data-Engineering-Deep-Dive` | Databases for storage layer |
| Full cybersecurity curriculum | `Security-Deep-Dive` | **Last** — synthesizes everything above |

---

## 7. Recommended learning phases

Phases are **themes**, not rigid gates. Overlap is fine; security depth stays in Phase 4.

### Phase 1 — Platform & fundamentals (months 1–6+)

**Repos:** DevOps Handbook, DSA, Cheatsheets, Containerization  
**Goal:** Operate systems, write automation, understand OS/runtime/container stack.

| Area | Topics to cover / deepen |
|------|--------------------------|
| DevOps `Methodologies/` | Culture, SDLC, collaboration, incident response basics |
| DevOps `Operating-Systems/` | Process, memory, I/O, shell, services, virtualization |
| DevOps `CiCd/` + `IAC/` | Pipelines, GitOps, Terraform/Pulumi patterns |
| DevOps `Cloud-Native/` | K8s concepts, service mesh intro, cloud primitives |
| DevOps `Observability/` | Metrics, logs, traces, SLO/SLI |
| DevOps `Security/` (intro) | Secrets, least privilege, SAST/DAST in pipeline — not full AppSec yet |
| Containerization Deep Dive | Docker/Podman, K8s networking/storage, managed clusters |
| DSA | Arrays, trees, graphs, DP, system-relevant patterns |
| Cheatsheets | Daily driver commands for Linux, git, kubectl, cloud CLI |

**Month tick example:** Pick 2–3 topic files per month; mark `- [x]` in repo README learning path or a `PROGRESS.md` per repo.

---

### Phase 2 — Data, networks & design (months 6–12+)

**Repos:** Databases, Networks, System Design, Tooling (start catalog)  
**Goal:** Reason about data at rest/motion, design systems, know major frameworks by name and role.

| Area | Topics to cover / deepen |
|------|--------------------------|
| Databases `Concepts/` | Normalization, transactions, indexing theory |
| Databases engines | PostgreSQL, Redis, MongoDB, Elasticsearch, vector stores (Weaviate, pgvector) |
| Databases `Blob-Object/` | S3, GCS — ties to DE and cloud security later |
| Networks `Foundations` → `Transport` | OSI/TCP/IP, TCP internals, troubleshooting |
| Networks `Routing-Switching` + `Services` | BGP, DNS, HTTP/TLS, load balancing |
| Networks `Security/` | Threats, encryption, firewalls, VPN, blue team **network angle** |
| Networks `Cloud-Native/` | VPC, K8s networking, Cilium/eBPF |
| System Design | Caching, messaging, sharding, CAP, case studies (URL shortener, feed, etc.) |
| Tooling (seed) | Index major stacks: Web (React, Next), Backend (Spring, FastAPI), Data (Spark, dbt), Cloud SDKs |

---

### Phase 3 — Data engineering & AI (months 12–18+)

**Repos:** Data-Engineering-Deep-Dive, Data-Science-AI-Deep-Dive, Tooling (expand)  
**Goal:** End-to-end data platforms and production ML/AI — aligns with your Purplle/blog experience.

#### Data-Engineering-Deep-Dive — planned structure

```
Data-Engineering-Deep-Dive/
├── README.md                    ← Map + learning path + monthly checklist
├── Foundations/
│   ├── 1_Data_Modeling_Warehousing.md
│   ├── 2_Batch_vs_Streaming.md
│   └── 3_Data_Quality_Lineage.md
├── Ingestion/
│   ├── Batch/                   ← Airbyte, Fivetran patterns, GCS/S3 landing
│   └── Streaming/               ← Pub/Sub, Kafka, Flink intro
├── Processing/
│   ├── SQL_Transforms/          ← BigQuery, dbt, Dataform
│   └── Distributed/             ← Spark, Beam/Dataflow
├── Orchestration/
│   ├── Airflow_Composer/
│   └── Dagster_Prefect/
├── Storage/
│   ├── Lakehouse/               ← Delta, Iceberg, BigLake
│   └── Serving/                 ← OLAP, semantic layers
├── Platform-Ops/
│   ├── Cost_Governance.md
│   ├── Monitoring_SLAs.md
│   └── IaC_for_Data.md
└── Assets/
```

**Topics:** medallion architecture, idempotent pipelines, backfill, schema evolution, PII handling, cost/performance tuning, GCP/AWS data services you use in production.

#### Data-Science-AI-Deep-Dive — planned structure

```
Data-Science-AI-Deep-Dive/
├── README.md
├── Foundations/
│   ├── 1_Statistics_Probability.md
│   ├── 2_Linear_Algebra_Calculus_Refresher.md
│   └── 3_Experiment_Design.md
├── Classical-ML/
│   ├── Supervised_Unsupervised.md
│   ├── Feature_Engineering.md
│   └── Model_Evaluation.md
├── Deep-Learning/
│   ├── Architectures/
│   ├── Training_at_Scale/
│   └── Transfer_Learning.md
├── NLP-LLM/
│   ├── Embeddings_RAG.md
│   ├── Prompting_Fine_Tuning.md
│   ├── Evaluation_Safety.md
│   └── Agents_Tools.md
├── MLOps/
│   ├── Experiment_Tracking.md
│   ├── Model_Registry_Serving.md
│   └── GPU_Infra_Cost.md
├── Applied/
│   ├── Computer_Vision.md
│   ├── Tabular_Production.md
│   └── Case_Studies/            ← Cross-link blog LLM series + portfolio projects
└── Assets/
```

**Cross-links:** Blog LLM basics series → `NLP-LLM/`; Databases vector section → embeddings storage; DE → feature pipelines for ML.

#### Tooling-and-Frameworks-Deep-Dive — planned structure

Organize by **domain**, tag each entry as *framework / library / SDK / platform / runtime / spec*:

```
Tooling-and-Frameworks-Deep-Dive/
├── README.md                    ← Master index + "when to use what"
├── Web-Frontend/                ← React, Vue, Angular, Svelte, Next, Nuxt…
├── Web-Backend/                 ← Spring, Django, FastAPI, Express, .NET…
├── Mobile/                      ← Flutter, React Native, SwiftUI…
├── Data-ML/                     ← Spark, Pandas, PyTorch, TensorFlow, Hugging Face…
├── Data-Eng/                    ← dbt, Airflow, Beam, Flink…
├── Cloud-Platform/              ← AWS/GCP/Azure SDKs, CDK, Pulumi…
├── Infra-Runtime/               ← Node, JVM, .NET, WASM; K8s ecosystem (Helm, Argo…)
├── Security/                    ← Burp, Metasploit, Trivy, Falco — catalog only; depth in Security-Deep-Dive
├── Enterprise/                  ← SAP, Salesforce — as needed
└── Specs-Standards/             ← OpenAPI, OAuth, gRPC, OpenTelemetry…
```

**Not:** Re-document language syntax (that stays in DevOps `Languages/`). **Yes:** What the tool is, when to pick it, hello-world + architecture diagram, link to official docs.

---

### Phase 4 — Cybersecurity capstone (months 18+)

**Repo:** Security-Deep-Dive  
**Prerequisite:** Comfortable with Phases 1–3 (you don't need 100% completion — you need *working depth* across stack).

#### Security-Deep-Dive — planned structure

```
Security-Deep-Dive/
├── README.md                    ← Roadmap + prerequisites + link to all related repos
├── Foundations/
│   ├── 1_Security_Principles_Confidentiality_Integrity_Availability.md
│   ├── 2_Threat_Modeling_STRIDE.md
│   └── 3_Risk_Assessment.md
├── Identity-Access/
│   ├── IAM_AuthN_AuthZ.md
│   ├── SSO_OAuth_OIDC_SAML.md
│   └── Zero_Trust.md
├── Application-Security/
│   ├── OWASP_Top_10.md
│   ├── Secure_SDLC.md
│   ├── API_Security.md
│   └── Web_Mobile_Client_Security.md
├── Cloud-Security/
│   ├── CSPM_CWPP.md
│   ├── Secrets_KMS.md
│   ├── Container_K8s_Security.md
│   └── Supply_Chain_SBOM.md
├── Network-Security/            ← Pointer-heavy: full depth in Networks-Deep-Dive/Security/
│   └── README.md                ← "Read Networks-Deep-Dive first; this adds enterprise SOC angle"
├── Defensive-Operations/
│   ├── SIEM_SOAR.md
│   ├── Incident_Response.md
│   ├── Forensics.md
│   └── Logging_Detection.md
├── Offensive-Red-Team/          ← Ethical scope, lab-only
│   ├── Recon_Enumeration.md
│   ├── Exploitation_Fundamentals.md
│   └── Pentest_Methodology.md
├── Governance-Compliance/
│   ├── NIST_CSF.md
│   ├── ISO_27001_Overview.md
│   ├── CIS_Benchmarks.md
│   └── MITRE_ATT_CK.md
├── Cryptography/
│   ├── Symmetric_Asymmetric.md
│   ├── TLS_PKIX.md
│   └── Practical_Crypto_Pitfalls.md
├── Labs/
│   └── Home_Lab_Setup.md        ← DVWA, TryHackMe-style paths, CTF notes
└── Assets/
```

**Overlap rule:** Networks repo owns packet/firewall/VPN depth; DevOps repo owns pipeline/secrets/supply-chain in delivery; Security repo owns **holistic cyber program** (GRC, AppSec, IR, offensive methodology, cloud posture).

---

## 8. Mature repos — what remains to deepen

These already have substantial content. Ongoing work = fill gaps, not greenfield.

| Repo | Already strong | Planned additions |
|------|----------------|-------------------|
| **DevOps Handbook** | Full section tree, 1k+ topics | CNCF landscape, web tier/servers, artifact registries — per Part E DevOps completeness plan |
| **Networks** | Full section map | Finish TBD placeholders; expand labs |
| **Databases** | Engine-per-folder depth | More managed-service parity; link DE/DS-AI vector topics |
| **System Design** | Case studies & components | Industry coverage matrix (Part E) + primer-gaps (12 topics); failure-modes; cases 1–17; deepen Observability/security |
| **Containerization** | Runtimes + K8s | Security hardening cross-link to Security-Deep-Dive |
| **DSA** | Theory (Algorithms + DataStructures + Foundation) | Part E problems list + [system-design-bridge/](../../Deep-Dives/Datastructures-and-Algorithms/system-design-bridge/README.md) — empty LeetCode categories |
| **Cheatsheets** | Broad command ref | New tools as you adopt them in other repos |

---

## 9. Blog & portfolio overlap

| Surface | Role in the plan |
|---------|------------------|
| **Blog** | Narrative depth — series (DB mastery, containers, LLM), war stories, deployment guides |
| **Portfolio** | Proof of work — Purplle data/ML/RAG, security improvements, infra projects |
| **DocHub repos** | Structured reference — topic files, checklists, copy-paste commands |
| **This report** | Master plan — phases, boundaries, planned folder trees |

**Pattern:** Deep reference in repos; polished story on blog; outcomes on portfolio. Link all three.

---

## 10. Monthly workflow (practical)

1. **Pick a phase theme** (or one repo) for the month — e.g. "August: Networks Transport + Databases PostgreSQL."  
2. **Select 2–4 topic files** — realistic, not entire sections.  
3. **Study → notes in repo** (or tick existing files if already written).  
4. **Mark progress** — `- [x]` in README learning path or `PROGRESS.md`; commit & push.  
5. **Optional blog post** if a topic deserves a narrative (Purplle-style case study).  
6. **Refresh DocHub** — `npm run update-repos` in `dochub/` after pushes.  
7. **Review boundaries** — if a topic belongs in another repo, add a pointer, don't duplicate.

---

## 11. Immediate next steps (content priority)

**Active calendar:** [Current focus — deadline 30 September 2026](#current-focus--deadline-30-september-2026) in Part A. That table is the source of truth until the deadline.

| Priority | Action | Repo |
|----------|--------|------|
| 1 | Fill **DevOps** delivery spine concepts (CiCd → Security gates → IAC → Observability); strengthen existing DevOps identity | `DevOps-Handbook` |
| 2 | Finish **network security** notes you would defend | Networks `Security/` (+ Tooling scanner install only if needed) |
| 3 | Make **System Design** Fundamentals defendable + chosen cases | `System-Design-Concepts` |
| 4 | Close **Database** Concepts + engines you operate | `Databases-Deep-Dive` |
| 5 | Side lane only: AI Foundations / retrieval | `Data-Science-AI-Deep-Dive` |
| 6 | Park until after 30 Sep (unless a real job forces it) | DE full tree, Security-Deep-Dive program, Tooling framework backlog, Containerization gap stubs |

---

## 12. Summary

| Layer | Status |
|-------|--------|
| DocHub | **11 repos** configured and cached |
| Local clones | All 11 under `Personal_Project/` (`git@ghub-p:`) |
| Mature content | DevOps, DSA, Databases, Networks, System Design, Container, Cheatsheets |
| Coverage audit | **Section 13** — industry benchmark vs all 11 repos (August 2026) |
| New shells | DE, DS-AI, Tooling, Security — **structure planned in Section 7 + Section 13** |
| Learning order | Platform → data/networks/design → DE/AI/tooling → **security last** |
| Expertise today | **DevOps strong**; full stack & product arch **in progress**; security **exposure** |
| Entrepreneur gaps | GTM, pricing, customer discovery, finance — **Section 2 code block** |
| Progress tracking | Git-tracked markdown checklists; DocHub display-only for now |

---

## 13. Full ecosystem coverage audit (August 2026)

**Purpose:** One chart so you never wonder “am I missing a domain?” Benchmarked against 2025–2026 industry roadmaps (system design interview rubrics, full-stack+DevOps paths, data engineering roadmaps, cybersecurity curricula). **Detailed System Design map:** Part E industry coverage matrix.

**Legend:** ✅ solid · ⚠️ partial/stubs · ❌ empty · 🔗 owned by related repo (intentional)

### 13.1 Repo readiness snapshot

| # | Repo | MD files | Scaffold | Content | Industry benchmark |
|---|------|----------|----------|---------|-------------------|
| 1 | DevOps-Handbook | ~1,099 | Entry-Points ✅ | ✅ mature | ✅ Matches DevOps/SRE roadmaps; ~146 stubs remain |
| 2 | Containerization-Deep-Dive | ~101 | ✅ full | ✅ solid | ✅ Docker/K8s/managed — gap stubs (containerd, GitOps) |
| 3 | Databases-Deep-Dive | ~214 | ✅ full | ⚠️ 6/30+ engines | ⚠️ Engine depth partial; data-platform stubs |
| 4 | Networks-Deep-Dive | ~87 | ✅ full | ✅ solid | ✅ L1–L7 + security; labs/service-mesh stubs |
| 5 | System-Design-Concepts | ~170+ | ✅ full | ⚠️ breadth yes, depth gaps | ⚠️ See **13.2** — skeleton complete after primer-gaps |
| 6 | Datastructures-and-Algorithms | ~90+ | ✅ | ✅ | ✅ | Problems to fill (Part E) + system-design-bridge |
| 7 | Commands-and-Cheatsheets | ~86 | ❌ none | ✅ useful | ⚠️ Dated/GCP-heavy; no K8s depth |
| 8 | Data-Engineering-Deep-Dive | 1 | ❌ | ❌ empty | ❌ vs DE roadmap (Airflow, dbt, Spark, lakehouse) |
| 9 | Data-Science-AI-Deep-Dive | 1 | ❌ | ❌ empty | ❌ vs ML/MLOps/LLM roadmaps |
| 10 | Tooling-and-Frameworks-Deep-Dive | 1 | ❌ | ❌ empty | ❌ vs full-stack framework catalogs |
| 11 | Security-Deep-Dive | 1 | ❌ | ❌ empty | ❌ vs OWASP/MITRE/SOC curricula (capstone — last) |

**Scaffolded repos (write order + start-here content live in Part E; Entry-Points on repos):** DevOps (partial), Containerization, Databases, Networks, System Design — **5/11 with full nav**; **all 11 have write order in Part E**; **most have Start here in Part E** (DevOps uses Methodologies path; Cheatsheets reference-only).

### 13.2 System Design — industry checklist verdict

**You are NOT missing the architecture skeleton.** Core building blocks exist: LB, CDN, cache, queues, SQL/NoSQL, sharding, replication, CAP, consistent hashing, patterns (CQRS, circuit breaker), and 17 case file stubs.

**Gaps closed in this audit (stubs added):**

| Gap (industry lists) | Now in repo |
|----------------------|-------------|
| Gossip, Bloom filters, CRDT, Merkle | [Primer-Gaps/](../../Deep-Dives/System-Design-Concepts/Primer-Gaps/README.md) |
| 2PC / saga standalone | Primer-Gaps/1 |
| Search at scale | Primer-Gaps/3 |
| RAG / LLM gateway (2026 tier) | Primer-Gaps/12 |
| Multi-region, multi-tenancy, batch/stream | Primer-Gaps/8–10 |
| Failure modes (stampede, split brain, cascade) | [Failure-Modes/](../../Deep-Dives/System-Design-Concepts/Failure-Modes/README.md) |
| Security trade-offs at design time | [Security-Tradeoffs/](../../Deep-Dives/System-Design-Concepts/Security-Tradeoffs/README.md) |
| Missing interview cases (notifications, email, tickets, crawler, etc.) | [Cases/12–17](../../Deep-Dives/System-Design-Concepts/README.md) |

**Still to WRITE (not missing from map — on your fill list):**

- Deepen **Observability/** (9 thin files) and **Security/** (7 thin files)
- Fill **Primer-Gaps/** bodies + **Cases/** failure-mode sections
- **2026 rubric:** cost reasoning in every case; back-of-envelope math in HLD

**Intentionally elsewhere (not duplicates):**

| Topic | Primary repo |
|-------|--------------|
| TCP/TLS/DNS wire depth | Networks-Deep-Dive |
| Engine tuning, pgvector ops | Databases-Deep-Dive |
| Prometheus/Grafana runbooks | DevOps-Handbook |
| OWASP labs, MITRE ATT&CK program | Security-Deep-Dive (capstone) |
| Pipeline authoring, dbt, Airflow | Data-Engineering-Deep-Dive |
| Model training, eval, MLOps | Data-Science-AI-Deep-Dive |
| React/Spring/FastAPI catalogs | Tooling-and-Frameworks-Deep-Dive |

### 13.3 Cross-domain coverage matrix (all repos)

| Domain | Primary repo | Status | Industry topics still open |
|--------|--------------|--------|----------------------------|
| **Platform / DevOps / SRE** | DevOps-Handbook | ✅ | CNCF landscape, artifact registries, web tier |
| **Containers / K8s** | Containerization + DevOps Cloud-Native | ✅ | containerd, GitOps packaging stubs |
| **Networking** | Networks-Deep-Dive | ✅ | labs-expanded, service-mesh stubs |
| **Databases** | Databases-Deep-Dive + SD `Databases/` | ⚠️ | 24+ engine stubs; pgvector v1 priority |
| **System design / architecture** | System-Design-Concepts | ⚠️ | coverage matrix fill list (Part E) |
| **DSA** | Datastructures-and-Algorithms | ⚠️ theory ✅; ~18 problems | Problems to fill (Part E) + system-design-bridge scaffolded |
| **Data engineering** | Data-Engineering-Deep-Dive | ❌ | Entire Section 7 Phase 3 tree |
| **Data science / AI / RAG** | Data-Science-AI-Deep-Dive | ❌ | Entire Section 7 Phase 3 tree |
| **Tooling / full-stack frameworks** | Tooling-and-Frameworks-Deep-Dive | ❌ | Entire Section 7 catalog |
| **Cybersecurity (capstone)** | Security-Deep-Dive | ❌ | Entire Section 7 Phase 4 tree |
| **Commands reference** | Commands-and-Cheatsheets | ✅ | Modernize K8s/AWS; cross-links |
| **Entrepreneur / GTM** | *(no repo)* | ❌ | Section 2 `business_entrepreneur_*` gaps |

### 13.4 Recommended order after this audit

**Until 30 Sep 2026:** Part A Current focus wins — **DevOps delivery spine → Networks Security**, then System Design / Databases.

After the deadline (or if Part A is cleared early):

1. **DevOps** — finish remaining Lane A / completeness-plan stubs (tool folders after concepts)  
2. **Networks** — maintain Security/; deepen Advanced/Labs if needed  
3. **System Design** — Part E industry coverage matrix: short Fundamentals/Observability notes → primer-gaps → cases  
4. **Databases** — pgvector, GCS/S3 per Part E engines list  
5. **Empty shells** — DE → DS-AI → Tooling (Phase 3); Security-Deep-Dive last (Phase 4)  
6. **DSA** — fill Part E problems list categories; implement system-design-bridge problems  
7. **Quarterly** — re-run Section 13 against new industry checklists (AI tier evolves fast)

### 13.5 Where the plan lives

All write-order, start-here copy, engines/cases/problems lists, and coverage matrices live in **Part E of this syllabus**. Deep-Dive repos keep public `README.md` + topic notes only — do not look for planning files on repo roots.

---

*This document is the master plan. Update it when you add repos, finish phases, or shift monthly focus. **Section 13** is the “am I missing anything?” chart — refresh after major scaffold passes.*

---

# Part E — Per-repo order, goals, and topic status

Moved out of Deep-Dive repo roots so GitHub/DocHub only show the public README + notes.

---

## DevOps-Handbook

Public intro: [Deep-Dives/DevOps-Handbook/README.md](../../Deep-Dives/DevOps-Handbook/README.md)

### Start here

# Start here — DevOps Handbook

[← README](./README.md) · Write order

**Why a security engineer opens this:** you cannot secure a pipeline, an image, or a secret you do not understand. Delivery is part of the security job.

You can start this repo knowing nothing about DevOps. Languages/ is from-scratch syntax. Methodologies/0 is the SE on-ramp. You do not need Containerization first — that is the *depth* of Docker.

## Path (basic → advanced)

0. [README](./README.md) then [CiCd/](./CiCd/README.md) — Git/Make live in [Tooling Utility/](../Tooling-and-Frameworks-Deep-Dive/Utility/README.md)
1. [Methodologies/0 — SE learning DevOps](./Methodologies/0_SE_Learning_DevOps_Start_Here.md)
2. [Operating-Systems/Fundamentals/](./Operating-Systems/README.md) if processes/memory are new
3. [CiCd/](./CiCd/README.md) — how software ships
4. [IAC/](./IAC/README.md) → [Cloud/](./Cloud/README.md)
5. [Observability/](./Observability/README.md) + [Security/](./Security/README.md) (pipeline grain)
6. Related repos on the [README](./README.md) when you need Docker / networks / DBs in full

*(Content TBD — stub created September 2026)*

### Write order

# DevOps Handbook — content write order

**Created:** August 2026  
**Purpose:** Single map of every stub folder/file and what to fill. Work top-to-bottom; do not re-derive the plan later.

**Status key:** `stub` = placeholder exists · `folder` = structure only · `expand` = existing TBD file to flesh out

---

## Lane A (recommended)

**Sept sprint (priority 1):** concept files first — strengthen DevOps identity. Then Networks (Part A priority 2).

| Step | Location | Action |
|------|----------|--------|
| 1 | [Methodologies/0_SE_Learning_DevOps_Start_Here.md](./Methodologies/0_SE_Learning_DevOps_Start_Here.md) | SE on-ramp + links to related repos |
| 2 | [CiCd/1–7](./CiCd/README.md) | Full delivery loop: pipelines → tools map → strategies → artifacts → verify → supply chain → DB migrations |
| 3 | [Security/1–5](./Security/README.md) | Secrets, compliance grain, tools map, **gate chain**, OIDC/CI least privilege |
| 4 | [IAC/1–3](./IAC/README.md) | Patterns, state/modules/backends, multi-cloud practices |
| 5 | [Observability/1–3](./Observability/README.md) | Metrics, logs/traces, tools map |
| 6 | [Methodologies/](./Methodologies/README.md) topics 1–8 | Culture → branching → SRE/on-call → DORA → ChatOps → docs → FinOps (as needed) |
| 7 | [README](./README.md) related-repos table | Keep pointers current — no `Entry-Points/` folder |
| 8 | [Servers/](./Servers/README.md) / [Cloud/](./Cloud/README.md) | Web servers + cloud literacy when delivery notes need them |
| 9 | [Cloud-Native/4_CNCF_Everyday_Tools.md](./Cloud-Native/4_CNCF_Everyday_Tools.md) + tool stubs | cert-manager, ExternalDNS, Backstage |
| 10 | Vendor / tool folders under CiCd, Security, IAC, Observability | After concepts exist — one folder at a time when you use the tool |

**Defer:** `Languages/` (mature), deep per-tool prose in every CiCd vendor folder until concepts exist. **After Lane A concepts:** Part A → Networks `Security/`.

---

## From completeness plan (still in force)

These were already promised in the completeness plan. They stay on this write-order so they are not forgotten. Tick in the PLAN file when the *entry or folder* exists and is filled.

| PLAN item | Home in this repo (or pointer) | Status in tree |
|-----------|--------------------------------|----------------|
| SE orientation | [Methodologies/0](./Methodologies/0_SE_Learning_DevOps_Start_Here.md) | exists |
| Artifact registries | [CiCd/4](./CiCd/4_Artifacts_And_Registries.md) | stub/concept |
| Supply-chain (SBOM, cosign, SLSA) | `CiCd/` + `Security/` | planned |
| Cloud literacy | [Cloud/](./Cloud/README.md) | folder exists |
| Docker/Podman door | [README](./README.md) Containers row | exists |
| Data / messaging / cache doors | [README](./README.md) | exists; Kafka *engine* → DE `Systems/` |
| DNS / CDN / LB doors | [README](./README.md) Networking + System Design rows | exists |
| On-call tooling | Practice: [Methodologies/3](./Methodologies/3_Team_Patterns_SRE_Incident.md). Product: [Observability/PagerDuty](./Observability/PagerDuty/README.md) | exists |
| Azure DevOps / Buildkite / Unleash | [CiCd/](./CiCd/README.md) | exists |
| Atlantis | [IAC/Atlantis](./IAC/Atlantis/README.md) | exists |
| FinOps | [Methodologies/](./Methodologies/README.md) | stub |
| OpenTofu / Packer | [IAC/](./IAC/README.md) | planned |
| Kyverno / Loki / Backstage | Cloud-Native / Observability indexes | planned |
| Synthetic / e2e in verify (k6, Playwright) | `CiCd/` verify; Playwright → Tooling `Quality-And-Testing/Playwright` | planned |
| DB migrations in pipelines | CiCd entry + Databases `Tools/Flyway` | planned |
| Local dev parity | [README](./README.md) + Containerization `Local-Dev/` | planned |
| Maintenance / legacy (SWEBOK) | [Methodologies/9](./Methodologies/9_Maintenance_And_Legacy.md) | stub |
| Application frameworks | **Not here.** [Tooling-and-Frameworks-Deep-Dive](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive) | README row |

---

## New top-level sections

| Folder | README | Role |
|--------|--------|------|
| [Servers/](./Servers/) | Yes | nginx, Apache, Caddy, Traefik, HAProxy, IIS, host lifecycle |
| [Cloud/](./Cloud/) | Yes | Multi-cloud literacy for SEs doing DevOps |

**Not a new folder here:** Application frameworks → [Tooling-and-Frameworks-Deep-Dive](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive). Related-repo pointers live on the [README](./README.md).

---

## Related repos (README table)

| Repo | Pointer |
|------|---------|
| Containerization-Deep-Dive | README Containers / Local-Dev rows |
| Networks-Deep-Dive | README Networking row |
| Databases-Deep-Dive | README Databases + data/messaging rows |
| System-Design-Concepts | README System design row |
| Tooling-and-Frameworks-Deep-Dive | README Tooling row |
| Security-Deep-Dive | README Cybersecurity row |
| Data-Engineering / Data-Science-AI | README rows |

---

## Completeness contract

Full gap matrix: DevOps completeness plan below

Mark a stub **done** when: standalone prose, image or diagram if useful, copy-paste example, related-repo link if depth lives elsewhere, pitfalls/trade-offs section.

### DevOps completeness plan

# Plan: DevOps concepts beyond Languages

[← Back to handbook](./README.md)

**Status:** Planning only — content bodies for the gaps below are **not** started yet.  
**Purpose:** Resume later without re-deriving the map. This file is also the **completeness contract** for software engineers reading DevOps.

---

## Promise to software engineers (frontend / backend / fullstack / platform)

Anyone who ships software and wants to learn **DevOps** should be able to open **this handbook** and either:

1. **Learn it here** (concepts + tools at DevOps depth), or  
2. **See a clear entry here** (what it is, why DevOps cares, day-to-day use) **plus a link** to a related deep-dive when depth lives elsewhere.

They should **not** discover months later that “networking / Docker / databases / system design” were silently assumed and never pointed to.

| Reader | What this plan guarantees |
|--------|---------------------------|
| **Backend / fullstack SE** | Delivery path, servers, CI/CD security, IaC/automation literacy, and links for data stores, queues, design |
| **Frontend SE** | Frameworks literacy (planned), static/CDN/edge doors, CI for web apps, env/config, observability of UX-impacting failures |
| **Platform / DevOps-leaning SE** | Full toolchain map below; OS + Cloud-Native + Observability + Security as first-class |
| **Any SE new to ops** | Day-to-day practice catalog + “where do I go next?” links—no orphan topics |

**Rule when writing later:** every major SE-facing DevOps topic gets either a **chapter/folder here** or an **entry chapter** (short) that links out. Prefer entry+link over duplicating a deep-dive.

---

## Related deep-dives (already exist — link, don’t rebuild)

Use **GitHub repo URLs** in public handbook content (same rule as root README).

| Domain | Repository | SE should use it for |
|--------|------------|----------------------|
| **Networking** | [Networks-Deep-Dive](https://github.com/thisiskushal31/Networks-Deep-Dive) | TCP/HTTP, DNS deep, routing, firewalls, cloud-native net, net security |
| **Containers & orchestration depth** | [Containerization-Deep-Dive](https://github.com/thisiskushal31/Containerization-Deep-Dive) | Docker/Podman, Swarm, OpenShift, managed K8s (GKE/EKS/AKS) depth |
| **Databases & object storage** | [Databases-Deep-Dive](https://github.com/thisiskushal31/Databases-Deep-Dive) | SQL/NoSQL/Cache/search/vector; **S3/GCS-style object stores** |
| **System design** | [System-Design-Concepts](https://github.com/thisiskushal31/System-Design-Concepts) | LB, CDN, API gateway, caching, messaging, HA/DR, patterns |
| **Commands cheat sheets** | [Commands-and-Cheatsheets](https://github.com/thisiskushal31/Commands-and-Cheatsheets) | Quick command lookup (incl. DevOps-And-Cloud-Essentials) |
| **DSA** | [Datastructures-and-Algorithms](https://github.com/thisiskushal31/Datastructures-and-Algorithms) | Interview/algos—**not** required for DevOps path; optional door only |

---

## Completeness map — day-to-day DevOps for SEs

Status key:

| Status | Meaning |
|--------|---------|
| **HERE-deep** | Handbook section exists or is the right deep home (may still be stub/TBD prose) |
| **HERE-plan** | Explicitly committed in this plan (build when work resumes) |
| **ENTRY+link** | Add/keep a **short DevOps entry** here; depth in related repo or official docs |
| **GAP** | Missing from plan until now — **must add** entry or folder so SEs aren’t blind |

### A. Culture, process, collaboration

| Topic | Day-to-day tools / ideas | Status | Home |
|-------|--------------------------|--------|------|
| DevOps culture, blameless, learning | Rituals, reviews | **HERE-deep** (thin) | `Methodologies/` |
| Branching / PR / trunk vs GitFlow | GitHub/GitLab/Bitbucket | **HERE-plan** | `Methodologies/` |
| Agile / shift-left | Ceremony vs delivery | **HERE-deep** (named in stubs) | `Methodologies/` |
| ChatOps / Slack-Teams notifications | Slack, Teams | **HERE-plan** | `Methodologies/` / `CiCd/` |
| Incident / on-call | PagerDuty, Opsgenie, Grafana OnCall | **HERE-deep** (SRE stub) + **GAP** tool literacy | `Methodologies/3` + optional `Observability/` or Security ops entry |
| DORA / delivery metrics literacy | Deploy freq, lead time, CFR, MTTR | **HERE-plan** | `Methodologies/` |
| Docs as code / runbooks | Markdown, Notion/Git | **ENTRY+link** | Short entry in Methodologies; don’t fork wiki products |

### B. Source → build → test → release (CI/CD)

| Topic | Day-to-day tools / ideas | Status | Home |
|-------|--------------------------|--------|------|
| CI platforms (GitHub Actions) | Workflows + runners on GitHub | **HERE-deep** ([GitHub_Actions 01–24](../../Deep-Dives/DevOps-Handbook/CiCd/GitHub_Actions/README.md)) | `CiCd/GitHub_Actions/` |
| CI platforms (GitLab CI) | `.gitlab-ci.yml` + GitLab platform literacy | **HERE-deep** ([GitLab_CI 01–26](../../Deep-Dives/DevOps-Handbook/CiCd/GitLab_CI/README.md)) | `CiCd/GitLab_CI/` |
| CI platforms (Jenkins) | Automation server; Pipeline + classical estates | **HERE-deep** ([Jenkins 01–26](../../Deep-Dives/DevOps-Handbook/CiCd/Jenkins/README.md)) | `CiCd/Jenkins/` |
| CI platforms (Tekton) | K8s-native Pipelines/Triggers/PAC/Chains | **HERE-deep** ([Tekton 01–26](../../Deep-Dives/DevOps-Handbook/CiCd/Tekton/README.md)) | `CiCd/Tekton/` |
| CI platforms (CircleCI) | CircleCI Cloud + config.yml | **HERE-deep** ([CircleCI 01–24](../../Deep-Dives/DevOps-Handbook/CiCd/CircleCI/README.md)) | `CiCd/CircleCI/` |
| CI platforms (Buildkite) | Buildkite Pipelines + agents | **HERE-deep** ([Buildkite 01–26](../../Deep-Dives/DevOps-Handbook/CiCd/Buildkite/README.md)) | `CiCd/Buildkite/` |
| CI platforms (Bitbucket) | Bitbucket Cloud + Pipelines | **HERE-deep** ([Bitbucket 01–21](../../Deep-Dives/DevOps-Handbook/CiCd/Bitbucket/README.md)) | `CiCd/Bitbucket/` |
| CI platforms (Azure DevOps) | Azure DevOps (Pipelines + suite) | **HERE-deep** ([Azure_DevOps 01–25](../../Deep-Dives/DevOps-Handbook/CiCd/Azure_DevOps/README.md)) | `CiCd/Azure_DevOps/` |
| CD / GitOps | Argo CD, Flux | **HERE-deep** (Argo CD **01–18**; Flux **01–22** full track) | `CiCd/Argo_CD/`, `CiCd/Flux/` |
| Progressive delivery | Argo Rollouts, flags | **HERE-deep** ([Argo_Rollouts 01–16](../../Deep-Dives/DevOps-Handbook/CiCd/Argo_Rollouts/README.md); Unleash still entry) | `CiCd/3`, `CiCd/9`, tool folders |
| Full path test→deploy→verify | Environments, promotion, approvals | **HERE-plan** | `CiCd/` + `Methodologies/` |
| Artifact registries | GHCR, ECR, GCR/AR, Harbor, Artifactory, Nexus | **GAP → HERE-plan** (concepts + 1–2 tools) | New under `CiCd/` or `Servers/` adjacent — **artifact management chapter** |
| Package registries | npm, PyPI, Maven, Go proxy | **ENTRY+link** | Languages tracks + short CiCd entry |
| Supply chain (SBOM, sign, provenance) | Syft/Grype, cosign/Sigstore, SLSA literacy | **GAP → HERE-plan** | `CiCd/` + `Security/` |
| Feature flags | LaunchDarkly, Unleash, OpenFeature, custom | **HERE-plan** (practice) + **GAP** tool entry | `CiCd/3` / Methodologies |


### Tekton track plan (CiCd/Tekton/) — from Archive scrape 2026-09-15

**Stance:** Kubernetes-native CI/CD product surface (Pipelines core + Triggers + Pipelines-as-Code + CLI/Dashboard + Chains + Results/Pruner + Operator/Resolution + Catalog/Hub literacy). Not every hub.tekton.dev Task YAML; not contributor/developer internals encyclopedia.

**Guardrails:** Part A rules 8–10 — plan lives here; public chapters Concepts→Advanced→Applications→official References only; no Archive leaks; full-spectrum doors to forge CI (Actions/GitLab/Jenkins) and GitOps CD (Argo/Flux); Containerization owns cluster internals.

**Public MD files to add under `Deep-Dives/DevOps-Handbook/CiCd/Tekton/`:**

| # | File | Focus |
|---|------|--------|
| 01 | `01_What_Is_Tekton.md` | CNCF automation; vs forge CI; when it fits |
| 02 | `02_Install_Pipelines_And_Operator.md` | Release YAML install; Operator path; prereqs |
| 03 | `03_Core_Model_Tasks_Pipelines_Runs.md` | Task / Pipeline / TaskRun / PipelineRun |
| 04 | `04_First_Task_And_PipelineRun.md` | First apply; kubectl/`tkn`; lab loop |
| 05 | `05_Tasks_Steps_Params_And_Results.md` | Steps, params, results, scripts, when |
| 06 | `06_Pipelines_Ordering_And_Finally.md` | Graph, finally, pipelines-in-pipelines |
| 07 | `07_Workspaces_Artifacts_And_Volumes.md` | Workspaces, artifacts, volumes, isolation |
| 08 | `08_Auth_ServiceAccounts_And_RBAC.md` | SA, RBAC, registry push, secrets |
| 09 | `09_Pod_Templates_Compute_And_Affinity.md` | PodTemplate, resources, affinity assistants |
| 10 | `10_Matrix_CustomRuns_And_StepActions.md` | Matrix fan-out; CustomRun; StepAction literacy |
| 11 | `11_Resolvers_Bundles_And_Remote_Resources.md` | Git/Hub/Bundle/Cluster/HTTP resolvers |
| 12 | `12_Triggers_EventListeners_And_Interceptors.md` | Triggers stack; CEL interceptors |
| 13 | `13_Pipelines_As_Code.md` | `.tekton/`; providers; Repository CRD |
| 14 | `14_Catalog_Hub_And_Reusable_Tasks.md` | Catalog/Hub reuse; digest pin |
| 15 | `15_CLI_tkn.md` | `tkn` day-2 |
| 16 | `16_Dashboard.md` | Web UI literacy |
| 17 | `17_Chains_Supply_Chain_Security.md` | Signing / SLSA / Sigstore door |
| 18 | `18_Results_And_Pruner.md` | Long-term results; retention/GC |
| 19 | `19_Operator_Platform_Config.md` | TektonConfig / component CRs |
| 20 | `20_Observability_HA_Debug_And_Windows.md` | Metrics/events/HA/debug; Windows literacy |
| 21 | `21_Worked_Example_Build_Test_Push.md` | End-to-end lab |
| 22 | `22_Best_Practices_And_When_Not_Tekton.md` | Judgment; forge CI / Jenkins doors |
| 23 | `23_Feature_And_Offering_Coverage_Map.md` | Full product + config inventory |
| 24 | `24_YAML_CRD_Catalog_And_Troubleshooting.md` | Config index + playbook |
| 25 | `25_Migrate_Versioning_And_Extras.md` | API migrations; extras |
| 26 | `26_GitOps_Handoff_And_Spectrum.md` | Argo/Flux handoff; delivery spectrum |

Plus folder `README.md` (track intro). Status: **public 01–26 + README added** (2026-09-16); **final harden/coverage pass** same day (offering-class complete; Hub encyclopedia upstream).


### C. Pipeline security (AppSec in delivery)

| Topic | Day-to-day tools / ideas | Status | Home |
|-------|--------------------------|--------|------|
| SAST / quality | SonarQube, Semgrep, CodeQL | **HERE-plan** | `Security/` + `CiCd/` gates |
| SCA / deps | Snyk, Trivy, Dependabot/Renovate | **HERE-deep** / plan | `Security/` |
| Secrets in git | gitleaks, platform secret scanning | **HERE-plan** | `Security/` + CiCd |
| Secrets at rest | Vault | **HERE-deep** | `Security/Vault` |
| IaC / policy scan | Checkov, OPA, Kyverno (K8s policy) | **HERE-deep** + **GAP** Kyverno entry | `Security/` / Cloud-Native |
| Image scan | Trivy, Snyk Container | **HERE-deep** | `Security/` |
| DAST | OWASP ZAP | **HERE-plan** | `Security/ZAP` |
| WAF | Cloud/vendor WAF | **HERE-plan** | `Security/` |
| IAM / least privilege (DevOps angle) | Cloud IAM, OIDC to cloud from CI | **HERE-deep** (stub) + **GAP** OIDC-CI entry | `Security/1` + CiCd |

### D. Infrastructure, cloud, IaC, automation

| Topic | Day-to-day tools / ideas | Status | Home |
|-------|--------------------------|--------|------|
| IaC | Terraform, Pulumi, CloudFormation, Crossplane | **HERE-deep** | `IAC/` |
| OpenTofu | Terraform-compatible fork | **GAP → ENTRY+link** | Under `IAC/Terraform` or short entry |
| Config management / deploy automation | Ansible, Chef, Puppet | **HERE-deep** (scaffold) | `Automation/` + `IAC/` |
| Image baking | Packer | **GAP → ENTRY+link** | `IAC/` or `Servers/` |
| Cloud providers (SE literacy) | AWS, GCP, Azure — regions, IAM, network, managed K8s | **GAP → HERE-plan** | New **`Cloud/`** entry track *or* strong entries under IAC/Cloud-Native — **not** full cloud cert dumps |
| Cost / FinOps literacy | Rightsizing, idle resources, budgets | **GAP → ENTRY+link** | Methodologies or Cloud entry |
| DNS / CDN / global edge | Route53/Cloud DNS, CloudFront/Cloudflare, Fastly | **ENTRY+link** | Handbook short entry → [System-Design fundamentals](https://github.com/thisiskushal31/System-Design-Concepts) (+ Networks for DNS depth) |
| Load balancers | Cloud LB, HAProxy, nginx LB | **HERE-plan** (Servers) + **ENTRY+link** design | `Servers/` + System-Design |
| API gateways | Kong, AWS API GW, Apigee, … | **ENTRY+link** | System-Design + short DevOps entry (when used in delivery) |

### E. Servers, OS, web tier (classic deploy)

| Topic | Day-to-day tools / ideas | Status | Home |
|-------|--------------------------|--------|------|
| Linux / Windows / Unix / macOS | systemd, services, firewall, users | **HERE-deep** | `Operating-Systems/` |
| Host lifecycle + web servers | nginx, Apache httpd, IIS, Caddy, Traefik, HAProxy, Envoy | **HERE-plan** | **New `Servers/`** |
| Deploy automation onto hosts | Ansible roles, CI→SSH/WinRM | **HERE-plan** | `Automation/` ↔ `Servers/` |
| SSH / bastion / SSM | Access patterns | **ENTRY+link** | OS + Security practices |

### F. Containers & Kubernetes

| Topic | Day-to-day tools / ideas | Status | Home |
|-------|--------------------------|--------|------|
| Docker / Podman (operator literacy) | Build, run, compose | **ENTRY+link** (must be obvious from handbook) | Thin Cloud-Native or Servers entry → [Containerization-Deep-Dive](https://github.com/thisiskushal31/Containerization-Deep-Dive) |
| Kubernetes (DevOps angle) | Workloads, services, deploys | **HERE-deep** (scaffold) | `Cloud-Native/Kubernetes` + Containerization for depth |
| Helm | Charts | **HERE-deep** | `Cloud-Native/Helm` |
| Service mesh | Istio, Linkerd | **HERE-deep** | `Cloud-Native/` |
| Managed K8s | EKS/GKE/AKS | **ENTRY+link** | Containerization `Managed-Services` |
| CNCF starter (cert-manager, ExternalDNS, Gateway) | Everyday cluster add-ons | **HERE-plan** | `Cloud-Native/` |

### G. Observability & reliability

| Topic | Day-to-day tools / ideas | Status | Home |
|-------|--------------------------|--------|------|
| Metrics | Prometheus, Grafana, Datadog, New Relic | **HERE-deep** | `Observability/` |
| Logs | Elastic/ELK, Loki (entry if missing) | **HERE-deep** + **GAP** Loki entry if needed | `Observability/` |
| Traces | OpenTelemetry, Jaeger/Tempo literacy | **HERE-deep** (OTel) + **ENTRY** Tempo/Jaeger | `Observability/` |
| SLO/SLI/error budgets | SRE practices | **HERE-deep** (stubs) | Observability + Methodologies |
| Synthetic / smoke after deploy | Scripts, k6, Playwright in CI | **GAP → HERE-plan** | `CiCd/` verify stage |

### H. Data, messaging, caching (SE apps — DevOps must know enough)

| Topic | Day-to-day tools / ideas | Status | Home |
|-------|--------------------------|--------|------|
| Datastores ops literacy | Backups, migrations, connection strings, managed DB | **ENTRY+link** | Handbook entry → [Databases-Deep-Dive](https://github.com/thisiskushal31/Databases-Deep-Dive) |
| Object storage | S3/GCS/Azure Blob | **ENTRY+link** | Databases-Deep-Dive `Blob-Object` |
| Cache / Redis | Session/cache in prod | **ENTRY+link** | Databases + System-Design caching |
| Queues / streams | Kafka, SQS, RabbitMQ | **ENTRY+link** | Kafka *engine* → [DE Systems/Kafka](https://github.com/thisiskushal31/Data-Engineering-Deep-Dive); design-time “do I need a log?” → System-Design messaging |
| Migrations in CI/CD | Flyway, Liquibase, Rails/Django migrate | **GAP → ENTRY+link** | CiCd + Databases |

### I. Application frameworks (how SEs’ apps meet DevOps)

**Do not create `Frameworks/` in this handbook.** The catalog lives in [Tooling-and-Frameworks-Deep-Dive](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive). Old rows below were written before that repo existed.

| Topic | Day-to-day tools / ideas | Status | Home |
|-------|--------------------------|--------|------|
| Frontend | React, Next.js, Angular | **ENTRY+link** | Tooling `Web-Frontend/` (Angular: add folder when you use it) |
| Backend | Spring, Nest, Django, FastAPI, Express, Rails, Laravel, … | **ENTRY+link** | Tooling `Web-Backend/` (Nest/Rails/Laravel: add folder when you use it) |
| Language depth | Go, Python, TS, … | **HERE-deep** | `Languages/` (done / mature) |
| Mobile / desktop | Flutter, RN, native | **ENTRY+link** | Tooling `Mobile/` / `Desktop/` |

### J. Platform engineering & developer experience

| Topic | Day-to-day tools / ideas | Status | Home |
|-------|--------------------------|--------|------|
| IDP / paved road | Backstage, Port, custom portals | **HERE-deep** (platform stub) + **GAP** Backstage entry | `Cloud-Native/3` |
| Internal templates | Cookiecutter, copier, org skeletons | **ENTRY+link** | Platform / Methodologies |
| Local dev parity | Devcontainers, Tilt, Skaffold, compose | **GAP → ENTRY+link** | Cloud-Native / Containers entry |

### K. Explicitly out of DevOps-handbook deep scope (door only)

| Topic | Where instead |
|-------|----------------|
| LeetCode / DSA grind | Datastructures-and-Algorithms |
| Full UI/UX design systems | Not DevOps |
| Full cloud certification dumps | Thin Cloud literacy + vendor docs |
| Product system-design case studies | System-Design-Concepts `Cases/` |

---

## Gaps to schedule (so nothing is “forgotten”)

When work resumes, treat these as **explicit backlog** (entry or folder—not optional fluff):

1. **SE orientation page** in handbook root or Methodologies — “If you are an SE learning DevOps, start here” + matrix link to this plan’s map (or a reader-facing trimmed version).  
2. **Artifact registries** chapter (promote immutable artifacts; don’t rebuild per env).  
3. **Supply-chain literacy** (SBOM, signing/cosign, provenance).  
4. **Cloud provider literacy** track (AWS/GCP/Azure — shared concepts, not three encyclopedias).  
5. **Docker/Podman entry** in handbook that **must** link Containerization-Deep-Dive (today easy to miss).  
6. **Data/Messaging/cache DevOps entries** linking Databases + System-Design.  
7. **DNS/CDN/LB/API gateway** short entries linking System-Design (+ Networks where deep).  
8. **On-call tooling** literacy (PagerDuty/Opsgenie/Grafana OnCall).  
9. **FinOps** short entry.  
10. **OpenTofu / Packer / Kyverno / Loki / Backstage / Azure DevOps** as index entries.  
11. **Synthetic/e2e in verify stage** (k6/Playwright-class).  
12. **DB migrations in pipelines** entry.  
13. **Local dev parity** (devcontainers/compose) entry.  
14. Everything already listed earlier: **Tooling door (not Frameworks/ here)**, **Servers/**, **SAST/DAST chain**, branching, ChatOps, CNCF starter.

---

## Clarifications (terms)

| Term | Meaning |
|------|---------|
| **WAF** | Web Application Firewall — runtime HTTP filter |
| **SAST / DAST / SCA** | Static / dynamic / composition analysis in the delivery path |
| **OWASP ZAP** | Primary open-source DAST example — **in scope** |
| **ChatOps / Slack** | Notifications + optional approve-from-chat — practice literacy |
| **Web server / reverse proxy** | nginx, Apache httpd, Caddy, IIS, Traefik, … |
| **ENTRY+link** | Enough for an SE to act tomorrow + pointer to depth |

---

## Intent (build list — condensed)

1. CNCF / cloud-native everyday tools  
2. Frameworks literacy — **Tooling repo**, door from this handbook  
3. Quality & security tools (Sonar, WAF, existing scanners)  
4. Full CI/CD practices + **security gate chain**  
5. Full delivery path test→deploy→verify→feedback  
6. ChatOps / visibility  
7. Branching practices  
8. **Servers / web servers / host deploy + OS applied + Automation**  
9. **SE completeness:** entries for anything covered in related repos; no silent gaps  
10. **New gaps above** (artifacts, supply chain, cloud literacy, Docker entry, data/CDN doors, …)

---

## DevOps delivery practices (test → deploy and the full loop)

**Goal:** Whole delivery story—not only scanners or only K8s.

```text
Idea / ticket
  → branch / PR (Methodologies)
  → build + unit/integration tests (CiCd)
  → security gates: secrets → SAST → SCA → IaC → image (+ sign/SBOM)
  → publish immutable artifact (registry)
  → provision / update host or cluster (IAC + OS + Automation / Cloud-Native)
  → configure web server / Ingress / TLS (Servers / Cloud-Native)
  → deploy app (systemd / container / K8s)
  → DEV/preview → e2e/smoke/DAST
  → promote → STAGING → (approvals) → PRODUCTION
  → strategy: rolling / blue-green / canary / flags
  → verify: health, metrics, logs, traces (Observability)
  → notify (Slack/Teams) + record release
  → bad path: rollback / forward-fix + incident
  → day-2: patch OS, renew certs, cost/capacity, improve gates
```

Practice catalog, SAST/DAST tables, and Servers/web-server v1 lists from prior revisions remain in force—see sections below for detail still needed at write time.

### Practice catalog (primary homes)

| Practice area | Primary home |
|---------------|--------------|
| CI vs CD vs GitOps; testing in pipeline; artifacts; environments; approvals; strategies; rollback | `CiCd/` + `Methodologies/` |
| Security gate chain | `CiCd/` + `Security/` |
| Host / web-server deploy | **`Servers/`** + `Operating-Systems/` + `Automation/` |
| ChatOps / DORA literacy / branching / incidents | `Methodologies/` |
| Verify after deploy | `CiCd/` ↔ `Observability/` |
| Platform / IDP | `Cloud-Native/3` |

---

## CI/CD security testing (SAST, DAST, full gate chain)

| Stage | Examples | When |
|-------|----------|------|
| Secret scanning | gitleaks, platform scanners | PR / CI |
| SAST / quality | SonarQube, Semgrep, CodeQL | PR / build |
| SCA | Snyk, Trivy, Dependabot | PR / build |
| IaC / policy | Checkov, OPA, Kyverno | PR / build |
| Image scan | Trivy, Snyk Container | After image build |
| Sign / SBOM | cosign, Syft | Before promote |
| Quality gate | Sonar gate, coverage floors | PR / promote |
| DAST | **OWASP ZAP** | After deploy to test/preview |
| WAF | Vendor/cloud WAF | Continuous |
| Pen test | Periodic door | Release / periodic |

**Rule:** Teach the **chain** in `CiCd/`; teach each **scanner** in `Security/`.

---

## Servers, web servers, OS, deploy automation

**Reuse:** `Operating-Systems/` (deep), `Automation/` (Ansible/Chef/Puppet stubs), `IAC/` (provision), Containerization-Deep-Dive (containers).

**New:** `Servers/` — one folder per product.

**v1 must-have:** nginx, Apache httpd, IIS  
**v1 strong add:** Caddy, Traefik, HAProxy, Envoy  

Distinguish: proxy vs app upstream vs K8s Ingress vs WAF.

---

## Inventory snapshot

| Area | Today |
|------|--------|
| Methodologies / CiCd / IAC / Automation / Cloud-Native / Observability / Security | Scaffolded or partial — **fill** |
| Operating-Systems / Languages | Strong — **cross-link** for deploy & SE paths |
| Servers / Cloud literacy / artifact+supply-chain entries | **Planned / gaps** (frameworks → Tooling) |
| Related deep-dives | **Link from SE entries** — do not duplicate |

---

## Recommended lanes

| Lane | Focus |
|------|--------|
| **A — Ship & collaborate** (default) | Methodologies → CiCd (path + gates) → Servers+Automation → Security tools → Tooling door → CNCF → **SE gap entries** |
| **B** | CNCF / K8s first |
| **C** | Application frameworks first — in [Tooling-and-Frameworks-Deep-Dive](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive), not here |
| **D** | Servers / classic host deploy first |
| **E — SE on-ramp first** | Write SE orientation + ENTRY+link matrix into handbook, then A |

---

## CNCF starter (v1)

| Tier | Tools |
|------|-------|
| Core | Kubernetes, Helm |
| Delivery | Argo CD and/or Flux |
| Observability | Prometheus, Grafana, OpenTelemetry |
| Next | cert-manager, ExternalDNS, Ingress/Gateway, Cilium (pick 2–3) |

---

## Frameworks v1 (related repo)

Write these in [Tooling-and-Frameworks-Deep-Dive](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive). This handbook only keeps the deploy/observe lens.

**FE:** React, Next.js (Angular: add in Tooling when used)  
**BE:** FastAPI, Spring, Express exist as stubs; Nest / Rails / Laravel — add in Tooling when used  
**Lens here:** what DevOps must configure / build / deploy / observe

---

## Kickoff checklist

- [ ] Confirm lane: **A** / B / C / D / **E (SE on-ramp)**  
- [ ] Publish reader-facing “SE learning DevOps — start here” that mirrors the completeness map  
- [ ] Confirm every **GAP** row gets an owner (entry vs folder) before deep tool prose  
- [ ] Confirm branching house default  
- [ ] Confirm Servers v1 list + Automation primary (Ansible …)  
- [ ] Confirm CI security track (SAST/DAST/SCA/secrets/IaC/image/WAF/sign-SBOM)  
- [ ] Confirm SonarQube + ZAP as primary examples  
- [ ] Confirm artifact registry + supply-chain chapters in CiCd/Security  
- [ ] Confirm Cloud literacy approach (`Cloud/` vs entries under IAC)  
- [ ] Confirm Docker/Podman handbook entry → Containerization-Deep-Dive  
- [ ] Confirm data/Messaging/CDN/LB entries → Databases + System-Design + Networks  
- [x] `Servers/` and `Cloud/` exist; frameworks live in Tooling — do not add `Frameworks/` here  
- [ ] Keep Languages = languages; OS = OS; deep dives = deep dives  

---

## Out of scope for this plan file

- Writing all chapter bodies now  
- Duplicating Networks / Containers / Databases / System-Design inside this repo  
- Full cloud certification curricula  
- Exhaustive CNCF landscape dump  
- DSA as a DevOps requirement  

---

## Related entry points

- [Handbook README](./README.md)  
- [Methodologies](./Methodologies/README.md) · [CiCd](./CiCd/README.md) · [IAC](./IAC/README.md) · [Automation](./Automation/README.md)  
- [Cloud-Native](./Cloud-Native/README.md) · [Observability](./Observability/README.md) · [Security](./Security/README.md)  
- [Operating-Systems](./Operating-Systems/README.md) · [Languages](./Languages/README.md)  
- Related repos: [Networks](https://github.com/thisiskushal31/Networks-Deep-Dive) · [Containers](https://github.com/thisiskushal31/Containerization-Deep-Dive) · [Databases](https://github.com/thisiskushal31/Databases-Deep-Dive) · [System Design](https://github.com/thisiskushal31/System-Design-Concepts) · [Commands](https://github.com/thisiskushal31/Commands-and-Cheatsheets)

---

## Containerization-Deep-Dive

Public intro: [Deep-Dives/Containerization-Deep-Dive/README.md](../../Deep-Dives/Containerization-Deep-Dive/README.md)

### Start here

# Start here — Containerization Deep Dive

[← Back to README](./README.md) · Write order

*(Content TBD — stub created August 2026)*

**Why a security engineer opens this:** workloads run in containers. Escape, image supply chain, and NetworkPolicy live here — not as a second Security book.

## Planned coverage

- Who this repo is for (platform engineer, backend SE moving to K8s, DevOps, security engineer)
- **Learning path** (copy from root README, add checkboxes):
  - [ ] [Containerization-Basic](./Containerization-Basic/README.md) then [Runtimes/Docker](./Runtimes/Docker/README.md). CLIs (kubectl, k9s, Helm) → [Tooling Containers](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive/tree/main/Containers)
  - [ ] Containerization-Basic (4 topics)
  - [ ] Runtimes/Docker (+ optional podman)
  - [ ] Orchestration/Kubernetes
  - [ ] Managed-Services (pick your cloud)
  - [ ] Local-Dev + Serverless-Containers (new sections)
- When to read **DevOps-Handbook** vs this repo (delivery vs container/K8s depth)
- Related repos → [README](./README.md)

## You already have content here

Most of `Containerization-Basic/`, `Runtimes/`, `Orchestration/Kubernetes`, and `Managed-Services/` are **written**. Start gaps from Write order step 3 onward unless you are a beginner — then follow root learning path.

## Checklist before marking done

- [ ] Checkbox learning path for monthly tracking
- [ ] Related-repo pointers on README
- [ ] One diagram: VM → container → orchestrator → managed K8s

### Write order

# Containerization Deep Dive — content write order

**Created:** August 2026  
**Repo #2** in the engineering knowledge base (after [DevOps-Handbook](../DevOps-Handbook/README.md)).

**Unlike DevOps-Handbook:** this repo already has **~66 topic files with real content**. Do not rewrite what exists — **fill gaps** below and deepen thin areas.

---

## What is already solid (expand only if you find holes)

| Section | Files | Status |
|---------|-------|--------|
| [Containerization-Basic/](./Containerization-Basic/README.md) | 4 topics | **Written** — concepts, images, net/storage, security basics |
| [Runtimes/Docker/](./Runtimes/Docker/README.md) | 5 topics | **Written** — install through workshop |
| [Runtimes/Podman/](./Runtimes/Podman/README.md) | 5 topics | **Written** |
| [Orchestration/Kubernetes/](./Orchestration/Kubernetes/README.md) | 5 topics | **Written** — getting started → production |
| [Orchestration/OpenShift/](./Orchestration/OpenShift/README.md) | 10 topics | **Written** |
| [Orchestration/Swarm/](./Orchestration/Swarm/README.md) | 6 topics | **Written** |
| [Managed-Services/GKE|eks|aks/](./Managed-Services/README.md) | 5+5+5 topics | **Written** |
| [Managed-Services/](./Managed-Services/1_Overview_When_to_Use.md) | overview + turnkey | **Written** (turnkey = index only — see [Local-Dev/](./Local-Dev/README.md)) |

---

## Lane B — recommended fill order (gaps first)

| Step | Location | Why |
|------|----------|-----|
| 1 | Start here | On-ramp + related-repo matrix |
| 2 | [README](./README.md) | Doors to DevOps, Networks, Security, System Design |
| 3 | [Local-Dev/](./Local-Dev/README.md) | kind, minikube, k3d, Tilt/Skaffold — expand turnkey one-liners |
| 4 | [Runtimes/Containerd/](./Runtimes/Containerd/README.md) + [CRI-O/](./Runtimes/CRI-O/README.md) | What K8s actually runs under Docker |
| 5 | [Serverless-Containers/](./Serverless-Containers/README.md) | Cloud Run, Fargate, Azure Container Apps |
| 6 | [Security-Advanced/](./Security-Advanced/README.md) | Beyond basics → link Security-Deep-Dive |
| 7 | [Networking-Advanced/](./Networking-Advanced/README.md) | Cilium/eBPF, NetworkPolicy depth → link Networks |
| 8 | [GitOps-Packaging/](./GitOps-Packaging/README.md) | Helm, Kustomize, GitOps entry → link DevOps CiCd |
| 9 | [Runtimes/Buildah-Skopeo/](./Runtimes/Buildah-Skopeo/README.md) | Daemonless image build/push |
| 10 | [Orchestration/Nomad/](./Orchestration/Nomad/README.md) | Optional second orchestrator |
| 11 | Deepen existing | K8s `5-production` add GitOps/admission; GKE add Cloud Run cross-link |

---

## Related repos (link, do not duplicate)

| Domain | Repository | Entry file |
|--------|------------|------------|
| Delivery / CI / scanners | [DevOps-Handbook](https://github.com/thisiskushal31/DevOps-Handbook) | [DevOps Handbook](../DevOps-Handbook/README.md) |
| Network depth | [Networks-Deep-Dive](https://github.com/thisiskushal31/Networks-Deep-Dive) | [Networks Deep Dive](../Networks-Deep-Dive/README.md) |
| Full cyber program | [Security-Deep-Dive](https://github.com/thisiskushal31/Security-Deep-Dive) | [Security Deep Dive](../Security-Deep-Dive/README.md) |
| LB, CDN, design patterns | [System-Design-Concepts](https://github.com/thisiskushal31/System-Design-Concepts) | [System Design Concepts](../System-Design-Concepts/README.md) |
| Commands | [Commands-and-Cheatsheets](https://github.com/thisiskushal31/Commands-and-Cheatsheets) | root README |

DevOps handbook points **in** here → [DevOps Handbook](../DevOps-Handbook/README.md).

---

## Done when (repo #2)

- [ ] Every **stub** folder has at least one filled topic (not just README)
- [ ] `Start here` links learning path + related repos
- [ ] Serverless + Local-Dev sections exist (today: gaps)
- [ ] containerd/CRI-O documented for K8s operators
- [ ] Security-Advanced points to Security-Deep-Dive for AppSec/IR depth

---

## Marking topics complete

Same as DevOps-Handbook: replace `*(Content TBD)*`, satisfy **Planned coverage** bullets, check **Checklist before marking done**, optional `- [x]` in section README.

---

## Networks-Deep-Dive

Public intro: [Deep-Dives/Networks-Deep-Dive/README.md](../../Deep-Dives/Networks-Deep-Dive/README.md)

### Start here

# Start here — Networks Deep Dive

[← README](./README.md) · Write order

*(Content TBD — stub created August 2026)*

**Why a security engineer opens this:** Nmap, TLS, and Wireshark only make sense if you can read the wire. This is that book.

## Planned coverage

- Who this repo is for (platform engineer, SRE, security engineer building network foundation, system design interview prep with wire-level depth)
- **Learning path** (checkboxes — copy/adapt from root README):
  - [ ] CLIs: [Tooling Network-Utilities](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive/tree/main/Network-Utilities) (ping, dig, curl). Nmap *install* → [Tooling Security/Nmap](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive/tree/main/Security/Reconnaissance/Nmap)
  - [ ] [Foundations/](./Foundations/README.md) — L1–L3, IP, subnetting, VLANs
  - [ ] [Transport/](./Transport/README.md) — TCP/UDP internals, NAT, performance
  - [ ] [Routing-Switching/](./Routing-Switching/README.md) — OSPF/BGP, DC spine-leaf
  - [ ] [Services/](./Services/README.md) — DNS, HTTP/TLS, load balancing
  - [ ] [Security/](./Security/README.md) — firewalls, VPN, NIDS, blue team network angle
  - [ ] [Cloud-Native/](./Cloud-Native/README.md) — VPC, K8s networking, Cilium/eBPF
  - [ ] [Observability/](./Observability/README.md) — tcpdump, Wireshark, flow logs
  - [ ] [Labs/](./Labs/README.md) + [Labs-Expanded/](./Labs-Expanded/README.md) — hands-on
  - [ ] [Home-Lab/](./Home-Lab/README.md) — build a safe practice network
  - [ ] [Advanced/](./Advanced/README.md) — QUIC, wireless, enterprise Cisco
- When to read **Security/** here vs **Security-Deep-Dive** (network layer vs full cyber program)
- Related repos → [README](./README.md)

## You already have content here

Most of Foundations through Observability is **written** (~60 topic files). Start from step 2 in Write order unless you are new to networking — then follow the checkbox path above from Foundations.

## Checklist before marking done

- [ ] Checkbox learning path for monthly tracking
- [ ] Related-repo pointers on README
- [ ] One diagram: home lab → enterprise → cloud VPC (ASCII or Assets/)

### Write order

# Networks Deep Dive — content write order

**Created:** August 2026  
**Repo #4** after [DevOps-Handbook](../DevOps-Handbook/README.md), [Containerization-Deep-Dive](../Containerization-Deep-Dive/README.md), and [Databases-Deep-Dive](../Databases-Deep-Dive/README.md).

**Unlike DevOps/Databases:** this repo already has **~66 topic files with real depth** (L1–L7, security, cloud-native, observability). Do not rewrite — **deepen short notes** and **expand labs**.

---

## What is already solid (maintain only)

| Section | Topics | Status |
|---------|--------|--------|
| [Foundations/](./Foundations/README.md) | 5 | **Written** — OSI/TCP/IP, L1–L3, IP/ICMP/ARP |
| [Transport/](./Transport/README.md) | 6 | **Written** — UDP/TCP, NAT, sockets, performance |
| [Routing-Switching/](./Routing-Switching/README.md) | 5 | **Written** — OSPF/BGP, MPLS, DC design |
| [Services/](./Services/README.md) | 8 | **Written** — DNS, HTTP/TLS, LB, DHCP |
| [Security/](./Security/README.md) | 10 | **Written** — network-layer security (feeds Security-Deep-Dive capstone) |
| [Cloud-Native/](./Cloud-Native/README.md) | 4 | **Written** — VPC, K8s/Cilium, SDN |
| [Observability/](./Observability/README.md) | 6 | **Written** — capture, Wireshark, QoS, NetOps |
| [Advanced/](./Advanced/README.md) | 5 | **Partial** — several files &lt;50 lines — deepen before new folders |
| [Labs/](./Labs/README.md) | 5 | **Partial** — index strong; walkthrough depth thin |

---

## Lane D — recommended fill order (gaps first)

| Step | Location | Why |
|------|----------|-----|
| 1 | Start here + [README](./README.md) | On-ramp + related-repo matrix |
| 2 | Advanced + Labs short notes | Deepen short Advanced/Labs files before new folders |
| 3 | [Home-Lab/](./Home-Lab/README.md) | Guided home/SOHO lab path → links [Labs/4](./Labs/4_Labs_Vms.md) + Routing scale spectrum |
| 4 | [Labs-Expanded/](./Labs-Expanded/README.md) | Step-by-step captures and validation labs |
| 5 | [Service-Mesh/](./Service-Mesh/README.md) | Envoy/Istio/mTLS east–west — complements [Cloud-Native/2](./Cloud-Native/2_Docker_Kubernetes.md) |
| 6 | Deepen [Advanced/](./Advanced/README.md) | TLS 0-RTT, QUIC/DC transport, wireless (thin today) |
| 7 | Deepen [Labs/](./Labs/README.md) | Code examples, CTF pointers, VM security labs |
| 8 | [Cloud-Native/4_Iot_5g.md](./Cloud-Native/4_Iot_5g.md) | Optional — only if IoT/5G slice on your path |

---

## Related repos (link, do not duplicate)

| Domain | Repository | Entry file |
|--------|------------|------------|
| Delivery, cloud VPC ops, DevSecOps | [DevOps-Handbook](https://github.com/thisiskushal31/DevOps-Handbook) | [DevOps Handbook](../DevOps-Handbook/README.md) |
| Container/K8s operator view | [Containerization-Deep-Dive](https://github.com/thisiskushal31/Containerization-Deep-Dive) | [Containerization Deep Dive](../Containerization-Deep-Dive/README.md) |
| Holistic cyber program (capstone) | [Security-Deep-Dive](https://github.com/thisiskushal31/Security-Deep-Dive) | [Security Deep Dive](../Security-Deep-Dive/README.md) |
| LB, CDN, design cases | [System-Design-Concepts](https://github.com/thisiskushal31/System-Design-Concepts) | [System Design Concepts](../System-Design-Concepts/README.md) |
| Commands | [Commands-and-Cheatsheets](https://github.com/thisiskushal31/Commands-and-Cheatsheets) | root README |

**Inbound links:** DevOps [DNS_CDN_And_Load_Balancers](../DevOps-Handbook/README.md) · Containerization [Networking-Advanced](../Containerization-Deep-Dive/Networking-Advanced/README.md) · [Networks_Deep_Dive](../Containerization-Deep-Dive/README.md)

**Overlap rule:** This repo owns **packet path, routing, firewalls, VPN, NIDS, TLS at wire level**. [Security-Deep-Dive](https://github.com/thisiskushal31/Security-Deep-Dive) owns **GRC, AppSec, IR, offensive methodology, cloud posture** — link here for L3–L7 network angle only.

---

## Repo #4 done when

- [ ] Every **stub** folder has at least one filled topic (not just README)
- [ ] Short Advanced/Labs notes expanded to full-depth style
- [ ] `Start here` has checkbox learning path for monthly tracking
- [ ] labs-expanded has ≥2 runnable walkthroughs with copy-paste commands
- [ ] Service-Mesh/ links Containerization Networking-Advanced without duplicating CNI install guides

---

## Marking topics complete

Same convention as other repos: replace `*(Content TBD)*`, satisfy **Planned coverage** bullets, check **Checklist before marking done**, optional `- [x]` in section README.


---

## Databases-Deep-Dive

Public intro: [Deep-Dives/Databases-Deep-Dive/README.md](../../Deep-Dives/Databases-Deep-Dive/README.md)

### Start here

# Start here — Databases Deep Dive

[← README](./README.md) · Write order · Engines to fill

*(Content TBD — stub created August 2026)*

**Why a security engineer opens this:** data is the prize. Engines, injection surfaces, and encryption-at-rest live here.

## Planned coverage

- Who this repo is for (DBA, backend SE, data engineer, architect, security engineer)
- **10 database types** table with checkboxes (link root README)
- Learning paths:
  - **Clients:** [Tooling Database-Clients](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive/tree/main/Database-Clients) (psql, sqlite3, DBeaver). **Migrations:** [Schema-Migration](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive/tree/main/Schema-Migration)
  - **Foundations:** [Concepts/DBMS-Fundamentals/](./Concepts/DBMS-Fundamentals/README.md)
  - **Relational track:** MySQL, PostgreSQL, or [DuckDB](https://github.com/thisiskushal31/Databases-Deep-Dive/tree/main/Relational/duckdb)
  - **NoSQL track:** pick type folder from root README
  - **Cloud:** [Cloud-Managed/](./Cloud-Managed/README.md)
  - **AI/RAG track:** [Vector/Qdrant/](./Vector/Qdrant/README.md) (priority) then [pgvector](./Vector/Pgvector/README.md) → retrieval job in DS-AI
- When to read **blog series** vs **this repo** (strategy vs implementation)
- Related repos → [README](./README.md)

## Already written (start reading, not writing)

MySQL, PostgreSQL, DuckDB (embedded OLAP), MongoDB, Redis, Aerospike, Elasticsearch, DBMS fundamentals, cloud-managed overview.

## Checklist before marking done

- [ ] Checkbox paths for monthly learning
- [ ] Related-repo pointers on README

### Write order

# Databases Deep Dive — content write order

**Created:** August 2026  
**Repo #3** after [DevOps-Handbook](../DevOps-Handbook/README.md) and [Containerization-Deep-Dive](../Containerization-Deep-Dive/README.md).

---

## What is already solid (maintain / fix links only)

| Section | Status |
|---------|--------|
| [Relational/MySQL/](./Relational/MySQL/README.md) | **Written** (7 topics) + blog series |
| [Relational/PostgreSQL/](./Relational/PostgreSQL/README.md) | **Written** (10 topics) |
| [Document/MongoDB/](./Document/MongoDB/README.md) | **Written** (7 topics) + blog series |
| [Key-Value/Redis/](./Key-Value/Redis/README.md) | **Written** (7 topics) + blog series |
| [Key-Value/Aerospike/](./Key-Value/Aerospike/README.md) | **Written** (7 topics) + blog series |
| [Search-Engine/Elasticsearch/](./Search-Engine/Elasticsearch/README.md) | **Written** (7 topics) + blog |
| [Concepts/DBMS-Fundamentals/](./Concepts/DBMS-Fundamentals/README.md) | **Written** (7 topics) |
| [Cloud-Managed/README.md](./Cloud-Managed/README.md) | **Written** (single long guide) |
| [Concepts/README.md](./Concepts/README.md) | **Written** — fix stale links to old `NoSQL/*.md` paths (see step 0) |

**~103 markdown files today.** Majority of **engine depth** lives in 6 engines above.

---

## Lane C — recommended fill order

| Step | Focus | Why |
|------|--------|-----|
| 0 | Fix [Concepts/README.md](./Concepts/README.md) broken links | Points to removed `NoSQL/1-mysql.md` paths |
| 1 | Start here + [README](./README.md) | Navigation + related repos |
| 2 | **Vector** — [Qdrant](./Vector/Qdrant/README.md) first (production priority), then [pgvector](./Vector/Pgvector/README.md), then Weaviate/Milvus/Pinecone | RAG / DS-AI path — retrieval *job* stays in DS-AI |
| 3 | **Blob/object** — [GCS/](./Blob-Object/GCS/README.md), [S3/](./Blob-Object/S3/README.md), MinIO | DE + backups + static assets |
| 4 | [Data-Platform/](./Data-Platform/README.md) | Pipelines, migrations, ops at platform layer → DE repo |
| 5 | **Wide-column** — Cassandra, ScyllaDB | Scale-out patterns |
| 6 | **Key-value** — DynamoDB | Cloud-native apps |
| 7 | **Relational** — SQLite, SQL Server, Oracle (by need) |
| 8 | Graph, time-series, search (Solr, Meilisearch), cache (Memcached, Hazelcast) |
| 9 | Split [Cloud-Managed/](./Cloud-Managed/README.md) into topic files (optional refactor) |

Track per-engine progress in Engines to fill below.

---

## Related repos

| Domain | Repository | Entry |
|--------|------------|-------|
| Data engineering pipelines | [Data-Engineering-Deep-Dive](https://github.com/thisiskushal31/Data-Engineering-Deep-Dive) | [Data Engineering Deep Dive](../Data-Engineering-Deep-Dive/README.md) |
| ML / RAG / embeddings science | [Data-Science-AI-Deep-Dive](https://github.com/thisiskushal31/Data-Science-AI-Deep-Dive) | [Data Science AI Deep Dive](../Data-Science-AI-Deep-Dive/README.md) |
| System design (caching, sharding cases) | [System-Design-Concepts](https://github.com/thisiskushal31/System-Design-Concepts) | [System Design Concepts](../System-Design-Concepts/README.md) |
| Delivery / managed DB ops | [DevOps-Handbook](https://github.com/thisiskushal31/DevOps-Handbook) | [DevOps Handbook](../DevOps-Handbook/README.md) |
| Blog narratives | [blog](https://thisiskushal31.github.io/blog/) | linked from root README |

---

## Stub convention (planned engines)

Each **📁 planned** engine README now lists:

- **Planned coverage** bullets  
- **Topic files** table (`1-*.md`, …)  
- **Checklist before marking done**  

Topic files marked `*(Content TBD)*` — fill using same style as MySQL/PostgreSQL topics.

---

## Repo #3 done when

- [ ] All 📁 engines have ≥1 filled topic (not just README)
- [ ] pgvector + GCS/S3 v1 complete (your GCP + RAG path)
- [ ] Concepts/README links fixed
- [ ] Data-Platform/ links DE repo without duplicating pipeline authoring

### Engines to fill

# Engines to fill

**Status:** 📁 = stub scaffold only · ✅ = multi-topic deep dive exists

Update `- [ ]` → `- [x]` when an engine has **all** topic files in its README filled (not TBD).

## ✅ Complete deep dives

- [x] MySQL — [Relational/MySQL/](./Relational/MySQL/README.md)
- [x] PostgreSQL — [Relational/PostgreSQL/](./Relational/PostgreSQL/README.md)
- [x] DuckDB — [Relational/DuckDB/](./Relational/DuckDB/README.md) (embedded OLAP; DE pointer only)
- [x] MongoDB — [Document/MongoDB/](./Document/MongoDB/README.md)
- [x] Redis — [Key-Value/Redis/](./Key-Value/Redis/README.md)
- [x] Aerospike — [Key-Value/Aerospike/](./Key-Value/Aerospike/README.md)
- [x] Elasticsearch — [Search-Engine/Elasticsearch/](./Search-Engine/Elasticsearch/README.md)

## 📁 Relational (stubs)

- [ ] SQLite — [Relational/SQLite/](./Relational/SQLite/README.md)
- [ ] SQL Server — [Relational/SQL-Server/](./Relational/SQL-Server/README.md)
- [ ] Oracle — [Relational/Oracle/](./Relational/Oracle/README.md)

## 📁 Document (stubs)

- [ ] CouchDB — [Document/CouchDB/](./Document/CouchDB/README.md)
- [ ] Firestore — [Document/Firestore/](./Document/Firestore/README.md)

## 📁 Key-value (stubs)

- [ ] DynamoDB — [Key-Value/DynamoDB/](./Key-Value/DynamoDB/README.md)

Memcached is **not** here — [Cache/memcached](./Cache/Memcached/README.md). `Key-Value/Memcached` is a pointer.

## 📁 Wide-column (stubs)

- [ ] Cassandra — [Wide-Column/Cassandra/](./Wide-Column/Cassandra/README.md)
- [ ] HBase — [Wide-Column/HBase/](./Wide-Column/HBase/README.md)
- [ ] ScyllaDB — [Wide-Column/ScyllaDB/](./Wide-Column/ScyllaDB/README.md)
- [ ] Bigtable — [Wide-Column/Bigtable/](./Wide-Column/Bigtable/README.md)

## 📁 Graph (stubs)

- [ ] Neo4j — [Graph/Neo4j/](./Graph/Neo4j/README.md)
- [ ] Neptune — [Graph/Neptune/](./Graph/Neptune/README.md)
- [ ] ArangoDB — [Graph/ArangoDB/](./Graph/ArangoDB/README.md)

## 📁 Time-series (stubs)

- [ ] InfluxDB — [Time-Series/InfluxDB/](./Time-Series/InfluxDB/README.md)
- [ ] TimescaleDB — [Time-Series/TimescaleDB/](./Time-Series/TimescaleDB/README.md)
- [ ] Prometheus — [Time-Series/Prometheus/](./Time-Series/Prometheus/README.md)

## 📁 Search (stubs)

- [ ] Solr — [Search-Engine/Solr/](./Search-Engine/Solr/README.md)
- [ ] Meilisearch — [Search-Engine/Meilisearch/](./Search-Engine/Meilisearch/README.md)

## 📁 Cache (stubs)

- [ ] Memcached — [Cache/Memcached/](./Cache/Memcached/README.md)
- [ ] Hazelcast — [Cache/Hazelcast/](./Cache/Hazelcast/README.md)

## 📁 Blob/object (stubs) — **priority**

- [ ] Amazon S3 — [Blob-Object/S3/](./Blob-Object/S3/README.md)
- [ ] Google Cloud Storage — [Blob-Object/GCS/](./Blob-Object/GCS/README.md)
- [ ] Azure Blob — [Blob-Object/Azure-Blob/](./Blob-Object/Azure-Blob/README.md)
- [ ] MinIO — [Blob-Object/MinIO/](./Blob-Object/MinIO/README.md)

## 📁 Vector (stubs) — **priority**

- [ ] pgvector — [Vector/Pgvector/](./Vector/Pgvector/README.md)
- [ ] Weaviate — [Vector/Weaviate/](./Vector/Weaviate/README.md)
- [ ] Milvus — [Vector/Milvus/](./Vector/Milvus/README.md)
- [ ] Pinecone — [Vector/Pinecone/](./Vector/Pinecone/README.md)
- [ ] Qdrant — [Vector/Qdrant/](./Vector/Qdrant/README.md) — **priority (production)**

## Priority order (v1)

1. Qdrant (production) → 2. pgvector → 3. GCS → 4. S3 → 5. DynamoDB → 6. Cassandra

---

## System-Design-Concepts

Public intro: [Deep-Dives/System-Design-Concepts/README.md](../../Deep-Dives/System-Design-Concepts/README.md)

### Start here

# Start here — System Design Concepts

[← README](./README.md) · Write order · Cases to fill

*(Content TBD — stub created August 2026)*

## Planned coverage

**Why a security engineer opens this:** you threat-model a *product*, not a tool. Abuse cases and trade-offs start in HLD.

- Who this repo is for (backend SE, architect path, interview prep, security engineer reading a design)
- **Learning path** (checkboxes):
  - [ ] Open [Tooling Diagramming](../Tooling-and-Frameworks-Deep-Dive/Diagramming/README.md) (Mermaid, C4) **while** you read — drawing is not the design
  - [ ] [Fundamentals/0_Requirements_and_Constraints.md](./Fundamentals/0_Requirements_and_Constraints.md)
  - [ ] [Fundamentals/1_Intro_and_Approach.md](./Fundamentals/1_Intro_and_Approach.md) + [12_HLD_and_LLD.md](./Fundamentals/12_HLD_and_LLD.md)
  - [ ] [Fundamentals/](./Fundamentals/README.md) — DNS, CDN, LB, scaling, APIs
  - [ ] [Databases/](./Databases/README.md) — selection, sharding, replication, CAP
  - [ ] [Caching/](./Caching/README.md) + [Messaging/](./Messaging/README.md)
  - [ ] [Consistency/](./Consistency/README.md) + [Availability/](./Availability/README.md)
  - [ ] [Patterns/](./Patterns/README.md) + [Performance/](./Performance/README.md)
  - [ ] [Security/](./Security/README.md) + [Security-Tradeoffs/](./Security-Tradeoffs/README.md)
  - [ ] [Observability/](./Observability/README.md)
  - [ ] [Failure-Modes/](./Failure-Modes/README.md) — what breaks in production
  - [ ] [Cases/](./Cases/README.md) — product designs end-to-end
- When to read **Networks** (wire depth) vs **this repo** (component trade-offs)
- When to read **Databases-Deep-Dive** (engine ops) vs **Databases/** here (design selection)
- Related repos → [README](./README.md)

## Already written (start reading)

Most component folders have content; **Observability/** and several **Fundamentals/** files are still short — deepen those before new folders. Cases 1–6 exist; expand with failure sections per Write order step 6.

## Checklist before marking done

- [ ] Checkbox paths for monthly tracking
- [ ] Related-repo pointers on README
- [ ] One diagram: requirements → HLD → components → bottlenecks → failure modes

### Write order

# System Design Concepts — content write order

**Created:** August 2026  
**Repo #5** after [DevOps-Handbook](../DevOps-Handbook/README.md), [Containerization-Deep-Dive](../Containerization-Deep-Dive/README.md), [Databases-Deep-Dive](../Databases-Deep-Dive/README.md), and [Networks-Deep-Dive](../Networks-Deep-Dive/README.md).

**Unlike DevOps/Networks:** this repo already has **~119 topic files** across fundamentals, components, and cases. Do not rewrite — **deepen short notes**, add **failure modes**, expand **cases**, link **security trade-offs**.

---

## What is already solid (maintain only)

| Section | Topics | Status |
|---------|--------|--------|
| [Fundamentals/](./Fundamentals/README.md) | 19 | **Written** — several files still short — deepen before new folders |
| [Databases/](./Databases/README.md) | 12 + taxonomy | **Written** — engine depth → [Databases-Deep-Dive](https://github.com/thisiskushal31/Databases-Deep-Dive) |
| [Caching/](./Caching/README.md) | 9 | **Written** — strategy files vary in depth |
| [Messaging/](./Messaging/README.md) | 8 | **Written** |
| [Patterns/](./Patterns/README.md) | 8 | **Written** |
| [Consistency/](./Consistency/README.md) | 6 | **Written** — overlaps CAP with Databases/ (intentional cross-link) |
| [Availability/](./Availability/README.md) | 9 | **Written** — several thin |
| [Storage/](./Storage/README.md) | 5 | **Written** — thin |
| [Performance/](./Performance/README.md) | 4 | **Written** |
| [Security/](./Security/README.md) | 7 | **Written** — design-time security; capstone → Security-Deep-Dive |
| [Observability/](./Observability/README.md) | 9 | **Written** — many files need depth |
| [Cases/](./Cases/README.md) | 6 cases + index | **Partial** — expand failure sections + Cases to fill |

---

## Lane E — recommended fill order (gaps first)

| Step | Location | Why |
|------|----------|-----|
| 1 | Start here + [README](./README.md) | On-ramp + related-repo matrix |
| 2 | Fundamentals + Observability | Deepen short notes (observability, availability, fundamentals) first |
| 3 | [Failure-Modes/](./Failure-Modes/README.md) | Design-time failure analysis — ecosystem gap |
| 4 | [Security-Tradeoffs/](./Security-Tradeoffs/README.md) | Link [Security/](./Security/README.md) → Security-Deep-Dive without duplicating |
| 5 | [Primer-Gaps/](./Primer-Gaps/README.md) | **Industry gaps** — gossip, Bloom, 2PC/saga, search, RAG — see Industry coverage matrix |
| 6 | [Cases/](./Cases/README.md) + Cases to fill | Cases 1–17; deepen existing + fill stubs |
| 7 | Deepen [Cases/1–6](./Cases/README.md) | Add **Failure modes**, **Capacity math**, **What breaks first** sections |
| 7 | [Fundamentals/12_HLD_and_LLD.md](./Fundamentals/12_HLD_and_LLD.md) | Interview framework + back-of-envelope math |
| 8 | Cross-link wire depth | DNS/LB/TLS → [Networks-Deep-Dive](../Networks-Deep-Dive/README.md) |

---

## Related repos (link, do not duplicate)

| Domain | Repository | Entry file |
|--------|------------|------------|
| Wire-level DNS, HTTP, TLS, LB | [Networks-Deep-Dive](https://github.com/thisiskushal31/Networks-Deep-Dive) | [Networks Deep Dive](../Networks-Deep-Dive/README.md) |
| Engine ops, SQL tuning depth | [Databases-Deep-Dive](https://github.com/thisiskushal31/Databases-Deep-Dive) | [Databases Deep Dive](../Databases-Deep-Dive/README.md) |
| Delivery, SLOs, observability stack | [DevOps-Handbook](https://github.com/thisiskushal31/DevOps-Handbook) | [DevOps Handbook](../DevOps-Handbook/README.md) |
| Holistic cyber program (capstone) | [Security-Deep-Dive](https://github.com/thisiskushal31/Security-Deep-Dive) | [Security Deep Dive](../Security-Deep-Dive/README.md) |
| Algorithms for design interviews | [Datastructures-and-Algorithms](https://github.com/thisiskushal31/Datastructures-and-Algorithms) | [Datastructures and Algorithms](../Datastructures-and-Algorithms/README.md) |
| K8s scale, serverless containers | [Containerization-Deep-Dive](https://github.com/thisiskushal31/Containerization-Deep-Dive) | [Containerization Deep Dive](../Containerization-Deep-Dive/README.md) |

**Inbound links:** DevOps [DNS_CDN_And_Load_Balancers](../DevOps-Handbook/README.md) · Networks [System_Design](../Networks-Deep-Dive/README.md) · Databases [System_Design](../Databases-Deep-Dive/README.md)

**Overlap rule:** This repo owns **trade-offs at architecture level** (CAP, sharding, caching, case studies). Related repos own **implementation and operations depth**.

---

## Repo #5 done when

- [ ] Every **stub** folder has ≥1 filled topic (not just README)
- [ ] Industry coverage matrix — no ❌ rows left without stub or related-repo link
- [ ] Priority short Fundamentals/Observability/Security notes expanded to full style
- [ ] [Primer-Gaps/](./Primer-Gaps/README.md) — 12 industry topics filled
- [ ] Cases 1–17 have **Failure modes** + capacity sketch where applicable

---

## Marking topics complete

Replace `*(Content TBD)*`, satisfy **Planned coverage** + **Checklist before marking done**, optional `- [x]` in section README or Cases to fill below.

### Industry coverage matrix

# System Design — industry coverage matrix

**Purpose:** Map **2025–2026 industry checklists** (DesignGurus, FAANG prep guides, CalibreOS HLD rubric) to **this repo** so nothing is forgotten. Update when you fill a gap.

**Legend:** ✅ covered (adequate depth) · ⚠️ partial / thin · 📁 stub only · ❌ missing · 🔗 related repo owns depth

Benchmark sources (August 2026): [DesignGurus 2026 rubric](https://www.designgurus.io/system-design-interview), [CalibreOS HLD guide](https://www.calibreos.com/blog/hld-system-design-interview-complete-guide), common FAANG topic lists (rate limiter, feed, chat, storage, search, payments).

---

## Tier 1 — Traffic & distribution (every interview)

| Industry topic | Status | Where in repo | Gap action |
|----------------|--------|---------------|------------|
| Load balancing L4/L7, algorithms | ✅ | [Fundamentals/5_Load_Balancers.md](./Fundamentals/5_Load_Balancers.md) | Deepen if needed |
| CDN / edge | ✅ | [Fundamentals/4_CDN.md](./Fundamentals/4_CDN.md) | — |
| Caching strategies (aside, through, behind) | ⚠️ | [Caching/](./Caching/README.md) — several short | deepen Caching notes |
| Cache stampede / hot keys | 📁 | [Failure-Modes/1_Cache_Stampede_and_Hot_Keys.md](./Failure-Modes/1_Cache_Stampede_and_Hot_Keys.md) | **Fill** |
| Rate limiting (token bucket, sliding window) | ⚠️ | [Performance/2_Rate_Limiting.md](./Performance/2_Rate_Limiting.md) + [Cases/10_Rate_Limiter_Design.md](./Cases/10_Rate_Limiter_Design.md) | Deepen + fill case |
| Message queues / event buses | ✅ | [Messaging/](./Messaging/README.md) | — |
| API Gateway / BFF | ⚠️ | [Fundamentals/13_API_Gateway.md](./Fundamentals/13_API_Gateway.md) | Deepen |
| DNS (design level) | ⚠️ | [Fundamentals/3_DNS.md](./Fundamentals/3_DNS.md) | 🔗 [Networks Services/DNS](../Networks-Deep-Dive/Services/2_DNS.md) |

---

## Tier 2 — Data & state (every interview)

| Industry topic | Status | Where in repo | Gap action |
|----------------|--------|---------------|------------|
| SQL vs NoSQL selection | ✅ | [Databases/2_SQL_vs_NoSQL_Selection.md](./Databases/2_SQL_vs_NoSQL_Selection.md) | — |
| Sharding / partitioning | ✅ | [Databases/4_Database_Sharding.md](./Databases/4_Database_Sharding.md), [Storage/2_Partitioning.md](./Storage/2_Partitioning.md) | — |
| Replication & consistency | ✅ | [Databases/5_Database_Replication.md](./Databases/5_Database_Replication.md), [Consistency/](./Consistency/README.md) | Some files thin |
| CAP theorem | ✅ | [Databases/6_CAP_Theorem.md](./Databases/6_CAP_Theorem.md), [Consistency/2_CAP_Theorem.md](./Consistency/2_CAP_Theorem.md) | Add PACELC → [Primer-Gaps/](./Primer-Gaps/README.md) |
| Consistent hashing | ✅ | [Fundamentals/17_Consistent_Hashing.md](./Fundamentals/17_Consistent_Hashing.md) | — |
| Indexing (B-tree, LSM) | ⚠️ | [Storage/1_Indexing.md](./Storage/1_Indexing.md) | Deepen LSM |
| Search at scale (inverted index, ranking) | 📁 | [Primer-Gaps/3_Search_At_Scale.md](./Primer-Gaps/3_Search_At_Scale.md) | **Fill** — case 3 Twitter partial |
| Idempotency / exactly-once UX | ⚠️ | [Consistency/4_Idempotency.md](./Consistency/4_Idempotency.md) | Deepen; link Stripe case |
| Distributed transactions | 📁 | [Primer-Gaps/1_Distributed_Transactions_and_Saga.md](./Primer-Gaps/1_Distributed_Transactions_and_Saga.md) | Was only in compensating-tx |
| 2PC / 3PC | 📁 | same as above | **Fill** |
| Saga pattern | ⚠️ | [Consistency/6_Compensating_Transactions.md](./Consistency/6_Compensating_Transactions.md) | Standalone primer gap |
| Consensus (Raft/Paxos) | ⚠️ | [Consistency/5_Consensus_Algorithms.md](./Consistency/5_Consensus_Algorithms.md) | Deepen |
| Leader election | ⚠️ | [Patterns/3_Leader_Election.md](./Patterns/3_Leader_Election.md) | Deepen |
| Unique IDs (Snowflake, UUID) | 📁 | [Primer-Gaps/2_Unique_Ids_and_Ordering.md](./Primer-Gaps/2_Unique_Ids_and_Ordering.md) | **Fill** |
| Object / blob storage | ✅ | [Databases/3_Storage_Systems.md](./Databases/3_Storage_Systems.md) | 🔗 Databases-Deep-Dive blob-object |

---

## Tier 3 — Patterns & resilience

| Industry topic | Status | Where in repo | Gap action |
|----------------|--------|---------------|------------|
| Circuit breaker / bulkhead / retry | ⚠️ | [Patterns/4_Circuit_Breaker.md](./Patterns/4_Circuit_Breaker.md), [Patterns/5_Bulkhead_and_Retry.md](./Patterns/5_Bulkhead_and_Retry.md) | Deepen |
| CQRS / event sourcing | ✅ | [Patterns/1_Event_Sourcing.md](./Patterns/1_Event_Sourcing.md), [Patterns/2_Cqrs.md](./Patterns/2_Cqrs.md) | — |
| Fan-out on write vs read | ⚠️ | [Cases/3_Twitter.md](./Cases/3_Twitter.md), Instagram stub | Deepen in cases |
| Split brain / partition | 📁 | [Failure-Modes/2_Split_Brain_and_Partition.md](./Failure-Modes/2_Split_Brain_and_Partition.md) | **Fill** |
| Cascading failures | 📁 | [Failure-Modes/3_Cascading_Failures_and_Timeout_Storms.md](./Failure-Modes/3_Cascading_Failures_and_Timeout_Storms.md) | **Fill** |
| Data loss / RPO-RTO | 📁 | [Failure-Modes/4_Data_Loss_and_Durability_Gaps.md](./Failure-Modes/4_Data_Loss_and_Durability_Gaps.md) | **Fill** |
| Gossip protocol | 📁 | [Primer-Gaps/4_Gossip_and_Membership.md](./Primer-Gaps/4_Gossip_and_Membership.md) | **Fill** |
| Bloom filter / HyperLogLog / Count-Min | 📁 | [Primer-Gaps/5_Probabilistic_Data_Structures.md](./Primer-Gaps/5_Probabilistic_Data_Structures.md) | **Fill** |
| CRDT | 📁 | [Primer-Gaps/6_Crdt_and_Collaborative_State.md](./Primer-Gaps/6_Crdt_and_Collaborative_State.md) | **Fill** |
| Merkle trees | 📁 | [Primer-Gaps/7_Merkle_Trees_and_Sync.md](./Primer-Gaps/7_Merkle_Trees_and_Sync.md) | **Fill** — Drive case |
| Multi-region / geo | 📁 | [Primer-Gaps/8_Multi_Region_and_Geo.md](./Primer-Gaps/8_Multi_Region_and_Geo.md) | **Fill** |
| Multi-tenancy | 📁 | [Primer-Gaps/9_Multi_Tenancy.md](./Primer-Gaps/9_Multi_Tenancy.md) | **Fill** |
| Batch / stream processing | 📁 | [Primer-Gaps/10_Batch_and_Stream_Processing.md](./Primer-Gaps/10_Batch_and_Stream_Processing.md) | **Fill** — 🔗 DE repo |

---

## Tier 4 — Observability & ops (2026 rubric)

| Industry topic | Status | Where in repo | Gap action |
|----------------|--------|---------------|------------|
| Four golden signals / SLI-SLO | ⚠️ | [Observability/](./Observability/README.md) — **9 files thin** | **Batch deepen** Observability notes |
| Distributed tracing | ⚠️ | [Observability/9_Distributed_Tracing.md](./Observability/9_Distributed_Tracing.md) | Deepen · 🔗 DevOps Observability |
| Cost vs performance | ⚠️ | [Performance/4_Cost_vs_Performance.md](./Performance/4_Cost_vs_Performance.md) | Deepen — **2026 rubric** |
| Back-of-envelope / capacity math | ⚠️ | [Fundamentals/12_HLD_and_LLD.md](./Fundamentals/12_HLD_and_LLD.md) | Add dedicated section or primer |

---

## Tier 5 — Security at design time

| Industry topic | Status | Where in repo | Gap action |
|----------------|--------|---------------|------------|
| Authn vs authz | ⚠️ | [Security/7_Authentication_vs_Authorization.md](./Security/7_Authentication_vs_Authorization.md) | Deepen |
| OAuth / JWT / federated identity | ⚠️ | [Security/2_Federated_Identity.md](./Security/2_Federated_Identity.md) | Deepen |
| TLS / encryption trade-offs | ⚠️ | [Security/6_SSL_and_TLS.md](./Security/6_SSL_and_TLS.md) | 🔗 Networks Security |
| Threat modeling | 📁 | [Security-Tradeoffs/1_Threat_Modeling_At_Design_Time.md](./Security-Tradeoffs/1_Threat_Modeling_At_Design_Time.md) | **Fill** |
| Zero trust / mTLS | 📁 | [Security-Tradeoffs/2_Auth_Design_vs_Zero_Trust.md](./Security-Tradeoffs/2_Auth_Design_vs_Zero_Trust.md) | **Fill** |
| DDoS / abuse at design level | 📁 | [Primer-Gaps/11_Abuse_and_Ddos_Design.md](./Primer-Gaps/11_Abuse_and_Ddos_Design.md) | **Fill** |
| Full AppSec / OWASP program | 🔗 | [Security Deep Dive](../Security-Deep-Dive/README.md) | Security-Deep-Dive capstone |

---

## Tier 6 — Modern / AI era (2024+ rubric — was not in older prep)

| Industry topic | Status | Where in repo | Gap action |
|----------------|--------|---------------|------------|
| Vector DB / embeddings storage | ⚠️ | [Databases/README.md](./Databases/README.md) type 10 | 🔗 Databases pgvector · DS-AI repo |
| RAG pipeline design | 📁 | [Primer-Gaps/12_RAG_and_LLM_Gateway_Design.md](./Primer-Gaps/12_RAG_and_LLM_Gateway_Design.md) | **Fill** · 🔗 DS-AI |
| LLM gateway (rate limit, cache, routing) | 📁 | same | **Fill** |
| OWASP LLM Top 10 (design angle) | 📁 | security-tradeoffs + Security-Deep-Dive | Cross-link when Security repo built |

---

## Case studies — industry “top 15” vs repo

| Common interview prompt | Status | File |
|-------------------------|--------|------|
| URL shortener | ⚠️ moderate | [Cases/6_URL_Shortener.md](./Cases/6_URL_Shortener.md) |
| Rate limiter | 📁 stub | [Cases/10_Rate_Limiter_Design.md](./Cases/10_Rate_Limiter_Design.md) |
| News / social feed | ⚠️ | [Cases/3_Twitter.md](./Cases/3_Twitter.md), [8_Instagram_Feed.md](./Cases/8_Instagram_Feed.md) |
| Chat / messaging | ⚠️ | [Cases/2_Whatsapp.md](./Cases/2_Whatsapp.md), [7-discord.md](./Cases/7_Discord_Messaging.md), [11_Slack_Realtime.md](./Cases/11_Slack_Realtime.md) |
| Video (YouTube/Netflix) | 📁 stub | [Cases/5_Youtube_Netflix.md](./Cases/5_Youtube_Netflix.md) |
| File sync (Drive/Dropbox) | 📁 stub | [Cases/1_Google_Drive_File_Sync.md](./Cases/1_Google_Drive_File_Sync.md) |
| Ride-sharing / maps | 📁 stub | [Cases/4_Uber.md](./Cases/4_Uber.md) |
| Payments (Stripe) | 📁 stub | [Cases/9_Stripe_Payments.md](./Cases/9_Stripe_Payments.md) |
| Notification system | ❌ | Cases to fill — add case 12 |
| Search engine | ❌ | primer-gaps + planned case |
| Email service | ❌ | planned case |
| Ticket / event booking | ❌ | planned case |
| Recommendation engine | ❌ | planned case |
| Distributed cron / scheduler | ❌ | planned case |
| Web crawler | ❌ | planned case |

Full list: Cases to fill below

---

## Verdict (August 2026)

**You are NOT missing the skeleton** — fundamentals, databases, caching, messaging, CAP, consistent hashing, and core cases exist.

**You ARE missing depth and modern tier:**

1. **~40+ short topic files** — especially `Observability/` and `Security/`
2. **12 primer-gaps stubs** — gossip, bloom filters, 2PC/saga standalone, search-at-scale, etc.
3. **Cases** — most are outlines; need failure modes + capacity math
4. **2026 tier** — RAG/Vector/LLM gateway design (stubs in `Primer-Gaps/`)
5. **Related repos** — engine depth (Databases), wire depth (Networks), cyber capstone (Security) — by design, not duplication

**Fill order:** Write order → [Primer-Gaps/](./Primer-Gaps/README.md) → Cases to fill


### Cases to fill

# Cases to fill

Cases with **full writeups** vs **stubs** or **index-only** (August 2026 audit). Tick `- [x]` when a case matches existing case file quality (requirements, HLD, concept links, failure modes, further reading).

## Existing cases (deepen — add Failure modes section)

- [ ] [1 — Google Drive / file sync](./Cases/1_Google_Drive_File_Sync.md)
- [ ] [2 — WhatsApp](./Cases/2_Whatsapp.md)
- [ ] [3 — Twitter / feed](./Cases/3_Twitter.md)
- [ ] [4 — Uber / geospatial](./Cases/4_Uber.md)
- [ ] [5 — YouTube / Netflix](./Cases/5_Youtube_Netflix.md)
- [ ] [6 — URL shortener](./Cases/6_URL_Shortener.md)

## New case stubs (fill in order)

| Priority | Case | File | Key concepts |
|----------|------|------|--------------|
| v1 | Discord messaging at scale | [Cases/7_Discord_Messaging.md](./Cases/7_Discord_Messaging.md) | Wide-column/Cassandra, snowflake IDs, hot partitions |
| v1 | Instagram feed / photos | [Cases/8_Instagram_Feed.md](./Cases/8_Instagram_Feed.md) | Sharding, CDN, fan-out, object storage |
| v2 | Stripe / payments API | [Cases/9_Stripe_Payments.md](./Cases/9_Stripe_Payments.md) | Idempotency, ledger, exactly-once, PCI boundaries |
| v2 | Distributed rate limiter | [Cases/10_Rate_Limiter_Design.md](./Cases/10_Rate_Limiter_Design.md) | Token bucket, Redis, sliding window, edge vs central |
| v3 | Slack real-time messaging | [Cases/11_Slack_Realtime.md](./Cases/11_Slack_Realtime.md) | WebSockets, presence, channel fan-out |
| v2 | Notification system (push/email/SMS) | [Cases/12_Notification_System.md](./Cases/12_Notification_System.md) | Queues, fan-out, device tokens, dedup |
| v2 | Email service (Gmail-scale) | [Cases/13_Email_Service.md](./Cases/13_Email_Service.md) | SMTP, storage, search, spam |
| v3 | Ticket / event booking | [Cases/14_Ticket_Booking.md](./Cases/14_Ticket_Booking.md) | Concurrency, locks, overselling |
| v3 | Recommendation engine | [Cases/15_Recommendation_Engine.md](./Cases/15_Recommendation_Engine.md) | Offline/online features, ranking |
| v3 | Distributed cron / scheduler | [Cases/16_Distributed_Scheduler.md](./Cases/16_Distributed_Scheduler.md) | Leader election, exactly-once runs |
| v3 | Web crawler | [Cases/17_Web_Crawler.md](./Cases/17_Web_Crawler.md) | Frontier, politeness, dedup (Bloom) |
| v3 | Pastebin / object-heavy | *(covered in 6)* | Extend case 6 if needed |

**Resource index:** [Cases/0_Companies_and_Products.md](./Cases/0_Companies_and_Products.md) — external links only; convert priority rows into in-repo cases over time.

---

## Datastructures-and-Algorithms

Public intro: [Deep-Dives/Datastructures-and-Algorithms/README.md](../../Deep-Dives/Datastructures-and-Algorithms/README.md)

### Start here

# Start here — Data Structures & Algorithms

[← README](./README.md) · Write order · Problems to fill · [SystemDesignBridge](./SystemDesignBridge/README.md)

*(Updated August 2026)*

## Who this repo is for

Interview coding prep + pattern reference. **Theory is here;** scale trade-offs live in [System-Design-Concepts](../System-Design-Concepts/README.md).

**Why a security engineer opens this:** interviews, and the occasional structure behind crypto/parsers — not the main security path.

## Learning path (checkboxes)

### Foundations
- [ ] [Foundation/Coding_Patterns.md](./Foundation/Coding_Patterns.md) — 16 patterns
- [ ] [Algorithms/00_Logic_Building.md](./Algorithms/00_Logic_Building.md)
- [ ] [Algorithms/01_Time_Complexity_and_Space_Complexity.md](./Algorithms/01_Time_Complexity_and_Space_Complexity.md)

### Data structures (pick depth by need)
- [ ] Core: Array, Linked List, Stack, Queue, Hash, Heap, Tree, Graph — [DataStructures/](./DataStructures/README.md)
- [ ] Advanced: Trie, Segment Tree, BIT — when problems require it

### Algorithms
- [ ] [Algorithms/02_Searching_and_Sorting.md](./Algorithms/02_Searching_and_Sorting.md)
- [ ] [Algorithms/04_Dynamic_Programming.md](./Algorithms/04_Dynamic_Programming.md)
- [ ] [Algorithms/12_Graph_Algorithms.md](./Algorithms/12_Graph_Algorithms.md)

### Practice (your gap — expand here)
- [ ] [Leetcode/Two_Pointers/](./Leetcode/Readme.md) — continue checklist
- [ ] Leetcode/Design/ — LRU, LFU stubs
- [ ] Leetcode/Graph/ — empty today
- [ ] [SystemDesignBridge/](./SystemDesignBridge/README.md) — patterns that appear in SD interviews

## Related repos

→ related repos on the [README](./README.md)

## Checklist before marking done

- [ ] All checkbox sections above ticked for your target level (working → strong)
- [ ] 50+ problems solved with Readme writeups

### Write order

# Data Structures & Algorithms — content write order

**Created:** August 2026  
**Repo #6** after [System-Design-Concepts](../System-Design-Concepts/README.md).

**Unlike System Design:** this repo has **strong theory** (19 algorithm + 23 data structure topic files, Foundation patterns) but a **thin problem bank** (~18 LeetCode folders solved; Leetcode/Readme lists 100+ unchecked).

---

## What is already solid (maintain only)

| Section | Files | Status |
|---------|-------|--------|
| [Algorithms/](./Algorithms/README.md) | 19 topics (00–18) | **Written** — logic, complexity, DP, graphs, etc. |
| [DataStructures/](./DataStructures/README.md) | 23 topics | **Written** — array through RB-tree, trie, segment tree |
| [Foundation/](./Foundation/Readme.md) | 2 + patterns | **Written** — 16 coding patterns cheatsheet |
| [Template/](./Template/) | C++/Java snippets | **Written** — BIT, segtree, graph, math |
| [Leetcode/](./Leetcode/Readme.md) | 18 solved folders | **Partial** — Two Pointers, Binary Search, Linked List only |
| [GeekforGeeks/](./GeekforGeeks/Readme.md) | ~19 topic folders | **Partial** — mostly code, sparse READMEs |

---

## Lane J — recommended fill order

| Step | Location | Why |
|------|----------|-----|
| 1 | Start here + [README](./README.md) | On-ramp + related repos |
| 2 | Problems to fill | Track empty LeetCode categories + target count (below) |
| 3 | [SystemDesignBridge/](./SystemDesignBridge/README.md) | Map patterns → System Design (rate limit, LRU, top-K) |
| 4 | Fill **Design** + **Heap** LeetCode categories | Interview staples (LRU, LFU, 295, 703) |
| 5 | Fill **Graph** + **BFS/DFS** + **Union Find** | SD-relevant (connectivity, islands) |
| 6 | Fill **Dynamic Programming** (classic 15) | Interview core |
| 7 | Expand **GeekforGeeks** READMEs per problem | Match LeetCode quality |
| 8 | Tag solved problems with `SD:` in Readme when relevant | Link to SystemDesignBridge |

---

## Related repos

| Domain | Repository | Entry file |
|--------|------------|------------|
| Architecture trade-offs | [System-Design-Concepts](https://github.com/thisiskushal31/System-Design-Concepts) | [System Design Concepts](../System-Design-Concepts/README.md) |
| Command templates | [Commands-and-Cheatsheets](https://github.com/thisiskushal31/Commands-and-Cheatsheets) | [Commands and Cheatsheets](../Commands-and-Cheatsheets/README.md) |
| Delivery / interview loops | [DevOps-Handbook](https://github.com/thisiskushal31/DevOps-Handbook) | [DevOps Handbook](../DevOps-Handbook/README.md) |

**Inbound:** [System Design Concepts](../System-Design-Concepts/README.md)

---

## Repo #6 done when

- [ ] Problems to fill — every empty LeetCode category has ≥3 solved OR explicitly deferred
- [ ] [SystemDesignBridge/](./SystemDesignBridge/README.md) — ≥8 pattern writeups with SD links
- [ ] 50+ curated problems with Readme + solution (realistic v1; 150 = stretch)
- [ ] `Start here` checkbox learning path complete

---

## Marking problems complete

Use `- [x]` in [Leetcode/Readme.md](./Leetcode/Readme.md) and Problems to fill below. Each new problem folder: `Readme.md` (approach, complexity) + `.cpp`/`.java` solution.

### Problems to fill

# Problems to fill

Track **empty LeetCode categories** and priority fills. Source checklist: [Leetcode/Readme.md](./Leetcode/Readme.md) (100+ listed; ~18 folders exist).

**Industry target:** 50 curated v1 · 150 stretch (NeetCode / Blind 75 style).

---

## Solved today (~18 folders)

| Category | Count | Notes |
|----------|-------|-------|
| Two Pointers | ~14 listed, many solved | Strongest area |
| Binary Search | 2 | 033, 069 |
| Linked List | 4 | 061, 082, 086, 142 |

---

## Empty LeetCode categories (0 solution folders)

Fill in order below — tick category when ≥3 problems have Readme + code.

- [ ] **Hash Map** — 1 Two Sum, 49 Group Anagrams, 128 Longest Consecutive
- [ ] **Heap / Priority Queue** — 215 Kth Largest, 295 Find Median, 973 K Closest Points
- [ ] **Design** — 146 LRU Cache, 460 LFU, 355 Design Twitter
- [ ] **Tree** — 102 Level Order, 104 Max Depth, 236 LCA
- [ ] **Graph / BFS / DFS** — 200 Number of Islands, 133 Clone Graph, 207 Course Schedule
- [ ] **Dynamic Programming** — 70 Climbing Stairs, 322 Coin Change, 300 LIS
- [ ] **Trie** — 208 Implement Trie, 211 Design Add Search
- [ ] **Union Find** — 547 Number of Provinces, 684 Redundant Connection
- [ ] **Stack** — 20 Valid Parentheses, 155 Min Stack, 739 Daily Temperatures
- [ ] **Backtracking** — 78 Subsets, 46 Permutations, 39 Combination Sum
- [ ] **Bit Manipulation** — 136 Single Number, 191 Number of 1 Bits
- [ ] **Segment Tree / BIT** — defer unless contest path

---

## Design + Heap (priority v1 — SD bridge)

| Problem | SD link | Status |
|---------|---------|--------|
| 146 LRU Cache | [Caching/7-eviction](../System-Design-Concepts/Caching/7_Cache_Eviction_Policies.md) | 📁 [stub](./SystemDesignBridge/1_LRU_Cache.md) |
| 460 LFU Cache | caching eviction | 📁 stub |
| 295 Find Median from Data Stream | streaming aggregates | 📁 stub |
| 380 Insert Delete GetRandom O(1) | URL shortener key pool | 📁 stub |
| 355 Design Twitter | feed fan-out case | 📁 stub |

---

## System-design-tagged classics

| Problem | Pattern | System Design link |
|---------|---------|-------------------|
| 215 Kth Largest | Heap / quickselect | Top-K, dashboards |
| 347 Top K Frequent | Heap + hash | Hot keys, rate limit windows |
| 128 Longest Consecutive | Hash set | Dedup sets |
| 200 Islands | BFS/DFS | Graph connectivity |
| 56 Merge Intervals | Sort + merge | Calendar, scheduling |

Full bridge index: [SystemDesignBridge/README.md](./SystemDesignBridge/README.md)

---

## GeekforGeeks

~19 topic folders — mostly code without Readme depth. Align with LeetCode pattern fills above; add Readme per problem when touching.

---

## Commands-and-Cheatsheets

Public intro: [Deep-Dives/Commands-and-Cheatsheets/README.md](../../Deep-Dives/Commands-and-Cheatsheets/README.md)

### Start here

# Start here — Commands and Cheatsheets

[← README](./README.md)

This repo is a **reference**, not a course. If you know nothing: pick the tool you are staring at, open that folder, copy the command. Full “why” lives in the matching Deep-Dive.

**Why a security engineer opens this:** incident and lab — you need the command now, the chapter later.

## Path

1. Find the topic in [README.md](./README.md)
2. If you need *why*, open the related Deep-Dive (DevOps, Networks, Databases, …)

*(Content TBD — stub created September 2026)*

### Write order

# Commands and Cheatsheets — content write order

**Repo #7** · ~86 MD files · **Reference only** — no deep dives (related repos own depth).

## Lane K — maintain order

| Step | Action |
|------|--------|
| 1 | Cross-link to related repos in root README |
| 2 | Add K8s, Docker, AWS CLI cheatsheets (today GCP-heavy) |
| 3 | ~~Fix `Langauges/` typo~~ → `Languages/` |
| 4 | New tools → add here when adopted in other repos |

**Not a learning repo** — daily driver commands only.

---

## Data-Engineering-Deep-Dive

Public intro: [Deep-Dives/Data-Engineering-Deep-Dive/README.md](../../Deep-Dives/Data-Engineering-Deep-Dive/README.md)

### Start here

# Start here — Data Engineering Deep Dive

[← README](./README.md) · Write order · Topics to cover · Writing rules

## Who this repo is for

Platform and data engineers. Learn the **path of a fact** (layers). Give Spark, Kafka, Flink, Airflow, … each a **folder** under [Systems/](./Systems/README.md) — same idea as one folder per language in the DevOps handbook.

A new engine is a new `Systems/<Name>/`. It is not a new layer.

## Learning path

- [ ] [Systems/](./Systems/README.md) — Kafka, Spark, … ; DuckDB engine is [Databases Relational/duckdb](https://github.com/thisiskushal31/Databases-Deep-Dive/tree/main/Relational/duckdb)
- [ ] Foundations (contracts, bounded vs unbounded)
- [ ] Capture + Movement *as jobs*
- [ ] [Systems/Kafka](./Systems/Kafka/README.md) — one log
- [ ] Transformation *as a job*
- [ ] [Systems/Spark](./Systems/Spark/README.md) — one compute engine (batch + streaming as topics, not layers)
- [ ] A [Use-Cases/](./Use-Cases/README.md) path that uses more than one system
- [ ] Storage roles, serving, governance

## Related-repo matrix

→ related repos on the [README](./README.md)

## Checklist before marking this file done

- [x] Layers + Systems/ + Use-Cases/ exist
- [x] Related-repo pointers on README
- [ ] First Foundations topic filled (not just stubbed)

### Write order

# Data Engineering Deep Dive — content write order

**Repo #8** · **Status:** timeless layers + Systems catalog (September 2026) · **Phase:** 3

**Rule:** Writing rules · **List:** Topics to cover

Fill **layers** (the job) enough to think, then a **system** folder (Spark, Kafka — like a language track), then a **use case** that wires several systems. Do not fill “Spark first because it’s popular.”

## Lane F — fill order

| Step | What | Why |
|------|------|-----|
| 1 | `Start here` + Writing rules + `Systems/README.md` | Two axes: layers vs named systems. DuckDB engine → [Databases](https://github.com/thisiskushal31/Databases-Deep-Dive/tree/main/Relational/duckdb) |
| 2 | Foundations | Grain, time, bounded vs unbounded |
| 3 | Capture + Movement (patterns) | The job |
| 4 | **Systems/Kafka** (or another Movement system) | One named log, Languages-style |
| 5 | Transformation (patterns) | The job |
| 6 | **Systems/Spark** (and/or Flink, dbt) | One named compute engine |
| 7 | Orchestration + Storage roles | Then Airflow / Iceberg folders as needed |
| 8 | Use-Cases/ | CDC path, unbounded path, feature path |
| 9 | Serving, Governance, Platform-Ops | |
| 10 | Instances/ | Dated index only |

**Related repos:** [Databases](../Databases-Deep-Dive/README.md) · [DevOps-Handbook Languages](../DevOps-Handbook/Languages/README.md) · [System-Design Primer-Gaps/10](../System-Design-Concepts/Primer-Gaps/10_Batch_and_Stream_Processing.md) · [Data Science & AI](../Data-Science-AI-Deep-Dive/README.md)

### Writing rules

# Writing rules

[← README](./README.md)

**Two axes, like DevOps-Handbook Languages vs Methodologies:**

| Axis | What it is | When something new appears |
|------|------------|----------------------------|
| **Layers** (`Foundations/` … `Platform-Ops/`) | Jobs on the path of a fact | Almost never add a layer |
| **Systems/** | One folder per named engine/framework (Spark, Kafka, …) — same as one folder per language | Add a folder here |
| **Use-Cases/** | Paths that span several systems (CDC path, feature path, …) | Add a case file |

Layers must still make sense when Spark and Kafka are gone. Systems folders are allowed to rot or be replaced.

## Do

- Name a **layer** after a job: capture, move, transform, store, orchestrate, serve, govern, operate.
- Give Spark, Kafka, Flink, Airflow, dbt, Iceberg, … each **one folder** under `Systems/`, with what → model → ops → use cases.
- A system that plays two roles keeps **one folder** (Kafka = log; Connect is a topic inside it).
- Cross-system stories go in `Use-Cases/`, not inside a vendor folder.

## Do not

- Name a **layer** after a vendor or this year’s stack.
- Put Spark at the same level as Transformation (Spark *is* a transformation system).
- Duplicate database engines here (MySQL, BigQuery, …) — [Databases-Deep-Dive](../Databases-Deep-Dive/README.md).

## Order of layers (path of a fact)

1. Foundations — contracts, grain, time, quality, bounded vs unbounded  
2. Capture — how facts enter  
3. Movement — buffers, replay, backpressure  
4. Transformation — change shape and meaning  
5. Storage — roles of stores  
6. Orchestration — time, dependency, idempotency  
7. Serving — how consumers read or are activated  
8. Governance — privacy, access, cost  
9. Platform ops — SLAs, failure, provisioning  

Then: [Systems/](./Systems/README.md) (catalog) · [Use-Cases/](./Use-Cases/README.md) (shapes) · [Instances/](./Instances/README.md) (dated index only)

### Topics to cover

# Topics to cover — next step forward

[← README](./README.md) · Write order · Writing rules

Tick when a file has no `*(Content TBD)*`. Order is the **path of a fact**, not this year’s stack.

---

## Next (learn the path)

- [ ] [Foundations/1_Contracts_And_Grain.md](./Foundations/1_Contracts_And_Grain.md)
- [ ] [Foundations/4_Bounded_Vs_Unbounded.md](./Foundations/4_Bounded_Vs_Unbounded.md)
- [ ] [Capture/1_Sources_And_Extract.md](./Capture/1_Sources_And_Extract.md)
- [ ] [Capture/3_Delivery_Guarantees.md](./Capture/3_Delivery_Guarantees.md)
- [ ] [Transformation/1_Declarative_Vs_Procedural.md](./Transformation/1_Declarative_Vs_Procedural.md)
- [ ] [Orchestration/2_Idempotency_Backfill_Replay.md](./Orchestration/2_Idempotency_Backfill_Replay.md)
- [ ] [Storage/1_Roles_Of_Stores.md](./Storage/1_Roles_Of_Stores.md)
- [ ] [Serving/1_Read_Models.md](./Serving/1_Read_Models.md)
- [ ] [Governance/1_Privacy_And_Retention.md](./Governance/1_Privacy_And_Retention.md)

## 1 · Foundations

- [ ] [1_Contracts_And_Grain.md](./Foundations/1_Contracts_And_Grain.md)
- [ ] [2_Time_And_Change.md](./Foundations/2_Time_And_Change.md)
- [ ] [3_Quality_And_Lineage.md](./Foundations/3_Quality_And_Lineage.md)
- [ ] [4_Bounded_Vs_Unbounded.md](./Foundations/4_Bounded_Vs_Unbounded.md)

## 2 · Capture

- [ ] [1_Sources_And_Extract.md](./Capture/1_Sources_And_Extract.md)
- [ ] [2_Change_Data.md](./Capture/2_Change_Data.md)
- [ ] [3_Delivery_Guarantees.md](./Capture/3_Delivery_Guarantees.md)

## 3 · Movement

- [ ] [1_Transport_Buffers_Replay.md](./Movement/1_Transport_Buffers_Replay.md)
- [ ] [2_Backpressure.md](./Movement/2_Backpressure.md)

## 4 · Transformation

- [ ] [1_Declarative_Vs_Procedural.md](./Transformation/1_Declarative_Vs_Procedural.md)
- [ ] [2_Stateful_Computation.md](./Transformation/2_Stateful_Computation.md)
- [ ] [3_Distributed_Compute_Patterns.md](./Transformation/3_Distributed_Compute_Patterns.md)
- [ ] [4_Schema_Evolution.md](./Transformation/4_Schema_Evolution.md)

## 5 · Storage

- [ ] [1_Roles_Of_Stores.md](./Storage/1_Roles_Of_Stores.md)
- [ ] [2_File_Table_Log.md](./Storage/2_File_Table_Log.md)
- [ ] [3_Analytical_And_Serving_Stores.md](./Storage/3_Analytical_And_Serving_Stores.md)

## 6 · Orchestration

- [ ] [1_Dependency_And_Time.md](./Orchestration/1_Dependency_And_Time.md)
- [ ] [2_Idempotency_Backfill_Replay.md](./Orchestration/2_Idempotency_Backfill_Replay.md)
- [ ] [3_Schedulers_As_A_Class.md](./Orchestration/3_Schedulers_As_A_Class.md)

## 7 · Serving

- [ ] [1_Read_Models.md](./Serving/1_Read_Models.md)
- [ ] [2_Semantic_Access.md](./Serving/2_Semantic_Access.md)
- [ ] [3_Activation_And_Reverse_Flows.md](./Serving/3_Activation_And_Reverse_Flows.md)

## 8 · Governance

- [ ] [1_Privacy_And_Retention.md](./Governance/1_Privacy_And_Retention.md)
- [ ] [2_Access_And_Contracts.md](./Governance/2_Access_And_Contracts.md)
- [ ] [3_Cost_As_A_Constraint.md](./Governance/3_Cost_As_A_Constraint.md)

## 9 · Platform ops

- [ ] [1_SLAs_And_Failure.md](./Platform-Ops/1_SLAs_And_Failure.md)
- [ ] [2_Observability.md](./Platform-Ops/2_Observability.md)
- [ ] [3_Provisioning_As_A_Class.md](./Platform-Ops/3_Provisioning_As_A_Class.md)

## 10 · Systems (one folder each — like Languages)

Catalog: [Systems/README.md](./Systems/README.md). Tick the system README when the track is filled.

**Movement:** [Kafka](./Systems/Kafka/README.md) · [Pulsar](./Systems/Pulsar/README.md) · [NATS](./Systems/NATS/README.md) · [Kinesis](./Systems/Kinesis/README.md) · [PubSub](./Systems/PubSub/README.md)

**Capture:** [Debezium](./Systems/Debezium/README.md) · [Airbyte](./Systems/Airbyte/README.md)

**Transformation:** [Spark](./Systems/Spark/README.md) · [Flink](./Systems/Flink/README.md) · [Beam](./Systems/Beam/README.md) · [dbt](./Systems/dbt/README.md) · [Dataform](./Systems/Dataform/README.md)

**Orchestration:** [Airflow](./Systems/Airflow/README.md) · [Dagster](./Systems/Dagster/README.md) · [Prefect](./Systems/Prefect/README.md)

**Storage (table-on-files):** [Iceberg](./Systems/Iceberg/README.md) · [Delta](./Systems/Delta/README.md) · [Hudi](./Systems/Hudi/README.md)

- [ ] [Systems/Spark/README.md](./Systems/Spark/README.md) *(start here for distributed compute)*
- [ ] [Systems/Kafka/README.md](./Systems/Kafka/README.md) *(start here for the log)*

## 11 · Use cases (cross-system shapes)

- [ ] [1_Bounded_Analytical_Path.md](./Use-Cases/1_Bounded_Analytical_Path.md)
- [ ] [2_Change_Data_Path.md](./Use-Cases/2_Change_Data_Path.md)
- [ ] [3_Unbounded_Event_Path.md](./Use-Cases/3_Unbounded_Event_Path.md)
- [ ] [4_Feature_Path_For_Learning.md](./Use-Cases/4_Feature_Path_For_Learning.md)
- [ ] [5_Activation_Path.md](./Use-Cases/5_Activation_Path.md)
- [ ] [6_Replay_And_Backfill.md](./Use-Cases/6_Replay_And_Backfill.md)

## 12 · Instances (dated index only)

- [ ] [1_Current_Market_Map.md](./Instances/1_Current_Market_Map.md)

---

## Intentionally elsewhere

| Problem | Primary repo |
|---------|----------------|
| Engine internals, 10 store types | [Databases-Deep-Dive](../Databases-Deep-Dive/README.md) |
| Batch/stream at HLD grain | [System-Design Primer-Gaps/10](../System-Design-Concepts/Primer-Gaps/10_Batch_and_Stream_Processing.md) |
| Learning, retrieval, eval | [Data-Science-AI-Deep-Dive](../Data-Science-AI-Deep-Dive/README.md) |
| CI/CD, IaC products, observability stack | DevOps-Handbook |
| Named framework hello-world | Tooling-and-Frameworks-Deep-Dive |

---

## Data-Science-AI-Deep-Dive

Public intro: [Deep-Dives/Data-Science-AI-Deep-Dive/README.md](../../Deep-Dives/Data-Science-AI-Deep-Dive/README.md)

### Start here

# Start here — Data Science & AI Deep Dive

[← README](./README.md) · Write order · Topics to cover · Writing rules

## Who this repo is for

Engineers who will still need these notes after the current model family, serving runtime, and agent framework are replaced. Learn **layers**. Put today’s names in [Instances/](./Instances/README.md).

## Learning path

Follow Topics to cover **Next** — build one retrieval system so the layers are not abstract.

- [ ] Libraries (PyTorch, scikit-learn) → [Tooling Data-ML](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive/tree/main/Data-ML)
- [ ] Representation (tokens, embeddings)
- [ ] Retrieval and grounding + one applied case
- [ ] Evaluation of grounded generation
- [ ] Control (tool use) and safety (threat model)
- [ ] Sequence/attention + inference memory
- [ ] Adaptation strategies (condition vs update weights vs memory)
- [ ] Foundations when an eval design blocks you

## Related-repo matrix

→ related repos on the [README](./README.md)

## Checklist before marking this file done

- [x] Layers match Writing rules
- [x] Related-repo pointers on README
- [ ] First Representation or Retrieval topic filled (not just stubbed)

### Write order

# Data Science & AI Deep Dive — content write order

**Repo #9** · **Status:** timeless stub tree (September 2026) · **Phase:** 3

**Rule:** Writing rules · **List:** Topics to cover

Fill **layers** (Representation → Retrieval → Evaluation → …). Do not fill in “current job-description” order. Dated tools only in `Instances/`.

## Lane G — fill order (layers)

| Step | Layer | Why this position |
|------|--------|-------------------|
| 1 | `Start here` + README related-repos + Writing rules | Navigation. Libraries → [Tooling Data-ML](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive/tree/main/Data-ML) |
| 2 | Representation | Nothing else exists without an encoding |
| 3 | Retrieval-And-Grounding + Applied case | Evidence-conditioned systems |
| 4 | Evaluation | Otherwise you cannot tell if a change worked |
| 5 | Control-And-Agency + Safety-And-Adversaries | Tools and untrusted context |
| 6 | Learning (sequence / attention) + Inference-And-Serving | How sequence models actually run |
| 7 | Adaptation | Four strategies after a base exists |
| 8 | Foundations | When experiment design blocks you |
| 9 | Instances/ | Optional dated map — last, and disposable |

**Related repos:** [Data Engineering](../Data-Engineering-Deep-Dive/README.md) · [Databases vector](../Databases-Deep-Dive/README.md) · [System-Design Primer-Gaps/12](../System-Design-Concepts/Primer-Gaps/12_RAG_and_LLM_Gateway_Design.md)

### Writing rules

# Writing rules

[← README](./README.md)

**Folders are problems and strategies. They must still make sense when the current tools are gone.**

This repo will outlive any tokenizer, adapter recipe, serving runtime, tool protocol, or “top 10” list. Those things belong in [Instances/](./Instances/README.md), dated, and are allowed to rot.

## Do

- Name a layer after a **job**: represent, learn, adapt, retrieve, control, evaluate, defend, serve.
- Treat a named product as an **example** inside a topic, with a date.
- When something new appears: add a row in `Instances/`, or a bullet under Planned coverage — **do not add a top-level folder named after it**.
- **Named libraries** (PyTorch, vLLM, LangChain) → [Tooling Data-ML](https://github.com/thisiskushal31/Tooling-and-Frameworks-Deep-Dive/tree/main/Data-ML). **Do not add a `Tools/` folder in this repo.**

## Do not

- Name sections after a vendor, a cloud SKU, a framework, or this year’s architecture brand.
- Order topics by “what jobs are hiring for this quarter.”
- Duplicate engine ops (Databases), pipeline capture/transform (Data Engineering), or gateway design (System Design).

## Order of layers (not market order)

1. Foundations — uncertainty and comparison  
2. Representation — how the world is encoded  
3. Learning — fitting a mapping  
4. Adaptation — change behavior after a base exists  
5. Retrieval and grounding — condition on evidence  
6. Control and agency — tools and multi-step work  
7. Evaluation — how you know  
8. Safety and adversaries — untrusted context  
9. Inference and serving — memory, latency, cost  
10. Applied — systems that use the layers  
11. Instances — dated market map  

### Topics to cover

# Topics to cover — next step forward

[← README](./README.md) · Write order · Writing rules

Tick when a file has no `*(Content TBD)*`. Order is **layers of the problem**, not this year’s stack.

---

## Next (learn the layers by building)

- [ ] [Representation/2_Tokens.md](./Representation/2_Tokens.md)
- [ ] [Representation/3_Embeddings.md](./Representation/3_Embeddings.md)
- [ ] [Retrieval-And-Grounding/1_Evidence_And_Indexes.md](./Retrieval-And-Grounding/1_Evidence_And_Indexes.md)
- [ ] [Retrieval-And-Grounding/2_Retrieve_Rerank_Generate.md](./Retrieval-And-Grounding/2_Retrieve_Rerank_Generate.md)
- [ ] [Applied/Case_Studies/2_Personal_Retrieval_Over_Notes.md](./Applied/Case_Studies/2_Personal_Retrieval_Over_Notes.md)
- [ ] [Evaluation/2_Grounded_Generation_Metrics.md](./Evaluation/2_Grounded_Generation_Metrics.md)
- [ ] [Control-And-Agency/1_Tool_Use.md](./Control-And-Agency/1_Tool_Use.md)
- [ ] [Safety-And-Adversaries/1_Threat_Model.md](./Safety-And-Adversaries/1_Threat_Model.md)
- [ ] [Learning/2_Sequence_And_Attention.md](./Learning/2_Sequence_And_Attention.md)
- [ ] [Inference-And-Serving/1_Memory_And_Compute.md](./Inference-And-Serving/1_Memory_And_Compute.md)
- [ ] [Adaptation/2_Conditioning_Without_Weight_Updates.md](./Adaptation/2_Conditioning_Without_Weight_Updates.md)
- [ ] [Adaptation/3_Parameter_Updates.md](./Adaptation/3_Parameter_Updates.md)

## 1 · Foundations

- [ ] [1_Statistics_Probability.md](./Foundations/1_Statistics_Probability.md)
- [ ] [2_Linear_Algebra_Calculus_Refresher.md](./Foundations/2_Linear_Algebra_Calculus_Refresher.md)
- [ ] [3_Experiment_Design.md](./Foundations/3_Experiment_Design.md)

## 2 · Representation

- [ ] [1_Features.md](./Representation/1_Features.md)
- [ ] [2_Tokens.md](./Representation/2_Tokens.md)
- [ ] [3_Embeddings.md](./Representation/3_Embeddings.md)
- [ ] [4_Other_Modalities.md](./Representation/4_Other_Modalities.md)

## 3 · Learning

- [ ] [1_Supervised_And_Unsupervised.md](./Learning/1_Supervised_And_Unsupervised.md)
- [ ] [2_Sequence_And_Attention.md](./Learning/2_Sequence_And_Attention.md)
- [ ] [3_Layered_Differentiable_Models.md](./Learning/3_Layered_Differentiable_Models.md)

## 4 · Adaptation

- [ ] [1_Reuse_And_Transfer.md](./Adaptation/1_Reuse_And_Transfer.md)
- [ ] [2_Conditioning_Without_Weight_Updates.md](./Adaptation/2_Conditioning_Without_Weight_Updates.md)
- [ ] [3_Parameter_Updates.md](./Adaptation/3_Parameter_Updates.md)
- [ ] [4_Memory_As_Adaptation.md](./Adaptation/4_Memory_As_Adaptation.md)

## 5 · Retrieval and grounding

- [ ] [1_Evidence_And_Indexes.md](./Retrieval-And-Grounding/1_Evidence_And_Indexes.md)
- [ ] [2_Retrieve_Rerank_Generate.md](./Retrieval-And-Grounding/2_Retrieve_Rerank_Generate.md)
- [ ] [3_State_And_Context_Windows.md](./Retrieval-And-Grounding/3_State_And_Context_Windows.md)

## 6 · Control and agency

- [ ] [1_Tool_Use.md](./Control-And-Agency/1_Tool_Use.md)
- [ ] [2_Multi_Step_Control.md](./Control-And-Agency/2_Multi_Step_Control.md)
- [ ] [3_Human_In_The_Loop.md](./Control-And-Agency/3_Human_In_The_Loop.md)
- [ ] [4_MCP_And_Tool_Protocols.md](./Control-And-Agency/4_MCP_And_Tool_Protocols.md)

## 7 · Evaluation

- [ ] [1_Prediction_Metrics.md](./Evaluation/1_Prediction_Metrics.md)
- [ ] [2_Grounded_Generation_Metrics.md](./Evaluation/2_Grounded_Generation_Metrics.md)
- [ ] [3_Offline_Vs_Online.md](./Evaluation/3_Offline_Vs_Online.md)
- [ ] [4_Experiment_Tracking.md](./Evaluation/4_Experiment_Tracking.md)

## 8 · Safety and adversaries

- [ ] [1_Threat_Model.md](./Safety-And-Adversaries/1_Threat_Model.md)
- [ ] [2_Untrusted_Context_And_Exfil.md](./Safety-And-Adversaries/2_Untrusted_Context_And_Exfil.md)
- [ ] [3_Current_Catalogs.md](./Safety-And-Adversaries/3_Current_Catalogs.md) *(dated lists live here)*

## 9 · Inference and serving

- [ ] [1_Memory_And_Compute.md](./Inference-And-Serving/1_Memory_And_Compute.md)
- [ ] [2_Serving_Patterns.md](./Inference-And-Serving/2_Serving_Patterns.md)
- [ ] [3_Cost_And_Resources.md](./Inference-And-Serving/3_Cost_And_Resources.md)
- [ ] [4_Lifecycle_And_Registry.md](./Inference-And-Serving/4_Lifecycle_And_Registry.md)

## 10 · Applied

- [ ] [1_Prediction_Systems.md](./Applied/1_Prediction_Systems.md)
- [ ] [Case_Studies/1_Blog_Series.md](./Applied/Case_Studies/1_Blog_Series.md)
- [ ] [Case_Studies/2_Personal_Retrieval_Over_Notes.md](./Applied/Case_Studies/2_Personal_Retrieval_Over_Notes.md)
- [ ] [Case_Studies/3_Production_Retrieval_App_Layer.md](./Applied/Case_Studies/3_Production_Retrieval_App_Layer.md)

## 11 · Instances (dated)

- [ ] [1_Current_Market_Map.md](./Instances/1_Current_Market_Map.md)

---

## Intentionally elsewhere

| Problem | Primary repo |
|---------|----------------|
| Vector *engines* | [Databases-Deep-Dive/vector](../Databases-Deep-Dive/Vector/README.md) |
| Gateway / cache / rate limit | [System-Design-Concepts/Primer-Gaps/12](../System-Design-Concepts/Primer-Gaps/12_RAG_and_LLM_Gateway_Design.md) |
| Capture → transform → orchestrate | [Data-Engineering-Deep-Dive](../Data-Engineering-Deep-Dive/README.md) |
| Runtime / GPU cluster | Containerization · DevOps-Handbook |
| Full cyber program | Security-Deep-Dive |
| Hello-world of a named framework | Tooling-and-Frameworks-Deep-Dive |

---

## Tooling-and-Frameworks-Deep-Dive

Public intro: [Deep-Dives/Tooling-and-Frameworks-Deep-Dive/README.md](../../Deep-Dives/Tooling-and-Frameworks-Deep-Dive/README.md)

### Start here

# Start here — Tooling and frameworks

*(On-ramp for Tooling — atlas / writing rules / topics live in this syllabus.)*

## Who this repo is for

A **backend engineer** who wants Spring or FastAPI. A **frontend engineer** who wants React. Anyone who needs “when to pick this framework” without a language textbook.

If you wanted **how DevOps works**, you are in the wrong room → [DevOps Handbook](../DevOps-Handbook/Methodologies/0_SE_Learning_DevOps_Start_Here.md).  
If you wanted **architecture**, → [System Design](../System-Design-Concepts/README.md).

## Path

- [ ] [Utility/](./Utility/README.md) (Git / Make) · [Network-Utilities/](./Network-Utilities/README.md) (ping, dig, curl) · [Containers/](./Containers/README.md) (kubectl)
- [ ] [Database-Clients/](./Database-Clients/README.md) · [Security/](./Security/README.md) · [Diagramming/](./Diagramming/README.md) · [Data-ML/](./Data-ML/README.md)
- [ ] Backend: [Web-Backend](./Web-Backend/README.md) → FastAPI or Spring  
- [ ] Frontend: [Web-Frontend](./Web-Frontend/README.md) → React, then Next if you need that delivery shape  
- [ ] Specs: [OpenAPI](./Specs-Standards/OpenAPI/README.md) (APIs as contracts)  
- [ ] Add a new framework folder when you actually use one  

## Checklist

- [x] Domains match the atlas (backend / frontend doors)
- [ ] First framework topic filled (not just stubbed)

### Write order

# Tooling — content write order

**Repo #10** · Door for application code — see Part B (reader atlas) in this file.

**Rule:** Writing rules · **List:** Topics to cover

Fill the framework you *use*, not a popularity list.

## Lane H

| Step | Where |
|------|--------|
| 1 | Atlas + Start here |
| 2 | `Web-Backend/` — FastAPI, Spring, or [Express](./Web-Backend/Express/README.md) (your stack) |
| 3 | `Web-Frontend/` — React, Next if needed |
| 4 | `Specs-Standards/` — OpenAPI first; SOAP + MCP already stubbed |
| 5 | Add named software under the *job* domain (`Network-Utilities/`, `Containers/`, `Data-ML/`, `Security/`, …). **Never** a `Tools/` folder. |
| 6 | Do **not** duplicate Spark/Kafka/Airflow — DE `Systems/` |

## Frameworks v1 (seed in Tooling — not created yet)

The old DevOps plan listed these as a `Frameworks/` folder **in DevOps**. That home is this repo. **Do not add a folder until you use the tool** — this table is only so the old list is not lost.

| Named tool | Likely folder if you add it | Already here? |
|------------|-----------------------------|---------------|
| React, Next | `Web-Frontend/` | yes (stubs) |
| FastAPI, Spring, Express | `Web-Backend/` | yes (stubs) |
| Django, Flask | `Web-Backend/` | yes (stubs) |
| Vue | `Web-Frontend/` | yes (stubs) |
| Angular | `Web-Frontend/Angular/` | no — ask before creating |
| Nest | `Web-Backend/Nest/` | no — ask before creating |
| Rails, Laravel | `Web-Backend/` | no — ask before creating |

### Writing rules

# Writing rules

[← README](./README.md) · atlas now lives in Part B of this file

This repo is the **application-code door**: backend, frontend, mobile, specs. It is not language syntax (DevOps `Languages/`) and not “how CI works” (DevOps `CiCd/`).

| Axis | Stays | Example |
|------|--------|---------|
| Domain folder | The *job* of that kind of software | `Web-Backend/`, `Web-Frontend/` |
| One folder per framework | Named framework on a language | `Web-Backend/Django/` (Python syntax stays in DevOps Languages) |
| One folder per named thing under its *job* | Not a `Tools/` dump | `Utility/Git/`, `Security/Reconnaissance/Nmap/`, `Diagramming/Mermaid/` |
| Named software (CLI, library, scanner, GUI) | Lives in **this** repo under the *job* domain | `Network-Utilities/ping/`, `Containers/kubectl/`, `Data-ML/Learning/PyTorch/` |
| Specs | Contracts that outlive frameworks | `Specs-Standards/OpenAPI/`, GraphQL, gRPC |
| Quality / edge / inner loop | How you test, where else code runs, how you edit | `Quality-And-Testing/`, `Runtime-And-Edge/`, `Developer-Workflow/` |

A new framework: add a folder under the domain. Do not add a new domain unless the job is new (e.g. you actually build games).

Spark / Kafka / Airflow / Trino **do not live here** — [Data-Engineering Systems](https://github.com/thisiskushal31/Data-Engineering-Deep-Dive/tree/main/Systems). Learning *jobs* live in [DS-AI](https://github.com/thisiskushal31/Data-Science-AI-Deep-Dive); a library hello-world lives under `Data-ML/`. **Never add a `Tools/` folder** — this whole repo is that catalog, split by job.

### Topics to cover

# Topics to cover — next step forward

[← README](./README.md) · atlas / timeless now live in this file

Tick when a file has no `*(Content TBD)*`. Add rows when you add a framework folder.

## Next

- [ ] [Web-Backend/FastAPI](./Web-Backend/FastAPI/README.md) or [Spring](./Web-Backend/Spring/README.md) — pick the one you write
- [ ] [Web-Frontend/React](./Web-Frontend/React/README.md)
- [ ] [Specs-Standards/OpenAPI](./Specs-Standards/OpenAPI/README.md)
- [ ] [Quality-And-Testing](./Quality-And-Testing/README.md) — survey (was a landscape gap)

## Web-Backend

- [ ] [FastAPI](./Web-Backend/FastAPI/README.md)
- [ ] [Spring](./Web-Backend/Spring/README.md)
- [ ] [Express](./Web-Backend/Express/README.md)
- [ ] [Django](./Web-Backend/Django/README.md)
- [ ] [Flask](./Web-Backend/Flask/README.md)

## Web-Frontend

- [ ] [React](./Web-Frontend/React/README.md)
- [ ] [Next](./Web-Frontend/Next/README.md)
- [ ] [Vue](./Web-Frontend/Vue/README.md)
- [ ] [Vite](./Web-Frontend/Vite/README.md)

## Utility

- [ ] [Git](./Utility/Git/README.md)
- [ ] [Make](./Utility/Make/README.md)

## Network-Utilities

- [ ] [ping](./Network-Utilities/ping/README.md)
- [ ] [dig](./Network-Utilities/dig/README.md)
- [ ] [curl](./Network-Utilities/curl/README.md)

## Containers

- [ ] [kubectl](./Containers/kubectl/README.md)

## Quality-And-Testing

- [ ] [Jest](./Quality-And-Testing/Jest/README.md)
- [ ] [Playwright](./Quality-And-Testing/Playwright/README.md)

## Security (lab software)

- [ ] [Nmap](./Security/Reconnaissance/Nmap/README.md)
- [ ] [Wireshark](./Security/Defensive/Wireshark/README.md)

## Diagramming

- [ ] [Mermaid](./Diagramming/Mermaid/README.md)
- [ ] [C4](./Diagramming/C4/README.md)

## Database-Clients

- [ ] [DBeaver](./Database-Clients/DBeaver/README.md)

## Automation

- [ ] [n8n](./Automation/n8n/README.md)

## Data-ML workbench

- [ ] [Jupyter](./Data-ML/Workbench/Jupyter/README.md)

## Specs

- [ ] [OpenAPI](./Specs-Standards/OpenAPI/README.md)
- [ ] [OAuth](./Specs-Standards/OAuth/README.md)
- [ ] [OpenTelemetry](./Specs-Standards/OpenTelemetry/README.md)
- [ ] [GraphQL](./Specs-Standards/GraphQL/README.md)
- [ ] [gRPC](./Specs-Standards/gRPC/README.md)
- [ ] [SOAP](./Specs-Standards/SOAP/README.md) — legacy
- [ ] [MCP](./Specs-Standards/MCP/README.md) — agent protocol

## Survey doors (2026 landscape — know they exist)

- [ ] [Quality-And-Testing](./Quality-And-Testing/README.md)
- [ ] [Runtime-And-Edge](./Runtime-And-Edge/README.md)
- [ ] [Developer-Workflow](./Developer-Workflow/README.md)
- [ ] [Desktop](./Desktop/README.md)
- [ ] [Web-Frontend/5_Accessibility_And_I18n.md](./Web-Frontend/5_Accessibility_And_I18n.md)

## Survey (no framework folders yet)

- [ ] [Mobile/README.md](./Mobile/README.md)
- [ ] [Data-ML/README.md](./Data-ML/README.md) — workbench here; learning jobs in DS-AI
- [ ] [Cloud-Platform/README.md](./Cloud-Platform/README.md)

---

## Security-Deep-Dive

Public intro: [Deep-Dives/Security-Deep-Dive/README.md](../../Deep-Dives/Security-Deep-Dive/README.md)

### Start here

# Start here — Security Deep Dive

[← README](./README.md) · Topics · Write order

You can open this repo **knowing nothing**. You do not have to finish Networks or DevOps first. Those homes hold *wire* and *pipeline* depth. This home is the security path from first VM to a program (AppSec, SOC, GRC).

Prose is still last. The **places** are here so you can fill later.

## Path (basic → advanced)

1. Named lab software → [Tooling Security](../Tooling-and-Frameworks-Deep-Dive/Security/README.md) — start [Nmap](../Tooling-and-Frameworks-Deep-Dive/Security/Reconnaissance/Nmap/README.md), then Wireshark / OSINT / web / creds on an **isolated lab** (never the public internet)  
2. [Foundations/](./Foundations/README.md) — CIA, STRIDE, controls  
3. [Threats/](./Threats/README.md) — actors, vectors, vulns  
4. [Cryptography/](./Cryptography/README.md) — pitfalls (TLS handshake → Networks)  
5. [Identity/](./Identity/README.md) · [AppSec/](./AppSec/README.md)  
6. [Cloud-Security/](./Cloud-Security/README.md) · [Defensive-Ops/](./Defensive-Ops/README.md)  
7. [Offensive/](./Offensive/README.md) — PTES phases (OSINT → report), lab only  
8. [GRC/](./GRC/README.md) · [Labs/](./Labs/README.md)

## When you want another slice

| Slice | Home |
|-------|------|
| Packets, Nmap on the wire, Wireshark filters | Networks-Deep-Dive |
| Secrets and scanners in CI | DevOps-Handbook `Security/` |
| Design-time trade-offs | System-Design-Concepts `Security-Tradeoffs/` |

See the related-repos line on the [README](./README.md).

### Write order

# Security Deep Dive — content write order

**Repo #11** · **Status:** folders + stub files exist · **Phase:** 4 **CAPSTONE** — prose last

Prerequisites: working depth in DevOps, Networks, System Design, Databases, Containers (Ecosystem Report §7 Phase 4).

Planned tree: **README (lab rule) → Foundations → Threats → Cryptography → Identity → AppSec → Cloud-Security → Defensive-Ops → Offensive → GRC → Labs.** Named software (Nmap, Wireshark, Burp) → Tooling `Security/`.

## Lane I — fill order (after Phase 1–3 repos have substance)

| Step | Section | Industry benchmark |
|------|---------|-------------------|
| 1 | README intro (isolated lab; never scan the public internet) | Security+ domain 1 |
| 2 | Tooling `Security/` — Nmap, then Wireshark, tcpdump, Burp (install + first use) | Hands-on; wire depth → Networks |
| 3 | Foundations: CIA, STRIDE, controls | CompTIA Security+ / SOC paths |
| 3 | Application-Security: OWASP Top 10, API, secure SDLC | |
| 4 | Identity: OAuth/OIDC/SAML, zero trust | |
| 5 | Cloud-Security: CSPM, secrets, K8s, supply chain | |
| 6 | Defensive-Ops: SIEM, IR, forensics | MITRE ATT&CK |
| 7 | Offensive (lab-only): recon, methodology | |
| 8 | GRC: NIST, ISO overview, MITRE ATT&CK mapping | |
| 9 | Cryptography (practical pitfalls) | |
| 10 | Labs: HTB/TryHackMe paths | |

**Do NOT duplicate:** Networks/Security (L3–L7) · DevOps/Security (pipeline) · System-Design/security-tradeoffs (design-time)

### Topics to cover

# Topics to cover — Security Deep Dive

[← README](./README.md) · Write order · Start

Tick when a file has no `*(Content TBD)*`. Path is **basic → advanced**. You can fill this repo without finishing the other ten.

## Next

- [ ] [Nmap install](../Tooling-and-Frameworks-Deep-Dive/Security/Reconnaissance/Nmap/1_Install.md)
- [ ] [Wireshark install](../Tooling-and-Frameworks-Deep-Dive/Security/Defensive/Wireshark/1_Install.md)

## Tree (in path order)

- [ ] Named lab software → [Tooling Security](../Tooling-and-Frameworks-Deep-Dive/Security/README.md) (Nmap, Wireshark, theHarvester, Burp, Nuclei)
- [ ] [Offensive/](./Offensive/README.md) — PTES phases 1–9
- [ ] [Foundations](./Foundations/README.md)
- [ ] [Threats](./Threats/README.md)
- [ ] [Cryptography](./Cryptography/README.md)
- [ ] [Identity](./Identity/README.md)
- [ ] [AppSec](./AppSec/README.md)
- [ ] [Cloud-Security](./Cloud-Security/README.md)
- [ ] [Defensive-Ops](./Defensive-Ops/README.md)
- [ ] [Offensive](./Offensive/README.md)
- [ ] [GRC](./GRC/README.md)
- [ ] [Labs](./Labs/README.md)
