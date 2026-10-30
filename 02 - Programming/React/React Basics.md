---
tags: [learning, react, javascript]
topic: React Basics
category: Frontend Development
---

# ⚛️ React Basics

## What Is It?

React is a **JavaScript library for building user interfaces**. Created by Facebook (Meta), it lets you build web apps by creating **reusable components** — small, self-contained pieces of UI that you combine together like LEGO blocks.

Instead of building one massive HTML page, you build small components (`Header`, `UserCard`, `DonationList`) and compose them together.

## Why Is It Important?

- **Most popular frontend library** — used by Facebook, Instagram, Netflix, Airbnb
- **Component-based** — promotes reusable, maintainable code
- **Strong job market** — most frontend developer jobs require React
- **Your projects use it** — Bayanihan Hub and Incident Monitoring System are React apps
- **Rich ecosystem** — React Router, state management, thousands of component libraries

## Syntax / Concepts

### Components (Functional)
```jsx
// A simple component
function Welcome({ name }) {
    return <h1>Hello, {name}!</h1>;
}

// Arrow function component
const ProjectCard = ({ title, status }) => {
    return (
        <div className="card">
            <h2>{title}</h2>
            <span>{status}</span>
        </div>
    );
};
```

### JSX — HTML in JavaScript
```jsx
// JSX lets you write HTML-like code in JavaScript
const element = <h1 className="title">Hello, Jeho!</h1>;

// Use {} to insert JavaScript expressions
const greeting = <p>You have {projects.length} projects</p>;

// Conditional rendering
const status = isLoggedIn ? <Dashboard /> : <LoginForm />;
```

### useState — Managing State
```jsx
import { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);
    
    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
        </div>
    );
}
```

### useEffect — Side Effects
```jsx
import { useState, useEffect } from 'react';

function UserList() {
    const [users, setUsers] = useState([]);
    const [loading, setLoading] = useState(true);
    
    useEffect(() => {
        // Runs when component mounts
        fetch('/api/users')
            .then(res => res.json())
            .then(data => {
                setUsers(data);
                setLoading(false);
            });
    }, []); // Empty array = run once on mount
    
    if (loading) return <p>Loading...</p>;
    
    return (
        <ul>
            {users.map(user => (
                <li key={user.id}>{user.name}</li>
            ))}
        </ul>
    );
}
```

### Props — Passing Data to Components
```jsx
// Parent passes data via props
function App() {
    return (
        <ProjectCard 
            title="Bayanihan Hub" 
            status="In Progress"
            tech={["React", "Flask"]}
        />
    );
}

// Child receives props
function ProjectCard({ title, status, tech }) {
    return (
        <div>
            <h2>{title}</h2>
            <p>Status: {status}</p>
            <p>Tech: {tech.join(", ")}</p>
        </div>
    );
}
```

## Example

```jsx
// A donation list component for Bayanihan Hub
import { useState, useEffect } from 'react';

function DonationList() {
    const [donations, setDonations] = useState([]);
    const [error, setError] = useState(null);
    
    useEffect(() => {
        fetch('/api/items')
            .then(res => {
                if (!res.ok) throw new Error('Failed to fetch');
                return res.json();
            })
            .then(data => setDonations(data))
            .catch(err => setError(err.message));
    }, []);
    
    if (error) return <p className="error">{error}</p>;
    
    return (
        <div className="donation-list">
            <h2>Available Donations</h2>
            {donations.length === 0 ? (
                <p>No donations available.</p>
            ) : (
                donations.map(item => (
                    <div key={item.id} className="donation-card">
                        <h3>{item.title}</h3>
                        <p>{item.description}</p>
                        <span className="status">{item.status}</span>
                    </div>
                ))
            )}
        </div>
    );
}

export default DonationList;
```

## How It Works

1. React creates a **Virtual DOM** — a lightweight copy of the real page
2. When state changes, React compares the Virtual DOM to the real DOM
3. React only updates the **parts that actually changed** — this is fast!
4. Components **re-render** when their state or props change
5. Data flows **one-way** — from parent to child via props

## Common Mistakes

1. **Modifying state directly** — always use `setX()`, never `x = newValue`
2. **Missing `key` prop** — every item in a list needs a unique `key`
3. **Infinite useEffect loops** — forgetting the dependency array causes infinite re-renders
4. **Not handling loading/error states** — always show loading and error states for API calls
5. **Prop drilling** — passing props through many levels; consider Context or state management

## Debugging Tips

- **React DevTools** — Chrome extension that lets you inspect component state and props
- **Console** — `console.log` inside components to trace renders
- **Check the Network tab** — verify API calls are returning expected data
- **Key warnings** — if React warns about missing keys, add `key={item.id}` to list items

## Practice

- [ ] Create a simple counter component with useState
- [ ] Build a component that fetches and displays data from an API
- [ ] Create a form component with controlled inputs (useState for each field)
- [ ] Build a todo list app with add, delete, and complete functionality
- [ ] Practice passing props between parent and child components

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[JavaScript Basics]]
- [[HTML and CSS]]
- [[REST APIs]]
- [[Flask Basics]]
- [[Bayanihan Hub]]
