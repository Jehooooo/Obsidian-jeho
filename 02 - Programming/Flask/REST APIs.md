---
tags: [learning, rest-api]
topic: REST APIs
category: Backend Development
---

# 🔌 REST APIs

## What Is It?

A REST API (Representational State Transfer Application Programming Interface) is a way for **different software systems to communicate** over the internet using HTTP. It's how your React frontend talks to your Flask backend.

Think of it like a waiter at a restaurant: your frontend (the customer) places an order (request), the API (the waiter) takes it to the kitchen (backend), and brings back the food (response).

## Why Is It Important?

- **How frontend talks to backend** — React sends requests, Flask responds with data
- **Universal standard** — almost every web application uses REST APIs
- **Your projects need it** — Bayanihan Hub and Incident Monitoring System both use REST APIs
- **Career essential** — every software engineer works with APIs

## Syntax / Concepts

### HTTP Methods

| Method | Purpose | Example |
|--------|---------|---------|
| **GET** | Read/retrieve data | Get all donation items |
| **POST** | Create new data | Submit a new incident report |
| **PUT** | Update existing data | Update incident status |
| **DELETE** | Remove data | Delete a post |
| **PATCH** | Partial update | Update just the status field |

### Status Codes

| Code | Meaning | When to Use |
|------|---------|-------------|
| 200 | OK | Successful GET/PUT |
| 201 | Created | Successful POST |
| 400 | Bad Request | Invalid input data |
| 401 | Unauthorized | Not logged in |
| 403 | Forbidden | Logged in but not allowed |
| 404 | Not Found | Resource doesn't exist |
| 500 | Server Error | Something broke on the server |

### JSON — The Data Format
```json
{
    "id": 1,
    "title": "Flooding at Main Building",
    "status": "Pending",
    "location": "DMMMSU-SLUC Main Building",
    "created_at": "2026-09-15T10:30:00"
}
```

## Example

### Flask API Endpoint
```python
@app.route('/api/incidents', methods=['GET'])
def get_incidents():
    incidents = get_all_incidents_from_db()
    return jsonify(incidents), 200

@app.route('/api/incidents', methods=['POST'])
def create_incident():
    data = request.get_json()
    new_incident = save_incident_to_db(data)
    return jsonify(new_incident), 201
```

### React Calling the API
```javascript
// GET request
const fetchIncidents = async () => {
    const response = await fetch('http://localhost:5000/api/incidents');
    const data = await response.json();
    setIncidents(data);
};

// POST request
const createIncident = async (incidentData) => {
    const response = await fetch('http://localhost:5000/api/incidents', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(incidentData)
    });
    const result = await response.json();
    return result;
};
```

## How It Works

1. Client (React) sends an **HTTP request** to a URL (endpoint)
2. Server (Flask) receives the request and processes it
3. Server queries the **database** if needed
4. Server sends back a **JSON response** with a status code
5. Client receives the response and updates the UI

## Common Mistakes

1. **Wrong HTTP method** — use GET to read, POST to create, PUT to update
2. **Not sending `Content-Type: application/json`** — the server won't parse your data
3. **Not handling errors** — always check response status codes
4. **Hardcoding URLs** — use environment variables for API base URLs
5. **Returning wrong status codes** — 200 for everything is wrong

## Debugging Tips

- **Use Postman** — test APIs without building a frontend first
- **Check the Network tab** — see requests, responses, and errors in browser DevTools
- **`console.log` the response** — make sure you're getting what you expect
- **Check Flask terminal** — see incoming requests and server errors

## Practice

- [ ] Build a Flask API with GET and POST endpoints for managing items
- [ ] Test your API using Postman or Thunder Client
- [ ] Write React code to fetch data from your Flask API
- [ ] Handle 404 and 400 errors properly in your API
- [ ] Add authentication (token or session) to an API endpoint

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Flask Basics]]
- [[JavaScript Basics]]
- [[React Basics]]
- [[MySQL]]
