---
tags: [learning, database]
topic: Database Normalization
category: Databases
---

# 🗄️ Database Normalization

## What Is It?

Database normalization is the process of **organizing your database to reduce redundancy and improve data integrity**. It's a set of rules (called Normal Forms) that ensure your data is stored efficiently without unnecessary duplication.

Think of it like organizing your closet — instead of throwing everything in one pile, you separate clothes by type, so finding what you need is faster and you don't have duplicate items taking up space.

## Why Is It Important?

- **Required in your projects** — Bayanihan Hub uses 3NF database design
- **Prevents data problems** — no duplicate data that can get out of sync
- **Saves storage** — less repeated data means smaller database
- **Easier updates** — change data in one place, not many
- **Interview topic** — normalization is commonly asked in technical interviews

## Syntax / Concepts

### First Normal Form (1NF)
**Rule:** Every column must contain **atomic (single)** values. No lists or repeating groups.

```
❌ BAD (not 1NF):
| id | name  | skills              |
|----|-------|---------------------|
| 1  | Jeho  | Python, React, Flask |

✅ GOOD (1NF):
| id | name  | skill  |
|----|-------|--------|
| 1  | Jeho  | Python |
| 1  | Jeho  | React  |
| 1  | Jeho  | Flask  |

✅ BETTER (with separate table):
Users: | id | name |
Skills: | user_id | skill |
```

### Second Normal Form (2NF)
**Rule:** Must be in 1NF AND every non-key column must depend on the **entire** primary key.

```
❌ BAD (not 2NF) — course_name depends only on course_id, not on student_id:
| student_id | course_id | course_name | grade |

✅ GOOD (2NF) — separate table for courses:
Enrollments: | student_id | course_id | grade |
Courses: | course_id | course_name |
```

### Third Normal Form (3NF)
**Rule:** Must be in 2NF AND no non-key column depends on another non-key column (no transitive dependencies).

```
❌ BAD (not 3NF) — department_name depends on department_id, not on staff_id:
| staff_id | name | department_id | department_name |

✅ GOOD (3NF):
Staff: | staff_id | name | department_id |
Departments: | department_id | department_name |
```

## Example

Designing the Bayanihan Hub database in 3NF:

```sql
-- Users table (3NF)
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    role_id INT,
    FOREIGN KEY (role_id) REFERENCES roles(id)
);

-- Roles table (separated from users — 3NF)
CREATE TABLE roles (
    id INT PRIMARY KEY AUTO_INCREMENT,
    role_name VARCHAR(50) UNIQUE NOT NULL
);

-- Items table (3NF)
CREATE TABLE items (
    id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    title VARCHAR(200) NOT NULL,
    category_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (category_id) REFERENCES categories(id)
);

-- Categories table (separated — 3NF)
CREATE TABLE categories (
    id INT PRIMARY KEY AUTO_INCREMENT,
    category_name VARCHAR(50) UNIQUE NOT NULL
);
```

## How It Works

1. **Start with all data in one table** (unnormalized)
2. **Apply 1NF** — make all values atomic
3. **Apply 2NF** — remove partial dependencies
4. **Apply 3NF** — remove transitive dependencies
5. **Create relationships** — use foreign keys to connect tables

## Common Mistakes

1. **Over-normalizing** — sometimes a little redundancy is OK for performance
2. **Forgetting foreign keys** — normalized tables MUST be connected with foreign keys
3. **Storing calculated data** — don't store things you can calculate (like age from birthdate)
4. **Mixing concerns** — one table should represent one entity

## Practice

- [ ] Take an unnormalized table and convert it to 1NF, 2NF, and 3NF
- [ ] Draw an ER diagram for the Bayanihan Hub database
- [ ] Identify transitive dependencies in a sample table
- [ ] Write CREATE TABLE statements for a 3NF schema
- [ ] Explain 1NF, 2NF, and 3NF in your own words

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[MySQL]]
- [[Bayanihan Hub]]
- [[Incident Monitoring System]]
- [[Software Engineering]]
