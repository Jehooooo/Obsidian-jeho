# 🧠 Obsidian-Jeho — Software Engineering Second Brain

Personal Obsidian knowledge base, AI prompt vault, and custom coding-agent skills for **Jehosue Biscarra** across **Web, Mobile, Cloud, AI, and Embedded IoT** development.

---

## 📂 Vault Structure

| Folder | Purpose |
|---|---|
| [`00 - Dashboard/`](./00%20-%20Dashboard/) | Main [`Home.md`](./00%20-%20Dashboard/Home.md) dashboard, [`How to Use Second Brain in Projects.md`](./00%20-%20Dashboard/How%20to%20Use%20Second%20Brain%20in%20Projects.md), quick-capture inbox, and weekly reviews |
| [`01 - Daily Notes/`](./01%20-%20Daily%20Notes/) | Daily engineering logs, wins, and blockers |
| [`02 - Programming/`](./02%20-%20Programming/) | Technical notes for Python, Flask, React, Flutter, Java, MySQL (3NF), MongoDB, ESP32/IoT, DSA, Git, and Cybersecurity |
| [`03 - Projects/`](./03%20-%20Projects/) | End-to-end project specs, schemas, tasks, dev logs, and bug trackers |
| [`04 - Career/`](./04%20-%20Career/) | Software engineering roadmap, skills matrix, portfolio, and interview prep |
| [`05 - Resources/`](./05%20-%20Resources/) | [`AI Prompts.md`](./05%20-%20Resources/AI%20Prompts/AI%20Prompts.md) & [`My Best IDE Prompts (Antigravity Vault).md`](./05%20-%20Resources/AI%20Prompts/My%20Best%20IDE%20Prompts%20(Antigravity%20Vault).md) |
| [`06 - Personal/`](./06%20-%20Personal/) | Personal engineering goals, ideas, and reflections |
| [`99 - Templates/`](./99%20-%20Templates/) | Reusable templates for projects, bugs, daily notes, weekly reviews, and AI prompts |
| [`AGENTS/`](./AGENTS/) | AI coding agent architecture (`CLAUDE.md`, `claude-skills.md`, `subagents.md`, `commands.md`) |
| [`.agents/skills/`](./.agents/skills/) | Custom IDE skills (`open-graph-preview`, `second-brain`) shared across workspaces |

---

## 🛠️ Custom Agent Skills Included

- **`open-graph-preview`** ([`.agents/skills/open-graph-preview/SKILL.md`](./.agents/skills/open-graph-preview/SKILL.md)) — Automates Open Graph (`og:*`) meta tags, Twitter/X `summary_large_image` cards, case-sensitive canonical `https://` URLs, and `1200×630` (`< 250 KB`) social preview banners.
- **`second-brain`** ([`.agents/skills/second-brain/SKILL.md`](./.agents/skills/second-brain/SKILL.md)) — Bridges any local coding project directly to this Obsidian vault for 1-line project kickoff, prompt reuse, and end-of-session dev-log/bug syncing.

---

## 🚀 Quick Setup on a New Machine

1. Clone this repository into `Documents`:
   ```bash
   git clone https://github.com/Jehooooo/Obsidian-jeho.git "Jeho's Second Brain"
   ```
2. Open the folder as a vault in **Obsidian**.
3. Register `.agents/skills` globally in `~/.gemini/config/skills.json`:
   ```json
   {
     "entries": [
       { "path": "~/Documents/Jeho's Second Brain/.agents/skills" }
     ]
   }
   ```
