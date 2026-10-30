---
tags: [ai-prompts, resource]
---

# 🤖 AI Prompts Library

> A collection of reusable AI prompts for software development. Copy, customize, and paste into your AI tool.
>
> 🏆 **Looking for real battle-tested prompts from my IDE sessions?** Open **[[My Best IDE Prompts (Antigravity Vault)]]** (30 curated prompts extracted across all 79 Antigravity IDE conversations) and **[[Bayanihan Hub Admin Demo Data Prompt]]**.

---

## 📋 Project Planning Prompts

### MVP Planning Prompt
**Purpose:** Get an AI to help you plan a Minimum Viable Product
**When to use:** Starting a new project or feature

```
I'm building [project name], a [type of application] for [target users].

The main problem it solves: [problem description]

Core features I need:
1. [feature 1]
2. [feature 2]
3. [feature 3]

My tech stack: [technologies]

Help me define the MVP — what is the simplest version that delivers value?
Include: essential features, database schema, and a task breakdown.
Skip features that can be added later.
```

### Full-Stack Application Prompt
**Purpose:** Plan a complete application architecture
**When to use:** Designing a new application from scratch

```
I need to build a [type] application with these requirements:
- Frontend: [React/etc]
- Backend: [Flask/etc]
- Database: [MySQL/etc]

The application should:
1. [requirement 1]
2. [requirement 2]
3. [requirement 3]

User roles: [list roles]

Please provide:
1. System architecture overview
2. Database schema (3NF)
3. API endpoint list
4. Frontend page/component structure
5. Authentication approach
6. A phased development plan
```

### Database Design Prompt
**Purpose:** Design a normalized database schema
**When to use:** Creating or redesigning a database

```
I need a MySQL database for [project description].

The main entities are:
1. [Entity 1] — [description]
2. [Entity 2] — [description]
3. [Entity 3] — [description]

Relationships:
- [Entity 1] has many [Entity 2]
- [etc.]

Requirements:
- Use 3NF normalization
- Include appropriate data types
- Add necessary indexes
- Include created_at timestamps

Provide CREATE TABLE statements and explain the normalization decisions.
```

### API Design Prompt
**Purpose:** Design REST API endpoints
**When to use:** Planning backend API structure

```
I'm building a REST API with Flask for [project description].

Resources to manage:
1. [Resource 1] — CRUD operations
2. [Resource 2] — CRUD operations

Authentication: [type]
User roles: [roles]

Provide:
1. Complete endpoint list (method, URL, description, auth required)
2. Request/response JSON examples for each endpoint
3. Error handling approach
4. Status codes to use
```

---

## 🐛 Debugging Prompts

### Frontend Debugging Prompt
**Purpose:** Get help fixing a frontend bug
**When to use:** React/JavaScript bug you can't figure out

```
I have a bug in my React application.

Component: [component name]
Tech stack: React, [other technologies]

What should happen: [expected behavior]
What actually happens: [actual behavior]
Console errors: [paste errors, or "none"]

Here's my code:
```[paste relevant code]```

Steps to reproduce:
1. [step 1]
2. [step 2]

What I've already tried:
- [attempt 1]
- [attempt 2]

Please explain what's wrong and why the fix works.
```

### Backend Debugging Prompt
**Purpose:** Get help fixing a backend/API bug
**When to use:** Flask/Python API issues

```
I have a bug in my Flask API.

Endpoint: [method] [URL]
Tech stack: Flask, MySQL, [others]

What should happen: [expected behavior]
What actually happens: [actual behavior]
Error message: [paste exact error]

Here's my code:
```[paste relevant code]```

Database schema for relevant tables:
```[paste CREATE TABLE or describe]```

What I've already tried:
- [attempt 1]

Please explain the root cause and fix.
```

### Error Explanation Prompt
**Purpose:** Understand an error message
**When to use:** You see an error and don't understand it

```
I got this error in my [language/framework] application:

```
[paste the full error message / traceback]
```

My code that triggered the error:
```[paste code]```

Explain:
1. What this error means in simple terms
2. Why it happened
3. How to fix it
4. How to prevent it in the future
```

---

## 🎨 UI/UX Prompts

### UI Improvement Prompt
**Purpose:** Get suggestions to improve your UI
**When to use:** Your UI works but looks basic

```
I'm building [page/component description] for [project].

Current design: [describe what it looks like now]
Design goals: [dark theme / modern / minimalist / etc.]
Framework: React with [Tailwind CSS / custom CSS]

Suggest improvements for:
1. Visual design (colors, spacing, typography)
2. User experience (flow, feedback, loading states)
3. Responsiveness (mobile, tablet, desktop)
4. Accessibility (keyboard navigation, screen readers)

Provide specific CSS/component code for the top 3 improvements.
```

### Responsive Design Prompt
**Purpose:** Make a component responsive
**When to use:** Component doesn't work well on mobile

```
This component needs to be responsive:

```[paste component code]```

It currently looks good on desktop but breaks on mobile.

Requirements:
- Mobile: [describe mobile layout]
- Tablet: [describe tablet layout]
- Desktop: [current layout]

Using: [Tailwind CSS / custom CSS]

Provide the responsive code with breakpoints.
```

---

## 🧪 Testing Prompts

### Manual Testing Prompt
**Purpose:** Create a testing checklist
**When to use:** Before deploying or submitting a project

