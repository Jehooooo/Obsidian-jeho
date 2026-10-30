---
tags: [learning, mysql, database]
topic: MySQL
category: Databases
---

# 🗄️ MySQL

## What Is It?

MySQL is a **relational database management system (RDBMS)** that stores data in organized **tables** with rows and columns. You interact with it using **SQL** (Structured Query Language). MySQL is one of the most popular databases in the world, used by Facebook, Twitter, YouTube, and millions of other applications.

Think of a database as a super-organized spreadsheet that your application can read, write, and search through instantly.

## Why Is It Important?

- **Your projects use it** — Bayanihan Hub and Incident Monitoring System both use MySQL
- **Industry standard** — used in most web applications
- **SQL is universal** — SQL skills transfer to PostgreSQL, SQLite, SQL Server
- **Data integrity** — enforces rules to keep your data consistent and clean
- **XAMPP integration** — easy to set up for local development

## Syntax / Concepts

### Creating Tables
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    role ENUM('Admin', 'Staff', 'Community Member') DEFAULT 'Community Member',
    verified BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    title VARCHAR(200) NOT NULL,
    description TEXT,
    category VARCHAR(50),
    status ENUM('Available', 'Claimed', 'Removed') DEFAULT 'Available',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
```

### CRUD Operations
```sql
-- CREATE
INSERT INTO users (name, email, password_hash) 
VALUES ('Jeho', 'jeho@email.com', 'hashed_password');

-- READ
SELECT * FROM users WHERE role = 'Admin';
SELECT name, email FROM users WHERE verified = TRUE;

-- UPDATE
UPDATE items SET status = 'Claimed' WHERE id = 5;

-- DELETE
DELETE FROM items WHERE id = 10;
```

### JOINs
```sql
-- Get items with their donor's name
SELECT i.title, i.status, u.name AS donor_name
FROM items i
JOIN users u ON i.user_id = u.id;

-- Get unread messages for a user
SELECT m.content, u.name AS sender
FROM messages m
JOIN users u ON m.sender_id = u.id
WHERE m.receiver_id = 1 AND m.read = FALSE;
```

### Useful Queries
```sql
-- Count items per category
SELECT category, COUNT(*) as count 
FROM items GROUP BY category;

-- Search items by keyword
SELECT * FROM items 
WHERE title LIKE '%laptop%' OR description LIKE '%laptop%';

-- Get recent items with pagination
SELECT * FROM items 
ORDER BY created_at DESC 
LIMIT 10 OFFSET 0;
```

## Example

```sql
-- Complete schema for a simple donation system
CREATE DATABASE bayanihan_hub;
USE bayanihan_hub;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    role ENUM('Admin', 'Community Member') DEFAULT 'Community Member',
    verified BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    title VARCHAR(200) NOT NULL,
    description TEXT,
    category VARCHAR(50),
    condition_state VARCHAR(50),
    status ENUM('Available', 'Claimed', 'Removed') DEFAULT 'Available',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE messages (
    id INT AUTO_INCREMENT PRIMARY KEY,
    sender_id INT NOT NULL,
    receiver_id INT NOT NULL,
    content TEXT NOT NULL,
    is_read BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (sender_id) REFERENCES users(id),
    FOREIGN KEY (receiver_id) REFERENCES users(id)
);
```

## Common Mistakes

1. **SQL injection** — never concatenate user input into SQL. Use parameterized queries.
2. **Not using foreign keys** — without them, your data has no integrity
3. **`SELECT *` in production** — only select the columns you actually need
4. **Not indexing** — add indexes to columns you frequently search or JOIN on
5. **Forgetting WHERE in UPDATE/DELETE** — this affects ALL rows!

## Debugging Tips

- **Use phpMyAdmin** (comes with XAMPP) — visual tool to see your database
- **Test queries in phpMyAdmin first** — before using them in Flask
- **Check for typos in column names** — SQL error messages usually tell you which column
- **Use `DESCRIBE tablename`** — to see the structure of a table

## Practice

- [ ] Create a database with two related tables (users and items)
- [ ] Write CRUD queries for both tables
- [ ] Write a JOIN query that combines data from two tables
- [ ] Practice GROUP BY to count items per category
- [ ] Write a parameterized query in Flask to prevent SQL injection

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Database Normalization]]
- [[Flask Basics]]
- [[REST APIs]]
- [[Bayanihan Hub]]
- [[Incident Monitoring System]]
