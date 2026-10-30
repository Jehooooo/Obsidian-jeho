---
tags: [project, active]
status: In Progress
type: Web Application
---

# 🏗️ Bayanihan Hub

## Project Overview

| Field | Details |
|-------|---------|
| **Project Name** | Bayanihan Hub |
| **Project Type** | Community Web Application |
| **Description** | A community platform for donation, requesting, and exchanging items. Connects people who want to give with people who need help. |
| **Problem Being Solved** | Communities lack a centralized platform to coordinate donations, item requests, and exchanges. People want to help but don't know who needs what, and people who need help don't know where to ask. |
| **Target Users** | Community members, donors, organizations, administrators |
| **Current Status** | In Progress |
| **Start Date** | |
| **Deadline** | |
| **Team Members** | Jehosue Biscarra (Lead Developer) |
| **Client / Organization** | |
| **Tech Stack** | React, Flask, MySQL, Tailwind CSS |
| **Repository** | [GitHub: Jehooooo/BayanihanHub](https://github.com/Jehooooo/BayanihanHub.git) |
| **Local Path** | `C:\Users\Jeho\Documents\BayanihanHub` (branch: `main`) |
| **Deployment** | Local / Staging |

---

## 🎯 Project Goals

### Main Goal
Build a functional community platform where users can donate items, request items they need, and exchange items with each other — with proper admin oversight and verification.

### Core Features
- [ ] Donation listings — users can post items for donation
- [ ] Item requests — users can request items they need
- [ ] Item exchange — users can exchange items with each other
- [ ] User registration with admin verification
- [ ] Identity verification for trust and safety
- [ ] User profiles
- [ ] Messaging between users
- [ ] Notifications
- [ ] Report system
- [ ] Favorites / saved items
- [ ] Admin dashboard for managing users, posts, requests, reports, and approvals
- [ ] Community support features
- [ ] Responsive and accessible UI

### Minimum Viable Product (MVP)
- User registration and login
- Admin verification for new users
- Post items for donation
- Request items
- Basic messaging between users
- Admin dashboard to manage users and posts
- Responsive UI

### Future Improvements
- Mobile app version
- Location-based matching
- Donation tracking and impact reports
- Community forums
- Integration with delivery services
- Real-time notifications

---

## ✅ Tasks

### Setup & Infrastructure
- [ ] Set up React project with Tailwind CSS
- [ ] Set up Flask backend
- [ ] Design and create MySQL database (3NF)
- [ ] Set up API structure
- [ ] Configure environment variables
- [ ] Set up Git repository

### Authentication & Users
- [ ] User registration form
- [ ] Admin approval workflow for new registrations
- [ ] Login / logout functionality
- [ ] Identity verification system
- [ ] User profile pages
- [ ] User settings

### Core Features
- [ ] Create donation listing form
- [ ] Display donation listings
- [ ] Create item request form
- [ ] Display item requests
- [ ] Item exchange workflow
- [ ] Search and filter items
- [ ] Category system

### Communication
- [ ] Messaging system between users
- [ ] Fix: Messages disappearing before sending
- [ ] Messaging reliability improvements
- [ ] Notification system
- [ ] Report system

### Admin Dashboard
- [ ] Admin user management
- [ ] Admin post management
- [ ] Admin request management
- [ ] Admin report management
- [ ] Admin approval management
- [ ] Fix: Admin approval display issues

### UI/UX
- [ ] Responsive design for all pages
- [ ] Fix: Responsive UI issues
- [ ] Photo upload and preview
- [ ] Fix: Photo preview after posting
- [ ] Favorites toggle state management
- [ ] Fix: Report dropdown visibility
- [ ] User post deletion

### Testing & Deployment
- [ ] Test all user workflows
- [ ] Test admin workflows
- [ ] Fix all known bugs
- [ ] Deploy to production

---

## 📋 Features

### Feature: Donation Listings

| Field | Details |
|-------|---------|
| **Description** | Users can post items they want to donate with photos, description, category, and condition |
| **Priority** | High |
| **Status** | In Progress |
| **Notes** | Must use real database data, not hardcoded mock data |

### Feature: Item Requests

| Field | Details |
|-------|---------|
| **Description** | Users can post requests for items they need |
| **Priority** | High |
| **Status** | In Progress |
| **Notes** | |

### Feature: Item Exchange

| Field | Details |
|-------|---------|
| **Description** | Users can propose and manage item exchanges |
| **Priority** | High |
| **Status** | Not Started |
| **Notes** | |

### Feature: Messaging

| Field | Details |
|-------|---------|
| **Description** | Direct messaging between users to coordinate donations/exchanges |
| **Priority** | High |
| **Status** | In Progress |
| **Notes** | Known bug: messages disappearing before sending. Needs reliability improvements. |

### Feature: Admin Dashboard

| Field | Details |
|-------|---------|
| **Description** | Admin panel to manage users, posts, requests, reports, and approvals |
| **Priority** | High |
| **Status** | In Progress |
| **Notes** | Known issue: Admin approval display not working correctly |

### Feature: Notifications

| Field | Details |
|-------|---------|
| **Description** | Notify users about messages, approvals, and activity |
| **Priority** | Medium |
| **Status** | Not Started |
| **Notes** | Requirements need to be defined |

### Feature: Favorites

| Field | Details |
|-------|---------|
| **Description** | Users can save/favorite items for later |
| **Priority** | Medium |
| **Status** | In Progress |
| **Notes** | Known issue: Favorites state not persisting correctly |

### Feature: Reports

| Field | Details |
|-------|---------|
| **Description** | Users can report inappropriate posts or users |
| **Priority** | Medium |
| **Status** | In Progress |
| **Notes** | Known issue: Report dropdown visibility problems |

---

## 🗄️ Database Documentation

### Database Overview
MySQL database using Third Normal Form (3NF) design. All data should come from the database — no hardcoded mock data in the frontend.

### Entities

| Entity | Description | Key Fields |
|--------|-------------|------------|
| Users | Registered community members | id, name, email, password_hash, role, verified, created_at |
| Items | Posted donations and exchange items | id, user_id, title, description, category, condition, photos, status |
| Requests | Item requests from users | id, user_id, title, description, category, urgency, status |
| Messages | Direct messages between users | id, sender_id, receiver_id, content, timestamp, read |
| Reports | User reports on posts or users | id, reporter_id, reported_id, type, reason, status |
| Favorites | Saved/favorited items | id, user_id, item_id |
| Notifications | User notifications | id, user_id, type, content, read, created_at |

### Relationships
- Users → Items (one-to-many): A user can post many items
- Users → Requests (one-to-many): A user can make many requests
- Users → Messages (one-to-many): A user can send/receive many messages
- Users → Reports (one-to-many): A user can file many reports
- Users → Favorites (one-to-many): A user can favorite many items
- Items → Favorites (one-to-many): An item can be favorited by many users

### 3NF Considerations
- **1NF:** All columns contain atomic values. No repeating groups.
- **2NF:** All non-key attributes depend on the entire primary key.
- **3NF:** No transitive dependencies. Each non-key attribute depends only on the primary key.

### Important SQL Queries

```sql
-- Get all approved donations with user info
SELECT i.*, u.name as donor_name 
FROM items i 
JOIN users u ON i.user_id = u.id 
WHERE i.status = 'approved';

-- Get pending user registrations for admin
SELECT * FROM users WHERE verified = FALSE;

-- Get conversation between two users
SELECT * FROM messages 
WHERE (sender_id = ? AND receiver_id = ?) 
   OR (sender_id = ? AND receiver_id = ?)
ORDER BY timestamp ASC;
```

### Schema Changes Log

| Date | Change | Reason |
|------|--------|--------|
| | Initial schema design | Project setup |

---

## 🔧 Technical Documentation

### Architecture
```
Frontend (React + Tailwind CSS)
        ↕ HTTP/REST API
Backend (Flask / Python)
        ↕ SQL Queries
Database (MySQL)
```

### Frontend
- **Framework:** React
- **Styling:** Tailwind CSS
- **Key Pages:** Home, Listings, Requests, Profile, Messages, Admin Dashboard
- **State Management:** TBD
- **Routing:** React Router

### Backend
- **Framework:** Flask (Python)
- **API Style:** REST
- **Authentication:** TBD
- **Database Driver:** mysql-connector-python or PyMySQL

### API Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | /api/register | Register new user | No |
| POST | /api/login | Login | No |
| GET | /api/items | Get all donation items | No |
| POST | /api/items | Create new donation item | Yes |
| GET | /api/requests | Get all item requests | No |
| POST | /api/requests | Create new request | Yes |
| GET | /api/messages/:userId | Get messages with user | Yes |
| POST | /api/messages | Send message | Yes |
| GET | /api/admin/users | Get all users (admin) | Admin |
| PUT | /api/admin/users/:id/verify | Verify user (admin) | Admin |

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| DATABASE_URL | MySQL connection string | Yes |
| SECRET_KEY | Flask secret key | Yes |
| FLASK_ENV | development/production | Yes |

> ⚠️ **Never store actual secrets in notes.** Use `.env` files in your project.

---

## 🐛 Known Bugs

### Bug: Messages Disappearing Before Sending

| Field | Details |
|-------|---------|
| **Date Discovered** | |
| **Status** | Open |
| **Priority** | High |
| **Symptoms** | Messages disappear from the input field or chat before they are actually sent to the server |
| **Expected Behavior** | Messages should appear in the conversation after sending |
| **Actual Behavior** | Messages vanish before or during the send process |
| **Possible Cause** | State management issue, premature input clearing, or API call failure |
| **Solution Attempted** | |
| **Final Solution** | |

### Bug: Admin Approval Display

| Field | Details |
|-------|---------|
| **Date Discovered** | |
| **Status** | Open |
| **Priority** | High |
| **Symptoms** | Admin approval interface not displaying correctly |
| **Expected Behavior** | Admin should see pending users/items and approve/reject them |
| **Actual Behavior** | Display issues with the approval workflow |
| **Possible Cause** | Frontend rendering or API data issue |

### Bug: Registration and Approval Flow

| Field | Details |
|-------|---------|
| **Date Discovered** | |
| **Status** | Open |
| **Priority** | High |
| **Symptoms** | Registration and admin approval flow not working as expected |
| **Expected Behavior** | New users register → Admin reviews → Admin approves/rejects → User gets notified |
| **Actual Behavior** | Flow has issues (specific symptoms to be documented) |

### Bug: Responsive UI Issues

| Field | Details |
|-------|---------|
| **Date Discovered** | |
| **Status** | Open |
| **Priority** | Medium |
| **Symptoms** | Some pages don't display correctly on mobile or smaller screens |
| **Expected Behavior** | All pages should be responsive and accessible |
| **Actual Behavior** | Layout breaks on certain screen sizes |

### Bug: Photo Preview After Posting

| Field | Details |
|-------|---------|
| **Date Discovered** | |
| **Status** | Open |
| **Priority** | Medium |
| **Symptoms** | Photo preview not working correctly after posting an item |

### Bug: Report Dropdown Visibility

| Field | Details |
|-------|---------|
| **Date Discovered** | |
| **Status** | Open |
| **Priority** | Medium |
| **Symptoms** | Report dropdown menu visibility issues |

### Bug: Favorites State

| Field | Details |
|-------|---------|
| **Date Discovered** | |
| **Status** | Open |
| **Priority** | Low |
| **Symptoms** | Favorites state not persisting or updating correctly |

### Bug: User Post Deletion

| Field | Details |
|-------|---------|
| **Date Discovered** | |
| **Status** | Open |
| **Priority** | Medium |
| **Symptoms** | Issues with users deleting their own posts |

---

## 📓 Development Log

| Date | What I Worked On | Notes |
|------|------------------|-------|
| | Project setup | Initial project structure |

---

## 🤔 Project Decisions

| Decision | Reason | Date | Alternatives Considered |
|----------|--------|------|------------------------|
| React for frontend | Modern, component-based, widely used | | Vue.js, vanilla JS |
| Flask for backend | Python-based, lightweight, familiar | | Django, Express.js |
| MySQL for database | Relational data, 3NF design | | PostgreSQL, MongoDB |
| Tailwind CSS for styling | Utility-first, rapid development | | Bootstrap, custom CSS |
| 3NF database design | Data integrity, no redundancy | | Denormalized design |

---

## 📝 Lessons Learned

### Technical Lessons
<!-- Document technical lessons as you build -->

### Process Lessons
<!-- Document process lessons as you build -->

### What I Would Do Differently
<!-- Fill this in as you progress -->

---

## Related Notes

- [[Bayanihan Hub Admin Demo Data Prompt]]
- [[React Basics]]
- [[Debug React State Issues]]
- [[Flask Basics]]
- [[MySQL]]
- [[Database Normalization]]
- [[REST APIs]]
- [[Software Engineering]]
