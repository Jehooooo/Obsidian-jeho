---
tags: [resource, reference, cheatsheet]
---

# 📚 Quick Reference & Cheat Sheets

> Essential cheatsheets and quick lookups for day-to-day software and hardware development.

---

## ⚡ Vault Internal Cheat Sheets

- **Git & GitHub:** [[Git and GitHub]] — Essential commands, branching, resolving merge conflicts.
- **Python Data Structures:** [[Python Data Structures]] — Time complexities, list comprehensions, dictionary methods.
- **Python Debugging:** [[Python Debugging]] — Tracebacks, logging, breakpoints.
- **React State Debugging:** [[Debug React State Issues]] — Stale closures, batching, re-render avoidance.
- **Database Normalization:** [[Database Normalization]] — 1NF, 2NF, 3NF rules and real-world examples.
- **REST APIs:** [[REST APIs]] — HTTP verbs, status codes, standard JSON response patterns.
- **Flutter Mobile:** [[Flutter Basics]] — Stateless vs Stateful widgets, StreamBuilder, common layout trees.
- **Embedded C++:** [[Embedded Systems and IoT]] — Non-blocking `millis()`, HX711 scale calibration, PlatformIO CLI.

---

## 🌐 HTTP Status Codes Quick Lookup

| Status Code | Meaning | When to Use |
|---|---|---|
| **200 OK** | Success | Standard response for successful HTTP requests |
| **201 Created** | Resource Created | Successful POST resulting in new record created |
| **204 No Content** | Success, No Body | Successful DELETE or action returning no body |
| **400 Bad Request** | Invalid Input | Malformed JSON or failed schema validation |
| **401 Unauthorized** | Missing/Invalid Auth | User is not logged in or token is expired |
| **403 Forbidden** | Insufficient Rights | User is logged in but lacks required role (e.g., non-admin) |
| **404 Not Found** | Resource Missing | Endpoint or record ID does not exist |
| **409 Conflict** | State Conflict | Duplicate email or unique constraint violation |
| **500 Server Error** | Unhandled Bug | Backend crash or uncaught exception |

---

## 🗄️ Git Quick Reset Cheatsheet

```bash
# Undo last commit but keep changes in working directory (staged)
git reset --soft HEAD~1

# Undo last commit and unstage changes (safe undo)
git reset HEAD~1

# Discard all local changes to match remote main (destructive)
git fetch origin
git reset --hard origin/main

# Clean untracked files
git clean -fd
```

---

## 🔗 Related Notes
- [[Documentation]]
- [[Useful Links]]
- [[AI Prompts]]
