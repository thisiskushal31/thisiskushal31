# ChatGPT prompt: generate project banner image for Data Science Infrastructure (Project 8)

Use this prompt in ChatGPT (with image generation) to create a banner image that matches the style of the other project images in `assets/projects/` (e.g. 1, 4, 5, 6, 7, 9).

---

**Prompt to paste into ChatGPT:**

Create a clean, modern **architecture diagram** image for a GitHub project README with this exact style and content:

**Style (match these project banner images):**
- **Layout:** White or very light grey background. Title at top (large, bold, dark grey sans-serif). One line of key metrics directly below in smaller blue or grey text.
- **Main area:** Left-to-right or grouped flow diagram. Use **rounded rectangular boxes** for components. **Solid grey or blue arrows** for primary data/flow; **dashed arrows** for secondary connections or boundaries. Slight 3D/shadow on boxes. Group related items inside **dashed outlines**.
- **Icons:** Use recognizable tech icons where possible (Kubernetes wheel, cloud icons for GCP, database cylinder, server/laptop, document/code). Simple, line-art or flat style. Blue for main components, green for positive outcomes, orange only for alerts if needed.
- **Bottom:** A row of **summary badges/cards** (small rounded rectangles with icon + short label) for key metrics or technologies.
- **Overall:** Professional, uncluttered, easy to read. No photos. Diagram should look like the other Purplle infrastructure project banners (e.g. Monitoring, AdTech, RAG, Grid Platform).

**Content to show:**

1. **Title (top):**  
   **Data Science Infrastructure**  
   Subtitle: **Two Infrastructures | Multi-Project GCP**

2. **Key metrics line (below title):**  
   **₹700 Cr Revenue Backbone | 50–60% Cost Saving**

3. **Main diagram – two flows:**

   **Flow 1 – Kubernetes (serving):**  
   Nginx Ingress / SSL → **Kubernetes** (Python containerized services) → Internal domain → consumers: Recommendation engine, Data engineering, Storefront. Then show: **K8s → Vertex AI** (one arrow from K8s to Vertex AI, labeled e.g. “hits for inference”). Vertex AI is a single box at the end; do not show Vertex AI in the middle of any flow.

   **Flow 2 – Training → Vertex AI:**  
   **Jupyter VM** (training) → “model” or “storage” → **Vertex AI** (model upload). Show triggers: **Cloud Function** (with arrow “hits K8s first” to the K8s box), **Script on VM**, **Direct (IAM)**.

   **Critical:** Vertex AI must appear only as (a) the **destination** of the model upload from Jupyter and (b) the **inference endpoint** that **only K8s calls** (one-way arrow from K8s to Vertex AI). Vertex AI does not have arrows going out to other components (it only returns output to the caller).

4. **Bottom badges (row of small cards):**  
   Kubernetes | Jupyter | Vertex AI | Cloud Function | Nginx | Multi-Project GCP | CI/CD

Output a single image, landscape orientation, suitable for a README (e.g. 1200×630 or similar banner aspect). No watermarks. Match the visual style of standard DevOps/architecture diagrams (blue/grey/white, clear arrows, labeled boxes).

---

**Note:** If ChatGPT cannot generate images, use DALL·E or another image model with this same description. The image should be saved as `8_Data_Science_Infrastructure.png` in the repo under `assets/projects/`.
