# Cold Email Generator - Value-Driven Prompt System

A recursive prompt system to generate short, crisp, and value-driven cold emails that demonstrate excitement and clear value proposition.

> **📌 Important:** Before using these prompts, load the comprehensive career context from `../career-context.md` which contains all your professional information, achievements, skills, projects, and metrics. This will ensure your emails are accurate and value-driven.

## 📋 Two-Stage Process

### Stage 1: Information Collection

**IMPORTANT:** First, load the career context from `../career-context.md` to get all professional information, achievements, and skills.

**Prompt to use:**

```
I need to craft a value-driven cold email. I've provided my complete career context below. Please use it along with the following information:

**My Career Context:**
[PASTE CONTENTS FROM ../career-context.md HERE]

**Stage 1 - Additional Information Needed:**

1. **Job Description (JD)**:
   - Job title
   - Key responsibilities
   - Required skills
   - Company name and role context

2. **Company Profile**:
   - Company name
   - What they do (industry, products/services)
   - Recent news, initiatives, or projects
   - Company values or mission
   - Any specific challenges they might be facing
   - Their tech stack (if known)

3. **Contact & Context**:
   - Recipient's name/email (if known)
   - Any mutual connections
   - How you found out about the role/company
   - Specific reason for reaching out

Once you have all this information, I'll move to Stage 2 to generate the personalized cold email.
```

---

### Stage 2: Email Generation

**Prompt to use (after Stage 1 data is collected):**

```
Based on the following information, generate a short, crisp, value-driven cold email:

**My Complete Career Context:**
[PASTE CONTENTS FROM ../career-context.md HERE - OR reference it if already loaded]

**Job Description:**
[PASTE JD HERE]

**Company Profile:**
[PASTE COMPANY INFO HERE]

**Contact & Context:**
[PASTE CONTACT & CONTEXT INFO HERE]

**Email Requirements:**
1. **Subject Line**: Create a compelling, personalized subject (max 50 characters)
2. **Opening**: Brief, personal connection or hook (1-2 sentences)
3. **Value Proposition**: 3-4 bullet points showing specific value you bring:
   - How your skills solve their problems
   - Quantifiable achievements relevant to the role
   - Unique insights or approaches you can offer
   - Specific contributions you can make
4. **Enthusiasm**: Show genuine excitement about the company/role (1 sentence)
5. **Clear Ask**: Specific, actionable request (1 sentence)
6. **Closing**: Professional but warm sign-off

**Style Guidelines:**
- Keep total email under 150 words
- Be specific, not generic
- Show you've researched the company
- Demonstrate clear value, not just interest
- Match the tone of the company culture
- Use active voice and strong verbs

Generate the email now.
```

---

## 🎯 Example Structure (Based on Best Practices)

### Email Template:

```
Subject: [Personalized, attention-grabbing, under 50 chars]

Hey [Name],

[1-2 sentence personal connection or hook - mention mutual connection, recent company news, or specific reason for reaching out]

I'm [your name], [brief role/background]. Here's how I can contribute:

• [Specific value point 1 - quantifiable if possible]
• [Specific value point 2 - tied to their needs]
• [Specific value point 3 - unique insight/approach]
• [Specific value point 4 - immediate impact]

[1 sentence showing genuine excitement about the company/role]

[Clear, specific ask - e.g., "Would love to discuss how I can help [specific goal] at [Company]."]

[Professional closing],
[Your name]
```

---

## 💡 Key Principles

1. **Value-First**: Lead with what you can do for them, not what you want
2. **Specificity**: Use concrete examples, numbers, and specific skills
3. **Research**: Show you understand their company and challenges
4. **Brevity**: Respect their time - get to the point quickly
5. **Enthusiasm**: Genuine excitement is contagious
6. **Clear Ask**: Make it easy for them to say yes

---

## 🔄 Usage Workflow

1. **Run Stage 1 Prompt**: Collect all necessary information
2. **Review & Refine**: Ensure all information is complete
3. **Run Stage 2 Prompt**: Generate the email with all collected data
4. **Review & Customize**: Personalize further if needed
5. **Send**: Proofread and send!

---

## 📝 Notes

- Always personalize - never use generic templates
- Research the company thoroughly before drafting
- Follow up if no response after 1-2 weeks
- Keep subject lines under 50 characters for mobile
- Test different subject lines for A/B testing
- Track which emails get responses to refine approach

## 🔗 Related Documents

- **Career Context:** `../career-context.md` - Complete professional profile, achievements, skills, and projects
- **Job Search Strategy:** `../plans/JOB_CHANGE_TASKS.md` - Job search tasks and alignment strategy
- **GitHub Profile:** `../README.md` - Public GitHub profile information

## 💡 Quick Start

1. **Load Career Context:** Read `../career-context.md` to get all your professional information
2. **Research Company:** Gather JD and company information
3. **Run Stage 1 Prompt:** Provide career context + company/JD info
4. **Run Stage 2 Prompt:** Generate the email
5. **Review & Send:** Customize if needed, then send!

