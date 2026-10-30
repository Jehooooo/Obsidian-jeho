---
tags: [project, active]
status: Planning
type: Personal Website
---

# 🏗️ Personal Portfolio & AI Knowledge Platform

## Project Overview

| Field | Details |
|-------|---------|
| **Project Name** | Personal Portfolio & AI Knowledge Platform |
| **Project Type** | Personal Website / AI Application |
| **Description** | A personal portfolio website with a black and purple theme, glassmorphism design, and an AI persona ("AI Jehosue") powered by Gemini API that represents my personality, knowledge, and experience. |
| **Problem Being Solved** | Need a professional online presence that showcases my projects, skills, and personality — plus an AI that can interact with visitors and answer questions about me. |
| **Target Users** | Recruiters, potential clients, fellow developers, visitors |
| **Current Status** | Planning |
| **Start Date** | |
| **Deadline** | |
| **Team Members** | Jehosue Biscarra |
| **Client / Organization** | Personal |
| **Tech Stack** | React, MongoDB, Gemini API |
| **Repository** | Pending Git Init |
| **Local Path** | `C:\Users\Jeho\Documents\fortfolio` |
| **Deployment** | Vercel / Netlify (Planned) |

---

## 🎯 Portfolio Goals

### Main Goal
Build a stunning personal portfolio that showcases my projects and skills, with an AI persona that can have conversations about my experience and knowledge.

### Core Features
- [ ] Hero section with animated introduction
- [ ] Projects showcase with live demos and source links
- [ ] AI Jehosue — Gemini API-powered chat
- [ ] Personal knowledge base for the AI
- [ ] Visitor chat storage (MongoDB)
- [ ] About me section
- [ ] Skills and tech stack section
- [ ] Contact section
- [ ] Responsive design (mobile-first)
- [ ] Dark theme with purple accents

### Design Philosophy
- **Theme:** Black and purple
- **Style:** Glassmorphism / Minimalism
- **Feel:** Modern, professional, tech-forward
- **Typography:** Clean, readable
- **Animations:** Subtle, purposeful micro-animations

### Future Improvements
- Blog section
- Project case studies
- Interactive resume
- Visitor analytics
- AI conversation history
- Multi-language support

---

## 📄 Pages

| Page | Description | Status |
|------|-------------|--------|
| Home / Hero | Animated intro, tagline, call to action | Not Started |
| About | Background, education, interests, personality | Not Started |
| Projects | Showcase of all projects with tech stack, links | Not Started |
| Skills | Tech stack, tools, experience level | Not Started |
| AI Jehosue | Chat interface to talk to the AI persona | Not Started |
| Contact | Contact form, social links | Not Started |

---

## 🤖 AI Architecture

### AI Jehosue — Persona Goals
The AI persona should accurately represent:
- **Education:** 3rd-year BS Computer Science student at DMMMSU-SLUC
- **Project experience:** Bayanihan Hub, Incident Monitoring System, portfolio, academic projects
- **Team leadership:** Experience leading programming teams and coordinating with classmates
- **Video editing experience:** Skills in video editing and content creation
- **Personality traits:** Curiosity, adaptability, problem-solving mindset, eagerness to learn
- **Learning style:** Practical, example-driven, AI-assisted development

### Important Rules
- The AI should **NOT** claim it built the website unless that is actually true
- The AI should represent Jeho's knowledge and personality **accurately**
- The AI should be helpful and conversational
- The AI should redirect questions it can't answer honestly

### Knowledge Base Structure
The AI's knowledge base should include:
- Personal bio and background
- Education details
- Project descriptions and tech stacks
- Skills and technologies
- Career goals and aspirations
- Work experience and leadership roles

### Gemini API Integration
- Use Gemini API for text generation
- System prompt defines the AI persona
- Knowledge base provides context
- Conversation history stored in MongoDB

---

## 🗄️ Database

### MongoDB Collections

| Collection | Description | Key Fields |
|------------|-------------|------------|
| conversations | Visitor chat sessions | session_id, messages[], created_at, updated_at |
| knowledge_base | AI persona knowledge entries | category, title, content, tags |
| projects | Portfolio project data | title, description, tech_stack, demo_url, repo_url, image |
| visitors | Visitor analytics (optional) | ip_hash, visits, last_visit |

### Why MongoDB?
- Flexible schema for chat conversations
- Easy to store nested message objects
- Scales well for unstructured data
- Good fit for a knowledge base with varied content

---

## 🔧 Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React |
| Styling | CSS (custom, glassmorphism) |
| AI | Gemini API |
| Database | MongoDB |
| Backend | TBD (Node.js/Express or Flask) |
| Deployment | TBD (Vercel, Netlify, or VPS) |

---

## 📝 Content Ideas

### Hero Section
- Animated typing effect or gradient text
- Tagline: something about building, learning, and solving problems
- Call to action: "View my projects" / "Talk to AI Jeho"

### Projects to Showcase
1. Bayanihan Hub — community donation, request, and exchange platform (React, Flask, MySQL)
2. Incident Monitoring System — institutional disaster reporting and monitoring system (React, Flask, Aiven MySQL)
3. Automatic Dispensing System — smart mobile-based solar-powered chicken feeder (Flutter, ESP32, Firebase)
4. Portfolio itself — meta showcase with Gemini API AI persona (React, MongoDB)
5. Mayerfeld Practicum — AI-assisted frontend development consulting work

### About Me Content
- CS student background
- Why I chose software engineering
- How I learn (AI-assisted, practical)
- Team leadership experience
- Video editing as a creative outlet
- Career aspirations

---

## 🚀 Deployment

### Options to Evaluate
- **Vercel** — Great for React apps, free tier
- **Netlify** — Similar to Vercel, good for static/SSR
- **VPS** — Full control, needed if running a backend
- **MongoDB Atlas** — Free tier for database hosting

---

## Related Notes

- [[React Basics]]
- [[MongoDB]]
- [[JavaScript Basics]]
- [[AI-Assisted Development]]
- [[Software Engineering]]
