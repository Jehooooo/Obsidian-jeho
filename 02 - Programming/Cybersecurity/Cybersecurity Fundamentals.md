---
tags: [learning, cybersecurity]
topic: Cybersecurity Fundamentals
category: Security
---

# 🔒 Cybersecurity Fundamentals

## What Is It?

Cybersecurity is the practice of **protecting computer systems, networks, and data from unauthorized access, attacks, and damage**. As a software developer, you need to know how to build secure applications that protect your users' data.

## Why Is It Important?

- **Protect your users** — your projects handle user data (emails, messages, personal info)
- **SQL injection** — your MySQL-based projects must prevent this
- **Authentication security** — login systems must be built correctly
- **Career advantage** — security-aware developers are highly valued
- **Legal responsibility** — data breaches have legal consequences

## Syntax / Concepts

### Common Vulnerabilities

**1. SQL Injection**
```python
# ❌ VULNERABLE — never do this!
query = f"SELECT * FROM users WHERE email = '{user_input}'"

# ✅ SAFE — use parameterized queries
cursor.execute("SELECT * FROM users WHERE email = %s", (user_input,))
```

**2. Cross-Site Scripting (XSS)**
```javascript
// ❌ VULNERABLE — inserting user input directly into HTML
element.innerHTML = userInput;

// ✅ SAFE — use textContent or sanitize input
element.textContent = userInput;
```

**3. Password Storage**
```python
# ❌ NEVER store plain text passwords
password = "user_password"  

# ✅ ALWAYS hash passwords
from werkzeug.security import generate_password_hash, check_password_hash
hashed = generate_password_hash("user_password")
is_correct = check_password_hash(hashed, "user_password")
```

### Security Best Practices

1. **Never trust user input** — validate and sanitize everything
2. **Use HTTPS** — encrypt data in transit
3. **Hash passwords** — never store plain text passwords
4. **Use environment variables** — never hardcode secrets
5. **Principle of least privilege** — give users only the access they need
6. **Keep dependencies updated** — outdated packages have known vulnerabilities

### Environment Variables
```python
# ❌ Bad
SECRET_KEY = "my-super-secret-key-123"
DB_PASSWORD = "password123"

# ✅ Good
import os
SECRET_KEY = os.environ.get('SECRET_KEY')
DB_PASSWORD = os.environ.get('DB_PASSWORD')
```

## Example

```python
# Secure login endpoint for Flask
from werkzeug.security import check_password_hash
from flask import request, jsonify

@app.route('/api/login', methods=['POST'])
def login():
    data = request.get_json()
    email = data.get('email', '').strip()
    password = data.get('password', '')
    
    if not email or not password:
        return jsonify({"error": "Email and password required"}), 400
    
    # Parameterized query (prevents SQL injection)
    cursor.execute("SELECT * FROM users WHERE email = %s", (email,))
    user = cursor.fetchone()
    
    if not user or not check_password_hash(user['password_hash'], password):
        # Don't reveal whether email exists (prevents enumeration)
        return jsonify({"error": "Invalid credentials"}), 401
    
    # Create session/token (don't expose sensitive data)
    return jsonify({
        "message": "Login successful",
        "user": {"id": user['id'], "name": user['name'], "role": user['role']}
    })
```

## Common Mistakes

1. **Storing passwords in plain text** — always hash with bcrypt or werkzeug
2. **SQL injection** — always use parameterized queries
3. **Exposing sensitive data** — never send password hashes or secrets to the frontend
4. **Committing `.env` files** — add `.env` to `.gitignore`
5. **Not validating input** — always check data types, lengths, and formats

## Practice

- [ ] Identify SQL injection vulnerabilities in a sample code and fix them
- [ ] Implement password hashing in a Flask registration endpoint
- [ ] Create a `.env` file and load secrets with `os.environ`
- [ ] Review one of your projects for security vulnerabilities
- [ ] Learn about CORS and why it matters for your React + Flask setup

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Flask Basics]]
- [[MySQL]]
- [[Software Engineering]]
- [[REST APIs]]
