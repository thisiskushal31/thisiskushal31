# Portfolio Website Build Prompt for Lovable

Create a modern portfolio website for Kushal Gupta (https://kushal.cv/) optimized for freelance clients (subtle messaging) while remaining recruiter-friendly. The site will be deployed on Vercel.

## Project Overview

Build a complete portfolio website from scratch with:
- **Complete redesign** - Fresh design inspired by blog homepage ([https://thisiskushal31.github.io/blog/#/blog](https://thisiskushal31.github.io/blog/#/blog))
- Single-page homepage with horizontal profile picture and personal details
- Separate pages for Experience, Projects, and Contact
- Configuration-driven architecture for easy content management
- Dark mode only design (no light mode toggle)
- Full responsive design
- **Profile Picture**: Horizontal/landscape photo of Kushal Gupta (will be provided, path in config)

## Design Direction

Design inspiration: **karadhub.dev** ([https://www.karadhub.dev/](https://www.karadhub.dev/)) and **primaspot.com** ([https://www.primaspot.com/](https://www.primaspot.com/)) - combining the best of both:

### From karadhub.dev:
- Clean, professional portfolio layout structure
- Hero section with profile picture, name, title, location, timezone
- Well-organized sections: About, Tech Stack, Experience, Education, Certifications, Projects, Blog, Contact
- Categorized tech stack display
- Timeline-based experience and education sections
- Professional certifications showcase
- Blog posts preview section
- Contact form integration

### From primaspot.com:
- **Dark mode only** - No light mode toggle, site is always in dark mode
- Ultra-clean, minimal aesthetic
- Elegant card-based layouts
- Generous whitespace
- Large, bold typography with clear hierarchy
- Professional dark color palette (dark backgrounds, light text)
- Subtle shadows and smooth animations
- Modern, sophisticated design

**Complete redesign** - This is a fresh design combining the structure and organization of karadhub.dev with the elegant, minimal aesthetic of primaspot.com.

- **Horizontal profile picture** - Professional horizontal/landscape photo of Kushal Gupta
- Clean, minimal hero section with personal details
- Stats displayed inline or as cards
- Full responsive design with mobile-first approach

Let Lovable make design decisions for spacing, colors, animations, and component styling while maintaining this aesthetic direction. All colors and styling should be optimized for dark mode.

## Color Format

Follow the color format from primaspot.com and karadhub.dev (professional dark mode):
- **Background**: Very dark gray/black (near-black, #0a0a0a or similar)
- **Card Backgrounds**: Slightly lighter dark gray (#1a1a1a or similar) with subtle borders
- **Primary Text**: White or very light gray (#ffffff or #f5f5f5)
- **Secondary Text**: Medium gray (#a0a0a0 or similar) for descriptions and muted content
- **Accent Colors**: Use sparingly for CTAs, links, and highlights (can be a vibrant blue, purple, or brand color)
- **Borders**: Subtle, low-opacity borders (#333333 or similar)
- **Hover States**: Slight brightness increase or subtle glow effects
- **Badges/Tags**: Subtle background with border, muted colors
- **Gradients**: Can use subtle gradients for text (name/headings) or backgrounds
- **Overall**: High contrast for readability, but not harsh - maintain elegance and sophistication

## Tech Stack

- React 18 + TypeScript
- Vite (build tool)
- React Router DOM (BrowserRouter - works on Vercel and better for SEO)
- Tailwind CSS + shadcn/ui components
- @radix-ui components (accordion, dialog, etc.)
- Lucide React icons
- **Dark mode only** - No theme toggle needed, site is always dark

## Configuration Structure

All content must be configuration-driven via `src/config/portfolio.ts`. Create this file with the following structure:

**Note**: Lovable is free to modify this config structure as needed to best fit the implementation. The structure below is a suggested starting point - feel free to reorganize, add fields, or adjust types as necessary for the best implementation.

```typescript
export const portfolioConfig = {
  personal: {
    name: string;
    initials: string;
    title: string;
    subtitle: string;
    description: string;
    location: string;
    timezone: string;
    email: string;
    profileImage?: string; // Path to horizontal profile picture
  },
  skills: {
    categories: Array<{
      title: string;
      icon: string; // emoji
      skills: string[];
    }>;
  },
  projects: Array<{
    title: string;
    company?: string;
    description: string;
    technologies: string[];
    features: string[];
    links?: {
      github?: string;
      demo?: string;
    };
    status: 'Production' | 'Active Development' | 'Beta' | 'Archived';
    category: 'Platform Engineering' | 'DevSecOps' | 'DevOps' | 'Software Engineering';
  }>;
  quickActions: Array<{
    name: string;
    url: string;
    icon: string; // Lucide icon name
    description: string;
  }>;
  socialLinks: Array<{
    name: string;
    url: string;
    icon: string; // 'Linkedin' | 'Github'
  }>;
  featuredProjects?: string[]; // Array of project titles to feature on homepage
  skillsDefaultExpanded?: string[]; // Array of category titles to expand by default
  blogUrl?: string; // Configurable blog link
  bioLinksUrl?: string; // Configurable bio links
  stats?: Array<{
    value: string; // e.g., "3+", "99%+"
    label: string; // e.g., "Years", "Uptime Achieved"
    color?: string; // Optional color override
  }>;
  targetRoles?: string[]; // Array of target roles for "Expanding Into" section
  experienceSummary?: string; // Summary text for experience card
  sections?: {
    about?: {
      title?: string;
      description?: string;
      focusAreas?: Array<{
        title: string;
        description: string;
      }>;
      closing?: string;
    };
    techStack?: {
      title?: string;
      categories?: string[]; // e.g., ["All", "Core DevOps", "Cloud", "Security"]
    };
    skills?: {
      title?: string;
      subtitle?: string;
    };
    currentFocus?: {
      title?: string;
      subtitle?: string;
      expandingIntoTitle?: string;
      expandingIntoDescription?: string;
      experienceTitle?: string;
      experienceButtonText?: string;
    };
    featuredProjects?: {
      title?: string;
      subtitle?: string;
      viewAllButtonText?: string;
    };
    latestInsights?: {
      title?: string;
      subtitle?: string;
      buttonText?: string;
    };
    finalCTA?: {
      title?: string;
      description?: string;
      buttonText?: string;
    };
  };
}
```

**Note**: Use placeholder/example data in the config file. The actual data values will be filled in later.

## Pages Structure

Create the following pages:

### 1. Homepage (`/` - `src/pages/Index.tsx`)
Single-page portfolio with all sections below. Skills are fully integrated here via expandable accordion.

### 2. Experience Page (`/experience` - `src/pages/Experience.tsx`)
Full experience page showing:
- Professional timeline with job history
- Achievements and responsibilities
- Technologies used
- Education section
- Company details and locations

### 3. Projects Page (`/projects` - `src/pages/Projects.tsx`)
Full projects page with:
- All projects from config
- Category filtering (All, DevOps, DevSecOps, Platform Engineering, Software Engineering)
- Project cards with full details
- Links to GitHub and demos

### 4. Contact Page (`/contact` - `src/pages/Contact.tsx`)
Contact page with:
- Contact information (email, location, timezone)
- Quick action buttons
- Collaboration types
- Response time information

## Homepage Sections (Detailed Requirements)

The homepage should be a single page displaying full work portfolio with these sections. **Add section navigation CTAs** to help users jump between sections (e.g., sticky navigation, floating buttons, or section links).

### 1. Hero Section (Inspired by karadhub.dev)
- **Layout**: Clean hero section with profile picture and personal details (inspired by karadhub.dev structure)
  - **Profile Picture**: Horizontal/landscape photo of Kushal Gupta (left side or centered)
    - Professional horizontal/landscape photo
    - Rounded corners or elegant frame
    - Responsive sizing
  - **Content Layout**: Name, title, and details (similar to karadhub.dev style)
- **Content** (inspired by karadhub.dev hero section):
  - **Name**: Large, bold heading (from config.personal.name) - "Kushal Gupta"
  - **Title**: Professional title (from config.personal.title) - "Software Engineer" or "BizOps Engineer" style
  - **Subtitle/Tags**: Skills/tags displayed as badges or inline (from config.personal.subtitle) - format: "DevOps • Cloud • SRE" or "Platform Engineering · DevOps · Cloud Infrastructure"
  - **Location**: Display location (from config.personal.location) - "Mumbai, India"
  - **Timezone**: Display timezone (from config.personal.timezone) - "UTC+05:30"
  - **Availability**: Optional availability status (can be from config)
  - **Description**: Professional tagline paragraph (from config.personal.description) - displayed below hero
- **CTA buttons**:
  1. "View My Work" → Smooth scroll to Featured Projects section
  2. "Connect" → Links to `/contact` page
  3. "All Links" → External link to bioLinksUrl (or default: `https://thisiskushal31.github.io/link/#/`) - opens in new tab
- **Social Links**: LinkedIn and GitHub icons (from config.socialLinks)
- **Profile Picture**: Horizontal/landscape photo - path from config (e.g., `config.personal.profileImage`)

### 2. Quick Stats Section (Optional - Can be integrated into Hero)
- **Note**: Stats can be displayed inline in the Hero section (like blog homepage) OR as a separate section
- If separate section:
  - **Layout**: Flexible, responsive grid that adapts to any number of stats
  - Use CSS Grid with `auto-fit` or `auto-fill` to handle variable stat counts gracefully
  - Mobile: 2 columns minimum
  - Desktop: Automatically adjusts to fit all stats (4-6 columns depending on count)
  - Equal spacing and sizing for all stat cards
  - Design should handle adding/removing stats without layout breaks or visual tension
- **Stats**: **MUST come from config.stats array** (not hardcoded)
  - Each stat has: value (e.g., "3+", "99%+"), label (e.g., "Years", "Uptime Achieved"), optional color
  - Example stats (will be in config):
    - "3+" Years
    - "6+" Projects Deployed
    - "99%+" Uptime Achieved
    - "2+" Cloud Platforms
    - Note: "1+ Clients Projects Delivered" can be added to config later - layout accommodates this seamlessly
- **Styling**: 
  - Large numbers, colored (primary, syntax-green, syntax-orange, syntax-purple, and additional accent colors as needed)
  - All stat cards should have equal width/height for consistency
  - Responsive text sizing
- **Animation**: Subtle slide-in animations with staggered delays

### 3. About Me Section (Inspired by karadhub.dev)
- **Title**: "About Me" (from config.sections.about.title or default)
- **Main Description**: Professional summary paragraph (from config.personal.description or config.sections.about.description)
- **Sub-sections** (inspired by karadhub.dev's About section):
  - Can have 3-4 key focus areas displayed as cards or sections
  - Examples: "Automation", "Resilience & Security", "Observability", "Enablement"
  - Each with a brief description
  - Content from config.sections.about.focusAreas array (optional)
- **Closing statement**: Optional closing line (from config.sections.about.closing)

### 4. Tech Stack Section (Inspired by karadhub.dev)
- **Title**: "My Tech Stack & Tools" (from config.sections.techStack.title or default)
- **Layout**: Categorized display similar to karadhub.dev
  - Categories: "All", "Core DevOps", "Cloud", "Security", "Observability", "Development", "Supporting" (or from config)
  - Filter buttons to show/hide categories
  - Skills displayed as badges/icons with names
- **Implementation**: 
  - Use expandable accordion OR filterable grid (Lovable can decide best approach)
  - Each category shows skills from config.skills.categories
  - Skills displayed as badges with icons (if available) or text
  - Clean, organized layout matching karadhub.dev style
- **All skills should be visible on homepage** (via filters or expanders)

### 5. Current Focus Section (Optional)
- **Layout**: Two-column grid (responsive: stacks on mobile)
- **Section Title**: From `config.sections.currentFocus.title` (optional)
- **Section Subtitle**: From `config.sections.currentFocus.subtitle` (optional)
- **Left Card** ("Expanding Into"):
  - Title: From `config.sections.currentFocus.expandingIntoTitle` (default: "Expanding Into")
  - Description: From `config.sections.currentFocus.expandingIntoDescription` (optional)
  - List of target roles: **MUST come from `config.targetRoles` array** (not hardcoded)
  - Each role as bullet point with colored dot
- **Right Card** ("Experience"):
  - Title: From `config.sections.currentFocus.experienceTitle` (default: "Experience")
  - Summary: From `config.experienceSummary` (not hardcoded)
  - **Prominent CTA button**: Text from `config.sections.currentFocus.experienceButtonText` (default: "View Experience") → Links to `/experience` page
- **Background**: Subtle muted background section

### 6. Featured Projects Section
- **Title**: From `config.sections.featuredProjects.title` (default: "Featured Projects" if not provided)
- **Subtitle**: From `config.sections.featuredProjects.subtitle` (optional)
- **Projects Display**:
  - Show 3-4 featured projects
  - Filter logic: `portfolioConfig.projects.filter(p => p.status === 'Production' || p.status === 'Active Development')`
  - If `featuredProjects` array exists in config, use those titles; otherwise take first 3-4 from filtered list
- **Project Card** (each):
  - Title, company badge (if exists), status badge (color-coded)
  - Description (1-2 lines, truncated if needed)
  - Key technologies (badges, max 5-6 most important)
  - 2-3 key features/achievements (bullet points)
  - Links: GitHub button (if available), Demo/Details button (if available)
- **Layout**: Grid (2 columns on desktop, 1 on mobile)
- **CTA button**: Text from `config.sections.featuredProjects.viewAllButtonText` (default: "View All Projects") → Links to `/projects` page (prominent, centered)

### 7. Latest Insights / Blog Section (Inspired by karadhub.dev)
- **Title**: "From My Blog" or from `config.sections.latestInsights.title` (default: "From My Blog" if not provided)
- **Subtitle**: "Insights on [topics]" or from `config.sections.latestInsights.subtitle` (optional)
- **Layout**: Display 3-4 latest blog posts (if available) OR just a CTA button
- **Blog Posts** (if displaying posts):
  - Each post card shows: title, excerpt, date, read time, views (if available)
  - "Read Full Post" link for each
  - "View all posts" button at the end
- **Button**: Text from `config.sections.latestInsights.buttonText` (default: "Read Blog" or "View all posts") → External link to `config.blogUrl` (or default: `https://thisiskushal31.github.io/blog`) - opens in new tab
- **Background**: Subtle muted background section

### 8. Final CTA Section
- **Title**: From `config.sections.finalCTA.title` (default: "Ready to Collaborate?" if not provided)
- **Description**: From `config.sections.finalCTA.description` (optional)
- **Button**: Text from `config.sections.finalCTA.buttonText` (default: "Get In Touch") → Links to `/contact` page (prominent, large)
- **Layout**: Centered, max-width container

## Section Navigation

Add navigation CTAs throughout the homepage to help users jump between sections:
- **Sticky navigation** (optional): Floating menu or anchor links to jump to sections
- **Section-to-section CTAs**: Links/buttons within sections to navigate to other relevant sections
- **Smooth scroll**: All internal section navigation should use smooth scroll behavior
- **Clear CTAs to full pages**: Make sure CTAs to `/experience`, `/projects`, and `/contact` pages are clear and prominent

## Navigation Component

Create a navigation component (`src/components/Navigation.tsx`) with:
- Logo/Brand (initials or name)
- Navigation links: Home, Experience, Projects, Contact
- Sticky positioning (top of page)
- Mobile menu (hamburger menu)
- Active state highlighting
- **No theme toggle** (dark mode only)

## Technical Requirements

### Configuration
- **ALL content must be configurable via `src/config/portfolio.ts`** - no hardcoded values
- Use the config structure provided above
- All text, titles, subtitles, stats, roles, and button labels should come from config
- Provide sensible defaults for optional fields if not specified in config
- The config file is the single source of truth for all content

### Skills Accordion
- Use shadcn/ui Accordion component from @radix-ui/react-accordion
- Map `portfolioConfig.skills.categories` to Accordion items
- Smooth animations, no layout shifts
- Accessibility: Proper ARIA labels, keyboard navigation

### Featured Projects
- Filter: `portfolioConfig.projects.filter(p => p.status === 'Production' || p.status === 'Active Development')`
- Use featuredProjects array if available, otherwise take first 3-4
- Smooth scroll to projects section when "View My Work" is clicked

### Routing
- Use BrowserRouter (works on Vercel and better for SEO with clean URLs)
- Routes:
  - `/` → Homepage (Index.tsx)
  - `/experience` → Experience page
  - `/projects` → Projects page
  - `/contact` → Contact page
  - `*` → 404/NotFound page
- Internal links: React Router `<Link>`
- External links: `<a>` with `rel="noopener noreferrer"` and `target="_blank"`
- Smooth scroll for anchor links within homepage

### Code Quality
- Maintainable, scalable, robust architecture
- TypeScript strict mode
- Proper error handling
- Responsive design (mobile-first)
- **Dark mode only** - No theme toggle, no theme switcher in navigation
- Accessibility compliance (ARIA labels, keyboard navigation, semantic HTML)
- Component-based architecture with reusable components

### Styling
- Tailwind CSS with custom configuration
- Use shadcn/ui components
- Custom animations (fade-in, slide-in)
- Responsive breakpoints (sm, md, lg, xl)
- Dark mode color palette (as specified above)

## Deliverables

1. **Complete website structure**:
   - Homepage (`src/pages/Index.tsx`) with all 7 sections
   - Experience page (`src/pages/Experience.tsx`)
   - Projects page (`src/pages/Projects.tsx`) with category filtering
   - Contact page (`src/pages/Contact.tsx`)
   - Navigation component (`src/components/Navigation.tsx`)
   - 404/NotFound page

2. **Configuration file** (`src/config/portfolio.ts`):
   - Complete TypeScript interface
   - Placeholder/example data

3. **Features**:
   - Skills fully integrated via expandable accordion on homepage
   - Section navigation CTAs to jump between sections
   - Clear CTAs to `/experience`, `/projects`, and `/contact` pages
   - Smooth scroll behavior
   - Category filtering on projects page

4. **Design**:
   - Dark mode only (no theme toggle)
   - Color format matching primaspot.com (very dark backgrounds, light text, subtle accents)
   - Full responsive design (mobile-first)
   - Smooth animations and transitions
   - Professional, elegant aesthetic

5. **Technical**:
   - TypeScript strict mode
   - Accessibility compliance
   - Error boundaries
   - Proper routing setup
   - External link security (rel="noopener noreferrer")

6. **Package.json**:
   - All necessary dependencies
   - Build scripts for Vercel deployment