```
I need a manual testing checklist for [project/feature name].

The feature does: [description]
User roles: [list roles]
Tech stack: [technologies]

Create a comprehensive testing checklist covering:
1. Happy path scenarios (everything works correctly)
2. Edge cases (empty inputs, long text, special characters)
3. Error handling (network errors, invalid data)
4. Responsive design (mobile, tablet, desktop)
5. Cross-browser testing
6. Security considerations
```

---

## 📝 Documentation Prompts

### README Prompt
**Purpose:** Generate a professional README
**When to use:** Publishing a project on GitHub

```
Generate a professional README.md for my project:

Project: [name]
Description: [what it does]
Tech stack: [technologies]
Features: [list main features]
Setup requirements: [what needs to be installed]

Include sections for:
1. Project title and description
2. Screenshots placeholder
3. Tech stack
4. Features list
5. Getting Started (prerequisites, installation, running)
6. API documentation (if applicable)
7. Contributing
8. License
```

### Code Explanation Prompt
**Purpose:** Understand code you didn't write or forgot about
**When to use:** Reading unfamiliar code

```
Explain this code line by line. I'm a beginner.

```[paste code]```

For each section, explain:
1. WHAT it does
2. WHY it does it that way
3. HOW it connects to the rest of the code

Use simple language — explain like I'm a senior high school student.
```

---

## 🌐 Open Graph (OG), Social Link Previews & Deployment Prompts

### Open Graph (OG) Meta Tags & Social Media Link Preview Prompt
**Purpose:** Add rich social media share cards (`1200×630` banner + synchronized title/description) for Messenger, Facebook, Discord, Telegram, WhatsApp, X/Twitter, LinkedIn, and iMessage
**When to use:** Deploying a website or web app to GitHub Pages, Vercel, Netlify, or a custom domain *(also auto-handled by the `open-graph-preview` skill)*

````
Add complete Open Graph (OG) Meta Tags and Twitter/X Large Summary Card metadata for social media link previews.

Target preview title / tag: "[YOUR PREVIEW TITLE, e.g. DAY WITH ME]"
Target description: "[1-2 sentence summary, 110-160 chars]"
Deployment platform: [GitHub Pages / Vercel / Custom Domain]
Production URL (if known): [https://username.github.io/EXACT_REPO_NAME/ or https://your-app.vercel.app/]

Requirements:
1. Inspect `git remote -v` and deployment config first to resolve the exact case-sensitive `https://` canonical URL. Never use relative paths for `og:image`, `twitter:image`, or `og:url`.
2. Prepare or crop a `1200x630` (`1.91:1`) `.jpg` or `.png` preview banner under `250 KB` with key text/artwork centered inside the middle safe zone so `1:1` mobile chat crops never cut off text.
3. Synchronize the title across `<title>`, `og:title`, `og:site_name`, `twitter:title`, and `apple-mobile-web-app-title`.
4. Include `og:type="website"`, `og:url`, `og:description`, `og:image`, `og:image:secure_url`, `og:image:type`, `og:image:width="1200"`, `og:image:height="630"`, `og:image:alt`, `<link rel="canonical">`, and `twitter:card="summary_large_image"`.
5. Inject into static `<head>` (`index.html`) or server-rendered metadata (`app/layout.tsx` `metadataBase`), never client-only JS.
````

### Frontend-Only UI Refactor Prompt (Zero Backend Changes)
**Purpose:** Polish spacing, hierarchy, and responsive layout without breaking working APIs or database logic
**When to use:** Your backend works, and you only want a clean production UI pass

````
Refactor the frontend UI/UX to make it clean, modern, and responsive.

STRICT SCOPE GUARDRAILS:
- Inspect the existing frontend components and routes first.
- Do NOT modify any backend routes, API endpoints, database schemas/models, authentication logic, or payload contracts.
- Preserve all existing working features, state flows, and event handlers.

UI Improvements Required:
1. Consistent 8px spacing scale, clear visual hierarchy, and aligned icons/cards.
2. Proper loading, empty, and error states for async data.
3. Responsive layout verified across mobile, tablet, and desktop (no horizontal overflow).
4. Extract repeated UI blocks into clean reusable components where helpful.
````

### Anti-Hallucination `PROJECT_STRUCTURE.md` Generator Prompt
**Purpose:** Generate accurate architecture documentation for both human developers and AI coding agents
**When to use:** Onboarding teammates, cleaning up a repo, or giving AI agents an accurate map of your codebase

````
Inspect the ENTIRE actual repository before writing anything.

Generate a complete `PROJECT_STRUCTURE.md` grounded strictly in the real files, folders, routes, models, and scripts currently in this codebase.

Rules:
- Never invent generic folders or placeholder files that do not exist.
- Document every active directory, entry point, environment variable name (placeholders only — never expose real secrets), API route group, database model, and frontend page/component relationship.
- Include clear end-to-end data flow diagrams (`UI -> API -> Database -> Response`) so both human developers and AI agents can navigate the project safely.
````

---

## Related Notes

- [[My Best IDE Prompts (Antigravity Vault)]]
- [[Bayanihan Hub Admin Demo Data Prompt]]
- [[Debug React State Issues]]
- [[claude-skills]]
- [[AI-Assisted Development]]
- [[AI Prompt Template]]
