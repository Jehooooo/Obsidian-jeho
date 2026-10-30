---
tags: [learning, software-engineering]
topic: Software Engineering
category: Professional Skills
---

# 🏗️ Software Engineering

## What Is It?

Software Engineering is the **systematic approach to designing, building, testing, and maintaining software**. It's not just about writing code — it's about writing code that works, is maintainable, scales well, and solves real problems.

The difference between "coding" and "software engineering" is like the difference between building a treehouse and building an apartment building. Both involve construction, but one requires planning, architecture, safety standards, and teamwork.

## Why Is It Important?

- **Your career goal** — you want to be a software engineer, not just a coder
- **Better projects** — proper engineering practices prevent bugs and save time
- **Team collaboration** — real software is built by teams, not individuals
- **Scalability** — engineering practices ensure your software can grow
- **Industry standard** — every company expects these skills

## Syntax / Concepts

### Software Development Life Cycle (SDLC)

```
Requirements → Design → Development → Testing → Deployment → Maintenance
```

### Design Principles

**SOLID Principles:**
- **S** — Single Responsibility: Each class/function does ONE thing
- **O** — Open/Closed: Open for extension, closed for modification
- **L** — Liskov Substitution: Subclasses should work wherever parent classes work
- **I** — Interface Segregation: Don't force classes to implement unused methods
- **D** — Dependency Inversion: Depend on abstractions, not concrete implementations

**DRY** — Don't Repeat Yourself
**KISS** — Keep It Simple, Stupid
**YAGNI** — You Aren't Gonna Need It (don't build features until needed)

### Code Quality

```python
# ❌ Bad: unclear names, no structure
def p(d):
    r = []
    for i in d:
        if i['s'] == 'a':
            r.append(i)
    return r

# ✅ Good: clear names, readable
def get_available_items(items):
    """Filter and return only available items."""
    return [item for item in items if item['status'] == 'available']
```

### Version Control Workflow
```
main (production-ready code)
  └── develop (integration branch)
       ├── feature/user-registration
       ├── feature/messaging
       └── bugfix/message-disappearing
```

## Example

Applying software engineering to the Bayanihan Hub project:

```
1. REQUIREMENTS
   - Users need to donate, request, and exchange items
   - Admin needs to verify users and manage content
   
2. DESIGN
   - Database: MySQL with 3NF normalization
   - Backend: Flask REST API
   - Frontend: React with Tailwind CSS
   - Architecture: Client-Server with REST API
   
3. DEVELOPMENT
   - Use Git branches for each feature
   - Write clean, documented code
   - Follow REST API conventions
   
4. TESTING
   - Test each API endpoint with Postman
   - Test each UI component manually
   - Document and fix bugs
   
5. DEPLOYMENT
   - Deploy frontend and backend
   - Set up production database
   - Monitor for errors
   
6. MAINTENANCE
   - Fix bugs reported by users
   - Add new features based on feedback
   - Keep dependencies updated
```

## Common Mistakes

1. **Skipping planning** — jumping into code without understanding requirements
2. **No version control** — not using Git properly
3. **No testing** — hoping code works without testing it
4. **Premature optimization** — making code complex before it even works
5. **Poor documentation** — future you won't remember why you wrote that code

## Practice

- [ ] Apply the SDLC to plan one of your projects
- [ ] Refactor a piece of code to follow the Single Responsibility Principle
- [ ] Write a README.md for one of your projects
- [ ] Create a Git branching strategy for your project
- [ ] Document 3 technical decisions you made and why

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Git and GitHub]]
- [[Data Structures and Algorithms]]
- [[Software Engineer Roadmap]]
- [[Bayanihan Hub]]
- [[Incident Monitoring System]]
