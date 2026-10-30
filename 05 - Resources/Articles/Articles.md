---
tags: [resource, articles]
---

# 📰 Curated Engineering Articles

> Recommended reading on software architecture, design patterns, clean code, and engineering principles.

---

## 🏛️ System Architecture & Best Practices

1. **Clean Architecture by Uncle Bob (Summary)**
   - *Core Concept:* Separation of concerns; business rules remain independent of UI, database, frameworks, or external agencies.
   - *Application in Projects:* Keep API routes lightweight in Flask; encapsulate database queries in services/models.

2. **Database Normalization Explained Simply**
   - *Key takeaway:* Eliminating redundancy (1NF -> 2NF -> 3NF) prevents update anomalies, saving disk space and ensuring consistency in relational systems like MySQL.
   - *Vault Reference:* [[Database Normalization]]

3. **React 18 Automatic Batching & Concurrent Rendering**
   - *Key takeaway:* React 18 batches multiple state updates even inside promises, timeouts, and native event listeners, minimizing re-renders.
   - *Vault Reference:* [[Debug React State Issues]]

4. **Designing Resilient IoT Systems**
   - *Key takeaway:* Always build hardware fail-safes (watchdog timers, local fallback schedules) so offline conditions don't freeze physical actuators.
   - *Vault Reference:* [[Embedded Systems and IoT]]

---

## 🔗 Related Notes
- [[Useful Links]]
- [[Documentation]]
- [[Software Engineering]]
