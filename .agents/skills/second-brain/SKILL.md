---
name: second-brain
description: >-
  Connect any coding project to Jehosue's Obsidian Second Brain vault
  (c:\Users\Jeho\Documents\Jeho's Second Brain). Use this skill whenever the user
  starts/initializes a new project and wants it tracked in their Second Brain, asks to sync
  project progress/tasks/bugs/decisions to Obsidian, wants to reuse prompts or notes from
  their Second Brain, or asks to wrap up a coding session and log what was built.
argument-hint: "[init | sync | log-bug | wrap-up] [project-name]"
---

# Second Brain Project Integration Skill

Bridges any active coding workspace on Jehosue's machine directly to his Obsidian Second Brain vault.

## Vault Root & Key Paths

- **Vault Root:** `c:\Users\Jeho\Documents\Jeho's Second Brain`
- **Dashboard:** `00 - Dashboard\Home.md`
- **Active Projects:** `03 - Projects\<Project Name>\<Project Name>.md`
- **Templates:**
  - `99 - Templates\Project Template.md`
  - `99 - Templates\Bug Report Template.md`
  - `99 - Templates\Daily Note Template.md`
  - `99 - Templates\AI Prompt Template.md`
- **Prompt Vaults:**
  - `05 - Resources\AI Prompts\My Best IDE Prompts (Antigravity Vault).md`
  - `05 - Resources\AI Prompts\AI Prompts.md`
- **Custom Skills Root:** `.agents\skills\` (shared globally via `~/.gemini/config/skills.json`)

> **Security Rule:** Never copy real `.env` values, API keys, database passwords, or private tokens from a project repo into any Second Brain Markdown note. Use variable names/placeholders only.

---

## Workflows

### 1. Kick Off / Register a Project (`init`)

When starting a new project (or linking an existing repo that isn't in `03 - Projects/` yet):
1. Inspect the active codebase (`package.json`, `requirements.txt`, `pubspec.yaml`, `git remote -v`, folder tree) to gather factual metadata.
2. Read `c:\Users\Jeho\Documents\Jeho's Second Brain\99 - Templates\Project Template.md`.
3. Create `c:\Users\Jeho\Documents\Jeho's Second Brain\03 - Projects\<Project Name>\<Project Name>.md` populated with:
   - **Project Overview** (Tech Stack, GitHub URL, Local Path, Status `Planning` or `In Progress`)
   - **MVP Scope & Core Features** (keep MVP lean — skip premature extras)
   - **Database Entities / API Endpoints / Environment Variable Names**
   - **Phased Tasks Checklist**
4. Add or update the project's row under `## 🏗️ Active Projects` and `⚡ Quick Navigation` in `00 - Dashboard\Home.md` using Obsidian `[[<Project Name>]]` wikilinks.
5. *(Optional, if requested)* Create a concise `AGENTS.md` (or `CLAUDE.md`) at the root of the coding repository summarizing its stack, run commands, and architectural guardrails.

### 2. Pull Proven Prompts & Notes During Development (`reuse`)

When planning architecture, refactoring UI, hardening AI personas, seeding data, or auditing a project:
1. Check `05 - Resources\AI Prompts\My Best IDE Prompts (Antigravity Vault).md` and `05 - Resources\AI Prompts\AI Prompts.md` for Jehosue's proven patterns:
   - **Inspect actual files first** — never invent fake folder trees or routes.
   - **Strict scope boundaries** — e.g., frontend UI refactors must not alter backend routes/models unless asked.
   - **Dynamic backend counts** — never hardcode `(0)` tab counters or mock arrays in production UIs.
   - **End-to-end verification** — trace `UI → API/Service → DB/Firmware → Response → Updated UI`.
2. Check `02 - Programming\` if project conventions for Python/Flask, React, Flutter, ESP32/IoT, MySQL (3NF), or MongoDB are relevant.

### 3. Log Bugs, Decisions, or Session Progress (`sync` / `wrap-up`)

When asked to update the Second Brain after fixing bugs or finishing a coding sprint:
1. Open `03 - Projects\<Project Name>\<Project Name>.md`.
2. Check off `[x]` completed tasks under `## ✅ Tasks`.
3. Append a dated entry to `## 📓 Development Log` summarizing what changed and which files/features were verified.
4. If a tricky bug was solved, document its **Symptoms → Root Cause → Final Solution** under `## 🐛 Bugs and Troubleshooting` (and if broadly reusable across projects, add a note in `02 - Programming\` or `05 - Resources\`).
5. If a new reusable multi-step workflow emerged, propose turning it into a skill in `.agents\skills\<name>\SKILL.md` or saving the prompt in `05 - Resources\AI Prompts\`.

