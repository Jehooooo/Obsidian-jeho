---
aliases: [Project Workflow, Second Brain Setup, How to Use Second Brain]
tags: [dashboard, workflow, antigravity]
created: 2026-10-30
---

# 🚀 How to Setup & Use This Second Brain in Any Project

> Your Second Brain is **globally wired** into Antigravity IDE (`~/.gemini/config/skills.json` + `~/.gemini/config/skills/second-brain/`) and Claude Code (`~/.claude/skills/second-brain/`). You do **not** need to copy-paste your vault into new repos.

---

## ⚙️ 1. One-Time Setup Check (Already Configured + 2 IDE Settings)

1. **Global Skills Bridge (Done ✅):**
   - `~/.gemini/config/skills.json` points directly to `~/Documents/Jeho's Second Brain/.agents/skills`.
   - Any new folder you add inside `.agents/skills/<skill-name>/SKILL.md` automatically works across **every project** on your laptop.
2. **Allow Cross-Folder Vault Sync in Antigravity Settings (10-Second Check):**
   - Open **Antigravity Settings → Global Settings → Non-Workspace File Access** and set it to **`allow`** (or **`ask`**).
   - *Why:* When you have `Documents\my-new-app` open, this lets the agent read your prompts in `05 - Resources/` and update `03 - Projects/` in your Second Brain directly.
   - *(Optional Multi-Root Pro Tip)*: In Antigravity IDE (VS Code menu), click **File → Add Folder to Workspace...** and add `Jeho's Second Brain` alongside your active code repo if you want `@` file autocomplete for vault notes right inside chat!

---

## 🛠️ 2. The 4-Step Workflow for Every Project

```
[1. Kickoff]  ──►  [2. Build Features]  ──►  [3. Audit & Ship]  ──►  [4. Wrap-Up Sync]
  03 - Projects       05 - AI Prompts          open-graph-preview       Dev Log & Bugs
  + AGENTS.md         + 02 - Programming       + QA Audit Prompt        + /learn or Skill
```

### Phase 1: Starting a Brand-New Project (`5 mins`)
Open your new project folder in Antigravity IDE and send:

```text
Initialize this project in my Second Brain and create a lean MVP plan + AGENTS.md for this repo.
```

**What happens automatically (via the `second-brain` skill):**
- Creates `03 - Projects/<Project Name>/<Project Name>.md` from [[Project Template]].
- Adds the project to [[Home]] under **Active Projects**.
- Creates an `AGENTS.md` in your code repo so every future chat session knows your stack, run commands, and rules.
- Need a full-stack blueprint first? Grab **Prompt #2 (Full-Stack RBAC Spec)** or **Prompt #4 / #5 (Tight MVP Spec)** from [[My Best IDE Prompts (Antigravity Vault)]].

---

### Phase 2: Building Features, UI & Backend (`Daily Coding`)
Keep **Obsidian** open on the side (or split-screen) on `03 - Projects/<Project Name>/<Project Name>.md` while coding in Antigravity IDE:

- **Planning complex features?** Type `/plan` first so the agent aligns on database schema + routes before writing code.
- **Polishing UI without breaking working APIs?** Tell the agent:
  ```text
  Use my Frontend-Only UI Refactor prompt from my Second Brain — do NOT touch backend routes, DB models, or auth.
  ```
- **Adding realistic seed/admin data?** Reference [[Bayanihan Hub Admin Demo Data Prompt]] (idempotent seed + dynamic backend tab counts, never hardcoded `(0)`).
- **Building AI chat / personas?** Pull **Prompts #6–#13** from [[My Best IDE Prompts (Antigravity Vault)]] (`pending_review` knowledge separation + prompt-injection defense).
- **Quick messy thoughts while coding?** Drop one-liners into [[Inbox]] — don't break your coding flow to format notes mid-sprint.

---

### Phase 3: Pre-Deployment / Pre-Defense & Link Previews (`Shipping`)
Before pushing to Vercel, GitHub Pages, or presenting at a defense:

1. **Social Media Share Card (`open-graph-preview` skill):**
   ```text
   Add Open Graph (OG) Meta Tags and a 1200x630 social media link preview for deployment. The tag title should say "YOUR_APP_TITLE".
   ```
2. **Full QA / Pre-Defense Audit:**
   ```text
   Run the 5-Pillar Pre-Deployment QA Audit (or Pre-Defense System Audit) from my Second Brain and verify every flow end-to-end.
   ```
3. **Architecture Docs for Teammates & Future AI Sessions:**
   ```text
   Generate PROJECT_STRUCTURE.md using my anti-hallucination codebase structure prompt from my Second Brain.
   ```

---

### Phase 4: End-of-Session Wrap-Up (`2 mins before closing IDE`)
Before closing your laptop after a productive session, send one line:

```text
Sync today's progress, completed tasks, and solved bugs for this project to my Second Brain.
```

**What gets saved automatically:**
- Checks off `[x]` finished tasks and adds a dated entry in `## 📓 Development Log` inside `03 - Projects/<Project Name>/`.
- Logs tricky bugs (`Symptoms → Root Cause → Fix`) so you never debug the same error twice.
- **Compounding Rule:** Whenever you craft a killer prompt or solve a repeatable workflow, tell the agent: *"Save this prompt to `05 - Resources/AI Prompts/`"* (or use `/learn` / add a `SKILL.md` in `.agents/skills/`).

---

## 🔗 Quick Links
- [[Home]] — Main Dashboard
- [[Project Templates]] · [[Project Template]]
- [[My Best IDE Prompts (Antigravity Vault)]] · [[AI Prompts]]
- [[claude-skills]] · [[README|AI Agents Architecture]]

