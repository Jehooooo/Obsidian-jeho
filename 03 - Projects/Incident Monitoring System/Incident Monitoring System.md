---
tags: [project, active]
status: In Progress
type: Web Application
---

# 🏗️ DMMMSU-SLUC Disaster/Emergency Incident Report Monitoring System

## Project Overview

| Field | Details |
|-------|---------|
| **Project Name** | DMMMSU-SLUC Disaster/Emergency Incident Report Monitoring System |
| **Project Type** | Institutional Web Application |
| **Description** | A system for reporting, tracking, and managing disaster and emergency incidents at DMMMSU-SLUC. Supports incident lifecycle from report to resolution. |
| **Problem Being Solved** | The institution lacks a centralized digital system for reporting and monitoring disaster/emergency incidents. Manual processes are slow, unorganized, and lack proper tracking. |
| **Target Users** | Community Members, Staff, Administrators |
| **Current Status** | In Progress |
| **Start Date** | |
| **Deadline** | |
| **Team Members** | Jehosue Biscarra (Lead Developer) |
| **Client / Organization** | DMMMSU-SLUC |
| **Tech Stack** | React, Flask, MySQL (XAMPP / Aiven Cloud), Tailwind CSS |
| **Repository** | [GitHub: Jehooooo/im_project](https://github.com/Jehooooo/im_project.git) |
| **Local Path** | `C:\Users\Jeho\Documents\campus-incident-system` (branch: `main`) |
| **Cloud DB** | Aiven Cloud MySQL (`dmmmsu-incident-reports`) |
| **Deployment** | Local / Staging |

---

## 🎯 Project Goals

### Main Goal
Build a disaster/emergency incident reporting and monitoring system that allows community members to report incidents and staff/admins to track, manage, and resolve them.

### Core Features
- [ ] Incident reporting with date, location, cause, and time
- [ ] Status workflow: Pending → In Progress → Solved
- [ ] User roles: Admin, Staff, Community Member
- [ ] PDF generation for incident reports
- [ ] DOCX upload/download for documents
- [ ] Email notifications
- [ ] Telegram fallback notifications
- [ ] Database-backed staff contact details
- [ ] Dashboard with incident overview
- [ ] Incident history and search

### Minimum Viable Product (MVP)
- Incident report submission
- Incident status tracking (Pending → In Progress → Solved)
- Admin/Staff dashboard to manage incidents
- User roles and authentication
- Basic report generation

### Future Improvements
- Real-time incident map
- Mobile app
- SMS notifications
- Analytics and trend reports
- Integration with emergency services

---

## ✅ Tasks

### Setup & Infrastructure
- [ ] Set up React project with Tailwind CSS
- [ ] Set up Flask backend
- [ ] Set up MySQL database (XAMPP)
- [ ] Design database schema
- [ ] Configure environment variables
- [ ] Initialize Git repository

### User Roles & Authentication
- [ ] User registration
- [ ] Login / logout
- [ ] Role-based access control (Admin, Staff, Community Member)
- [ ] Role-specific dashboards

### Incident Reporting
- [ ] Incident report form (date, location, cause, time, description)
- [ ] Photo/document attachment support
- [ ] Incident categorization
- [ ] Validation and submission

### Incident Management
- [ ] Incident list view with filtering
- [ ] Incident detail view
- [ ] Status workflow: Pending → In Progress → Solved
- [ ] Assign incidents to staff
- [ ] Add notes/updates to incidents
- [ ] Incident timeline

### Notifications
- [ ] Email notifications for new incidents
- [ ] Email notifications for status changes
- [ ] Telegram fallback notifications
- [ ] Staff contact details from database

### Document Management
- [ ] PDF report generation
- [ ] DOCX upload functionality
- [ ] DOCX download functionality
- [ ] Document storage and retrieval

### Dashboard & Reporting
- [ ] Admin dashboard with incident overview
- [ ] Incident statistics
- [ ] Incident search and filter
- [ ] Export reports

### Testing & Deployment
- [ ] Test incident reporting workflow
- [ ] Test role-based access
- [ ] Test notifications
- [ ] Test document generation
- [ ] Deploy to production

---

## 👥 User Roles

### Community Member
- Can submit incident reports
- Can view their own submitted reports
- Can receive notifications about their reports
- Cannot manage other users' reports

### Staff
- Can view all incident reports
- Can update incident status
- Can add notes to incidents
- Can be assigned to incidents
- Contact details stored in database

### Admin
- All Staff permissions
- Can manage users and roles
- Can manage system settings
- Can generate reports
- Can view analytics
- Full CRUD on all incidents

---

## 🗄️ Database Documentation

### Database Overview
MySQL database (via XAMPP) with tables for users, incidents, notifications, documents, and staff contacts.

### Entities

| Entity | Description | Key Fields |
|--------|-------------|------------|
| Users | System users (all roles) | id, name, email, password_hash, role, created_at |
| Incidents | Reported incidents | id, reporter_id, title, description, date, time, location, cause, category, status, assigned_to, created_at, updated_at |
| Incident_Updates | Status changes and notes | id, incident_id, user_id, status_change, note, timestamp |
| Documents | Uploaded/generated files | id, incident_id, filename, file_type, file_path, uploaded_by, uploaded_at |
| Staff_Contacts | Staff contact information | id, user_id, phone, email, department, position |
| Notifications | System notifications | id, user_id, incident_id, type, message, sent_via, read, created_at |

### Relationships
- Users → Incidents (one-to-many): A user can report many incidents
- Users → Incident_Updates (one-to-many): A user can create many updates
- Incidents → Incident_Updates (one-to-many): An incident has many updates
- Incidents → Documents (one-to-many): An incident can have many documents
- Users → Staff_Contacts (one-to-one): Staff members have contact details
- Users → Notifications (one-to-many): A user receives many notifications

### 3NF Considerations
- **1NF:** All columns contain atomic values
- **2NF:** All non-key attributes fully depend on the primary key
- **3NF:** No transitive dependencies — staff contacts are in a separate table

### Important SQL Queries

```sql
-- Get all incidents with reporter info, ordered by most recent
SELECT i.*, u.name as reporter_name 
FROM incidents i 
JOIN users u ON i.reporter_id = u.id 
ORDER BY i.created_at DESC;

-- Get incidents by status
SELECT * FROM incidents WHERE status = 'Pending';

-- Get incident timeline
SELECT iu.*, u.name as updater_name 
FROM incident_updates iu 
JOIN users u ON iu.user_id = u.id 
WHERE iu.incident_id = ?
ORDER BY iu.timestamp ASC;

-- Get staff contact details
SELECT u.name, sc.phone, sc.email, sc.department 
FROM staff_contacts sc 
JOIN users u ON sc.user_id = u.id;
```

---

## 🔧 Technical Documentation

### System Architecture
```
Community Members / Staff / Admin
        ↕ Browser (React + Tailwind CSS)
        ↕ HTTP/REST API
Flask Backend (Python)
        ↕ SQL Queries
MySQL Database (XAMPP)
        ↕ 
File System (Documents, PDFs)
        ↕
Notification Services (Email, Telegram)
```

### Frontend
- **Framework:** React
- **Styling:** Tailwind CSS
- **Key Pages:** Login, Dashboard, Report Incident, Incident List, Incident Detail, Admin Panel
- **Routing:** React Router

### Backend
- **Framework:** Flask (Python)
- **API Style:** REST
- **PDF Generation:** ReportLab or WeasyPrint
- **DOCX Handling:** python-docx
- **Email:** Flask-Mail or smtplib
- **Telegram:** Telegram Bot API (python-telegram-bot)

### API Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | /api/register | Register user | No |
| POST | /api/login | Login | No |
| POST | /api/incidents | Submit incident report | Yes |
| GET | /api/incidents | Get all incidents | Yes (Staff/Admin) |
| GET | /api/incidents/:id | Get incident details | Yes |
| PUT | /api/incidents/:id/status | Update incident status | Yes (Staff/Admin) |
| POST | /api/incidents/:id/notes | Add note to incident | Yes (Staff/Admin) |
| GET | /api/incidents/:id/documents | Get incident documents | Yes |
| POST | /api/incidents/:id/documents | Upload document | Yes |
| GET | /api/incidents/:id/pdf | Generate PDF report | Yes (Staff/Admin) |
| GET | /api/staff/contacts | Get staff contacts | Yes (Admin) |
| POST | /api/notifications/send | Send notification | Yes (Admin) |

### Incident Lifecycle

```
Community Member submits incident report
        ↓
Status: PENDING
        ↓
Staff/Admin reviews and updates
        ↓
Status: IN PROGRESS
(Staff assigned, notes added, documents attached)
        ↓
Incident resolved
        ↓
Status: SOLVED
(Final report generated)
```

### Notification Flow
1. **New Incident** → Email notification to relevant staff
2. **Status Change** → Email notification to reporter
3. **Email Failure** → Telegram fallback notification
4. Staff contact details come from the database (not hardcoded)

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| DATABASE_URL | MySQL connection string | Yes |
| SECRET_KEY | Flask secret key | Yes |
| MAIL_SERVER | Email SMTP server | Yes |
| MAIL_USERNAME | Email username | Yes |
| MAIL_PASSWORD | Email password | Yes |
| TELEGRAM_BOT_TOKEN | Telegram bot API token | For fallback |
| UPLOAD_FOLDER | Path for file uploads | Yes |

> ⚠️ **Never store actual secrets in notes.** Use `.env` files in your project.

---

## 🐛 Known Bugs

<!-- Document bugs as they are discovered -->
*No bugs documented yet. Use the [[Bug Report Template]] when bugs are found.*

---

## 📓 Development Log

| Date | What I Worked On | Notes |
|------|------------------|-------|
| | Project planning | Requirements gathering |

---

## 🤔 Project Decisions

| Decision | Reason | Date | Alternatives Considered |
|----------|--------|------|------------------------|
| React for frontend | Consistent with other projects, modern | | Vue.js, vanilla JS |
| Flask for backend | Python familiarity, lightweight | | Django, Express.js |
| MySQL via XAMPP | Local development, familiar tool | | PostgreSQL, Docker |
| Email + Telegram notifications | Email is standard; Telegram as fallback for reliability | | SMS, push notifications |

---

## 📝 Lessons Learned

### Technical Lessons
<!-- Document as you build -->

### Process Lessons
<!-- Document as you build -->

---

## Related Notes

- [[React Basics]]
- [[Flask Basics]]
- [[MySQL]]
- [[Database Normalization]]
- [[REST APIs]]
- [[Software Engineering]]
