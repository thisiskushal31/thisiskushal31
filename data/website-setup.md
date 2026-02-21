# Website setup and purpose

*Reference when you’re away from your PC: URLs, repos, who each site is for, what’s done vs to-do. Kept in the **thisiskushal31** repo.*

**Repos:** All under **thisiskushal31**. Private repo links are for you/authorized only.

---

## Quick map: URL → purpose

| Website | URL | Repo | Audience / purpose |
|--------|-----|------|--------------------|
| **Portfolio** | [kushal.cv](https://kushal.cv/) | — | Clients and employers. Presents you as a **DevOps engineer** (current focus). |
| **Blog** | [blog.kushal.cv](https://blog.kushal.cv/) | — | Your tech writing. Shows breadth beyond “only DevOps” (useful when some employers assume otherwise). |
| **Bio / link-in-bio** | [bio.kushal.cv](https://bio.kushal.cv/) | thisiskushal31/thisiskushal31.github.io | Employer-facing: social profiles, important links. Used when sharing with employers. |
| **Freelance link** | [link.kushal.cv](https://link.kushal.cv/) | [thisiskushal31/link-freelance](https://github.com/thisiskushal31/link-freelance) (private) | Presents you as a **software engineer who handles things end-to-end** (same as GitHub profile). **Keep hidden** from employers who only want "DevOps"; use for client/freelance outreach. |
| **DocHub** | [thisiskushal31.github.io/dochub](https://thisiskushal31.github.io/dochub/) | — | Documentation hub. Learning notes, references. |
| **GitHub Pages root** | [thisiskushal31.github.io](https://thisiskushal31.github.io/) | thisiskushal31/thisiskushal31.github.io | Redirects visitors to **bio.kushal.cv**. Backup if domain or hosting changes. |

---

## Per-website details

### 1. Portfolio → kushal.cv
- **Host:** Vercel → `kushal.cv`
- **Purpose:** Main professional face for both **clients and employers**. DevOps-focused as of now.
- **Tech:** React, Vite, TypeScript, Tailwind, BrowserRouter. Clean URLs, no hash.
- **Status:** ✅ Live. Analytics and Speed Insights on.

### 2. Blog → blog.kushal.cv
- **Host:** Vercel → `blog.kushal.cv`
- **Purpose:** Your blog. Proves you do more than “just DevOps” (writing, full-stack, etc.)—useful with employers who assume otherwise.
- **Tech:** React, Vite, TypeScript, Tailwind, BrowserRouter. Clean URLs: `blog.kushal.cv/{slug}`.
- **Status:** ✅ Live. SEO, sitemap, analytics.

### 3. Bio / link-in-bio → bio.kushal.cv
- **Repo:** github.com/thisiskushal31/thisiskushal31.github.io
- **Host:** GitHub Pages at `thisiskushal31.github.io`; custom domain `bio.kushal.cv` if configured.
- **Purpose:** Employer-facing: one link to socials, portfolio, blog, DocHub. Safe to share with any employer.
- **Tech:** React, Vite, TypeScript, Tailwind, **HashRouter** (for GitHub Pages). Routes like `/#/`, `/#/section/...`.
- **Status:** ✅ Live.

### 4. Freelance link → link.kushal.cv
- **Repo:** [github.com/thisiskushal31/link-freelance](https://github.com/thisiskushal31/link-freelance) (private)
- **Host:** Vercel → `link.kushal.cv`
- **Purpose:** Presents you as a **software engineer who handles things end-to-end**—aligned with your GitHub profile (full lifecycle, full-stack, DevOps, etc.). For client/freelance outreach. **Intentionally not shared** with employers who only see you as “DevOps.”
- **Tech:** React, Vite, TypeScript, Tailwind, BrowserRouter.
- **Status:** ✅ Live.

### 5. DocHub → thisiskushal31.github.io/dochub
- **Host:** GitHub Pages → `thisiskushal31.github.io/dochub/`
- **Purpose:** Your documentation hub (notes, references, learning).
- **Status:** ✅ Live.

### 6. GitHub Pages root → thisiskushal31.github.io
- **Repo:** github.com/thisiskushal31/thisiskushal31.github.io
- **Behavior:** Redirects visitors to **bio.kushal.cv** (or the bio link site).
- **Purpose:** Backup entry point if you change domain or hosting; people hitting the GitHub Pages URL still land on your bio.

---

## What’s done vs what needs to be done

- [x] Portfolio on kushal.cv (DevOps-focused).
- [x] Blog on blog.kushal.cv.
- [x] Bio/link site (thisiskushal31.github.io → bio.kushal.cv).
- [x] DocHub at thisiskushal31.github.io/dochub.
- [x] GitHub Pages root redirects to bio.
- [x] **link.kushal.cv** (repo: thisiskushal31/link-freelance): deployed and live. Keep off employer-facing materials.
- [x] Legacy link site (thisiskushal31.github.io/link) retired — deleted, no longer there.

---

## Important notes for future you

1. **Portfolio** = one face for clients and employers; currently DevOps.
2. **Blog** = proof you do more than DevOps; fine to share with employers.
3. **link.kushal.cv** = you as **end-to-end software engineer** (same as GitHub). For freelance/client use; don’t link from portfolio or bio when targeting “DevOps-only” employers.
4. **bio.kushal.cv** = main link you give to employers (portfolio, blog, DocHub, socials).
5. **thisiskushal31.github.io** = backup entry; redirects to bio so it still works if domain changes.

For full technical details (routers, deployment, URLs, verification checklist), see **WEBSITE_SETUP.md** (same repo or wherever you keep it).

---

*Last updated: Feb 2025. Repo: thisiskushal31.*
