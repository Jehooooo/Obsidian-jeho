---
tags: [learning, mongodb, database]
topic: MongoDB
category: Databases
---

# 🍃 MongoDB

## What Is It?

MongoDB is a **NoSQL document database** that stores data as flexible JSON-like documents instead of rigid tables with rows and columns. Unlike MySQL where you define a strict schema first, MongoDB lets you store data with different structures in the same collection.

Think of MySQL as a spreadsheet (fixed columns), and MongoDB as a filing cabinet where each folder can contain different types of documents.

## Why Is It Important?

- **Portfolio project** — your AI Knowledge Platform may use MongoDB for conversations
- **Flexible schema** — great for data that doesn't fit neatly into tables
- **JSON-native** — data format matches what JavaScript/React already uses
- **Scalable** — designed for large-scale applications
- **Modern stack** — used in MERN (MongoDB, Express, React, Node) and similar stacks

## Syntax / Concepts

### Documents and Collections
```javascript
// A document (like a row in MySQL, but flexible)
{
    "_id": ObjectId("..."),
    "name": "Jeho",
    "email": "jeho@example.com",
    "skills": ["Python", "React", "Flask"],
    "projects": [
        { "name": "Bayanihan Hub", "status": "In Progress" },
        { "name": "Portfolio", "status": "Planning" }
    ]
}
// A collection = a group of documents (like a table)
```

### CRUD Operations
```javascript
// CREATE
db.users.insertOne({ name: "Jeho", email: "jeho@example.com" });

// READ
db.users.find({ name: "Jeho" });
db.users.find({ role: "Admin" }).sort({ created_at: -1 });

// UPDATE
db.users.updateOne(
    { name: "Jeho" },
    { $set: { role: "Admin" } }
);

// DELETE
db.users.deleteOne({ name: "Jeho" });
```

### Python with MongoDB (PyMongo)
```python
from pymongo import MongoClient

client = MongoClient("mongodb://localhost:27017/")
db = client["portfolio"]
conversations = db["conversations"]

# Save a chat message
conversations.insert_one({
    "session_id": "abc123",
    "messages": [
        {"role": "user", "content": "Tell me about Jeho"},
        {"role": "ai", "content": "Jeho is a CS student..."}
    ]
})

# Get conversation history
history = conversations.find_one({"session_id": "abc123"})
```

## Example

```python
# MongoDB for the AI Knowledge Platform
from pymongo import MongoClient

client = MongoClient("mongodb://localhost:27017/")
db = client["portfolio_db"]

# Store knowledge base entries
knowledge = db["knowledge_base"]
knowledge.insert_one({
    "category": "education",
    "title": "CS Background",
    "content": "3rd-year BS Computer Science at DMMMSU-SLUC",
    "tags": ["education", "personal"]
})

# Search knowledge base
results = knowledge.find({"tags": "education"})
for doc in results:
    print(doc["title"], "—", doc["content"])
```

## When to Use MongoDB vs MySQL

| Use MongoDB When | Use MySQL When |
|-----------------|----------------|
| Flexible/varied data | Structured, relational data |
| Rapid prototyping | Data integrity is critical |
| Storing JSON documents | Complex JOINs needed |
| Chat/conversation logs | Financial transactions |
| Content management | E-commerce orders |

## Common Mistakes

1. **Using MongoDB for relational data** — if your data has lots of relationships, MySQL is better
2. **Not creating indexes** — queries get slow without indexes on frequently queried fields
3. **Storing everything in one document** — documents have a 16MB size limit
4. **Not validating data** — MongoDB doesn't enforce structure, so validate in your application

## Practice

- [ ] Install MongoDB and create a database
- [ ] Insert, read, update, and delete documents
- [ ] Use PyMongo to connect Python to MongoDB
- [ ] Store and retrieve conversation messages
- [ ] Practice queries with filters and sorting

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[MySQL]]
- [[Portfolio]]
- [[JavaScript Basics]]
- [[Flask Basics]]
