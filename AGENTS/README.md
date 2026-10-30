---
tags: [agents, claude-code, ai, workflows]
---

# 🤖 AI Agents & Developer Automation

> Architecture guide and operational reference for AI Coding Agents, Claude Code, Subagents, and Custom Commands.

---

## 🧭 System Overview

AI pair programming and agentic workflows in this workspace follow a hierarchical **Command → Agent → Skill** architecture:

```
[ User Prompt / Slash Command ]
              │
              ▼
    [ Orchestrator Agent ]
         /           \
        ▼             ▼
  [ Subagent A ]  [ Subagent B ]
        │             │
        ▼             ▼
   [ Skill 1 ]    [ Skill 2 ]
```

---

## 📁 Agent References

- **[[CLAUDE]]** (`AGENTS/CLAUDE.md`): Core instructions and workflow patterns for Claude Code pair programming.
- **[[commands]]** (`AGENTS/commands.md`): Custom slash commands reference library.
- **[[claude-skills]]** (`AGENTS/claude-skills.md`): Modular capabilities, **Skill vs. Agent vs. Rule** decision matrix, and custom installed skills (`open-graph-preview`).
- **[[subagents]]** (`AGENTS/subagents.md`): Subagent orchestration rules, permissions, and tool delegations.

---

## 🛠️ Active Custom Skills

- **`open-graph-preview`** (`~/.gemini/config/skills/open-graph-preview/SKILL.md` & `.agents/skills/open-graph-preview/SKILL.md`): End-to-end **Open Graph (`og:*`) Meta Tags & Social Media Link Preview** generator (`1200×630` `< 250 KB` banner + case-sensitive canonical `https://` URLs + Twitter/X `summary_large_image` cards).
- **`second-brain`** (`~/.gemini/config/skills/second-brain/SKILL.md` & `.agents/skills/second-brain/SKILL.md`, bridged globally via `~/.gemini/config/skills.json`): Connects any external coding project to this Obsidian vault for 1-line project kickoff, prompt reuse, and end-of-session dev-log/bug syncing. See **[[How to Use Second Brain in Projects]]**.

---

## 🔗 Related Notes
- [[My Best IDE Prompts (Antigravity Vault)]]
- [[AI Prompts]]
- [[Bayanihan Hub Admin Demo Data Prompt]]
- [[AI-Assisted Development]]
- [[Debug React State Issues]]
- [[Software Engineering]]
