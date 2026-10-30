---
tags: [learning, flask, python]
topic: Flask Basics
category: Backend Development
---

# 🔧 Flask Basics

## What Is It?

Flask is a **lightweight Python web framework** for building web applications and APIs. It's called a "micro-framework" because it gives you the essentials and lets you add what you need — unlike Django, which comes with everything built-in.

Flask is what powers the backend of your Bayanihan Hub and Incident Monitoring System projects.

## Why Is It Important?

- **Your backend framework** — used in your active projects
- **Beginner-friendly** — simple to learn, powerful enough for production
- **Python-based** — leverages your Python knowledge
- **REST API development** — perfect for building APIs that React connects to
- **Flexible** — add only the extensions you need

## Syntax / Concepts

### Basic Flask App
```python
from flask import Flask, jsonify, request

app = Flask(__name__)

@app.route('/')
def home():
    return "Hello, World!"

@app.route('/api/status')
def status():
    return jsonify({"status": "running", "app": "Bayanihan Hub"})

if __name__ == '__main__':
    app.run(debug=True)
```

### Routes and Methods
```python
# GET — retrieve data
@app.route('/api/items', methods=['GET'])
def get_items():
    return jsonify(items)

# POST — create data
@app.route('/api/items', methods=['POST'])
def create_item():
    data = request.get_json()
    # Process and save the data
    return jsonify({"message": "Item created"}), 201

# PUT — update data
@app.route('/api/items/<int:item_id>', methods=['PUT'])
def update_item(item_id):
    data = request.get_json()
    # Update the item
    return jsonify({"message": "Item updated"})

# DELETE — remove data
@app.route('/api/items/<int:item_id>', methods=['DELETE'])
def delete_item(item_id):
    # Delete the item
    return jsonify({"message": "Item deleted"})
```

### Connecting to MySQL
```python
import mysql.connector

def get_db_connection():
    return mysql.connector.connect(
        host='localhost',
        user='root',
        password='',  # XAMPP default
        database='bayanihan_hub'
    )

@app.route('/api/users')
def get_users():
    conn = get_db_connection()
    cursor = conn.cursor(dictionary=True)
    cursor.execute("SELECT id, name, email, role FROM users")
    users = cursor.fetchall()
    conn.close()
    return jsonify(users)
```

### Error Handling
```python
@app.errorhandler(404)
def not_found(e):
    return jsonify({"error": "Not found"}), 404

@app.errorhandler(500)
def server_error(e):
    return jsonify({"error": "Internal server error"}), 500
```

### CORS (for React frontend)
```python
from flask_cors import CORS
app = Flask(__name__)
CORS(app)  # Allow React to call your API
```

## Example

```python
# Incident reporting API endpoint
from flask import Flask, jsonify, request
from datetime import datetime

app = Flask(__name__)

@app.route('/api/incidents', methods=['POST'])
def create_incident():
    data = request.get_json()
    
    # Validate required fields
    required = ['title', 'location', 'cause']
    for field in required:
        if field not in data:
            return jsonify({"error": f"Missing field: {field}"}), 400
    
    # Create incident (in real app, save to database)
    incident = {
        "title": data['title'],
        "location": data['location'],
        "cause": data['cause'],
        "status": "Pending",
        "created_at": datetime.now().isoformat()
    }
    
    return jsonify({
        "message": "Incident reported successfully",
        "incident": incident
    }), 201

if __name__ == '__main__':
    app.run(debug=True, port=5000)
```

## How It Works

1. Flask listens for **HTTP requests** on specified routes
2. Each route has a **view function** that handles the request
3. The function processes the request and returns a **response**
4. Flask converts Python dictionaries to **JSON** with `jsonify()`
5. React sends requests to Flask, Flask processes them and sends back data

## Common Mistakes

1. **Forgetting CORS** — React can't call your API without CORS enabled
2. **Not using `debug=True`** — you won't see helpful error messages
3. **SQL injection** — always use parameterized queries, never string concatenation
4. **Not closing database connections** — leads to connection pool exhaustion
5. **Returning wrong status codes** — 200 for success, 201 for created, 400 for bad request, 404 for not found

## Debugging Tips

- **Check the terminal** — Flask prints request logs and errors
- **Use Postman or Thunder Client** — test your API endpoints before connecting React
- **Print request data** — `print(request.get_json())` to see what React is sending
- **Check CORS errors** — look for CORS errors in the browser console

## Practice

- [ ] Create a basic Flask app with a home route that returns "Hello, World!"
- [ ] Build a REST API with GET and POST endpoints for a simple resource
- [ ] Connect Flask to a MySQL database and read data
- [ ] Build a login endpoint that checks username and password
- [ ] Test your API endpoints using Postman or Thunder Client

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Python Basics]]
- [[REST APIs]]
- [[MySQL]]
- [[React Basics]]
- [[Bayanihan Hub]]
- [[Incident Monitoring System]]
